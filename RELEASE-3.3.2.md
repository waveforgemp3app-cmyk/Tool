# 3.3.2 — Automatic Updates, Bot Teams & Visual Fixes

[Download DK-3.3.2.zip](https://github.com/waveforgemp3app-cmyk/Tool/releases/download/v3.3.2/DK-3.3.2.zip) · [All releases](https://github.com/waveforgemp3app-cmyk/Tool/releases)

Automatic update notices, quest/dialog and GM spawn corrections, desktop UI alignment, authored skill/wing effects, and bot combat, teamwork, progression and load management. Bots remain OFF by default.

<details>
<summary>01 | Automatic updates in the launcher</summary>

- Checks for stable GitHub releases when the launcher opens and every five minutes; no notification checkbox to enable.
- A dark-and-gold update notice offers Click to install, Later and a link to the release notes.
- Downloads run in the background with a reusable cache. The updater checks the exact repository, release tag, asset name, byte count and GitHub SHA-256 digest.
- One update worker per installation prevents duplicate installers. Reopening the launcher shows the queued, waiting, installing or retry state.
- The worker runs outside the game folder so locked launcher/runtime files can be replaced after closure.
- Updates wait for that installation’s world, client and launcher to close. They do not force-stop a running game.
- Owned-install checks, safe ZIP extraction and transactional rollback protect replacement. Accounts, server settings, SQL selection, native profiles and valid preload receipts are retained.
- Offline checks leave the installed game available. Failed downloads can be retried; a partial or invalid download is not installed.
- Launchers from 3.2.2 and earlier need one manual installation of 3.3.2 before these automatic update checks become available.

</details>

<details>
<summary>02 | Quest flow, GM spawning and interface corrections</summary>

- After a quest is completed, the open NPC dialog refreshes eligibility for the next quest instead of retaining stale requirements and producing the reported 1050 refusal.
- GM callmonster publishes newly spawned actors after persistence completes, so an extra tick or attack is not needed to reveal them.
- Desktop interface fitting now keeps authored pixels at 1024×720 and larger, correcting the smaller font/UI scale in a 1280×720 window.
- Chat uses the native font/index metrics and 16-pixel line spacing instead of the older generic presentation.
- The minimap environment dial follows the world’s environment clock and uses the intended aperture.
- The potion belt repairs positions overlapping the HP/MP panel while preserving other saved drags and bottom anchoring when the window resizes.

</details>

<details>
<summary>03 | Equipment, wings and map effects</summary>

- Removed the default 24-scene equipment-effect cutoff and the 64-definition cache rejection. Existing explicit quality limits, distance culling and cleanup remain active.
- Repeated effect preloading no longer accumulates particle/decal offsets. Frozen anchors also restore their base rotation.
- World-space particle and decal attachments now apply authored bone-path translation, rotation and map scale.
- Wing controls can fall back to the wearer’s skeleton when the named attachment bone is absent from the wing rig.
- Mirrored bones retain their reflection: local offsets and effect geometry stay on the correct side, with particle/decal offset handling and billboard compensation.
- Map effect visibility follows the world’s configured range; the old separate 48-nearby-entry limit no longer silently cuts off nearby placements.
- The cross-catalog effect resolver retains same-file precedence and recovers a cross-file scene only when matching definitions are unambiguous. Conflicting definitions are not guessed.

</details>

<details>
<summary>04 | Authored skill-effect layers</summary>

- Added tailstep trail presentation for sprite ribbons, mesh afterimages and particle copies, with bounded lifetimes and cleanup.
- Baked trail copies own their UV/index buffers so later updates cannot overwrite another copy’s geometry.
- Over-range color keys use the saturated fixed-function color interpretation rather than an unintended HDR boost; the earlier boosted presentation remains a comparison policy.
- Effect meshes apply mesh_status UV scrolling.
- Skinned and unskinned effect meshes retain authored environment/specular maps.
- The verified movemevt attachment typo resolves to movement; unknown bone names are not broadly renamed.
- Added animPath attachment fallback and mesh rendering for leaftype mesh particles.
- Distortion/refraction approximation remains OFF by default because its original shader behavior is not established.
- Trail timing and animPath interpretation remain documented engine interpretations; these changes are not a claim of pixel-identical Global rendering.

</details>

<details>
<summary>05 | Bot combat decisions and teamwork</summary>

- Skill selection uses the server’s reach rules, approaches out-of-range targets and backs off repeated refusals per skill.
- AoE selection considers engaged versus idle enemies and keeps the focus target inside a moved blast center.
- Crowd control avoids targets already controlled or claimed by another party member.
- A short threat ledger, shared focus and target stickiness support healer/low-HP ally protection.
- Survival decisions include role/risk potion thresholds, fast-health-loss reactions, defensive skills, urgent heals and healer MP reserves.
- Bot field parties gain role-aware assistance, range-limited shared perception, readiness checks and formation positioning.
- Peeling can use a tank or the nearest suitable melee member instead of requiring a tank-only path.
- Stuck recovery tries ordinary repathing, alternate approaches and backtracking with bounded backoff. It does not teleport actors or bypass collision.
- Archetype-derived caution, commitment and reaction parameters feed combat decisions; explicit overrides and behavior kill switches remain available.

</details>

<details>
<summary>06 | Bot progression and population variety</summary>

- Nine deterministic player archetypes provide casual, regular and hardcore pacing without rewriting saved profiles or granting free gear/stats.
- Idle thinking and task choice vary by archetype while retaining legal activity, location, accepted-quest and instance constraints.
- Town duties use bounded preferences, dwell rotation and fairer admission; a departed-player city-duty crash is fixed.
- Time-of-day simulated login/logout schedules are separately opt-in and remain OFF by default.
- The bot planner skips talk-only exchange quest 53 instead of repeatedly requesting an invalid normal accept. This is separate from the player dialog fix.
- Quest feasibility checks supported objectives and available field spawns. Bounded stall handling defers temporary blocks and uses ordinary abandonment for permanent blocks; it does not abandon while a human party member is present.
- Loot decisions remember refusals and check bag fit before walking to a drop.
- At bag pressure, bots can sell eligible spare rank-0 gear or use placed storage through ordinary actions, honoring protected gear, wallet caps, deposit fees and capacity.

</details>

<details>
<summary>07 | Bot load management and preservation</summary>

- Bot-only saves can share atomic file writes; extra coalescing delay defaults to zero. Human/session saves remain separate and SQL acknowledgement is preserved.
- Combat option-name normalization is memoized and option handling uses a single pass while preserving calculation results.
- Routing caches native graph edges and uses indexed breadth-first traversal.
- Dormant-roster updates use a cached row index and per-map candidate lists.
- The optional bot backpressure governor measures event-loop delay and human request latency, with hysteresis before reducing optional bot decision concurrency or pausing new bot admissions.
- Human requests are not throttled by this governor. Bots remain OFF until the host enables them.
- These changes do not promise 50× intelligence, a fixed loading multiplier or zero stutter on every machine.

</details>

<details>
<summary>08 | Simple setup and release scope</summary>

- Fully update Global with its official launcher and keep a backup. Extract the WHOLE DK-3.3.2 ZIP; keep every Engine file together.
- Put your Global download beside Engine, or choose its folder when asked. Open Engine/Client.exe and let first preparation finish.
- Create an account, review Options and press the green Launch button. Choose DX11 Client for a window or DX11 Fullscreen for borderless play.
- Existing users should back up saves and close their world/game/launcher before opening the new Client.exe and selecting the owned installation if asked.
- SQL remains optional beta storage under Options > SQL / Storage. Missing SQL Express needs Microsoft terms and Windows administrator approval; remote provisioning is not automatic.
- This is an engine-only package with required dependency licenses and the offline Global reference library. It excludes original Global assets, development accounts, passwords and SQL backups.
- The desktop game window uses WebView2 with ANGLE/D3D11 and your supplied assets; it does not execute the original Global client.
- Specific weather/firefly resources, local lighting/fog behavior and some missing-resource/glow cases still require verification. Full Global visual parity and zero-stutter large fights are not claimed.
- Earlier guild emblem, Party chat, fullscreen, damage-number and 3.3.1 installation fixes remain included; they are historical work, not reannounced as new 3.3.2 fixes.

</details>

The named ZIP is the engine download. GitHub’s automatic source archive contains this documentation repository. Supply your own lawful, updated Global files. SQL and bots retain beta limitations; no new Android package is announced.

[3.3.1 installation hotfix](https://github.com/waveforgemp3app-cmyk/Tool/releases/tag/v3.3.1) · [3.3.0 Client & SQL update](https://github.com/waveforgemp3app-cmyk/Tool/releases/tag/v3.3.0) · [Earlier detailed first-post history](docs/archive/3.3.1-first-post.txt)
