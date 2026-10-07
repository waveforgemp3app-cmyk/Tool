# Dekaron Online — One Client & Engine

**1-Click Installer • Full Release • Multiplayer • GM Tools • Item & Map Builders**

**Current release: 2.2.3 Update.** This page always describes the newest build, the latest changes and the full feature list. The complete fix history of every version is in [CHANGELOG.md](CHANGELOG.md).

## Download

- **[Download Dekaron-2.2.3.zip (GitHub, latest release)](https://github.com/waveforgemp3app-cmyk/Tool/releases/latest)** — no password.
- Source (plain files, for inspection): `Dekaron-2.2.3-source.zip` on the same release page.
- [VirusTotal scan (Dekaron-2.2.3.zip)](https://www.virustotal.com/gui/file/ec5d4475cedcb68828f5031433ba7e81f322884a19d830df4de6e40ff74f22cd)
- [VirusTotal scan (Dekaron-2.2.3-source.zip)](https://www.virustotal.com/gui/file/d6956e65dfd9729a489a0aeafcc059a8f87e888b956e284b01811cd6397a1fef)

**VirusTotal (full details)**
- VirusTotal at upload (2026-10-07): 5 of 65 engines flag the installer zip, 5 of 63 the source zip. Flagged by: Bkav Pro, Elastic, Malwarebytes, MaxSecure, SentinelOne (Static ML) (installer); Bkav Pro, Elastic, Malwarebytes, MaxSecure, SentinelOne (Static ML) (source). No engine names a malware family: the labels are generic machine-learning scores ("MachineLearning/Anomalous", "susgen", "Suspicious Archive"). Microsoft, Kaspersky, ESET and BitDefender report nothing.
- Likely reasons (not proven): unsigned executables with no publisher and no real version info; every build is a new file with no reputation; a launcher that starts PowerShell scripts, a local server and a local port looks like a dropper to heuristics; the installer is a compressed self-extracting archive; the source zip shows the scripts as plain text. The cause is not established.
- Check it yourself: the source zip has the same files as plain text, the installer carries exactly those files, and the SHA-256 values in the table match the scan pages.

| File | SHA-256 |
|---|---|
| `Dekaron-2.2.3.zip` (installer + README, no password) | `ec5d4475cedcb68828f5031433ba7e81f322884a19d830df4de6e40ff74f22cd` |
| `Dekaron-2.2.3-source.zip` (plain engine files, for inspection) | `d6956e65dfd9729a489a0aeafcc059a8f87e888b956e284b01811cd6397a1fef` |

Download the release file, not GitHub's automatic "Source code" ZIP. The ZIP contains the engine only — no official game files, no accounts, no database to install. It reads the data from **your own, fully updated Dekaron Global installation**.

### Install in 1 click

1. Install and fully update your Dekaron Global client. Close the game and the official updater. **Back up the whole game folder.**
2. Extract `Dekaron-2.2.3.zip`. Inside are **RUN-ME-FOR-GAME.exe** and **README.txt**.
3. Run **RUN-ME-FOR-GAME.exe**, confirm your game folder (the Dekaron folder containing `data` and `bin`, not either subfolder), click **Start** and confirm the setup prompt.
4. The first preparation reads your game data (a few minutes, once). A **Dekaron Online** desktop shortcut is created — from then on just double-click it.

Already installed? Open the launcher and click Start — a ready installation launches straight away.

> **Important:** the first setup cleans the game folder root and keeps only `data`, `bin`, `engine` and `Client.exe` (the official launcher/updater is removed) and creates no backup. The launcher shows the exact list and asks you to confirm. If preparation fails nothing is deleted. Keep your own backup.

**Requirements:** Windows 10/11, Chrome or Edge, and your updated Global client. The DX11 Client uses the Microsoft Edge WebView2 Runtime (part of Windows 11). Node.js is used if you already have it; if not, the launcher downloads its own private copy automatically (checksum-verified, no admin rights, nothing added to your system PATH).

## 2.2.3 - Faster First Start

The last update of the 2.x line. It has one change: the preparation of the client data that runs on the first start after an install or an update now runs its steps in parallel. The game itself is unchanged.

### Loading

- **First start after an install or update:** The preparation used to take about 5 minutes (315 seconds on my PC) because its 21 steps ran one after another. Steps that do not depend on each other now run at the same time: the same preparation took 77 and 89 seconds in two runs on a 6-core PC with 32 GB of RAM (3.5 to 4 times faster; a PC with fewer cores gains less). The prepared files are identical to what the old order produced: compared file by file, every byte is the same except the time stamps inside 17 of the 57 data files.
- **How many steps run at once:** up to 4, fewer on a PC with fewer than 5 cores, and at most 2 on a PC with less than 6 GB of RAM (4 at once used up to 3.8 GB of memory on my PC). Set the environment variable `DEKARON_PREPARE_JOBS` before starting the launcher to choose another number; `DEKARON_PREPARE_JOBS=1` runs the steps one after another as before.
- **Safe on errors:** if one step fails or you close the launcher, all running steps are stopped before anything is cleaned up, and the previously prepared data stays in place.
- **One more preparation after updating:** the preparation program itself changed, so every install prepares once after updating to 2.2.3 (about 1.5 minutes now).
- **Changes to the channel files are noticed:** the preparation did not look at the channel rule files (`channel-data.mjs`, `channel-rules.js`), so editing them did not rebuild the prepared data. It does now.

## 2.2.0 (2026-10-04)

- **DX11 Client (Dekaron.exe):** The game opens in its own native window, Dekaron.exe, drawn through Direct3D 11 (Microsoft WebView2 host). It only opens after you sign in through the launcher and then signs you in by itself. It opens at 1280 x 720; a resolution applied in Options sizes the window and is remembered (F11 = fullscreen). Task Manager and the volume mixer list it as Dekaron.exe.
- **Launcher:** Three labelled ways to play on the sign-in panel and the dashboard: DX11 Client, Desktop App and Web Browser. "Other server..." opens another server with the same three choices. Closing the game returns to the dashboard.
- **Login:** All three go straight to the login hall (no loading screen) with the server button ready; Server Login enters with your launcher sign-in, no password asked again. The LOGIN SELECT window shows the server logo.
- **Smooth monsters:** Monster positions are played back on the server's own clock (measured with ~96 monsters: freezes mid-move 1.9 % of frames -> 0, biggest jump 7.93 -> 0.70).
- **Lag spikes:** First switch to first person 865 ms -> ~45-65 ms; summoning a mount in first person 418 ms -> ~45 ms; Trans Up 400-880 ms -> ~30-40 ms (shaders are prepared when the map loads).
- **Shield:** Full shield when you log in and when you respawn.
- **Dungeons:** One broken dungeon in the original files (181) could crash the whole server; now only that dungeon closes and its players are moved out.
- **Holy Water of Almighty:** Remote mailbox, remote storage and the remote shop work while the service is active; the enhancement bonus (+5 %, not above +11), EXP / DIL / drop scrolls, Party Warp and the Battle helper Potion Set follow the item text. NPC warp from the map needs the premium service (otherwise you walk there); the Deka Pass premium track follows the Global rules. GMs can set VIP Points.
- **Custom maps:** Ordinary players can enter a server's published custom maps (`/custommap`, the M map list, the Custom Maps NPC).
- **Disk space:** Desktop game windows no longer leave their throw-away browser profiles behind (16 GB had piled up).

## Older updates

<details>
<summary><b>2.2.2</b> (2026-10-07, shipped inside 2.2.3)</summary>

Bug Fix Update (2026-10-07): Ctrl field PK with a per-server switch, the Half Bagi Fury skills, deleting characters, a per-server starter pack switch, teleport quests that landed in the map corner (Parca Temple, Requies Beach, Avalon), Sergio's Swift Box, party members on the minimap, Guild of Glory emblems, the DIL / EXP chat lines, and the Personal Shop seller no longer moving. The full notes are in [CHANGELOG.md](CHANGELOG.md).

</details>

<details>
<summary><b>2.2.1</b> (2026-10-07, shipped inside 2.2.2)</summary>

Latency and Frames Update #1 (2026-10-07): lower ping and lag in big fights, much higher frame rate in towns, instant loading, auto attack hitting on every swing, summons and attack effects seen by other players, a frame pacer for the Max FPS options. The full notes are in [CHANGELOG.md](CHANGELOG.md).

</details>

<details>
<summary><b>2.1.2</b> (built 2026-10-04, shipped inside 2.2.0)</summary>

- **Fresh install:** The local admin gets the 15 max-level showcase characters. Existing admin characters are never touched.
- **Emotes:** The Action list plays the first emote and the same emote twice in a row; armed characters and GMs no longer have their emote cancelled by the combat stance; a refused emote (dead, fishing, casting, riding) says why in chat.
- **Battlefields on a normal install:** Arena, DK Square, Training Camp, Race, channels and the observer read the prepared client data (they could fail with "Shared world is temporarily unavailable").
- **Personal shop:** The window can be dragged by its title bar again; the Shop Name box sits inside its own frame.
- **Black Wizard orbs:** Orbs with a left-hand model show both orbs and keep orbiting while running and on the character screen (the orbit while running is engine-chosen).
- **Global updates:** A client table saved with a byte-order mark no longer breaks the rebuild.
- **Gem glow:** The 1-4 gem brightness steps from 2.1.1 are removed: the game data has no per-gem-count rule, so any socketed weapon shows its authored effect.
- **GM teleport:** Ctrl+click teleport works online (ground, Teleport-tab minimap, Players-tab map) and keeps working after other GM commands. The HUD minimap no longer teleports.
- **Map window (M):** Each NPC row has Add / Del (favorite) and Move for everyone, TP for admin / GM accounts; event NPCs show an EVENT tag.
- **First person:** All 15 classes reworked: weapons that were out of view while standing (Incar and Summoner staffs, others) are visible, oversized ones (Azure Knight sword + shield, Trie Muse) no longer fill the screen, the Segita Hunter bow sits at the hand, and the Black Wizard's coat sleeve no longer sweeps across the view. Framing values are engine-chosen / fitted (the game has no first-person view).
- **Tab weapon swap in first person:** The weapon lowers, swaps and comes back up (about 1 second; engine-chosen, the data has no swap animation).
- **Shield:** The awakening grade adds its shield amount.
- **Character and D-Shop previews:** No longer dim (the preview light levels are engine-chosen).
- **Launcher:** The "List your server publicly?" warning opens with Cancel selected instead of all its text highlighted.

</details>

<details>
<summary><b>2.1.1</b> (2026-10-03)</summary>

- **Aura glow:** Glowing weapons and refined gear cast a soft coloured halo in the world and in the character preview window, hidden behind walls. Built like the client's own glow and blur pass; radius and strength are fitted to Global screenshots (FITTED, not read from the data).
- **Icon halo:** Inventory and equipment icons get the wide soft "ghost" halo seen on Global.
- **Effects through walls:** Gem glow and sparkles no longer show through walls (measured 66,768 stray pixels down to 4).
- **Refinement orbs:** The +15 / refinement texture scroll no longer jumps back at every loop (largest per-frame jump 0.30 down to 0.003).
- **Battle Support (Auto Hunt):** The window is back with its real panel art, tabs, close button and radius dropdown (8 / 12 / 16 is engine-chosen). Some option boxes and slot buttons stay inactive because no data says what they do.
- **Damage numbers online:** PvP blocks show the Block word, heal and MP numbers show, crit and block hit sparks play, and basic attacks can crit on the server using your Critical Rate. Yellow numbers are critical hits.
- **Exact movement speed:** The server no longer caps speed to 1-6 units/s; buffs and slows match the game data (about 0.7 to 7.9), so speed buffs no longer rubber-band. Covered by a test of 28,980 class x buff combinations.
- **Saved logins:** "Save account" keeps a server-issued token (never your password) on your PC under Windows protection, bound to that one server. Accounts are per server.
- **Public server list:** Listing your server asks first with a clear warning and records your consent; a Settings switch turns it on or off without stopping the relay, plus a directory address box and a connection test. The project does not run a public directory.
- **Host IP protection:** Hosting is relay-only by default (no LAN address is shown or copied); a direct host listens on this PC only until you tick "Allow direct LAN connections". The relay gateway limits 24 connections per address and the directory limits list requests to 60 a minute. Four setup buttons (On this PC / VPS / Vercel / Cloudflare) write step-by-step guides; they deploy nothing. No relay is a DDoS shield by itself.
- **Launcher tabs:** One tidy grid in the top right: Dashboard, Accounts, Sign up / Hosting, Worlds, Settings.
- Checked, no change needed: Ardeca's pixelated textures are the map data's own nearest-pixel filtering; item sizes follow the game data (bows 2x4, starter Short Bow 1x3, shields 2x3, Dual Blades 1x4); GM Items +11 to +15 exist where the item family goes that high.

</details>

<details>
<summary><b>2.1.0</b> (2026-10-03)</summary>

- **Refinement glow:** +7 / +9 / +15 armor and weapons glow in their tier colour (+15 purple) in the world and on the character screen, with a slow pulse and a tier-coloured edge light. Colours come from the original tier textures; the rim light and pacing are ENGINE-CHOSEN.
- **Socket gems colour the weapon:** elemental gems give a glow and mist in the gem's colour in your hands, on the inventory icon and on the character screen.
- **Auto-attack on moving monsters:** the character keeps chasing until the swing's hit frame will still reach the monster, then lands the hit — no more repeated swings without damage.
- **D-Shop:** pages, tabs and the Wings catalog no longer open empty; pictures fill in as they finish and the next pages are prepared while you browse. Other windows are built in idle time, so panels open almost instantly.
- **Download:** a normal ZIP (RUN-ME-FOR-GAME.exe + README.txt) plus a separate `-source.zip` with the engine files as plain files.
- **Launcher:** first-time setup on PCs without Node.js hardened (the "AppendText" error at 8 % can no longer stop setup).
- **Inventory:** refined weapons (+7 and up) glow in their tier colour in the inventory; gem weapons show the glow as an outer aura so the texture stays visible.
- **HUD:** removed a stray crossbow-icon counter that duplicated the buff bar.

</details>

<details>
<summary><b>2.0.0 — Full Release</b> (2026-10-02)</summary>

- Colosseum, Siege War, DK Square, Arena and the event modes completed (see Features).
- PvP damage reads all 22 Global PvP option codes (it used 6).
- Guild storage / skills / board / rankings / alliances, messenger chat, chat item links, party finder, inspect, character trade, name change, personal shops, consignment, coin shops, wing services, skill master.
- Attendance and connect rewards, DK channels, multi-channel, per-map caps, request / exchange quests, production lists, option-change tables, costume upgrade.
- Visuals checked against the original formulas: materials, textures, terrain brightness, fog, LOD and view distance, wing animation speed, tooltip and HUD colours. Socket gems use the original effect textures, colours and pulse keys.
- Correct inventory sizes and socket layouts for every weapon and shield; HP / MP potion icons fixed.
- Auto-attack stops and attacks as soon as a moving monster is in range; smoother walk / run loops.
- Compressed game-data/map responses, versioned caching, background image decoding, progress reporting; server performance improved in the tested 52-player scenarios.
- New native launcher (Dashboard, Worlds, Hosting, Settings, server name on the HUD, instant admin sign-in after a restart); safer first-time installer cleanup.
- Final 2.0 fixes: Alokes and Trie Muse hand attachment points; inventory / F-slot swaps keep the displaced item on the cursor; costume removal and owner shutdown countdown; Blitz checks the caster's hidden state; a bounded ENGINE-CHOSEN contact allowance (0.5 map cell for 600 ms, once) for normal attacks on moving monsters; natural shield capacity from arithmetic recovered from a legacy server executable with the current Global class coefficients (monster damage bypasses the PvP shield); six top-left HUD buttons in two rows; inventory enhancement previews use the original effect scenes.

</details>

Earlier builds (Release Candidate 2 and 3, Alpha 1.0 / 1.0.1) are recorded in [CHANGELOG.md](CHANGELOG.md).

## Features

A complete alternative engine, client and server for Dekaron. Play solo, host your own shared world for friends, or join someone else's server — plus a full GM panel, an Item Builder and a Map Builder. It uses **native Global data** for classes, skills, items, monsters, maps, quests, shops, events and PvP. Where the data does not establish a rule or renderer behaviour, the reconstruction is documented and tagged `ENGINE-CHOSEN` (or `FITTED` when fitted to Global screenshots). The remaining items and limits are listed below. This is not a claim of complete original-executable parity.

### Client

- Three ways to play, all signed in from the launcher: **DX11 Client** (Dekaron.exe, its own native window), **Desktop App** or **Web Browser**. Straight into the login hall, no password asked twice.
- Native launcher with Dashboard, Accounts, Sign up, Hosting, Worlds and Settings, live server status and player counts. Start your own world with one click, host it for friends, or connect to a saved server. **Auto-sign in as local admin** on your own installation; "Save account" tokens for other servers.
- Original login scene, loading screens, character select and create screens with their native maps, framing and animated weapons; all 15 classes with their native models, equipment, animations, skills, skill trees, masteries and trans-up.
- Optional first-person view next to the normal third-person camera (B switches, remappable), tuned for all 15 classes.
- Rendering from the data: materials from the original boneanimation / itemmesh / glow shader formulas, each map's own texture filtering, fog and lighting from every map's light file, terrain and sky from the geometry / skybox shaders, authored object fog flags, bloom values per map. Refinement tier glow, gem-coloured weapon mist and the soft aura on glowing gear, hidden behind walls.
- Loading: tables, map textures/meshes and window art prepared while you are at login / character select; compressed responses and versioned caching.

### World and gameplay

- Server-owned movement, targeting, combat, skills, items, inventory, loot, quests and progression — the server validates what you do. Exact movement speeds from the animation clips; monsters smooth on the server clock; no rubber-banding tested at 0-300 ms lag.
- Quests, shops, D-Shop and coin shops, item boxes, enhancement, sockets and gems, option changes, production, crafting and fishing; correct item footprints and socket layouts from the data.
- Parties, party finder, Expedition (3 corps x 7, troop dungeons), durable trade, mail with attachments, messenger chat, world / shout / super chat, chat item links, emotes shared online.
- Guilds with storage, 72 guild skills, guild board, rankings, alliances, guild war and guild tournament.
- Pets (follow, auto-loot, bags, options, awakening), mounts and wings (upgrade and shape change), costumes (Transcendence, options, wardrobe).
- Dungeons and events: Dead Front, Ice Castle, Forgotten Shipwreck roulette, Wanted, Egutt, attendance and connect rewards, Deka Pass.
- DK channels, multi-channel, per-map level and ability caps, native map data, terrain, scenery, lighting, fog and sound; published custom maps enterable by everyone on the server.
- Premium / Holy Water of Almighty: Select Warp, Return Point, NPC warp, remote mailbox / storage / shop, EXP bonuses, Party Warp, enhancement bonus, Battle helper Potion Set, Deka Pass premium track.

### PvP and battlegrounds

- **Colosseum** — 16-player Battle Royale (16 > 8 > 4 > 2 > 1, champion and round rewards, B Point) and 2v2 Individual Match with MVP, matching, entry prompt, results and rankings.
- **Siege War (Zenoa Castle)** — registration, siege tunnels, guardian stones and pendants, empathy capture at Juto, castle ownership, gate fortification, tax ledger.
- **DK Square** — lobby team PvP (Miseria vs Ricchez) with battlefield HUD and results. **Arena** — Draco Desert Battlefield (4 squads, Sunstone communion, DP tiers, rank board) and Lost Horizon (7-player team battle with stun / skill-lock / meteor stone objectives).
- Race, mission titles, PvP duels, party PvP, Party War (Dead Front / Ice Castle), guild war hunting, DKR PvP, observer mode, training camp. PvP damage uses all 22 Global PvP option codes.

### Tools

- **GM Command Center (F10 or /GM):** searchable panel with the original command syntax; level, EXP, currency, VIP Points, stats and skills tools; GM flags and moderation; monster and item catalogs with live previews (+11 to +15 items included), drops, spawning, item editing; map / NPC lookup, Ctrl+click teleports, live player map; inventory / storage inspection and transfers; quest and world controls, event logs, model and UI viewers, GM fly camera; owner controls for GM roles — permissions always checked by the server.
- **Item Builder:** create or clone items (names, slots, ranks, classes, requirements, prices, stacks, trade flags, damage / defense / PvP fields, options, set bonuses, sockets, upgrade values), per-class models and icons with animated previews, **GLB mesh import** (Meshy exports work) with axis / scale / transform / tint controls, save / spawn / equip, import / export projects.
- **Map Builder:** blank or existing-map projects, terrain 64 / 128 / 256 / 512, `.dkmap` import / export, minimap capture, live preview; raise / lower / smooth / flatten / noise / vertex-colour brushes, ground types, holes, decals, water, collision painting; objects, monsters, NPC services and portals with snapping, multi-select, gizmos and undo / redo; lighting, sky, view distance, time of day, music, level limits; publish to your live server with version and collision checks; free-fly and first-person inspection with **full Xbox-style controller support** (Map Builder only).

More detail: [Feature catalog](docs/FEATURES.md) · [Tool reference](docs/TOOLS.md) · [Hosting guide](docs/HOSTING.md) · [Shared world](docs/MULTIPLAYER.md) · [Preparing a client](docs/CLIENT-UPDATES.md) · [Tool gallery](docs/showcase)

## Hosting — play with friends

- **Your own world:** Start = your local world on this PC. Hosting options = a separate world with its own accounts, name and EXP / DIL / drop rates, Invite only or Open (accounts required). Friends create their own accounts on your server; accounts and characters belong to the server you pick.
- **Connect:** friends enter your server address (or pick it from a saved list), sign up there and launch. Hosting is relay-only by default and the launcher shows no home address; a direct host listens on this PC only until you tick "Allow direct LAN connections" in Settings.
- **Online relay:** the host connects outbound to a managed HTTPS relay you control (named Cloudflare tunnel + token); players get the relay address, never the host's. The relay gateway strips forwarded IPs and caps 24 connections per address.
- **Guided setup:** four buttons — On this PC / My own VPS / Vercel / Cloudflare — write step-by-step guides and files under `hosting-setup\`; they deploy nothing and create no accounts. Docker / Railway / Render templates and a static Vercel / Cloudflare Pages connector are included for a persistent server (see [HOSTING.md](docs/HOSTING.md)).
- **Public server list:** optional; it asks with a warning, records your consent, can be switched off in Settings without stopping the relay, and only lists on a directory address you set. The project runs no public directory.
- Closing the game returns to the dashboard while your server stays running; closing the owned-server dashboard or clicking Stop Server saves and stops it.

## Known limits

- Not in the client data, so not invented: the Forgotten Shipwreck team rules, what unlocks Type 9 titles, the weekly shield, several Battle Support (Auto Hunt) option boxes.
- First person: body / legs when looking straight down are still being worked on; framing is engine-chosen (the game has no first-person view).
- Premium Holy Water of Almighty extras (account-wide service, daily VIP Points, dungeon-ticket discount) are not built yet: some values are not in the game data.
- The dashboard "Server capacity" panel is not built yet (the server side works).
- No relay is a DDoS shield by itself; that comes from the provider. Hosting sends your imported client data to the people you let in — host only for friends who have their own lawful client.
- Values the data does not establish are tagged `ENGINE-CHOSEN` or `FITTED` in the code; this is not a claim of complete original-executable parity.
- PK: the Safe Time after a kill, the tendency window and the drop penalty on death are not built yet; the Ctrl window, the kill counting and the fading speed are ENGINE-CHOSEN.
- Trans Up skills of the Segita Shooter (Gracio), Trie Muse (Ramir) and Alokes (Zart): the game data has no transformation entries for them, so they are refused instead of inventing a look.

## Reporting problems

Open an [issue](https://github.com/waveforgemp3app-cmyk/Tool/issues) or reply on the forum thread. Include the class / map / skill / item, what happened and the exact error text. Blank out passwords, IP addresses, account names and personal file paths in screenshots and logs.

## Rights

Unofficial fan project, not affiliated with or endorsed by the game's publisher. You need your own legitimate Global client. No original game files are distributed. Third-party components keep their own licenses (see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and [DISTRIBUTION.md](DISTRIBUTION.md)).
