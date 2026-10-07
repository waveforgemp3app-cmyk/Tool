# Dekaron Online (One Client & Engine) — Changelog

Every version, newest first. The newest build is always on the releases page: https://github.com/waveforgemp3app-cmyk/Tool/releases/latest

Where the game data does not establish a rule, the engine's own choice is marked ENGINE-CHOSEN (or FITTED when it was fitted to Global screenshots).

## 2.2.3 - Faster First Start

The last update of the 2.x line. It has one change: the preparation of the client data that runs on the first start after an install or an update now runs its steps in parallel. The game itself is unchanged.

### Loading

- **First start after an install or update:** The preparation used to take about 5 minutes (315 seconds on my PC) because its 21 steps ran one after another. Steps that do not depend on each other now run at the same time: the same preparation took 77 and 89 seconds in two runs on a 6-core PC with 32 GB of RAM (3.5 to 4 times faster; a PC with fewer cores gains less). The prepared files are identical to what the old order produced: compared file by file, every byte is the same except the time stamps inside 17 of the 57 data files.
- **How many steps run at once:** up to 4, fewer on a PC with fewer than 5 cores, and at most 2 on a PC with less than 6 GB of RAM (4 at once used up to 3.8 GB of memory on my PC). Set the environment variable `DEKARON_PREPARE_JOBS` before starting the launcher to choose another number; `DEKARON_PREPARE_JOBS=1` runs the steps one after another as before.
- **Safe on errors:** if one step fails or you close the launcher, all running steps are stopped before anything is cleaned up, and the previously prepared data stays in place.
- **One more preparation after updating:** the preparation program itself changed, so every install prepares once after updating to 2.2.3 (about 1.5 minutes now).
- **Changes to the channel files are noticed:** the preparation did not look at the channel rule files (`channel-data.mjs`, `channel-rules.js`), so editing them did not rebuild the prepared data. It does now.

## 2.2.2 - Bug Fix Update

Fixes for problems found after 2.2.1, and two new per-server switches. Most of these fixes are in the server: hosts must update and restart their server to get them.

### Combat and skills

- **Field PK (forced attack):** On open PvP maps (the maps the game data marks as PvP and not as a safety zone) hold **Ctrl** to attack other players: the cursor turns into the swords, a skill cast while Ctrl is held can hit players, and Ctrl+click attacks at once. Party mates, guild mates, safety zones and spectators are protected, with the game's own messages ("cannot be attacked", "Safety Zone"). Killing a player makes you wanted: other players see your name in purple (red in the heavier chaotic bands; your own name plate does not change colour yet), the value fades with time, and killing a wanted player or fighting on a map marked "no chaotic increase" adds nothing. Damage uses the same rules as duels. The 4 second window that Ctrl arms, the kill counting and the fading speed are the engine's own choice (ENGINE-CHOSEN) where the data is silent. Not in this version: the PK "Safe Time", the tendency window and the death drop penalty.
- **Half Bagi skills:** The Half Bagi's main attack skills (Wild Slash, Earth Divide, Furious Brandish, Skull Crusher, Burst Slash, the four Dances, Blow of Fury and the three Berserker steps: 13 skills) cost Fury instead of MP, and online they were all refused because the server never filled the Fury gauge. It does now. A landed hit adds 2 % of your maximum MP, a hit taken from a monster adds 3 %, and the gauge drains 0.2 % per second after a 10 second hold at the top (the drain and the 10 seconds are in the game data; the two gain rates are the engine's own choice). The gauge on your screen and the hotbar grey-out follow the server's value.

### Characters and server settings

- **Deleting characters:** Characters can be deleted from the character select screen again. Type the character's name to confirm. A character cannot be deleted while it is in a guild or while the account is in the world; the name is free again afterwards. Before, every delete was refused for online characters.
- **Starter pack switch (per server):** Dashboard > Settings > "New characters get the starter pack". When it is off, new characters on that server start without the starter kit. Existing characters keep what they have, and switching it on again does not hand the kit out afterwards.
- **PK switch (per server):** Dashboard > Settings > "Allow PK on open maps (hold Ctrl to attack players)". On by default; when off, Ctrl does not attack players on that server.

### Quests, NPCs and maps

