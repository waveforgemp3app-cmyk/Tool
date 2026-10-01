# Dekaron Engine — Alpha 1.0

**Bring your own compatible Dekaron client data. Build a world, play with friends, and create items and maps from the same Windows tool.**

Dekaron Engine is an independent engine reimplementation with a Windows launcher, desktop/browser client, shared-world server and integrated authoring tools. It reads supported data from your own client installation. Original game assets are not bundled. This project is unfinished and is not affiliated with the official game or publisher.

**[Download Alpha 1.0](https://github.com/waveforgemp3app-cmyk/Tool/releases/tag/v1.0.0-alpha.1)** · Archive: `Dekaron-Engine-Alpha-1.0.rar`

Archive password: `79576538508185188528157576021547`

SHA-256: `99089ae3d20e2bb8c4a3a4fa67e41ba14973825bd49ce35194f59f415d77f987`

## New installation — three steps to your own world

1. **Prepare your client.** Update your own supported Dekaron Global installation, close its updater, and back up the complete folder.
2. **Extract and run.** Extract the verified download using its supplied password, then open **RUN-ME-FOR-GAME.exe**.
3. **Confirm and play.** Confirm the detected folder and cleanup warning. Let preparation finish, then sign up or use the local owner sign-in option and open the game.

No coding or separate database installation is required for the local setup. **Preparation replaces the original launcher and removes unused files in the selected folder. Keep your backup outside that folder.** Hosting for friends requires the additional network and access setup described in the documentation. Supported installation layouts are checked; compatibility with every client build is not promised.

## Existing installation — update separately

1. **Back up first.** Keep a separate backup of your existing installation, accounts, characters, settings and builder projects. Close the client and stop its server before changing files.
2. **Run the new installer.** Extract the new release and open **RUN-ME-FOR-GAME.exe**. Select your existing game folder when prompted.
3. **Review, then restart.** Confirm the intended installation and update warning. The installer replaces verified engine files while retaining private accounts/settings and supplied data/bin. Reopen the launcher and check your characters before deleting the backup.

Managed installations and both verified RC3 download variants are recognized. Modified, mixed or unrecognized engine files are refused before replacement; do not delete your account files to force an update. First preparation or changed source data can take several minutes; unchanged prepared data is reused on later starts. The launcher installs a checked official Node.js runtime if needed; Chrome or Edge must already be available for the game window.

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

## What was checked

**One restored clean-install run passed using the exact downloadable installer. The owner has authorized this release and will perform the second acceptance test personally.** The installed flow checked folder discovery, original data/bin preservation, cleanup, desktop shortcut creation/recreation, local owner GM sign-in, a rendered game world, save/stop and repeat cached Start. These were scripted tests of the installed native launcher and isolated browser; physical mouse-click acceptance and an elevated administrator run are separate.

The payload, executable and extracted encrypted archive passed the privacy/manifest review. Incorrect passwords were rejected. No original game data, private accounts, host settings, chat logs or local runtime caches are bundled. Known-identifier scans are bounded checks, not a guarantee against every possible unknown identifier.

First-person checks include **15-class, 75-view full-body checks**, **135 mounted CPU cases across nine styles using the actual mount API**, six fresh native bike views, and 14 transformed views with separate weapon/body diagnostics. All 36 available native transformation meshes receive source-pose/clearance checks. Native weapon-style tests cover many class/style combinations, with declared-but-unwearable source cases recorded separately. These are bounded checks, not acceptance of every animation, every GPU or every client version. Of 599 source vehicle rows, 570 have native visual bindings; the 29 without bindings now refuse summoning instead of creating an invisible ride.

Focused tests cover source pose preservation, view/body heading, effects attachment, shader/material handling, native gear data, movement/skill cancellation, monster roaming, account persistence and permission enforcement. The CPU animation presentation benchmark excludes GPU rendering and asset loading; no zero-latency claim is made.

This remains an alpha project. Complete Global-client parity, every native server script, all PvP/PK/siege/rebirth rules, all mount visuals, unsupported services and universal instant loading are not promised. Known missing source references and remaining work are documented.

## Bug reports and feedback

Bug reports are welcome—post the details in this thread and I'll gladly investigate. I appreciate your comments and feedback! Include your release version, class, item or skill name, and the steps that caused the problem. A screenshot helps; please keep passwords, tokens, account files and personal information out of reports.

## Source, documentation and downloads

Project: https://github.com/waveforgemp3app-cmyk/Tool

The repository contains the feature catalog, tool references, setup/hosting guidance and remaining limits. Bring your own compatible client data; original meshes, textures, audio, private accounts and local configuration are not included in the public source package.



[Tool screenshots and gallery](https://github.com/waveforgemp3app-cmyk/Tool/tree/main/docs/showcase) · [Hosting guide](https://github.com/waveforgemp3app-cmyk/Tool/blob/main/docs/HOSTING.md) · [Feature catalog](https://github.com/waveforgemp3app-cmyk/Tool/blob/main/docs/FEATURES.md)

Third-party notices remain applicable. No project-wide open-source license or rights to the original game assets are granted by this download.
