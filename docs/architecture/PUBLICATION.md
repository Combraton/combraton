# Public architecture edition

Edition: `public-development-v1-20260913`. Source: `architecture-v1-20260912`.

The reviewed architecture is now distributed by ownership: shared product semantics in Combraton, execution specifications in PIO, memory specifications in CBR, and interoperability in Protocol. Each document has one authoritative repository. Cross-repository links are navigation links to main; an implementation task must record the actual commit it used.

The organization and repository names are **Combraton**. Historical product prose still uses **Comreton**; it describes the same product, not a fifth system. Local branding is not evidence of a different contract.

## What changed in this edition

All 25 current architecture chapters and four referenced diagrams were imported. Relative links were adapted to repository ownership. Private machine paths were replaced. Links to material outside the current chapters now lead to the historical-material explanation below. Publication headers identify the new edition. Repository-creation status and public entrypoint/authority wording were updated so excluded local archives or the HTML edition are not presented as available public sources. Historical links are labeled as not included.

[The import manifest](source-import.json) records original paths and SHA-256 hashes alongside the hashes of the published editions. The hashes intentionally differ for edited Markdown. This is provenance for the initial import, not a checksum lock that prevents future reviewed edits. Git history records later changes.

[DEVELOPMENT](../DEVELOPMENT.md) supersedes earlier bootstrap sequencing: use current external harnesses to ship roughly v0.1 of all four products before Combraton self-development. It also records repository names and development practices. It does not change product ownership or turn optional product templates into mandatory stages.

## Authority

The current owner's instruction establishes task authority. Record durable changes before dependent work relies on them. [BASELINE](BASELINE.md) and [DECISIONS](DECISIONS.md) establish accepted product boundaries; shared and domain specifications elaborate them. New cross-system architectural decisions belong in [decision records](../decisions/README.md), explicitly naming superseded sections. Protocol schemas and conformance fixtures, when implemented, must be versioned in Protocol. Research proposes or explains; it does not silently amend a spec.

No product executable, selected SDK, security guarantee, benchmark or shipped milestone follows from these documents. Code and test results are observations; discrepancies against intended semantics must be reconciled explicitly.

## Historical material

The original design workspace also contains old proposals, archived source snapshots, dated review reports, memory reading guides, validation reports and a generated HTML reading edition. They are not part of this public canonical import. Links redirected here mean **historical material not published**, not “this file contains that report.” Their titles in imported chapters preserve provenance, but cannot be used as a hidden implementation requirement.

The original local manifest and HTML validation reports describe the earlier local corpus, not the public repositories. Current public validation is described in [verification](../VERIFICATION.md). Markdown in the owning repositories is authoritative; there is no published HTML reading edition in this setup.

If a task needs a missing historical source, retrieve and review that specific source explicitly. Do not invent its contents or treat a title as evidence.

Redirected historical paths:

- `architecture-guide.html`
- `cbr/memory-guide/02-research-reading-guide.md`
- `cbr/memory-guide/03-memory-as-code-review.md`
- `reference/ARCHITECTURE-BASELINE-20260912.md`
- `reference/CBR-DREAMING-AND-TIMELY-CONTEXT-REVIEW-20260912.md`
- `reference/INTERNAL-REFINEMENT-20260909.md`
- `reference/SOURCE-AUDIT.md`
- `reference/VALIDATION.md`
- `reference/architecture-baseline-20260912.json`
- `reference/original-20260908/README.md`
- `reference/reading-edition-sources.json`
- `reference/reading-order.json`
- `reference/revisions/before-architecture-baseline-20260912/manifest.json`
- `reference/source-checks.json`

## Changes after the initial public import

[ADR 001](../decisions/001-standalone-first-and-evaluation.md) records the accepted standalone-first/client/evaluation update. The initial `source-import.json` hashes remain historical provenance for the first publication; current files can differ after reviewed changes, whose exact versions are in Git. Do not refresh the original import hashes to erase that distinction.
