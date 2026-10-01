# Dekaron Engine — feature and tool catalog

See [the complete tool reference](TOOLS.md) for every registered GM command and scripted builder control, with online availability and import limits.

Bring Your Own Client. Standalone RUN-ME-FOR-GAME.exe setup after updating and backing up your own client. No separate database server or database setup is required: accounts and world progress use the host's private local store.

This catalog describes the current development build. Alpha 1.0 publication follows final owner testing. A tool being listed does not mean all original game content is reproduced. Supported client formats, original data and the permissions of the connected server determine availability. Local presentation controls change your view; they are not shared world edits.

## Launcher, installation and accounts

- Animated launcher, Start/preparation progress, rounded controls, dedicated Sign Up and per-server Sign In.
- Standalone executable detects common game locations, with a folder-picker fallback; confirmation precedes installation and automatic preparation. Manual complete-engine adjacent installation remains available.
- Supported pack detection, automatic unpacking/preparation, verified runtime bootstrap, cached prepared generations and source-change detection.
- Explicit first-install target and deletion confirmation. Cleanup retains data, bin, engine and Client.exe; it deletes the original launcher/updater and other root entries. Back up the complete official installation yourself first.
- Desktop shortcut creation; repeated starts reuse current prepared data. Invalid or incomplete prepared generations do not qualify as ready.
- Local world dashboard, game launch choices, multiple account/client launches, server readiness checks, save/stop and installation-bound control verification.
- Native launcher signup/sign-in and website registration use the selected server's accounts. Successful signup clears fields. The sign-in panel and dashboard offer separate client and browser launch buttons.
- Installation-owner auto-sign-in for the protected local admin; no public default admin password. Ordinary accounts use their own credentials.
- One-use short-lived launch tickets, isolated app-window/browser entry, session replacement, saved logout and return to server selection.
- Server-authorized GM permissions. Signup fields, browser scripts and client saves cannot grant GM privileges.

## Hosting and connections

- Local Start; separate Host Friends world; saved host configuration; server name and EXP/DIL/drop rates.
- Invite-only or Open hosting. Separate invite password and account credentials; protected worlds cannot opt into the Open directory.
- Connect by permitted LAN/private-network or HTTPS address; verify server discovery and identify the selected server before signup/login.
- Per-server accounts, profiles, permissions, rates, custom items and maps.
- Signed-out server menu with current-world rates, manual address, configured open-directory search, Host and Help. Invite entry offers existing-account sign-in and server-local signup; logout returns here only after successful save/leave/signout.
- Browser launch and desktop app-window launch of the same renderer. This is not a separate native C++ game renderer.
- Local host dashboard stop/save lifecycle; remote dashboard cannot stop somebody else's server.
- Open-server directory client, host opt-in heartbeats and opt-out, compatibility filtering and revalidation before Join.
- Optional configured managed HTTPS relay and saved web-world connections. A static portal may be hosted separately; the persistent world requires a running Node host and storage.
- Provider, domain, TLS, relay token and firewall/network setup are separate configuration. No permanent shared public directory or relay is bundled as a managed service.
- Authentication for hosted game assets and listings, private revalidated caches and expired-session rejection. Hosting transmits imported assets; authentication is not a grant of distribution rights.

## Shared gameplay

