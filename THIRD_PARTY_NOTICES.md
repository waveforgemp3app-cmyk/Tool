# Third-party notices

Three.js 0.170.0 is distributed under the MIT License. Its full notice is included in
`node_modules/three/LICENSE` and copied to `vendor/LICENSE` in tool-only releases.
Included Three.js add-ons retain their source notices.

If no compatible Node.js is installed, the launcher downloads a pinned official Node.js Windows runtime
from nodejs.org and verifies its SHA-256 checksum. Its upstream LICENSE is retained next to node.exe
inside engine/runtime. This private runtime is not included in the tool release.

Optional managed relay mode can download Cloudflare's cloudflared 2026.9.3 Windows
runtime from its official GitHub release and verifies the pinned SHA-256. The
runtime is excluded from the tool-only archive. Its upstream license is Apache
2.0: https://github.com/cloudflare/cloudflared/blob/2026.9.3/LICENSE
Release/source: https://github.com/cloudflare/cloudflared/releases/tag/2026.9.3
If redistributing the runtime itself, review and retain its applicable license,
notices and dependency notices; this tool notice does not replace those files.

The three PNG files in client-assets are newly generated launcher artwork, not extracted from the original
game client. The website connector includes a copy of the generated logo. Generation prompts are excluded
from the prepared download.

Original Dekaron client content is not included in a tool-only release. The game name and any locally loaded
client artwork, models, audio, fonts and text remain the property of their respective owners. This project does
not grant rights to those materials and is not an official or endorsed client.

No project-wide open-source license has been selected for the engine code. The project's owner must choose
the intended distribution/license terms and review code provenance before a public release.
