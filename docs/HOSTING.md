# Hosting and connecting

## Content delivered by a hosted world

The tool-only download excludes original client assets. Browser-hosted play is
different: the world host sends imported game assets and generated tables to
players' browsers. Supplying files for the host does not mean each remote player
supplies those files. Account/invite controls, private storage and HTTPS do not
establish permission to transmit the content. Review the applicable client terms
and permissions before enabling access for other people.

Local setup needs no coding or command-line work after copying the engine folder
into a compatible updated installation and confirming Start. Internet hosting
still requires provider/relay, private data, storage and HTTPS configuration.

## Native launcher: host or connect

Open `Client.exe`. **Hosting options** selects a separate world with its own accounts and characters. Choose **Invite only** or **Open (accounts required)**, a server name, and the first host account credentials. That host account receives GM permission; players who sign up receive ordinary permission. Invite mode also needs a different server password. Open mode has no server password and does not automatically publish the server.

**Connect** checks the selected game API before showing its native account panel. Enter the invite password only for invite servers, then use **Sign up** to create an account there. Enter that server's account credentials and choose **Launch client** or **Launch browser**. Both buttons authenticate before opening the game through a 45-second, single-use handoff; passwords and cookies never appear in URLs. Account signup/login remain required on open servers. Each additional client uses a separate account and isolated browser profile. Chrome or Edge must be installed.

The launcher remembers the selected local/remote host and supported relay preferences, not account passwords. A saved remote destination is verified asynchronously and opens its remote dashboard; **Local world** selects local play again. The host dashboard can open another client and stop the owned world. Stop and dashboard close save progress before shutdown; they do not kill unrelated listeners. Keep the host/dashboard running while players connect. If an existing owned server belongs to an older engine generation, restart through the launcher so the updated code actually runs.

Host accounts, characters and rates stay separate from local 7777 play. A compatible game host reports protocol 1 and its current name/content/rates. A static connector is not a world server. Restart the host after code or content updates. LAN/private VPN addresses work only where reachable; plain HTTP is limited to private-network connections.

## Managed HTTPS relay and IP privacy

For Internet play, select **Online relay (managed HTTPS)** in hosting options, enter the managed HTTPS relay hostname and select the private cloudflared token file. The owner must already control the provider account, named tunnel and hostname. The launcher verifies the relay against the selected owned engine before opening it, keeps the backend on loopback, and stops only its own relay. It does not configure router/firewall rules, purchase hosting, allocate DNS or silently create a provider account.

The authenticated relay gateway removes forwarded player-IP headers before requests reach the game server, assigns an opaque rate-limit key, and blocks launcher/private discovery endpoints from public access. Players receive the relay hostname, not the backend/home address. This assumes the host uses the relay and does not expose its origin separately. Merely giving a direct server an ordinary DNS name does not hide its IP. Direct peer-to-peer/LAN/VPN connections cannot guarantee hidden peer addresses; the network/provider still sees the connections it carries.

A quick tunnel is a temporary test/preview path: its hostname can change, it has provider limits, and it is not a named production deployment. Quick-tunnel connections negotiate polling on world join instead of attempting unsupported SSE; normal direct/named paths retain SSE. This changes snapshot transport, not movement rules or gameplay timing. A managed named relay is the supported launcher configuration for a stable public address. Temporary public proofs do not establish permanent hosting availability.

TLS protects traffic in transit. It cannot hide a user's own browser traffic, code or packets from that user. Supported gameplay actions remain server-authoritative, with session/lease checks, command receipts, stale-input rejection and ordinary gameplay validation. This is not a claim that every cheat or denial-of-service attack is impossible.

## Opt-in open server directory

Only **Open** servers may select **List publicly (Open only)**. Enter the operator's HTTPS directory root after the managed relay is ready. Publication is a separate opt-in; invite servers never appear. The directory accepts only explicitly approved HTTPS relay hostnames, verifies the host's publication-secret proof and current open/protocol/content status, and evicts unhealthy or opted-out worlds. The public list includes name, relay URL, connected-player count and rates, not passwords, account stores or backend/home addresses.

The native public-server panel uses the operator's HTTPS directory address; `DEKARON_DIRECTORY_URL` can prefill it. Selecting a listed world still rechecks that host and requires its account signup/login. No central directory is hardcoded. An operator must deploy and configure the directory before this list is available.

From the clean engine directory, the directory operator can start a loopback listener for an HTTPS reverse proxy:

```powershell
$env:DEKARON_DIRECTORY_TOKEN = (node -e "process.stdout.write(require('node:crypto').randomBytes(32).toString('hex'))")
$env:DEKARON_DIRECTORY_RELAY_HOSTS = 'world.relay.example'
$env:HOST = '127.0.0.1'
$env:PORT = '7790'
node tools/start-directory.mjs
```

