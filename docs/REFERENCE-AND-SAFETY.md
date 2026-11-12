# Reference fork: provenance and safe review

Reviewed on **2026-11-12 UTC**, against the remote default branch `main` at
[`d4c4509ae85f44d6c95b2cdebc5f5746845a3664`](https://github.com/JDKristenson/claude-code-polished-documents-skills/commit/d4c4509ae85f44d6c95b2cdebc5f5746845a3664).
This document describes that baseline, not a promise of future upstream sync.

## Portfolio scope and attribution

**Retain as a reference/learning fork, not an original JD implementation showcase.**
The documentation cleanup and original editable workflow map are the fork's
new contribution; they do not establish authorship of inherited implementations.
Prepared for JD with Reason AI assistance. No skill, script, font, document,
configuration payload, license, or notice is changed by this cleanup.

GitHub's [repository metadata](https://api.github.com/repos/JDKristenson/claude-code-polished-documents-skills)
identifies [michellelandon/claude-code-polished-documents-skills](https://github.com/michellelandon/claude-code-polished-documents-skills)
as both fork parent and network source. The inherited README also links
[promptadvisers/claude-code-polished-documents-skills](https://github.com/promptadvisers/claude-code-polished-documents-skills).
Both public default-head responses resolved to the same baseline commit and tree
`da38458dd20121f5e110b4e68cbad9f38459583a` on the review date:
[parent commit](https://github.com/michellelandon/claude-code-polished-documents-skills/commit/d4c4509ae85f44d6c95b2cdebc5f5746845a3664),
[README-linked upstream commit](https://github.com/promptadvisers/claude-code-polished-documents-skills/commit/d4c4509ae85f44d6c95b2cdebc5f5746845a3664).
Thus no JD-specific source delta is evidenced at the pre-cleanup baseline.
This says nothing about contributions elsewhere or ongoing synchronization.

The complete, non-shallow default history at that baseline has three commits,
all dated 2025-12-03: the initial collection, quick-start prompts, and FireCrawl
setup guide. Their author records name promptadvisers, and their messages credit
Claude Code and Claude co-authorship. Preserve those human/account and AI credits;
namespaces and author fields alone do not prove sole authorship or real-world identity.
Anthropic and community notices remain authoritative for their own material.
No tracked `AGENTS.md`, `CLAUDE.md`, or `CONTRIBUTING` file was found; the README
has contribution guidance. No new upstream contribution is claimed.

## License boundaries

This is **not a blanket MIT distribution**. The root [LICENSE](../LICENSE)
contains MIT text, third-party caveats, dependency references, and a brand disclaimer.
It does not override nested terms. The inventory below is source-based guidance,
not legal advice or permission to redistribute.

- **Restricted document skills:** [docx](../.claude/skills/docx/LICENSE.txt),
  [pdf](../.claude/skills/pdf/LICENSE.txt), [pptx](../.claude/skills/pptx/LICENSE.txt),
  and [xlsx](../.claude/skills/xlsx/LICENSE.txt) have identical Anthropic terms.
  They restrict extraction/retention outside the Services, reproduction,
  derivatives, and distribution, among other acts. Obtain appropriate rights
  clarification before copying, executing, adapting, or redistributing them;
  do not infer rights from the root license or this fork's public visibility.
- **Apache 2.0 skill terms:** algorithmic-art, brand-guidelines, canvas-design,
  frontend-design, internal-comms, mcp-builder, skill-creator, slack-gif-creator,
  theme-factory, web-artifacts-builder, and webapp-testing each carry a nested
  `LICENSE.txt`. Preserve each applicable license, attribution, and required
  modification notices. [Example](../.claude/skills/algorithmic-art/LICENSE.txt).
- **Community fonts:** the [canvas-fonts directory](../.claude/skills/canvas-design/canvas-fonts/)
  contains 27 OFL notice files naming project authors and, where applicable,
  reserved font names. Preserve the individual notices and font-license boundaries.
  No independent font-binary provenance validation was performed.
- **Document Polisher:** no separate nested `LICENSE.txt` exists in its directory
  at the baseline. Do not broaden the root grant to unrelated bundled content.
- **Dependencies and services:** python-docx and optional providers have their
  own licenses/terms. Dependency installation and transitive notice reconciliation
  were not performed. This is not a complete software bill of materials.
- **Brand-inspired themes:** retain the root disclaimer. Brand names do not
  imply affiliation, endorsement, or permission to use protected assets.

The original editable diagram and SVG preview describe the workflow in new words;
they do not embed or reproduce skill payloads or third-party font/document assets.
All inherited notices remain in place. Unresolved rights are not remedied by
archiving; no archive, deletion, feature, or visibility change is part of this work.

## Setup status: NOT RUN

**No installation, build, tests, project scripts, document processing, Claude Code,
MCP server, provider requests, or credential-validity probes were run.** Only
source/documentation checks and rendering of the newly authored diagram preview
were performed. Existing installation and usage sections are inherited examples,
not tested promises. Python 3.8+ and optional Node.js 18+ are inherited declarations,
not independently verified minimum versions.

Source inspection finds:

- `apply_brand.py` imports `python-docx` and reads
  [brand-mapping.json](../.claude/skills/document-polisher/templates/brand-mapping.json),
  which contains ten themes. There is no root dependency manifest or lockfile.
  Two other skills have separate requirements files; `python-docx` alone is not
  a complete setup for the collection.
- Prefer reviewing one selected skill and its license/dependencies before a
  project-local setup. Do not copy the whole bundle globally or overwrite
  existing skill directories. Do not apply broad permission allowlists blindly.
- If authorized later, use an isolated Python environment and explicitly selected,
  reviewed dependency versions. Commands in [SETUP.md](SETUP.md) are examples,
  not reproducibility evidence or instructions that were executed here.
- FireCrawl is optional. The polisher reads local JSON and does not call a
  provider itself. The inherited package names, CLI flags, config paths,
  environment interpolation, tool schemas, pricing, and API behavior in
  [MCP-SERVERS.md](MCP-SERVERS.md) and the quick-start guides are **unverified**.
  Consult current official client/provider documentation before configuring them.
  Custom themes may also be configured manually; a provider is not mandatory.

## Source-inferred document risks: untested

The [polisher source](../.claude/skills/document-polisher/scripts/apply_brand.py)
creates a new document, copies paragraphs first and tables afterward, clears the
first output cell paragraph repeatedly, and saves directly to `output_path`.
It does not explicitly reject equal input/output paths. These observations imply
risks of reordered content, lost multi-paragraph cell content, and overwrite;
they are not runtime reproductions. Image, layout, metadata, and formatting
preservation are not established by this review. No runtime fix was attempted.

Before any future authorized trial, use only a disposable, synthetic DOCX,
keep its original untouched, choose a distinct output path, and inspect content
order, cell paragraphs, images, formatting, and fonts in the target native viewer.
Never treat a successful save as proof of faithful preservation. No real/private
documents were used here, and no native rendering was tested.

## Credentials and diagnostics

Never paste credentials into chat/prompts, shell arguments/history, issue bodies,
tracked JSON, screenshots, logs, or reports. Use the current client's supported
secret store or protected environment injection. Placeholder JSON in inherited
examples is illustrative only; environment substitution must not be assumed.
A `.gitignore` does not prevent leakage through logs, backups, or screenshots.

A presence-only POSIX shell check, if needed in an authorized future local setup:

```bash
if [ -n "${FIRECRAWL_API_KEY:-}" ]; then
  printf '%s\n' 'FIRECRAWL_API_KEY is set (value not shown)'
else
  printf '%s\n' 'FIRECRAWL_API_KEY is not set'
fi
```

This checks only non-emptiness, not format, correctness, permissions, account,
validity, or provider access. It was **not run** in this review. Do not print full
configuration files or parse them with commands that echo their contents/errors.
Sanitize diagnostics locally before sharing. Do not use real keys to validate
these inherited instructions. Follow the provider's revocation process if a
credential has been exposed; do not test whether it still works.

## Editable workflow map

- [Excalidraw source](portfolio-workflow.excalidraw): open/import into Excalidraw;
  all labels, boxes, and connectors are native editable elements, not an image.
- [SVG preview](portfolio-workflow.svg): accessible static companion; no external
  resources or embedded third-party assets. It is not an execution trace.
- [HTML preview](portfolio-workflow.html): theme-aware page using the same map
  content; suitable for local viewing. No provider/client code is invoked.

The map distinguishes inherited source from this documentation contribution,
marks FireCrawl as optional/unverified, and keeps license boundaries separate.
The pinned source snapshot is evidence; the diagram is an interpretation of it.