- Registered-account characters, server-owned profiles, current-map players/monsters, live online count, reconnect and single-character leases.
- WASD/click movement with immediate local presentation, server collision/path validation and authoritative speed; walkable arrivals and field-map level gates.
- Monster spawning, combat/health/AI, attacks, death/respawn, EXP/DIL and supported loot rewards.
- Level progression, stat allocation, class limits, starter weapon/skill, learned hotbar assignments and starter/level-up boxes.
- Original quest requirements, NPC dialogue/accept/turn-in, kill/collect objectives, choices, original rewards and supported quest travel. Remaining scripted objective types are explicitly limited.
- Original SkillEngine, status effects and summons: supported skill learning/books, prerequisites, MP, cooldowns, combos, buffs, defensive effects, summon state and local/remote playback.
- Source-backed Meister paths, reinforcement, Grand Meister quest rewards and Trans Up stage/expiry. A rank does not invent missing skill or transformation rows.
- Personal bag, equipment/presets/weapon tabs, cash delivery, personal bank and account-shared item/DIL storage.
- Exact inventory destinations and stack metadata, held-item tooltips, ranked option lines/colors, drop confirmation, item use and boxes.
- Original NPC shops, ordinary D-Shop cart purchases, receipt/replay handling, supported reinforcement/sockets/branding/amplification/option/conversion services.
- Nearby player parties, invitations, leader/leave/kick, original party ratios, party chat, shared eligible kill progress/EXP and supported loot distribution.
- Two-player trade through `/trade Name`, original trade window, revised offers/dual confirmation, partial stacks and atomic item/DIL transfer.
- Normal/party chat, cross-map private whispers and same-map shouts with mute/recipient/cooldown checks.
- Mail compose/read/sent history/delete, offline delivery, separate one-time item/DIL claims, exact-metadata escrow, inbox privacy and original-window adapters. Current 100-DIL postage is an explicit engine policy; earned DekaPass overflow System mail is supported with atomic receipts; generic reward routing is not implied.
- Supported guild founding, invitations/accept/decline, notices, member roster, DIL funds, leadership transfer, kick/leave, zero-fund disband and private cross-map guild chat. Original donations and explicit level-up are supported; broader ranks/battles and funded disband remain limited.
- Supported crest insert/extract and preservation tools, original-table stone production/crushing with locks, talisman appearance transform/reset and wardrobe deposit/withdraw/move/equip/unequip/swap. Unresolved price/option results fail without consuming resources; other costume services and gifts are not covered.
- Transport-slot mounts, summon/dismiss preparation, map/skill/boarding checks and rider presentation.
- Companion pet eggs/follow/autoloot/bags/options/blessings; supported awakening; original-table combination, appearance, restoration and disassembly with persistent service timers.
- Authoritative fishing, profession crafting and DekaPass progress/claims; rewards derive from server tables.
- Isolated dungeon runs and available original dungeon/event directors, including cooperative Dead Front and Ice Castle adapters. This is not a claim that every native script, phase or reward is implemented.

## Presentation and controls

- Original supplied model/skeleton/animation/texture data, maps, native UI art/fonts, item colors and available sounds. Camera occlusion preserves authored walkable floor/stair meshes while normal distance/frustum culling remains enabled.
- Character selection uses authored class framing, selection animation timing and animated weapons. Scene changes wait for the requested backdrop; saved equipment enables supported refinement/socket effects. Showcase outfits do not acquire an invented upgrade grade. Missing assets in the supplied client can still leave gaps in a scene.
- Authored object fog flags are preserved for static and animated scenery, with separate cached materials and bounded visibility. This restores fog-disabled backdrops without disabling normal scene fog.
- Inventory still/rotation caching, visible fallback/held-item feedback and bounded asset work; transient fetch/decode failure recovery.
- Source-backed refinement and supported full-socket effects, original potion recovery particles and sound mappings, corrected effect timing/anchors and skill camera shake.
- Optional keyboard/mouse first-person view, configurable FOV and reversible third-person projection/body visibility.
- Default B switches POV; Settings → Change Controls can remap/unbind it. Typing, modal/loading/death/focus and held-key guards apply. No native first-person arms rig is supplied.
- Accepted movement tuning is retained. Controller support applies only to Map Builder.
- Original Escape/return-to-character/login flows and GM Save & Stop Server countdown.
- Exact native UI/audio/effect parity and universal instant loading are not promised. See the current acceptance checklist for remaining reference and hardware tests.

## Command Center and authoring

Type `/GM` as an authorized GM, or use F10. Top search finds tools, tabs and commands without executing them. There are Commands, Monsters, Items, Teleport, NPCs, Character, Players, Inventory, Quests, World, Drops, Builders and Tools tabs.

- Searchable original command syntax/help and command controls.
- Monster catalog, model preview, original drop lookup, server-supported spawning/kill/respawn and AI controls; local drop simulations are inspection tools.
- Item catalog/spawner, owned item editing, box contents and embedded original item previews.
- Teleport map/destination/NPC lookup and minimap coordinates, with authoritative safe arrival.
- Character level/EXP/DIL/D-Shop allocation, stats/reset, grade points, supported skills/buffs, heal/revive, permitted GM flags and player renaming.
- Live Players map with small selectable markers, filters/name list, 1–8x cursor-centered zoom, pan/reset and stable refresh/selection.
- Selected-player commands and GM read-only inspection of online/offline characters' inventory, equipment/presets, personal stash, cash and supported storage.
- Quest definitions, objectives, rewards, state and supported server quest operations.
- World and inspection controls for time, weather, sky, music, effect preview, performance, debug geometry and hidden UI; local view controls do not broadcast a world edit.
- Supported shared notices, player counts and moderation. Unconnected server commands report unavailable instead of silently mutating a local character.
- Model viewer, window browser, tunable inspection, event log, position and save tools. Local save export/import/edit is not an online progression import path.
- Permission revocation clears private panels/embedded builders and restores normal controls.
- Right Alt GM detached camera begins at the standing character; fly with WASD/QE, Shift boost and right-drag look. Press again to return. This does not give the avatar noclip.
- Top-right GM author shortcuts and mode controls. Builder access requires a fully loaded authorized game.