Replace the example hostname with exact provider-owned relay hostnames the operator has approved; comma-separate multiple names. No wildcard or default allowlist is provided. Keep the operator token private. Optionally set `DEKARON_DIRECTORY_CONTENT_VERSION` to require a particular content generation. Put this listener behind HTTPS; do not publish its loopback HTTP address as the directory URL.

`GET /api/servers` is the safe public list. Hosts register themselves through the launcher using a publication proof; no global directory admin token is given to players or hosts. The owned publisher heartbeats every 30 seconds and removes its registration when stopped. Health failures/opt-out are detected on refresh. Directory entries currently live in memory; publishers re-register after a directory restart. The directory stores no accounts and does not relay the game itself.

## Static connector: Vercel or Cloudflare Pages

The static connector contains no original game assets or accounts. It checks a compatible game host's limited public status and opens that host; account signup/login stay on the chosen game server.

- Vercel: deploy only the clean release's `engine/web` directory. Framework **Other**; the included `vercel.json` serves `public`. No install/build command is needed.
- Cloudflare Pages: upload `web/public`, or use that folder as output with `exit 0` as the build command.
- Other static hosts can serve the same `web/public` directory.

An actual Vercel static deployment and compatible public-host connection have been verified. A permanent directory and managed named production relay have not been deployed by this project. An HTTPS portal cannot fetch an insecure LAN host cross-origin; its private-network connector navigates to that host instead. Public Internet addresses must use HTTPS. The portal does not collect host passwords or merge characters between servers.

References: [Vercel configuration](https://vercel.com/docs/project-configuration/vercel-json), [Cloudflare static HTML](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/).

## Persistent Docker, Railway or Render world

Use the audited tool-only release as source. Keep personal stores and original client files out of public repositories. The Docker entrypoint maintains one world under `/state`; privately provide your compatible Global `data` folder at `/state/data`. Original files are not bundled in the image. First startup imports the files; later startup reuses unchanged generations. Updates preserve the private volume.

First-start cloud templates initialize an invite world by default. Set `DEKARON_HOST_MODE=open` to initialize an Open world with account login and no invite password. Initial name and rates are saved with the private host configuration, so removing bootstrap settings does not discard them. Changing the bootstrap mode after initialization does not silently change an existing world's admission policy.

| Setting | Value |
| --- | --- |
| `DEKARON_HOST_ACCOUNT` | First host/GM ID |
| `DEKARON_HOST_MODE` | `invite` (default) or `open`; first initialization only |
| `DEKARON_HOST_PASSWORD` | Unique 12–128 character host password |
| `DEKARON_INVITE_PASSWORD` | Different 12–128 character invite password; invite mode only |
| `DEKARON_SERVER_NAME` | World name |
| `DEKARON_EXP_RATE`, `DEKARON_DIL_RATE`, `DEKARON_DROP_RATE` | Optional 0.1–100 multipliers; default 1 |

Existing stored host accounts are not reset on restart. Remove initial credential environment secrets after setup. Nonempty runtime rate settings override saved rates; remove or leave those optional fields blank to use the saved configuration. The Compose template allows bootstrap credentials to be removed after initialization; a fresh world still validates the required credentials before account creation. Keep one replica per world: file-backed accounts and the simulation are not a replicated database. Back up the private volume with the world stopped. Provider TLS deployments enable `DEKARON_SECURE_COOKIES=1`; standalone HTTPS reverse proxies need this setting too. Arbitrary forwarded headers do not establish trust.

- Railway: deploy the Dockerfile, attach a persistent volume at `/state`, privately populate client data, set secrets and generate HTTPS access. See [Docker deployment](https://docs.railway.com/builds/dockerfiles) and [volumes](https://docs.railway.com/volumes).
- Render: use the included `render.yaml`, provision its persistent disk, privately populate `/state/data`, set secrets and restart. See [Blueprints](https://render.com/docs/blueprint-spec) and [persistent disks](https://render.com/docs/disks).
- Own Docker host: provide `private-host/data`, set environment values, run `docker compose up --build -d`. The template binds localhost; configure an appropriate HTTPS proxy/relay. `docker compose stop` permits graceful saves.

These are templates, not preauthorized provider deployments. Billing, storage, private data transfer and HTTPS setup belong to the owner. The persistent world has not been deployed to Railway/Render by this project. Vercel's static connector does not run the ticking world or file-backed account store. Verify resource requirements on the chosen host; a local 52-account benchmark is not a cloud/browser/GPU capacity guarantee.

Bring your own compatible client files. This package does not establish permission to redistribute or publicly serve proprietary content; review the terms that apply to your own deployment.
