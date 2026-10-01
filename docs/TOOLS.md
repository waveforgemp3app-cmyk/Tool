# GM and builder tool inventory

This reference lists the available interfaces and every registered command, with online routing and import limits. Availability depends on the connected server and supplied client data. An original or solo-only handler is not an implemented multiplayer service.

## Command Center surfaces

F10 opens the Command Center; backquote opens the GM console; Ctrl/Shift+backquote opens the panel. `/GM`, `/gm panel`, command help, console history and the global tool search open/navigate tools without automatically executing the selected command. Account capabilities gate GM access; revocation closes tools and clears private cached inspection data.

The online dispatcher refuses every unsupported registered command before any transport request or local character mutation. The Commands Run control follows the same policy, including Save action changes. Character class/noclip/meister, Teleport bypass/dungeon controls, live NPC spawn, World rates/simulation speed/event/OX/shutdown and Tools tunables/snapshot/import/apply controls are disabled with an explanation online; their original solo behavior is retained. Time/weather/sky/music/effect controls remain enabled and visibly describe their scope as a local visual preview. Opening Notice editor sends no broadcast; explicit Send/Remove actions use the server.

| Tab/surface | Tools and property controls | Status |
|---|---|---|
| Commands | Category/list search, aliases, syntax/help/description, argument forms with catalog pickers, composed command, execute/copy, named tab navigation | UI/local inspection; execution follows per-command status below |
| Monsters | Original monster search/index, level/HP/rank/role/attack metadata, embedded animated model preview and external model viewer; count/radius/optional X/Z spawn, group/formation calls, monster kill/respawn; map/class drop layers and kill-count simulation | Catalog/model/drop inspection local. Call monster, kill all, respawn server-backed. Unsupported group/formation commands are guarded online |
| Items | Original item search/table filter; stats, requirements, footprint/stack, upgrade chain; grade/count/upgrade/sockets/stone/option pickers, bound/random roll/free-values flags, inventory/ground/cash destinations; Spawn, Copy as command, Who drops it, Model viewer; owned-instance edit; box contents and reverse drops | Spawn/edit use server item operations. Unsupported destinations/metadata are rejected; free/bound controls are not advertised as bypasses. Metadata and drop/model inspection local |
| Teleport | Maps/locations/dungeons/bookmarks, searchable list, minimap cell picker, X/Z, Go, Landing point, Here, Bookmark; per-floor dungeon Enter, Ctrl+click toggle, Ignore map limits, Return to town, Ardeca | Move/goloc/GM map travel server-backed. Bookmarks/minimap local. Online dungeon command, Ctrl+click and Ignore map limits guarded; no collision bypass |
| NPCs | Search original NPCs, names/roles/map placements/jobs, animated model preview/model viewer; spawn here, go to NPC, GM-only NPC convenience actions/service menus | Inspection local. Go to NPC server-backed. Ad-hoc NPC spawn and original GM NPC action commands guarded online; persisted custom-map NPC placement is available through Map Builder |
| Character | Level, EXP, DIL, D-Shop coins, grade, STR/DEX/SPR/HEAL and allocation/reset; class selector/reload; heal/revive; GM/god/hide/one-hit/infinite MP/speed/noclip/cooldown flags; skill search/learn/all/reset; status buff picker/minutes and original GM buff picker | Level/EXP/currency/stats/grade/heal/revive/core GM flags/skills/buff server-backed. Original GM buff picker resolves its original status and minutes through the supported buff command online; raw mapbuff menu commands remain unsupported. Class change, noclip and meister controls disabled with reason online |
| Players | Refresh/search online directory, live Players map and tracking/selection, player details, rename controls and target-player command tools | Live Players map; authenticated directory/rename/target-player server operations. Do not infer arbitrary player/account editing from the map UI |
| Inventory | Search/select online/offline characters, refresh, container/slot grids for bag/equipment/stash/shared/costume/cash, item detail/model preview, money values | Authenticated read-only server inspection. Hides stale details immediately on selection/revoke; normal owned-item edits use Items tools |
| Quests | Search, metadata/type/level, objective/reward inspection, stage/counter state; start/complete/reset/abandon commands; solo counter editor/fill/Mark done | Server-backed quest commands and queststate inspection. Online objective inputs are read-only; Save slot values/Fill all/Mark done are disabled with reason. Use server Complete for consistent rewards/persistence |
| World | Time/hour clock, weather none/clear/rain/snow/sandstorm/shower/blossom/pollen, sky picker, time-scale slider/reset, EXP/drop/DIL rate controls, notice all/map, event start/timetable, OX question/reveal controls, BGM picker/off, effect picker/scene/on/off, shutdown/cancel | Weather/sky/time/music/effects are local presentation. Notice server-backed. Rate changes, time scale, event/OX and shutdown original commands guarded online |
| Drops | Monster→items and item→monsters, map/class/player-level context, DIL/chance/layer tables, kill-count simulation and navigation to item/monster | Read-only local catalog analysis and random simulation; grants no actual loot |
| Builders | Item Builder and Map Builder buttons | Authenticated GM editor opening; editor drafts local, explicit persistence/publication server-backed |
| Tools | Free camera, performance overlay, Hide UI, collision/nav/spawn/NPC/grid/bounds overlays and none; console/system info/user monitor/notice editor/restraint window; original monster/NPC/class/item/target model picker; formula/system-variable selectors/value/Set, Apply all/Reset formula; map-tool command entry; Clear inventory/Repair all/Event log/Position; Save now/export/import/snapshot save/load; character JSON view/apply | Camera/debug/model/log inspection local. Clear inventory/Save now server-backed. Repair is informational (no original durability). Online tunable/formula/sysvar/apply-all/snapshot/import/JSON apply controls are disabled with reason. Export and read-only JSON viewing are local |
| GM 3D camera mode | Right Alt enter/return, Escape return; top-right Item/Map Builder buttons, fly movement/right-drag/height/speed; camera starts at standing character, stops movement and suspends avatar controller | GM-only camera/editor mode; does not make normal player flight authoritative. Returns exactly to normal follow camera and exits on load/disconnect/revoke |