## Item Builder

- Search/use/clone original catalog items; General, Stats, Options and Look pages.
- Name/description, kind/slot/rank/spawn grade, class masks, price/sell value, stack size, trade flag, bag footprint, sockets and rolled spawn options.
- Level/stat requirements; melee/magic/ranged damage; defense, PvP fields, block/range/speed/critical, upgrade level, HP/MP use and lifetime.
- Six base options, seven additional options and set-bonus selection. A data field does not add unsupported gameplay mechanics by itself.
- Per-class equipped model/material/texture, second-hand model, inventory model/icon, supported action table and explicit asset keys.
- Model/character previews, class and animation selection, turn/zoom, current definition/slot/library detail.
- Save/clone/spawn/equip/export/import and server-controlled custom definitions/assets within validated limits.
- Meshy-compatible rigid textured GLB import for supported attachments, class/slot target validation, axes/scale/transform/tint controls and imported geometry/material inspection. Inventory imports preserve equipped animations. Embedded content is validated; arbitrary skinned armor and automatic retargeting are not supported.

## Map Builder

- Blank or source-map projects, 64/128/256/512 terrain sizes, project open/save/save-as/delete, resize, `.dkmap` import/export and minimap capture.
- Local play preview; refresh/open/publish validated server-map drafts; authenticated catalog/assets; ordinary-player entry; saved revisions and restart persistence.
- Select/move/rotate/scale, object placement/duplication/deletion, multi-selection with a shared gizmo/history entry, inspector properties and undo/redo. Surface snapping recognizes authored walkable helper floors.
- Raise/lower/smooth/flatten/noise/vertex-color terrain brushes; strength/radius/falloff/min-max controls; soft hill/valley/detail/smooth/plateau/paint presets.
- Ground type/variant, hole/fill, texture decals with size/rotation/erase, water definition/offset/erase and collision painting.
- Searchable object library/categories, original monster spawns, NPC placement and portal regions; searchable NPC/job and original/published portal destination pickers. Original NPC service associations are validated by the server.
- Grid snapping, grid/collision overlays, terrain texture set, lighting/sky, clipping distance, day length/fixed hour, music map, level gates, return-scroll policy and editing water visibility.
- Free-fly/first-person inspection and visible top-right controls; keyboard/mouse shortcuts and editor-only standard Xbox-style controller mapping.
- Controller sticks navigate/look; triggers change height; A builds/selects; B clears; X/Y undo/redo; shoulders choose tools; D-pad radius/nudge; View snap; R3 view; Menu frame. Dead zones and focus/disconnect/held-button guards prevent continued painting.
- Empty-map publication uses server validation and revision checks. Occupied-map replacement/shared live terrain editing remains unavailable pending safe scene/collision migration.
- Browser-local drafts should be exported before clearing browser data. Physical controller acceptance and large-project/remaining asset cases remain separate tests.

## Limits that remain visible

Do not advertise unavailable original server scripts, all PvP/PK/siege/rebirth rules, every social/life service, gifts/payments, all skinned effects, original-map live editing, unsaved brush streaming or universal client/update compatibility as complete. Mail/guild and advanced item-service operations are detailed in MULTIPLAYER.md; original-window fixture/API tests do not replace installed-game acceptance. No local default credentials, host-specific deployments, accounts, original game assets or developer logs belong in the download.

Latest bounded scope (2026-09-30): Earned DekaPass full-bag rewards can enter private System mail through an atomic entitlement/escrow receipt; arbitrary client-created system rewards remain blocked. Original ADV donations convert 1,000 points to one GuildPoint and one contribution; DIL donations use 100,000-DIL bundles for treasury and contribution. PlayPoint/GPOINT and explicit original-cost guild level-up are distinct. Frontier/item donation, broader ranks/battles/officer systems and funded disband remain limited or unsupported.

Supported occupied CUSTOM-map revisions use authenticated CAS publication, atomic commit, collision/placement updates, safe relocation and generation-bound reload acknowledgments. Active casts, projectiles, companions, trades, fishing, warps or pending scene/reward transactions explicitly refuse publication. Original-map terrain editing and unsaved shared brush streaming remain unsupported.

Installation-owner Accounts UI/API grants and revokes permitted GM roles durably before lease invalidation; protected owner/admin accounts cannot be demoted through ordinary grant controls. No private owner roster is shipped.

Servant controls bind server-owned orders and Great gauge. Great charge remains an engine heuristic, not recovered native policy. Of 1,752 books, 270 reference 137 absent runtime skill IDs; unsupported mappings and missing Trans Up rows refuse without cost. Local fixture results do not certify all original effects or installed-game parity.
