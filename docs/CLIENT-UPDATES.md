# Preparing an owner's Global client

## One-file installation and engine updates

The one-file download starts with `RUN-ME-FOR-GAME.exe`. Fully update a compatible Global client, close its updater, and keep a separate backup. Run the installer, select the detected installation, and confirm its cleanup warning. After successful preparation the game root contains `data`, `bin`, `engine` and `Client.exe`; the launcher creates the desktop shortcut. Do not point cleanup at an unrelated folder.

For an existing installation, stop the owned server and close its game windows before running the new installer. Managed installs and the verified complete RC3/base and RC3/installer-hotfix payloads are recognized. The update verifies the entire previous managed file set before replacing it, preserving private files and the supplied `data`/`bin`. Mixed or modified managed files are refused before replacement; this is not permission to delete private accounts/settings to force an update. Keep backups of private accounts, settings and builder projects until you verify the updated installation.

There is no unattended Internet engine updater. Installing a new engine download and re-preparing changed original client data are separate operations. The instructions below describe preparation after the engine is installed.

Keep `engine` beside the original `data` and `bin` directories. Open `Client.exe`; Install & Play / Start ensures a compatible runtime and runs `tools/prepare-client.mjs` before starting the server. It detects changed source files, builder code, format readers, and JSON overrides. An unchanged source skips rebuilding. Restart through the launcher after updating the original client.

The complete release includes Three.js. If Node.js is missing, `tools/client-runtime.ps1` downloads a pinned official Windows runtime, verifies both archive and executable SHA-256 hashes before execution, extracts only node.exe and its license and atomically promotes a private runtime directory. It changes no system installation or PATH. A failed download preserves existing runtime files and stops setup before game-folder cleanup.

Preparation uses Node alone. It supports the known uncompressed Global `pack.hdr` / `pack.dNN` layout and loose data containing `share/maplist.csv`. Packs take precedence over a stale `data/unpacked/data` extraction. `DEKARON_DATA` or `--data` selects an explicit loose data root. Unknown, incomplete, encrypted, or compressed pack formats fail with an error; no external unpacker is downloaded or launched.

Packed sources are extracted into a new `engine/.client-cache/generations` directory. Builders start with an empty index directory and generate the game indexes and website PNG art from the owner's files. Original packs, loose assets, and the existing `engine/gamedata` directory remain intact. The manifest switches to the new generation only after every builder and validation step succeeds. A failure removes the new staging directory and preserves the previous complete generation. Source changes during preparation also prevent publication.

The currently inspected client contains 190,246 packed files with about 8.82 GiB of extracted payload. Allow additional space for indexes, filesystem overhead, and retained previous generations. First preparation can take several minutes; later unchanged launches skip extraction. Previous generations are retained so a failed update cannot remove the last usable version.

Place intentional full-file JSON overrides under `engine/gamedata-overrides`, preserving their generated relative paths. They are copied after builders and included in update detection. Preparation never rewrites the override sources. Invalid JSON prevents publication.

`node tools/prepare-client.mjs --check` reports source, fingerprint, and whether preparation is needed without changing files. `--force` builds another complete generation. The server resolves generated data and website art through the selected manifest and disables stale data caching. Direct server startup does not perform preparation; use the launcher to apply source updates.

Fingerprints use source file sizes and filesystem timestamps, plus hashes of pack headers, parsers, builders, and overrides. This detects normal client patching; it is not a cryptographic authenticity check of every packed payload. Linked cache directories, manifests, and generations are rejected. Assets are generated locally for the owner's client; this workflow does not grant redistribution rights or publish game assets.
