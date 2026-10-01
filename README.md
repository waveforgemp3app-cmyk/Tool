**[Download Alpha 1.0.1 — normal ZIP, no password](https://github.com/waveforgemp3app-cmyk/Tool/releases/tag/v1.0.1-alpha.1)**

# Dekaron Engine — Alpha 1.0.1

**Normal ZIP download — no archive password required.** Extract the ZIP before running anything. This package contains accessible engine source/runtime files and Client.exe; it is not another SFX wrapper.

## Setup in three steps
1. Fully update your compatible Global client, close the game/updater, and keep a separate full backup.
2. Extract Dekaron-Engine-Alpha-1.0.1.zip. Put its complete engine folder beside your data and bin folders, then open engine/Client.exe.
3. Review the cleanup warning, click Start, let preparation finish, then sign up or use the local owner sign-in option. Choose the desktop client or browser.

**Existing users:** stop your server and back up accounts, saves, settings and projects before replacing engine code. This ZIP is a manual package, not the old managed SFX installer. Do not delete private state to force an update; use a separate fresh client folder if unsure.

Windows PowerShell/.NET Framework and Chrome or Edge are required. A compatible Node.js 20+ is reused or a pinned official runtime is downloaded over HTTPS and SHA-256 checked. Three.js is included. First preparation can take several minutes.

## Changes in this patch
- Added server-wide world chat with a cooldown; /global maps to world and /map maps to map-wide shout.
- Improved first-person target selection with bounded aim assistance.
- Added one bounded retry for transient auto-attack range rejection while the same live target remains selected.
- Adjusted enhancement highlights toward warm gold and strengthened the shimmer.
- Repaired the Battle Support Start/Cancel handler and prevented its loop from interrupting a busy skill. Full panel skill assignment and in-game acceptance remain under review; this is not a claim that all Battle Support options are complete.
- Rebuilt Client.exe and provided a normal ZIP for users unable to extract the SFX.

## Verification for this package
Launcher compilation, runtime download/hash and failure-path tests, 37 installer fixture checks, preparation/reuse checks, three validate-only launcher location smoke cases, signup tests, targeting/retry tests, and world-chat/mail/guild tests passed. Guild tests verify supported existing behavior, not every Global guild feature.

The 1,276-file payload and extracted ZIP passed manifest/hash and privacy scans. Private accounts, local host configuration, logs, original game data and caches are excluded. Known machine/owner identifiers and credential patterns were checked. This is a bounded audit, not an absolute privacy guarantee.

**No new full clean-install-to-rendered-game acceptance run was performed for this ZIP.** Earlier Alpha 1.0 installer results do not count as tests of this new package. Remaining visual, mount, Battle Support and gameplay reports still need in-game acceptance; zero lag and complete Global parity are not promised.

SHA-256 (checksum, NOT a password):
`3294fc3e556430fc84f09d73d5a156416cc87ad1460db1b7112857080e85f0e9`

## Play in first person or third person

- Switch between the normal third-person camera and optional first-person view with a configurable field of view and remappable POV binding.
- First person presents your equipped native body, arms and weapons, retaining their original animation data. On-foot legs follow the view heading without changing server movement or attack authority. Mounted presentation keeps the native rider/seat relationship.
- Skill and buff effects remain connected to the local presentation. TransUp hides incompatible wings and restores them afterward.
- Mounted first person retains native vehicle/seat geometry and holstered equipment. Switching views reuses its prepared presentation. TransUp uses native hands/forearms with a separate body view to avoid oversized shoulder armor filling the camera.
- Warm golden enhancement waves repeat every few seconds while leaving base armor and weapon detail visible between peaks. Lower enhancement families retain their source appearance.
- Full eligible weapon sockets produce blade-shaped, pulsing native-color auras. Fire, ice, lightning, poison and curse retain their original effect selections. Full stat-stone sockets use the native default effect through a labeled reconstructed presentation policy; empty and partial sockets do not receive a full-socket aura.
- Selection scenes, gameplay equipment and cached inventory previews share the refinement material policy. Enhancement highlight math and blade-shaped aura coverage are reconstructions, not a claim of exact original-executable rendering.
- Character framing, animated equipment, native UI artwork/fonts, supplied map/model/texture data, available sounds, scenery fog flags and normal distance/frustum culling are supported.

## A shared world with server-owned gameplay

Create separate accounts and characters on each server, then play in the same world. Supported movement, targeting, combat, skills, equipment, inventory and progression are validated by the server rather than accepted as client-written results.

- First click selects an enemy; a second click starts an attack. Skills cancel auto-attack. Out-of-range targeted skills approach their bound target, then cast when the authoritative position reaches range; manual movement, target death and map changes cancel the pending action.
- Auto-attacks now check server-confirmed player and monster positions before stopping the chase or sending a hit. This repairs attacks rejected as out of range while the predicted model appears beside the monster. Held movement also retains its bounded prediction through delayed updates instead of repeatedly tugging backward.
- Repeated NPC clicks preserve the active route. Approaches stop before dialogue or the first attack swing. Nearby pickups avoid an unnecessary fallback movement jump.
- Idle monsters now explore using native walking speed, home radius and rest timing, with collision checks. Combat return remains separate; stationary objects, traps and protected boss patterns do not acquire roaming routes.
- Supported quests, loot, shops, item boxes, equipment enhancement and conversion, storage and server-table rewards.
- Parties, durable trade, supported mail/attachments, guild creation and membership, notices, funds, donations, explicit supported guild level-up and private guild chat.
- Companion pets, following/autoloot/bags/options/blessings and supported awakening, combination, appearance, restoration and disassembly services.
- Transport mounts, summon/dismiss preparation and riding/map/skill checks; authoritative fishing, profession crafting and DekaPass progress/claims.
- Isolated dungeon runs and available native dungeon/event adapters, including supported cooperative Dead Front and Ice Castle behavior. Individual scripts, phases and rewards still have documented limits.

## GM Command Center

Authorized GMs can open the searchable Command Center with **F10** or **/GM**. Search locates tools, tabs and commands without executing them.

- **Commands:** original command syntax/help and supported command controls.
- **Monsters:** searchable catalog, model previews, original drop lookup, supported spawning, kill/respawn and AI controls.
- **Items:** searchable catalog/spawner, owned-item editing, box contents and original item previews.
- **Teleport/NPCs:** map, destination, NPC and minimap lookup with server-validated safe arrival.
- **Character:** supported level/EXP/DIL/D-Shop allocations, stats/reset, grade points, skills/buffs, heal/revive, permitted GM flags and renaming.
- **Players:** live map markers, filters, selection, zoom/pan and supported selected-player operations.
- **Inventory:** authorized online/offline inspection and supported transfers involving equipment/presets, inventory, personal stash, cash and supported storage, with binding/capacity/concurrency checks.
- **Quests/World/Drops:** supported quest operations, drop inspection, notices, player counts and moderation; local time/weather/sky/music and visual inspection tools have their stated scope.
- **Tools:** model viewer, UI window browser, performance/debug geometry, event log, position and save tools. Local save editing is not an online progression import path.
- **GM fly camera:** detach from the standing character, inspect with WASD/QE, Shift and mouse look, then return. This does not grant avatar noclip.

GM access comes from the authenticated server account. Ordinary accounts see the POV binding without GM/editor controls. The server checks privileged requests independently of visible UI; editing browser HTML cannot grant server privileges. Revocation, disconnect and server replacement clear stale capabilities and private tool state. The installation owner can grant/revoke permitted roles through the protected Accounts controls.

## Item Builder

Search, use or clone catalog definitions and edit General, Stats, Options and Look pages:

- Names/descriptions, kind/slot/rank, class masks, requirements, prices, stacks, trade flags, bag footprint, sockets and supported rolled spawn options.
- Damage/defense/PvP fields, range/speed/critical, upgrade level, HP/MP use and lifetime; six base options, seven additional options and supported set-bonus selection.
- Per-class model/material/texture, second-hand model, inventory model/icon, supported action tables and explicit asset keys.
- Character/model previews, class/animation selection, turn/zoom and definition detail.
- Save, clone, spawn, equip and project export/import, with server-controlled custom definitions and validated asset limits.
- Supported rigid textured GLB attachments, including Meshy-compatible imports, with axes/scale/transform/tint controls and geometry/material inspection. Arbitrary skinned armor and automatic retargeting are not supported. Adding a data field does not implement an otherwise unsupported game mechanic.

## Map Builder

Create blank or source-map projects and use terrain, objects, spawns, NPCs and portals from one editor:

- 64/128/256/512 terrain sizes; project save/open/resize, .dkmap import/export, minimap capture and local play preview.
- Move/rotate/scale, duplicate/delete, multi-selection, shared gizmos, inspector properties, surface/grid snapping and undo/redo.
- Raise/lower/smooth/flatten/noise/vertex-color terrain brushes with radius/strength/falloff controls and useful presets.
- Ground types/variants, holes/fill, texture decals, water placement and visibility, and collision painting.
- Searchable object and monster libraries, NPC service selection and original/published portal destination pickers.
- Grid/collision overlays, terrain texture sets, lighting/sky, clipping distance, time/music, level gates and return-scroll policy.
- Validated custom-map publication, revisions and restart persistence. Supported occupied custom-map updates use version checks, collision/placement updates and safe relocation; active gameplay transactions can refuse an unsafe update.
- Keyboard/mouse free-fly and first-person inspection. **Xbox-style controller support is for Map Builder only**, with navigation/tool mappings and focus/disconnect guards; it is not advertised as gameplay controller support.

Original-map editing and shared brush sessions have their own documented constraints; do not assume every custom-map operation is available for native fields. Export browser-local drafts before clearing browser data.

## Inventory and quality-of-life improvements

- Cached inventory previews, transient asset retry, held-item feedback, readable native gem symbols and equipment-comparison tooltips.
- Three-socket weapons and four-socket staffs/large hammers use centered vertical gem columns; eligible four-socket armor keeps its centered 2×2 arrangement. Empty sockets remain empty holes.
- Owned-stack potion/buff belt use, native cooldown sweeps and save/relogin handling.
- One-, two- and three-row skill layouts; the buff HUD now uses all three native skill rows instead of dropping entries after ten. Supported status icons can be repositioned within remembered bounds.
- Hotbar weapon and native TransUp-stage requirements grey unavailable skills, while learned skills retain color when only MP is short. Activation skills remain available before the required transformed action mode.
- Native weapon swapping and alternate layouts retain cast restrictions. Character-name colors/lengths, overhead text and numeric monster HP received targeted checks.
- Nearby authored architectural gates/trees remain visible under the corrected occlusion handling. Original return-to-character/login flows and GM Save & Stop Server are retained.
- Edit Current remains open during temporary world-busy synchronization instead of treating it as a lost login; real permission or session loss still closes privileged tools.


## Feedback and documentation
Bug reports are welcome—please include your version, class, skill/item and reproduction steps. I appreciate the feedback and will investigate reports. Never include credentials or account files.

[Feature catalog](https://github.com/waveforgemp3app-cmyk/Tool/blob/main/docs/FEATURES.md) · [Tool gallery](https://github.com/waveforgemp3app-cmyk/Tool/tree/main/docs/showcase)

Independent project, not affiliated with the original publisher. Bring your own compatible client data. Original game assets are not distributed; third-party notices remain applicable.