- **Teleport quests that sent you to the map corner:** The Parca Temple "Six Bosses" gate quests (Gate of Challenge / Gate of Qualification), Verdi's "Altar of Terra Entrance" on Requies Beach (Move - Terra's Altar) and Tuban's Favnil's Altar teleport on Avalon Island used to drop you at the corner of the map. The game's location table lists these destinations without coordinates; the engine now uses the arrival point of the neighbouring entry of the same map (ENGINE-CHOSEN). 36 quests had this problem, 34 now arrive at a real position (the Draco Desert and Avalon 11202 entries have no arrival entry and are unchanged).
- **Sergio's Swift Box (Ardeca):** "Purchase Swift Box" now sells the box: ten purchases per character with the prices of the dialog (195,857 DIL for the first, three times more each time up to 3,855,044,794 DIL), from level 80, with the game's own messages for too little DIL, a full bag and "I don't have any left in stock" after the tenth. What the box contains is the item table's Swift Box (the NPC text gives only the name).

### Interface

- **Personal Shop (Ardeca):** While your shop is open your character now stays where it sat down: walking, click-to-move and movement reports are refused by the server (the game's "The shop is in operation." rule), and the client no longer walks the character. Before, a character could still be moved around while it was selling.
- **Party members on the minimap:** The minimap shows the members of your party that are on your map as dots, and as arrows on the edge of the minimap when they are out of view. Hover a dot for the name.
- **Guild of Glory emblems:** The glowing guild emblems from the shop (Guild of Glory) can be used: the guild leader uses the item, confirms, and the guild's emblem on name plates gets a golden glow (the Alliance of Glory glows the same way). Only the guild leader can use it and the item is used up. The guild mark NPC's delete option removes the glow first (the mark itself stays). The glow look is the engine's own choice.

### Messages

- **DIL and EXP lines:** A kill prints only "Obtained EXP: [ N ]". DIL drops on the ground and "Acquired DIL: [ N DIL]." appears when it is picked up (by you or by your pet), as in the original game. The old combined line showed a DIL number that was never paid. Picked-up items print the game's "[Message] <item> has acquired <count>." line.

## 2.2.1 - Latency and Frames Update #1

This update is about latency and frame rate: big fights, the HUD ping, loading and smoothness. Everything else that changed in 2.2.1 follows after it, grouped by topic.

### Latency and ping

- **Ping:** The HUD ping shows the real network time of the game's own requests to the host and no longer rises when the frame rate drops. 2.2.0 showed about 3 times the frame time, so a fight at 8 frames per second read 400 ms even on a fast link. With the host on your own PC the label now reads about 3 ms at every frame rate (before: 46, 166 and 402 ms at frame times of 12, 50 and 118 ms); with 80 ms of added network latency it reads 95-97 ms and stays there while the frames slow down (before: 115 ms, climbing to 402 ms). In a 10-minute scene with 70-450 monsters the average label went from 57 ms to 2 ms. The tooltip still shows the frame time next to the ping.
- **Big fights no longer freeze:** A skill that hits 50 monsters several times creates about 200 damage numbers at once, and each one cost 7.6-9.0 ms because the number sprite sheet was copied into every digit. In my test one Tempest Wing on 50 monsters held the screen for 1.3-1.6 s in a single frame (frame times 1,564 / 1,330 / 1,296 ms for three casts); now the worst frame is 25-42 ms in the final runs and 59-159 ms in earlier runs while the PC was busy with other work. Eight area skills in a row, 1.5 s apart: worst frame 1,334 -> 63 ms and the HUD ping peak 904 -> 122 ms. A number now costs 0.01-0.08 ms instead of 7.6-9.0 ms (about 150-300 times less) and numbers above the 60 that can be on screen are not even built. The numbers look exactly the same. Measured on a Ryzen 5 3600X, RTX 3070, 1080p.
- **Chat during mass kills:** The chat and system-message boxes read their size three times after every added line, and every read forced a new layout. They now do it once per batch of lines, before the next picture is drawn. 200 kill messages at once: 589 forced layouts -> 8, 110.7 ms -> 2.1 ms in the loop; 800 kills (the size of a /gm killall): worst frame 516 ms -> 54 ms. The chat looks and scrolls exactly as before.
- **Kills on the server:** Every kill built a full quest context (a deep copy of your character plus the whole quest database) even when none of your quests cares about that monster. The server now builds it only when one of your active quests can react to the kill; quests with kill objectives take the same path as before. Measured on a running server: /gm killall of 817 monsters, command answer 2.6 / 3.1 / 2.5 s -> 0.18 / 0.09 / 0.11 s; an area skill that kills 50 monsters, longest server stall 199 / 143 / 112 ms -> 27 / 12 / 10 ms; 90 monsters 122 / 140 / 96 ms -> 47 / 19 / 42 ms; per kill 3.1 ms -> 0.11 ms. With a very large character (285 KB) a 817-monster killall took 13-35 s before and 0.2-0.5 s now. Quest progress, events and drops are unchanged. Hosts have to restart the server to get this.
- **Skills respond at once:** The cast animation and the cooldown sweep start as soon as you press the key instead of after the server's answer; the host's answer confirms it, and a refusal or a timeout takes it back (dash, teleport and instant-projectile skills, mounted casts and skills that pick the nearest target still wait for the server) (first visible reaction after the key press 266 ms -> 9 ms in tests with a simulated 80 ms ping, measured with the 40 active skills of the Incar Magician). A key pressed while a skill is still playing is queued on the host (the newest press wins) instead of being answered "Skill is busy": in a chain of 6 skills one second apart, 6 of 6 now cast (3 of 6 before). When a skill cannot be used, a message appears next to your character as well as in the chat (the same text at most every 1.5 s); a press on a target that has just died gives the game's own message. The host also answers a cast without waiting for the account save. Cooldowns, MP costs and range are unchanged.
- **Quick skill presses:** A skill press no longer disappears without a message: when you press several skills quickly, each press is either cast or you are told why not (for example "Replaced by a newer skill press."). Before, one shared flag dropped every press silently while any cast waited for the host. Energy zap pressed 30 times: 5 presses dropped silently before, 0 now. Six different skills pressed 120 ms apart: 1 cast, 2 "busy" refusals and 3 silent drops before; 2 casts and 4 reported replacements now.
- **Cooldowns:** The hotbar cooldown now ends together with the server's cooldown (it is shortened by the time the answer needed to reach you), so a skill pressed the moment it is ready is no longer greyed out. With a simulated 80 ms ping the difference between the two went from about 80 ms to about 15 ms (median).
- **Skill messages:** Skill messages from the server now show the game's own text (for example "You don't have enough MP.") instead of a bare number like "(20)": the host now loads the game's skill message table.

### Frame rate and smoothness

- **Frame rate:** Frame rate in towns roughly doubled or better in our tests (about 60 fps before, about 100-160 fps now depending on what is on screen, on a mid-range PC), and the stutter spikes in town are gone. Fields gain less (about 90-100 fps before, about 110-130 now). Measured on my PC (Ryzen 5 3600X, RTX 3070, 1080p) with the same scenes before and after. Town: standing in Ardeca, with 10 other players, running and with three windows open; field: Deneb with 160 monsters idle, fighting and running. The main thread of the browser is the limit, so very high rates are not reached in every scene.
- **Less work per frame:** This is where the frame rate above comes from. The picture is unchanged.
  - Glowing gear: the glow pass sees the same lights as the main pass, so every lit material is no longer checked twice a frame (town script time 29.6 -> 23.9 ms on a fully loaded PC).
  - Props and rigs: animated props and instanced groups are culled per instance, use a shared-geometry draw path and update skeleton matrices only after a pose (town script time 20.7 -> 11.8 ms, draw calls 653 -> 266). A prop's first draw is no longer delayed to the moment the camera turns.
  - Sun shadow: above about 120 fps the shadow map is redrawn every 2nd frame (any change forces a draw); below 120 fps nothing changes.
  - Characters: the bone texture is uploaded only when the pose changed (12-13 % fewer uploads); above about 120 fps distant bodies are posed at 120 / 80 Hz (43 % fewer animator updates in town); hair and cape springs carry the skipped time.
  - Distant scenery: animated scenery is posed every 2nd or 3rd frame beyond 30 / 60 m.
  - Bookkeeping: status effects skip actors without statuses (131 -> 9 microseconds), standing remote players are not re-placed every frame, the connection panel makes no DOM writes when idle.
  - HUD: the canvas rectangle is cached (HUD step 0.27 -> 0.06 ms with windows open); name plates, floating numbers, minimap arrow / radar / labels and belt cooldowns are written only when they change.
  - Shaders for new monster bodies and item-icon renders are compiled in the background before they are drawn.
- **Max FPS:** The game has a new frame pacer: the Max FPS options 144 and 165 now hold their rate on a 239 Hz screen (143.9 and 164.9 frames per second measured; they used to deliver 119.5), and 75 delivers 75.0 (was 78.8). It handles stalls and window refocus without catch-up bursts, and Unlimited is a pass-through. A limit can only be held when the game itself can render that fast.
- **Instant loading:** The game tables (items, skills ...), the map's textures and meshes and the window art now load while you are at the login and character-select screens (up to 12 maps are prepared), and a gate's destination map is prepared in the background as you walk up to it (within 40 cells, maps you have visited before). Loading screen into Ardeca: 8.3-10.2 s -> 2.4-3.6 s (after 5 s at character select); the very first start: about 11 s -> 6.2-6.9 s. Returning to a map you already visited: 3.8-9.3 s -> 1.1-1.7 s. Times measured on my PC.
  - The D-Shop icons: only the first page is prepared while the game loads; the next pages of each tab and Wings pages 2-3 are prepared after the world is shown, at the lowest priority. 2.2.0 tried to bake the whole Wings catalogue (9,421 wings) in the background, which never finished, kept rendering during play and pushed your own bag icons out of the cache so they were prepared again on the next map load.
  - Map loads pause the icon prefetch, and Deka Pass reward icons load in the background.
  - Asset decoding uses between 2 and 6 worker threads depending on your CPU (it was a fixed 2).
  - The scan for native wings no longer copies about 95,000 item rows.
  - The items, life and extras systems start their module loads in parallel, and joining the shared world overlaps NPC placement.
  - The shop page queue sorts and pumps once per batch.
- **First-time hitches:** The first time a monster kind died, its fading corpse needed a new shader and the game froze for 100-452 ms at that moment (3-8 such frames in the first minutes of a fight with 70 monsters, more when an area skill killed several kinds at once). The game now builds that shader in the background as soon as the monster is loaded, and the five Dil pile models are built while the map loads (in a 10-minute test with 70-450 monsters those frames went from 3-8 to none). The first buff on your own character in a session can still cost one frame of about 0.25-0.3 s. The price: the very first load of a field map can take about 0.7-0.8 s longer (later loads show no difference).
- **Mass-kill loot:** When hundreds of items drop at once (a mass kill), their name labels are now built over the next few frames instead of all in the frame the drops arrive in: the work for 411-446 drops fell from 82 ms to 18 ms and the frame that receives them from 192-222 ms to 163-180 ms. The items themselves appear and can be picked up at once; the labels of a very large burst fill in within about a second (0.7 s on a slow 12 fps scene).

### Combat and skills

- **Auto attack:** Normal attacks in online play now deal damage on every swing of the combo (before, every second swing was skipped). Tested online with all 15 classes, 12 swings each: 90 of 180 swings dealt damage before, 180 of 180 now; with 80 ms of added delay (Segnale, Alokes, Segeuriper) 15 of 36 -> 36 of 36. Offline play was never affected. The host's limit on hits now follows each class's own combo timing from the game data instead of a flat 1,000 ms; hitting faster than the combo is still refused. Hosts have to restart the server to get this.
- **Attack effects:** Normal attacks of Segnale (red whip) and Trie Muse now play the attack effect from the game data, on your own character, on other players and in first person. Fixed along the way: a double effect after a body reload or gear change, an effect left running after an interrupted swing (it is cut before 90 % of the clip), and no effect on the first swing after login.
- **Summons:** Other players now see your summon's body (Vicious Summoner summons used to show only a name plate to other players). Summon circles and other looping cast effects (13 skills in the data loop) stop softly at the end of their combo step and at the end of the skill, on your screen and on other players' screens; before, they stacked up until the map changed. Offline, a summon's arrival burst plays once instead of pulsing under the summon for its whole life.
- **Other players' skills:** Effects of other players' skills now play to their full length on your screen: a finished cast used to stop every effect on observers' screens (the 60 s Dual Chakra aura showed for 0.7 s; 216 plays in 107 scenes were affected). Now only loops are stopped softly; an aborted cast still clears everything.
- **Damage over time:** A damage-over-time effect that kills its target no longer leaves an aura restarting on the dead or respawned unit, no longer removes the wrong status and no longer throws an error that cancelled the skill you were casting.
- **Channel change and map teleports:** Changing channel and the big map's NPC teleports use a 10 second bar titled "Channel": you cannot move while it runs, and taking damage, pressing Esc or Cancel stops it and releases the host's cast (the NPC teleport took 5 s before). Smart Warp stays at 3 seconds. Fixed along the way: Esc used to leave the cast running on the host, the bar now keeps running in a hidden tab, survives a stale snapshot, and only one warp can run at a time. The channel changes 10.1-10.5 s after the click and a hit closes the bar in about 0.66 s.
- **Select Warp / Party Warp:** The warp bar from the big map is titled "Select Warp" (it showed "Store Game Information") and, like the NPC teleports, takes 10 seconds (it was 3); pressing Esc, Cancel, a map change or death cancels it. Before, Esc closed the bar but the character still teleported 7.3 s later. Party Warp uses the same bar.
- **Channel change on a mount:** Changing channel while riding is refused with the game's own message "You cannot use teleportation while riding a creature." Before, the bar flashed and closed without a word.
- **Area skills stay where cast:** Area skills cast around you (Segnale's Curse field, the Protection sanctuary, the Shield field and the rest of that kind: 62 skills, about 50 of them pulse over time) now stay at the spot where you cast them and pulse there for their whole duration instead of following you. The game data has no rule that makes the field move with the caster. In a test with the caster walking 14 m during the field: field centre drift 10.7 m -> 0 m, the field seen by another player 9.9 m -> 0 m, hits on two monsters standing in the spot 8 and 5 -> 10 and 10 (of 10 pulses), hits on three monsters next to the walking caster but outside the spot 15 -> 0. A caster who stands still sees exactly the same pulses and damage as before.

### Monsters

- **Monsters leaving a fight:** Monsters no longer heal (+35 % per second, full heal on arrival), turn immune (every hit a miss), run home at 1.15 times their speed or snap home when you walk away from them: they stop chasing, take the state the game data names for giving up, stay hittable and fight back if you hit them again. Offline and on the server. A Crocuda stayed at 223 HP after giving up and every hit landed (before: 118 -> 375 HP in 4.3 s and every hit a miss). Damage a monster has taken is also kept in offline play after you walk far away and come back (a hurt monster that is streamed out keeps its HP fraction; killed monsters still respawn at full HP).
- **Monsters follow their own data online:** Every monster now uses its own sight range, give-up distance, run speed and attack reach from the game files. The server used to cap them all at 20 cells of sight, 40 cells of chase, run speed 6 and reach 8, so long-range monsters (Taron sees 200 cells, archers shoot from 14) acted like ordinary melee mobs. The 92 call-for-help monsters (Yetarian, Lizardman Knight ...) now call up to 2-3 idle neighbours on the first hit online. A monster fights whoever caused it the most hostility (first-hit bonus, a cap, a 30 s memory) and only switches for 20 % more; a plain hit adds hostility by class as the data says, and a summon's hit counts once instead of twice. Slows, roots and sleeps work on monsters on the server; event objects and traps never fight back.
- **Monster archers online:** Monster archers online play their full shot: the swing holds the animation's own length (it was cut at 0.7 s; the Yetarian Bow is 1.4 s long), uses the attack block's own clip and the archer faces its target (before it shot in its random spawn direction). A monster mid-swing no longer flinches.
- **Follow limit:** A monster only follows a target while fewer monsters than its own follow limit from the game data (the follow-target value of its row) already follow that target. Field monsters mostly have 2, 3 or 4 (88 % of the field spawns: 3 on 57 %, 4 on 23 %, 2 on 8 %; a few have 5-10 or 20-30, about 7 % have no limit). Dungeon monsters carry their own values and most have no limit (73 % of the dungeon spawns have 50, 100 or no value, the rest 2 or 15); nothing special-cased, applied as the data says. With 50 monsters around you, 3-4 chase you and the rest wait instead of all 50: followers 50 -> 4 or 3, hits on the player 13.8 -> 1.3 per second (24.6 -> 1.3 with area skills), host events down 58-96 %. Every player is a separate target, so a party of two is followed by about 4 + 3 monsters; online, a summon does not raise the limit (the host's monsters only target players), offline it counts as a target of its own. A monster whose top target is full tries the other players it hates. The limit does not change the frame rate by itself. Hosts have to restart the server to get this.
- **Roaming after a chase:** Monsters keep following you wherever you lead them: you can pull them across the whole map and they never walk back to their spawn point. A monster you outrun roams normally around the spot where it ended up (only monsters that roam at all; the others stay where the chase ended) and returns to its spawn point only after it dies, when it respawns there. Aggressive monsters follow on by themselves while you stay in their sight; a passive monster that gave up needs another hit to follow you again. In a test, monsters followed a player 120-134 cells away from their spawn.

### Items and loot

- **D-Shop Wings:** While the D-Shop is open the icon queue now runs 4 jobs at a time instead of 2, so paging through the wings shows icons sooner: the mean icon wait on pages 3-12 went from 755 ms to 538 ms (-29 %).
- **Pickup key:** The pickup key (Space) picks up one item per press. Before, one press sent a request for every drop within 3 m (up to 4, with 5 duplicates at 120 ms latency) and a closer drop replaced the item you were walking to, so you bounced from item to item. Now a press while a pickup is still running does nothing and the next press takes the next item (most requests from one press 4 -> 1, duplicate requests 17 -> 0, replaced walk orders 2 -> 0 over seven pickup situations at 0 and 120 ms latency; with 14 presses beside the drops, one burst took 16-20 items before and at most 12 now). Clicking an item and pet pickup work as before.
- **Ground items:** The mouse cursor turns into the hand (the game's grip cursor) when it is over an item on the ground, and holding Alt (View Drop Item Name in the key list) shows the real name of every item on the ground in its grade colour (before, the key labelled every item "Item" in white). Clicking an item to pick it up works as before.

### Interface and options

- **Esc:** With a target selected, one press of Esc opens the system menu (and releases the target). Drags, dropdowns and windows that close with Esc still take the press first.
- **Target plate:** Monster (and other player) buffs and debuffs now show on the target HP plate online, in the 8 original slots, with their icons from the status table and tooltips that count down.
- **Cursor:** The game's golden cursor is shown over every window and on the login, character-select and loading screens, not only over the 3D view. A missing cursor texture no longer causes an error.
- **Window:** The DX11 Client opens as a 1280 x 720 bordered window that fits your screen (a saved size larger than the work area is ignored); fullscreen is remembered only when you chose it, F11 is no longer undone, and the window-mode setting in Options reaches the Dekaron.exe window. In the desktop client a window size that does not fit the desktop is not applied (a note shows instead).
- **Map window (M):** The Map window opens with no NPC selected, and the selection is cleared when you close it. Clicking an NPC marker on the map selects it and its marker pulses gold (or red) on a 5 second cycle.
- **Damage numbers:** When many monsters hit you at the same moment their damage numbers now appear at the same spot over your head instead of each new number being lifted above the last (the game's damage-number data has no stacking rule). With 50 hits in one moment the highest number was 16,000-87,000 px above the head before and is 80 px now, the same as a single hit. A single number is unchanged, and the small random sideways offset and the cap of 60 numbers stay.

### Server and hosting

- **Busy servers:** The server does much less work per tick with very many monsters: each scene is checked for frozen state and viewers once per tick; idle monsters stand still when no player is near; each snapshot row is built once per broadcast and a snapshot lists only the nearest monsters; the skill status pass runs once per tick; broadcasts are sent in short slices; and a kill's reply no longer waits for the account to be written to disk (2.2.0 waited for every kill; saves now run in the background and merge).
- **Hosts:** Restart your server after updating: the auto attack, kill, follow-limit, area-skill and monster fixes above are in the server, not only in the client.

### Everything else

- **Party EXP:** The party bonus uses each map's own row of the group EXP table (by member count, capped by the group size) instead of the first row everywhere. Because of this the client data is prepared again once on the first start.

## 2.2.0 (2026-10-04)

- **DX11 Client (Dekaron.exe):** The game opens in its own native window, Dekaron.exe, drawn through Direct3D 11 (Microsoft WebView2 host). It only opens after you sign in through the launcher and then signs you in by itself. It opens at 1280 x 720; a resolution applied in Options sizes the window and is remembered (F11 = fullscreen). Task Manager and the volume mixer list it as Dekaron.exe.
- **Launcher:** Three labelled ways to play on the sign-in panel and the dashboard: DX11 Client, Desktop App and Web Browser. "Other server..." opens another server with the same three choices. Closing the game returns to the dashboard.
- **Login:** All three go straight to the login hall (no loading screen) with the server button ready; Server Login enters with your launcher sign-in, no password asked again. The LOGIN SELECT window shows the server logo.
- **Smooth monsters:** Monster positions are played back on the server's own clock (measured with ~96 monsters: freezes mid-move 1.9 % of frames -> 0, biggest jump 7.93 -> 0.70).
- **Lag spikes:** First switch to first person 865 ms -> ~45-65 ms; summoning a mount in first person 418 ms -> ~45 ms; Trans Up 400-880 ms -> ~30-40 ms (shaders are prepared when the map loads).
- **Shield:** Full shield when you log in and when you respawn.
- **Dungeons:** One broken dungeon in the original files (181) could crash the whole server; now only that dungeon closes and its players are moved out.
- **Holy Water of Almighty:** Remote mailbox, remote storage and the remote shop work while the service is active; the enhancement bonus (+5 %, not above +11), EXP / DIL / drop scrolls, Party Warp and the Battle helper Potion Set follow the item text. NPC warp from the map needs the premium service (otherwise you walk there); the Deka Pass premium track follows the Global rules. GMs can set VIP Points.
- **Custom maps:** Ordinary players can enter a server's published custom maps (/custommap, the M map list, the Custom Maps NPC).
- **Disk space:** Desktop game windows no longer leave their throw-away browser profiles behind (16 GB had piled up).

## 2.1.2 (built 2026-10-04, shipped inside 2.2.0)

- **Fresh install:** The local admin gets the 15 max-level showcase characters. Existing admin characters are never touched.
- **Emotes:** The Action list plays the first emote and the same emote twice in a row; armed characters and GMs no longer have their emote cancelled by the combat stance; a refused emote (dead, fishing, casting, riding) says why in chat.
- **Battlefields on a normal install:** Arena, DK Square, Training Camp, Race, channels and the observer read the prepared client data (they could fail with "Shared world is temporarily unavailable").
- **Personal shop:** The window can be dragged by its title bar again; the Shop Name box sits inside its own frame.
- **Black Wizard orbs:** Orbs with a left-hand model show both orbs and keep orbiting while running and on the character screen (the orbit while running is engine-chosen).
- **Global updates:** A client table saved with a byte-order mark no longer breaks the rebuild.
- **Gem glow:** The 1-4 gem brightness steps from 2.1.1 are removed: the game data has no per-gem-count rule, so any socketed weapon shows its authored effect.
- **GM teleport:** Ctrl+click teleport works online (ground, Teleport-tab minimap, Players-tab map) and keeps working after other GM commands. The HUD minimap no longer teleports.
- **Map window (M):** Each NPC row has Add / Del (favorite) and Move for everyone, TP for admin / GM accounts; event NPCs show an EVENT tag.
- **First person:** All 15 classes reworked: weapons that were out of view while standing are visible, oversized ones no longer fill the screen, the Segita Hunter bow sits at the hand, and the Black Wizard's coat sleeve no longer sweeps across the view. Framing values are engine-chosen / fitted (the game has no first-person view).
- **Tab weapon swap in first person:** The weapon lowers, swaps and comes back up (about 1 second; engine-chosen, the data has no swap animation).
- **Shield:** The awakening grade adds its shield amount.
- **Character and D-Shop previews:** No longer dim (the preview light levels are engine-chosen).
- **Launcher:** The "List your server publicly?" warning opens with Cancel selected instead of all its text highlighted.

## 2.1.1 (2026-10-03)

- **Aura glow:** Glowing weapons and refined gear cast a soft coloured halo in the world and in the character preview window, hidden behind walls. Built like the client's own glow and blur pass; radius and strength are fitted to Global screenshots (FITTED, not read from the data).
- **Icon halo:** Inventory and equipment icons get the wide soft "ghost" halo seen on Global.
- **Effects through walls:** Gem glow and sparkles no longer show through walls (measured 66,768 stray pixels down to 4).
- **Refinement orbs:** The +15 / refinement texture scroll no longer jumps back at every loop (largest per-frame jump 0.30 down to 0.003).
- **Battle Support (Auto Hunt):** The window is back with its real panel art, tabs, close button and radius dropdown (8 / 12 / 16 is engine-chosen). Some option boxes and slot buttons stay inactive because no data says what they do.
- **Damage numbers online:** PvP blocks show the Block word, heal and MP numbers show, crit and block hit sparks play, and basic attacks can crit on the server using your Critical Rate. Yellow numbers are critical hits.
- **Exact movement speed:** The server no longer caps speed to 1-6 units/s; buffs and slows match the game data (about 0.7 to 7.9), so speed buffs no longer rubber-band. Covered by a test of 28,980 class x buff combinations.
- **Saved logins:** "Save account" keeps a server-issued token (never your password) on your PC under Windows protection, bound to that one server. Accounts are per server.
- **Public server list:** Listing your server asks first with a warning and records your consent; Settings switch, directory address box and connection test. The project runs no public directory.
- **Host IP protection:** Hosting is relay-only by default (no LAN address is shown or copied); a direct host listens on this PC only until you tick "Allow direct LAN connections". Relay gateway: 24 connections per address; directory: 60 list requests a minute. Four setup buttons (On this PC / VPS / Vercel / Cloudflare) write guides; they deploy nothing.
- Checked, no change needed: Ardeca's pixelated textures are the map data's own nearest-pixel filtering; item sizes follow the game data (bows 2x4, starter Short Bow 1x3, shields 2x3, Dual Blades 1x4); GM Items +11 to +15 exist where the item family goes that high.

## 2.1.0 (2026-10-03)

- **Refinement glow:** +7 / +9 / +15 armor and weapons glow in their tier colour (+15 purple) in the world and on the character screen, with a slow pulse and a tier-coloured edge light. Colours come from the original tier textures; the rim light and pacing are ENGINE-CHOSEN.
- **Socket gems colour the weapon:** elemental gems give a glow and mist in the gem's colour in your hands, on the inventory icon and on the character screen.
- **Auto-attack on moving monsters:** the character keeps chasing until the swing's hit frame will still reach the monster, then lands the hit — no more repeated swings without damage.
- **D-Shop:** pages, tabs and the Wings catalog no longer open empty; pictures fill in as they finish and the next pages are prepared while you browse. Other windows are built in idle time, so panels open almost instantly.
- **Download:** a normal ZIP plus a separate -source.zip with the engine files as plain files.
- **Launcher:** first-time setup on PCs without Node.js hardened (the "AppendText" error at 8 % can no longer stop setup).
- **Inventory:** refined weapons (+7 and up) glow in their tier colour in the inventory; gem weapons show the glow as an outer aura so the texture stays visible.
- **HUD:** removed a stray crossbow-icon counter that duplicated the buff bar.

## 2.0.0 — Full Release (2026-10-02)

- Colosseum, Siege War, DK Square, Arena and the event modes completed (see Features).
- PvP damage reads all 22 Global PvP option codes (it used 6).
- Guild storage / skills / board / rankings / alliances, messenger chat, chat item links, party finder, inspect, character trade, name change, personal shops, consignment, coin shops, wing services, skill master.
- Attendance and connect rewards, DK channels, multi-channel, per-map caps, request / exchange quests, production lists, option-change tables, costume upgrade.
- Visuals checked against the original formulas: materials, textures, terrain brightness, fog, LOD and view distance, wing animation speed, tooltip and HUD colours. Socket gems use the original effect textures, colours and pulse keys.
- Correct inventory sizes and socket layouts for every weapon and shield; HP / MP potion icons fixed.
- Auto-attack stops and attacks as soon as a moving monster is in range; smoother walk / run loops.
- Compressed game-data/map responses, versioned caching, background image decoding, progress reporting; server performance improved in the tested 52-player scenarios.
- New native launcher (Dashboard, Worlds, Hosting, Settings, server name on the HUD, instant admin sign-in after a restart); safer first-time installer cleanup.
- Final 2.0 fixes: Alokes and Trie Muse hand attachment points; inventory / F-slot swaps keep the displaced item on the cursor; costume removal and owner shutdown countdown; Blitz checks the caster's hidden state; a bounded ENGINE-CHOSEN contact allowance (0.5 map cell for 600 ms, once) for normal attacks on moving monsters; natural shield capacity from arithmetic recovered from a legacy server executable (monster damage bypasses the PvP shield); six top-left HUD buttons in two rows; inventory enhancement previews use the original effect scenes.

## Earlier builds (release candidates and alphas)

- **Alpha 1.0.1:** Server-wide world chat with a cooldown (`/global` = world, `/map` = map shout); first-person target selection with bounded aim assistance; one bounded retry for a transient auto-attack range rejection; enhancement highlights toward warm gold with a stronger shimmer; the Battle Support Start / Cancel handler repaired and its loop no longer interrupts a busy skill; rebuilt Client.exe; a normal ZIP instead of a self-extracting file.
- **Alpha 1.0:** One-file RUN-ME-FOR-GAME.exe installer; update path for existing installs; first-person view for all 15 classes; vehicle and mount bindings (the vehicles without a visual binding in the data refuse to summon); GM Command Center (F10 or /GM), Item Builder with GLB import and Map Builder with Xbox-style controller support.
- **Release Candidate 3:** Packaged and published with an installer hotfix for fresh PCs (installer logging fix).
- **Release Candidate 2:** Install by placing the engine folder beside the game's data and bin folders and opening engine\Client.exe.