## Item Builder tools

- Catalog tabs: Mine, Items, Models, Textures, Icons; search/Find, category filter, selectable list/scroll, Use and Clone. Original asset/slot/class rules are reused. New starts a draft; custom library controls are Save, Save as New, Delete, Spawn, Spawn + Equip, Export and Import, plus Close.
- General: name, description, kind, derived slot label, rank, spawn grade, all/none and 15 class bits, price/sell, stack size, tradeable, footprint width/height, socket count and random-option roll.
- Stats: minimum/maximum required level, STR/DEX/SPR, melee/magic/ranged min/max damage, defense min/max, PvP damage/defense, block, range, speed class, critical, upgrade level, HP/MP use recovery and lifetime.
- Options: six regular option type/value rows, seven extra option type/value rows, union set selector and set information. Original option types and equipment sets are the source.
- Look: all/per-class model target; main/paired-left/inventory target; material index, original model/texture/icon catalog application, typed mesh/texture data keys; clear model, clear left, inventory same/clear, clear animation; model/action/texture information.
- Preview: Character, Model and Icon modes; class and authored animation selectors; orbit/zoom/reframe controls, character/native equipment attachments, rendered icon/tooltip and size/stats/status. Class restrictions and missing models are reported; inspection is not an equip authorization.
- Meshy/GLB panel: local file pick (embedded GLB, 32 MiB), Y/Z source up, unit scale, X/Y/Z rotation and translation, mirror X, material tint, triangle/material/texture/dimensions/warnings, upload/apply and cancel. Static rigid weapons/offhands require a real native attachment row for each affected allowed class; left target requires a paired kind. Inventory imports preserve equipped animation. Shared animated actions block unsafe left/class-specific replacement. Kind/class/target/model changes during upload reject application. FBX/OBJ/separate glTF require conversion; arbitrary skinned/morph/animated GLB and Meshy armor remain unsupported. Local imported-object inspection is not proof of native rig compatibility.
- Online item definitions/imports/deletion/spawn/equip use canonical authenticated server operations and private persistence. Original tables remain catalog inputs. Save/edit/spawn refusal preserves a draft and cannot grant ghost client items. Export is a local download. Installed owner-build acceptance and arbitrary real user GLB acceptance remain outstanding.

