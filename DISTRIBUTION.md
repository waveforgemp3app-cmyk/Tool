# Tool-only distribution

Create the distributable with the frozen packaging commands below. The default `node tools/build-release.mjs`
produces a marked development copy; archive tools refuse it. Never distribute this working folder or the installed game.
The output is a new directory under `engine/dist` containing an `engine` folder, a checksummed file manifest and
instructions. The release contains engine source, a compiled Client.exe and its C# source, launcher/import tools,
three newly generated launcher PNGs, an identical connector-logo copy and an icon, and the required MIT-licensed Three.js files and notice.
Art prompts, tests, proof fixtures and release-building tools remain in the development workspace, outside the download.
Use `npm run build:release` on Windows for a development rebuild. Complete all source and packaging changes
before capturing the release freeze. No files are uploaded or published by the builder.

The builder removes embedded generation credentials and identifiers from every release PNG; it keeps their
pixel data unchanged. The working illustrations remain intact. The icon contains only the resampled images and
ordinary color/resolution information. Upstream copyright and author notices remain in the dependencies.

After integration is complete, review the new output with `node tools/audit-release.mjs <release-folder>` and add
`PRIVACY-AUDIT.txt` describing the exact reviewed scope, counts and limitations. Then run
`node tools/encrypt-release.mjs <release-folder> --freeze-proof <private-proof.json> --engine <frozen-source-root>`
to create a compressed RAR with encrypted content and filenames. The payload must have been built from that freeze.
The tool generates a fresh 32-digit decimal password, checks integrity and wrong-password rejection, and compares
every extracted file's hash with the audited input. It writes the password and SHA-256 companions beside the
archive, outside its contents. Keep the password separately when sharing access. The plaintext release is retained.
Do not archive this working folder. Encryption does not establish distribution rights or prevent takedowns.

The allowlist excludes original `data`/`bin`, generated `gamedata` tables, extracted website artwork, screenshots,
private account/session stores, forum content, logs, downloaded runtimes and generated caches. The recipient supplies their own
compatible client installation. Preparation reads that local installation and creates its tables and artwork on
that recipient's computer. It does not download the official client or fetch updates from the publisher.

The installed working folder is not suitable for sharing: it contains proprietary derived content and may contain
private accounts. Do not add generated files back into the release archive. Keep the distribution manifest and
third-party notices. Select distribution terms for your own code separately; this project has no blanket license
grant covering the original game.

## Legal review still needed

This packaging boundary reduces redistribution of the original game's content; it does not establish that the
engine, import process, alternate service, branding or use complies with the applicable license or law. We have
not verified the particular Global client license accepted by each user, the provenance of every source line,
or a specific state's law. Get qualified IP counsel to review the exact package and applicable game terms before
a public release, or obtain the relevant rightsholder's permission.

In the United States, federal copyright law is relevant in addition to state law. The Copyright Office explains
that owning software does not provide unrestricted rights to distribute its copies, and the software license
also matters: https://www.copyright.gov/help/faq/faq-digital.html

17 U.S.C. 1201 includes anti-circumvention rules and a limited interoperability provision with conditions; it is
not a blanket exemption for any game engine or tool:
https://uscode.house.gov/view.xhtml?req=%28title%3A17+section%3A1201+edition%3Aprelim%29

The included unpacker supports the observed uncompressed pack layout. It does not implement account/license
bypasses or promise compatibility with future encrypted or unknown formats. A future format change requires
technical and, where applicable, legal review.

Separate mesh, skeleton and animation parsers decode supported obfuscated asset
formats. The outer pack reader's plain copying does not establish that every
parser avoids access-control issues. Assess the actual formats and use under the
applicable terms and law; no blanket interoperability exemption is claimed.

The current Global website links to UBIFUN Games Terms of Services dated
2025.01.01: https://www.ubifungames.com/Support/Policy?type=g . That reference does
not establish which agreements a particular installation accepted or that the
tool has permission. The exact client agreement, operating policies and written
permissions still need review.

Browser hosting sends imported assets and generated tables to players. The
tool-only archive boundary does not cover that separate delivery, nor does it
clear screenshots or authoring exports. Review their publication permissions
independently. Overlaid tools do not remove underlying game imagery.

## Frozen packaging routes

The default build-release command produces a marked development copy. Archive and installer tools refuse it. Read-only audits, source enumeration and launcher compilation remain available for development.

After all source and packaging changes are integrated, capture an explicit source/pipeline freeze outside the payload. Use the finalizer with --freeze-proof in every distributable mode. The one-file mode creates the two-file wrapper; legacy mutable hotfix/password-reuse commands are disabled.

Direct payload build: node tools/build-release.mjs --freeze-proof <private-proof.json> --output <new-payload>. Direct engine-only encryption: node tools/encrypt-release.mjs <frozen-payload> --freeze-proof <private-proof.json> --engine <frozen-source-root>. Direct build-installer.ps1 requires -FreezeProof and uses the same source/payload/privacy gate before and after compilation.

Source clones must match the executing packaging pipeline. Historical baseline releases are read-only audit inputs, not substitutes for current frozen source. Keep proof/identity records outside the distributable.

Synthetic native tests use -DevelopmentFixture with an explicit tiny development-fixture manifest in a disposable evidence directory. Their executables contain a marker that disables normal launch; ordinary archive/resource validation refuses that marker. The default encryption regression creates no archive; --real-archive explicitly tests only the complete frozen invented fixture.
