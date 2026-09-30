# Dekaron Engine — Release Candidate 2

Unofficial engine and launcher. Not affiliated with, endorsed by, or supplied by the original game's publisher. Supply your own lawfully obtained, compatible, updated client. Original game data and binaries are not bundled.

## Download

Get **Dekaron Online - Release Candidate 2.rar** from this repository's Releases page. This is a release candidate, not a guarantee of complete gameplay compatibility.

Archive password: `18390072856997798173715727436699`

SHA-256: `6d618228820762c79814f29af3b13d615b29002f1452dc6a19bf93612ca98ee1`

## Install — Windows

1. Install and fully update the official Dekaron client, then close it.
2. **Back up the entire installation. After confirming the install warning, this tool permanently deletes everything in the selected game root except `data`, `bin`, `engine`, and the replacement `Client.exe`.** Use a separate test copy first.
3. Extract the release archive using the password above.
4. Place the complete `engine` folder directly inside the game installation, beside `data` and `bin`.
5. Open `engine\Client.exe`, click **Start**, and confirm the cleanup warning. The launcher prepares and validates local game data, cleans the root, and creates the **Dekaron Online** desktop shortcut. When ready, use the local-owner auto-sign-in option or create an account on the selected server.

First preparation can take several minutes. Original root files remain until preparation succeeds. Subsequent launches reuse prepared data unless its inputs change. The final game root contains `data`, `bin`, `engine`, and `Client.exe`.

Accounts belong to the selected server. Local administrator access requires installation-owner authorization; there is no public universal administrator password. Internet hosting requires separately configured hosting/network services.

## Verification and limits

The package passed its manifest/privacy checks, encrypted-archive integrity test, wrong-password rejection, and extracted-file hash verification. A fresh installation produced the expected root layout and desktop shortcut. Additional fresh-install acceptance and a live retest of the GM teleport arrival fix remain pending. Some game systems and native visual parity remain incomplete; see the included `engine/docs/MULTIPLAYER.md`.

The privacy review checked known owner and machine identifiers, private state, metadata and secret patterns. It is not a guarantee against every possible identifier. Newly installed runtime data is private and must not be redistributed.

## Rights and distribution

Read [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and [DISTRIBUTION.md](DISTRIBUTION.md). Third-party components retain their own licenses and notices. No project-wide open-source license has been selected, and this repository does not grant rights to the original game's code, data, artwork, names or services.

Packaging without game assets does not establish legal clearance. Applicable game terms, code provenance, intellectual-property rights and any interoperability restrictions require review. Do not use this project to bypass authentication, access restrictions or license checks. Encryption does not prevent takedowns or grant distribution rights.

This is experimental software. Keep backups and review the installer before using it on valuable data. Do not publish accounts, tokens, machine details, installed game data or runtime caches in bug reports.