## Map Builder tools

- Map lifecycle: name, blank size 64/128/256/512, original map selector/From map, New, local map list/Open/Delete, Save/Save as new, `.dkmap` Export/Import, resize keeping origin content, Capture minimap, isolated sandbox Preview. Dirty saves/export/retry preserve current edits; strict import validation is atomic.
- Shared Server: select new/existing publication, Refresh server maps, Open server draft and Publish to server. Published archives are immutable/content-addressed with catalog revision/CAS and retry deduplication. Open creates a separate local draft. Supported occupied custom revisions use safe transactional reloads. Published map entry/travel and collision/level/portal bounds are server-backed. Unsaved shared brush streaming and original-map editing remain absent.
- Select, Move/Rotate/Scale gizmo, Shift-click additive object selection, group pivot and one drag/history entry; uniform MOL scale on every axis. Delete selection, Duplicate, keyboard/controller X/Z nudge, Undo/Redo. Pending model loading cannot resurrect deleted/undone placements. Inspector property edits use the same history.
- Terrain tools: Raise, Lower, Smooth, Flatten, Noise, vertex Color; presets Custom/Soft hill/Soft valley/Fine detail/Smooth terrain/Plateau/Soft color paint; radius, strength, smooth/soft/linear/hard falloff, height min/max and color. A continuous brush stroke is one undo entry.
- Ground tools: Type (four blend types), Variant, Hole/fill, Decal texture/size/quarter-turn rotation/erase. Environment tile folder selects the original texture atlas.
- Water: definition picker, offset and erase; editing water visibility. Collision: original MAC attribute selector and brush; grid and collision tint display. Runtime/server collision still uses validated map/MAC rules, not the visual bridge editor feature alone.
- Objects: searchable original library/category, thumbnail/model preview and click placement, snap off/0.25/0.5/1/2. Placement uses clicked original `ground*` helper floors where available; Snap to surface uses terrain/helper floor within 0.8 above the existing object and excludes selected objects themselves. Object inspector shows name/count, X/Z/Y offset/uniform Scale, Delete, Duplicate and Snap to surface. No arbitrary visible-mesh floor inference.
- Spawns: original monster name/index search, pick/armed placement; inspector monster metadata, X/Z/respawn seconds and Delete; marker dragging.
- NPCs: original NPC name/index search/pick/armed placement; inspector searchable NPC replacement, X/Z/direction/name, original jobs/subset picker, remove and Restore original jobs, Delete. Changing catalog NPC restores inheritance; custom jobs are limited to the original NPC's services. Original service table behavior depends on gameplay service support.
- Portals: armed rectangle placement/marker handles, X0/Z0/X1/Z1, searchable original/published/self destination map picker, destination X/Z/direction and Delete. Unknown imported references are retained visibly until corrected; server publication still validates destination references.
- Environment: original light file and sky/environment map, clip far, day length, optional fixed hour, BGM source map, minimum/maximum level gate, return-scroll flag, tile folder, editing water visibility. Terrain/environment changes and inspector changes are undoable.
- Navigation: top-right View (free-fly/first-person terrain), Frame map, tool/radius/snap/Undo/Redo; WASD/Q/E/Shift/right-drag camera. First-person editor follows terrain at 1.8 eye height. It does not provide shared player fly physics.
- Standard controller: enable/status/help, LS movement, RS look, LT/RT height, L3 boost, A build/select, B clear, X Undo/Y Redo, LB/RB tool, D-pad radius/nudge, View snap, R3 view, Menu frame. Blur/typing/busy/hide/disconnect interruptions clear input, close strokes and require held buttons to release. Injected snapshots pass; physical Xbox acceptance remains unverified.

## Verification and limits

Supported transactions and tools have focused source, server and disposable browser checks. Physical controller compatibility, installed hardware performance, every original asset and official-server parity remain separate acceptance requirements. Unsupported controls remain visibly limited rather than granting unsaved local rewards.

<!-- SOURCE APPENDIX -->

## Every registered GM command

