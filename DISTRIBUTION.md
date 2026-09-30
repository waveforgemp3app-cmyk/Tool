# Tool-only distribution

Distribute the output of `node tools/build-release.mjs`, not a copy of this working folder or the installed game.
The output is a new directory under `engine/dist` containing an `engine` folder, a checksummed file manifest and
instructions. The release contains engine source, a compiled Client.exe and its C# source, launcher/import tools,
three newly generated launcher PNGs, an identical connector-logo copy and an icon, and the required MIT-licensed Three.js files and notice.
Art prompts, tests, proof fixtures and release-building tools remain in the development workspace, outside the download.
Run `npm run build:release` on Windows to rebuild the executable before packaging. No files are uploaded or
published by the builder.

The builder removes embedded generation credentials and identifiers from every release PNG; it keeps their
pixel data unchanged. The working illustrations remain intact. The icon contains only the resampled images and
ordinary color/resolution information. Upstream copyright and author notices remain in the dependencies.

After integration is complete, review the new output with `node tools/audit-release.mjs <release-folder>` and add
`PRIVACY-AUDIT.txt` describing the exact reviewed scope, counts and limitations. Then run
`node tools/encrypt-release.mjs <release-folder>` to create a compressed RAR with encrypted content and filenames.
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
