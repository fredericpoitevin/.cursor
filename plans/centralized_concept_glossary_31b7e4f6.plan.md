---
name: Centralized Concept Glossary
overview: Add a single canonical glossary page for core agentic AI terms and link it into the existing Basic curriculum flow, while keeping current concept docs lightweight and consistent.
todos:
  - id: create-glossary-page
    content: Create `content/ops/basic/glossary.md` with canonical definitions and entry template.
    status: completed
  - id: add-nav-entry
    content: Add glossary page entry to `CURRICULUM.basic.pages` in `index.html` under the concepts section.
    status: completed
  - id: link-from-concepts
    content: Add a short pointer in `content/ops/basic/concepts.md` directing readers to the glossary for canonical definitions.
    status: completed
  - id: define-governance
    content: Add brief editorial rules in glossary to keep terms consistent and avoid duplicated definitions.
    status: completed
isProject: false
---

# Centralize Core Concepts

## Recommendation
Create one canonical glossary page and treat every other mention as a pointer to that source of truth.

- Add a dedicated page: [content/ops/basic/glossary.md](/Users/fpoitevi/sw/psagents/content/ops/basic/glossary.md)
- Include concise definitions for `agent`, `model`, `harness`, `tooling`, `RAG`, `SKILL`, `MCP`, plus optional related terms (`context window`, `evaluation`, `guardrails`).
- Use a consistent entry template per term:
  - **Definition (1-2 lines)**
  - **Why it matters in this curriculum (1 line)**
  - **Example at LCLS/Ops (1 line)**
  - **Common confusion (optional, 1 line)**

## Navigation Integration
Wire the glossary into the existing curriculum navigation in [index.html](/Users/fpoitevi/sw/psagents/index.html):

- Add a new page item under `CURRICULUM.basic.pages` with:
  - `id: "glossary"`
  - `title: "Core Terms Glossary"`
  - `path: "content/ops/basic/glossary.md"`
  - `section: "concepts"`
- Place it directly after `concepts` so users encounter it early.

## Keep Existing Docs Lean
Update [content/ops/basic/concepts.md](/Users/fpoitevi/sw/psagents/content/ops/basic/concepts.md) to avoid duplicate definitions:

- Keep the narrative framing (three layers) as-is.
- Add a short "See glossary" pointer near first use of terms that are now canonicalized.
- Preserve explanatory depth in concepts; keep glossary as the terminology reference.

## Editorial Rules (to prevent drift)
Define lightweight rules at the top of the glossary page:

- Glossary is canonical for term definitions.
- Other pages should link, not redefine.
- New terms are added only when used in at least one curriculum page.
- Keep each definition short and implementation-neutral when possible.

## Why this fits your repo
- Your app already loads markdown pages from `CURRICULUM` paths, so this is a small, low-risk content/navigation change.
- `basic/concepts.md` already introduces model/harness/tooling and SKILL framing, making it a natural place to point to a shared glossary rather than repeating wording elsewhere.