Source: gamedata/gmcommands.json (85 registry entries), commands.js (9 extras), GM.run dispatch and server/world/gm.mjs. Status describes online routing, not original registry intent. A server handler still validates arguments, ownership, permissions and supported tables.

| Command | Syntax | Aliases | Online status |
|---|---|---|---|
| notice | /gm notice <all\|map\|clear> <text…> | /notice, /gm announce | Server-backed GM command |
| mute | /gm mute <player> <minutes> | /gm restrainchat | Server-backed GM command |
| shutdown | /gm shutdown <minutes> | /gm finishgame | Disabled with reason online; solo handler retained |
| exprate | /gm exprate <multiplier> [minutes] | /gm expevent | Disabled with reason online; solo handler retained |
| droprate | /gm droprate <multiplier> [minutes] | /gm dropevent | Disabled with reason online; solo handler retained |
| dilrate | /gm dilrate <multiplier> [minutes] | /gm moneyevent | Disabled with reason online; solo handler retained |
| pcroomexp | /gm pcroomexp <percent> |  | Disabled with reason online; solo handler retained |
| usercount | /gm usercount |  | Server-backed GM command |
| mapusercount | /gm mapusercount [map] |  | Server-backed GM command |
| usermonitor | /gm monitor [player] |  | Local presentation/inspection |
| userlog | /gm userlog [count] |  | Local presentation/inspection |
| changescript | /gm reload [all\|quests\|dungeons\|shops\|monsters] | /gm changescript | Disabled with reason online; solo handler retained |
| resetmaxcount | /gm resetcounts | /gm resetmaxcount | Disabled with reason online; solo handler retained |
| sysvar | /gm sysvar <variable> <value> | /gm registry | Disabled with reason online; solo handler retained |
| formula | /gm formula <key> <value> |  | Disabled with reason online; solo handler retained |
| applyall | /gm applyall |  | Disabled with reason online; solo handler retained |
| siege | /gm siege <open\|start\|end\|reset> |  | Disabled with reason online; solo handler retained |
| siegemonitor | /gm observe [map] | /gm siegemonitor | Server-backed GM command |
| guildwarteleport | /gm guildwarteleport <map> |  | Server-backed GM command |
| partywar | /gm partywar <content> <open\|start\|end> | /gm deadfront, /gm icecastle | Disabled with reason online; solo handler retained |
| partywarevent | /gm partywarevent <content> |  | Disabled with reason online; solo handler retained |
| ai | /gm ai <on\|off\|reload> | /gm airegist | Server-backed GM command |
| mapbuff | /gm mapbuff <buff> | /gm gmbuff | Disabled with reason online; solo handler retained |
| oxentry | /gm oxentry <open\|close> |  | Disabled with reason online; solo handler retained |
| ox | /gm ox <wall\|unwall\|killo\|killx\|auto\|close\|end\|ask> [question] | /gm oxquiz | Disabled with reason online; solo handler retained |
| supply | /gm supply <voucher\|material> <which> |  | Disabled with reason online; solo handler retained |
| meister | /gm meister <A\|B> |  | Disabled with reason online; solo handler retained |
| console | /gm console | ` | Local presentation/inspection |
| sysinfo | /gm sysinfo |  | Local presentation/inspection |
| callmonster | /gm callmonster <monster> [count=1] [x y] | /call, /callmonster, /summon, /monster, /gm call | Server-backed GM command |
| callgroup | /gm callgroup <callGroup> |  | Disabled with reason online; solo handler retained |
| makeitem | /gm makeitem <item> [count=1] [upgrade=0] [sockets=0] [option value]… | /item, /makeitem, /createitem, /gm item | Server-backed GM command |
| move | /gm move <map> [x y] | /move, /warp, /teleport, /tp, /gm warp | Server-backed GM command |
| goloc | /gm goloc <location> | /gm location | Server-backed GM command |
| gotonpc | /gm gotonpc <npc> | /gm npcwarp | Server-backed GM command |
| level | /gm level <level> | /level, /gm lv | Server-backed GM command |
| exp | /gm exp <amount> |  | Server-backed GM command |
| dil | /gm dil <amount> | /dil, /gm money | Server-backed GM command |
| buff | /gm buff <status> [minutes] |  | Server-backed GM command |
| god | /gm god [on\|off] | /gm invincible | Server-backed GM command |
| hide | /gm hide [on\|off] | /gm invisible | Server-backed GM command |
| skill | /gm skill <skill> [level] |  | Server-backed GM command |
| skillreset | /gm skillreset |  | Server-backed GM command |
| statreset | /gm statreset |  | Server-backed GM command |
| quest | /gm quest <start\|complete\|reset\|abandon> <quest> |  | Server-backed GM command |
| speed | /gm speed <factor> |  | Server-backed GM command |
| emote | /<emote> |  | Disabled with reason online; solo handler retained |
| chat | <prefix><message>  \|  /<chattype> <message> |  | Disabled with reason online; solo handler retained |
| maptool | <maptool command> … |  | Local editor/preview routing; not direct shared-map mutation |
| tpclick | /gm tpclick [on\|off] |  | Disabled with reason online; solo handler retained |
| setstat | /gm setstat <str\|dex\|con\|spr\|points> <value> |  | Server-backed GM command |
| setclass | /gm setclass <class> |  | Disabled with reason online; solo handler retained |
| heal | /gm heal |  | Server-backed GM command |
| revive | /gm revive |  | Server-backed GM command |
| cooldowns | /gm cooldowns [off] |  | Server-backed GM command |
| infinitemp | /gm infmp [on\|off] |  | Server-backed GM command |
| onehit | /gm onehit [on\|off] |  | Server-backed GM command |
| noclip | /gm noclip [on\|off] |  | Disabled with reason online; solo handler retained |
| freecam | /gm freecam [on\|off] |  | Local presentation/inspection |
| time | /gm time <0-24\|freeze\|resume> |  | Local presentation/inspection |
| sky | /gm sky <sky> | /gm weather | Local presentation/inspection |
| spawnnpc | /gm spawnnpc <npc> [x y dir] |  | Disabled with reason online; solo handler retained |
| killall | /gm killall [radius] [drops] |  | Server-backed GM command |
| respawn | /gm respawn |  | Server-backed GM command |
| freeze | /gm freeze [on\|off] |  | Server-backed GM command |
| droptable | /gm droptable <monster\|item> |  | Local presentation/inspection |
| simdrops | /gm simdrops <monster> <kills> |  | Local presentation/inspection |
| queststate | /gm queststate [quest] |  | Server-backed GM command |
| dkc | /gm dkc <amount\|unlimited> | /gm dshopcoins | Server-backed GM command |
| clearinv | /gm clearinv [bag] |  | Server-backed GM command |
| repairall | /gm repairall |  | Informational only: original items have no durability |
| itemedit | /gm itemedit |  | Server item-edit operation; local editor UI |
| dropitem | /gm dropitem <item> [count] |  | Disabled with reason online; solo handler retained |
| allskills | /gm allskills |  | Server-backed GM command |
| unlockmaps | /gm unlockmaps |  | Disabled with reason online; solo handler retained |
| showdebug | /gm show <collision\|nav\|spawns\|npcs\|grid\|bounds\|none> |  | Local presentation/inspection |
| timescale | /gm timescale <factor> |  | Disabled with reason online; solo handler retained |
| inspect | /gm inspect |  | Local presentation/inspection |
| hideui | /gm hideui |  | Local presentation/inspection |
| snapshot | /gm snapshot <save\|load> <name> |  | Disabled with reason online; solo handler retained |
| mapevent | /gm mapevent <map> <code> |  | Disabled with reason online; solo handler retained |
| fps | /gm fps |  | Local presentation/inspection |
| effect | /gm effect <effectScene> [sceneId] [self\|target\|ground] | /gm fx | Local presentation/inspection |
| enterdungeon | /gm dungeon <dungeon> [floor] | /gm enterdungeon | Disabled with reason online; solo handler retained |
| bgm | /gm bgm <map\|off> | /gm music | Local presentation/inspection |
| help | /gm help [command] |  | Local presentation/inspection |
| panel | /gm panel [tab] |  | Local presentation/inspection |
| gmmode | /gm gmmode [on\|off] |  | Server-backed GM command |
| weatherfx | /gm weatherfx <none\|clear\|rain\|snow\|sandstorm\|shower\|blossom\|pollen> | /gm rain | Local presentation/inspection |
| event | /gm event <name> | /gm startevent | Disabled with reason online; solo handler retained |
| viewer | /gm viewer [monster\|npc\|class\|item] [id] |  | Local presentation/inspection |
| save | /gm save <export\|import\|edit\|now> |  | Server: now; local: export/edit view; online import/apply disabled |
| pos | /gm pos | /gm where, /gm loc | Local presentation/inspection |
| grade | /gm grade <points> |  | Server-backed GM command |

Extra dispatch aliases from GM/index.js: rain→weatherfx, startevent→event, where/loc→pos, gm→panel, weather→weatherfx, viewmodel→viewer, saveedit→save. Bare aliases and original syntaxes are retained in the table above.

## Every Item Builder scripted input/action

These are the actual generated interactive controls, including class/option slots and picker scroll controls. Draft and preview controls are local; Save/Save as/Delete/Spawn/Equip/Import use authenticated server operations online. Export downloads the current library. Close only closes the editor.

| ID | Control | Label or source field |
|---|---|---|
| btn_close | button | btn_close |
| btn_pick_lib | button | Mine |
| btn_pick_items | button | Items |
| btn_pick_models | button | Models |
| btn_pick_tex | button | Textures |
| btn_pick_icons | button | Icons |
| edit_search | edit | edit_search |
| btn_search | button | Find |
| com_pickfilter | combobox | com_pickfilter |
| lst_pick | listbox | lst_pick |
| lst_pick_scroll | vscroll | lst_pick_scroll |
| lst_pick_scroll_upbtn | button | lst_pick_scroll_upbtn |
| lst_pick_scroll_downbtn | button | lst_pick_scroll_downbtn |
| btn_pick_use | button | Use |
| btn_pick_clone | button | Clone |
| btn_tab_general | button | General |
| btn_tab_stats | button | Stats |
| btn_tab_options | button | Options |
| btn_tab_look | button | Look |
| edit_name | edit | edit_name |
| edit_desc | edit | edit_desc |
| com_kind | combobox | com_kind |
| com_rank | combobox | com_rank |
| com_grade | combobox | com_grade |
| btn_cls_all | button | All |
| btn_cls_none | button | None |
| chk_cls_0 | checkbox | Azure Knight |
| chk_cls_1 | checkbox | Segita Hunter |
| chk_cls_2 | checkbox | Incar Magician |
| chk_cls_3 | checkbox | Vicious Summoner |
| chk_cls_4 | checkbox | Segnale |
| chk_cls_5 | checkbox | Bagi Warrior |
| chk_cls_6 | checkbox | Aloken |
| chk_cls_7 | checkbox | Dragon Knight |
| chk_cls_8 | checkbox | Segita Shooter |
| chk_cls_9 | checkbox | Black Wizard |
| chk_cls_10 | checkbox | Conserra Summoner |
| chk_cls_11 | checkbox | Segeuriper |
| chk_cls_12 | checkbox | Half Bagi |
| chk_cls_13 | checkbox | Alokes |
| chk_cls_14 | checkbox | Trie Muse |
| edit_price | edit | edit_price |
| edit_sell | edit | edit_sell |
| edit_stack | edit | edit_stack |
| chk_trade | checkbox | Tradeable |
| edit_w | edit | edit_w |
| edit_h | edit | edit_h |
| edit_sockets | edit | edit_sockets |
| chk_roll | checkbox | Roll random options when spawned |
| edit_reqlv | edit | edit_reqlv |
| edit_maxlv | edit | edit_maxlv |
| edit_reqstr | edit | edit_reqstr |
| edit_reqdex | edit | edit_reqdex |
| edit_reqspr | edit | edit_reqspr |
| edit_melee0 | edit | edit_melee0 |
| edit_melee1 | edit | edit_melee1 |
| edit_magic0 | edit | edit_magic0 |
| edit_magic1 | edit | edit_magic1 |
| edit_ranged0 | edit | edit_ranged0 |
| edit_ranged1 | edit | edit_ranged1 |
| edit_def0 | edit | edit_def0 |
| edit_def1 | edit | edit_def1 |
| edit_pvpdmg | edit | edit_pvpdmg |
| edit_pvpdef | edit | edit_pvpdef |
| edit_block | edit | edit_block |
| edit_range | edit | edit_range |
| edit_speed | edit | edit_speed |
| edit_crit | edit | edit_crit |
| edit_itemlv | edit | edit_itemlv |
| edit_usehp | edit | edit_usehp |
| edit_usemp | edit | edit_usemp |
| edit_period | edit | edit_period |
| com_opt_0 | combobox | com_opt_0 |
| edit_optv_0 | edit | edit_optv_0 |
| com_opt_1 | combobox | com_opt_1 |
| edit_optv_1 | edit | edit_optv_1 |
| com_opt_2 | combobox | com_opt_2 |
| edit_optv_2 | edit | edit_optv_2 |
| com_opt_3 | combobox | com_opt_3 |
| edit_optv_3 | edit | edit_optv_3 |
| com_opt_4 | combobox | com_opt_4 |
| edit_optv_4 | edit | edit_optv_4 |
| com_opt_5 | combobox | com_opt_5 |
| edit_optv_5 | edit | edit_optv_5 |
| com_exo_0 | combobox | com_exo_0 |
| edit_exov_0 | edit | edit_exov_0 |
| com_exo_1 | combobox | com_exo_1 |
| edit_exov_1 | edit | edit_exov_1 |
| com_exo_2 | combobox | com_exo_2 |
| edit_exov_2 | edit | edit_exov_2 |
| com_exo_3 | combobox | com_exo_3 |
| edit_exov_3 | edit | edit_exov_3 |
| com_exo_4 | combobox | com_exo_4 |
| edit_exov_4 | edit | edit_exov_4 |
| com_exo_5 | combobox | com_exo_5 |
| edit_exov_5 | edit | edit_exov_5 |
| com_exo_6 | combobox | com_exo_6 |
| edit_exov_6 | edit | edit_exov_6 |
| com_set | combobox | com_set |
| com_lookclass | combobox | com_lookclass |
| com_mat | combobox | com_mat |
| btn_tex_reset | button | Reset texture |
| btn_mesh_clear | button | No model |
| btn_left_clear | button | Clear |
| btn_inv_same | button | Use game model |
| btn_inv_clear | button | Default |
| btn_action_clear | button | Remove |
| com_target | combobox | com_target |
| edit_meshkey | edit | edit_meshkey |
| btn_meshkey | button | Set |
| edit_texkey | edit | edit_texkey |
| btn_texkey | button | Set |
| btn_meshy | button | Import Meshy GLB |
| btn_mode_character | button | Character |
| btn_mode_item | button | Model |
| btn_mode_icon | button | Icon |
| com_pvclass | combobox | com_pvclass |
| com_pvanim | combobox | com_pvanim |
| btn_new | button | New |
| btn_save | button | Save |
| btn_saveas | button | Save as New |
| btn_delete | button | Delete |
| btn_spawn | button | Spawn |
| btn_equip | button | Spawn + Equip |
| btn_export | button | Export |
| btn_import | button | Import |

## Every Map Builder static input/action

All authoring/display controls edit or inspect the local draft. Refresh/Open/Publish in Shared Server use the authenticated map catalog. A local preview is isolated; GM entry to a published map is server-backed. Dynamically built inspector controls are listed in the authored sections above.

| ID or tool | HTML control | Visible label or field |
|---|---|---|
| mapName | input | mapName |
| newSize | select | newSize |
| newBase | select | newBase |
| btnNew | button | New |
| btnFromBase | button | From map |
| openList | select | openList |
| btnOpen | button | Open |
| btnDelete | button | Delete |
| btnSave | button | Save |
| btnSaveAs | button | Save as new |
| btnExport | button | Export .dkmap |
| fileImport | input | fileImport |
| (unnamed) | button | 64 |
| (unnamed) | button | 128 |
| (unnamed) | button | 256 |
| (unnamed) | button | 512 |
| btnMinimap | button | Capture minimap |
| btnPlay | button | Play ▶ |
| serverMapTarget | select | serverMapTarget |
| btnServerRefresh | button | Refresh server maps |
| btnServerOpen | button | Open server draft |
| btnServerPublish | button | Publish to server |
| select | button | Select |
| gzT | button | Move |
| gzR | button | Rotate |
| gzS | button | Scale |
| raise | button | Raise |
| lower | button | Lower |
| smooth | button | Smooth |
| flatten | button | Flatten |
| noise | button | Noise |
| vcolor | button | VColor |
| type | button | Type |
| variant | button | Variant |
| hole | button | Hole |
| decal | button | Decal |
| water | button | Water |
| collision | button | Collision |
| objects | button | Objects |
| spawns | button | Spawns |
| npcs | button | NPCs |
| portals | button | Portals |
| oPreset | select | oPreset |
| oRadius | input | oRadius |
| oFalloff | select | oFalloff |
| oStrength | input | oStrength |
| oMin | input | oMin |
| oMax | input | oMax |
| oColor | input | oColor |
| 0 | button | 0 |
| 1 | button | 1 |
| 2 | button | 2 |
| 3 | button | 3 |
| oErase | input | oErase |
| oDecal | select | oDecal |
| oDecalSize | input | oDecalSize |
| oDecalRot | button | 0° |
| oDecalErase | input | Erase (click a decal) |
| oWaterDef | select | oWaterDef |
| oWaterOffset | input | oWaterOffset |
| oWaterErase | input | oWaterErase |
| oAttr | select | oAttr |
| pSpawn | input | pSpawn |
| pNpc | input | pNpc |
| pPortal | input | pPortal |
| oSnap | select | oSnap |
| tGrid | button | Grid |
| tCollision | button | Collision tint |
| libSearch | input | libSearch |
| libCat | select | libCat |
| monSearch | input | monSearch |
| npcSearch | input | npcSearch |
| eLight | select | eLight |
| eEnvMap | select | eEnvMap |
| eClip | input | eClip |
| eDay | input | eDay |
| eFixedOn | input | eFixedOn |
| eHour | input | eHour |
| eBgm | input | eBgm |
| eMinLv | input | eMinLv |
| eMaxLv | input | eMaxLv |
| eReturn | input | eReturn |
| eTileFolder | select | eTileFolder |
| eWaterOn | input | eWaterOn |
| btnUndo | button | Undo |
| btnRedo | button | Redo |
| navMode | select | navMode |
| btnFrame | button | Frame map |
| quickTool | select | quickTool |
| quickUndo | button | Undo |
| quickRedo | button | Redo |
| radiusDown | button | Radius − |
| radiusUp | button | Radius + |
| quickSnap | button | Snap: off |
| padEnabled | input | Xbox / standard controller |

Latest bounded scope (2026-09-30): Earned DekaPass full-bag rewards can enter private System mail through an atomic entitlement/escrow receipt; arbitrary client-created system rewards remain blocked. Original ADV donations convert 1,000 points to one GuildPoint and one contribution; DIL donations use 100,000-DIL bundles for treasury and contribution. PlayPoint/GPOINT and explicit original-cost guild level-up are distinct. Frontier/item donation, broader ranks/battles/officer systems and funded disband remain limited or unsupported.

Supported occupied CUSTOM-map revisions use authenticated CAS publication, atomic commit, collision/placement updates, safe relocation and generation-bound reload acknowledgments. Active casts, projectiles, companions, trades, fishing, warps or pending scene/reward transactions explicitly refuse publication. Original-map terrain editing and unsaved shared brush streaming remain unsupported.

Installation-owner Accounts UI/API grants and revokes permitted GM roles durably before lease invalidation; protected owner/admin accounts cannot be demoted through ordinary grant controls. No private owner roster is shipped.

Servant controls bind server-owned orders and Great gauge. Great charge remains an engine heuristic, not recovered native policy. Of 1,752 books, 270 reference 137 absent runtime skill IDs; unsupported mappings and missing Trans Up rows refuse without cost. Local fixture results do not certify all original effects or installed-game parity.
