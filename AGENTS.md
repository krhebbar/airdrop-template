# AGENTS.md

## Purpose
This file defines how AI agents and human contributors must operate when authoring documentation for the **Airdrop Template** repository. The mission: produce a clean, runnable, Fumadocs-compatible documentation set that teaches engineers how to **build a successful airdrop connector** (with a cookbook/codelab using Todo + Notion examples).

---

## Core Objective
Create a complete documentation suite that teaches how to develop, test, and deploy an airdrop connector using the airdrop-template repo as ground truth. This includes:
- Concept docs (Introduction, Architecture, Concepts)
- Quick Start
- “Your first airdrop” guide (codelab)
- Cookbook examples (Todo + Notion connectors)
- API reference excerpts (grounded in code)
All output must be in **Fumadocs MDX** and placed under `content/docs/airdrop/`.

---

## Scope (Allowed / Not allowed)
**Allowed**
- Read & analyze everything in the local airdrop-template repository (`/` and `src/`).
- Create/modify MDX files under `content/docs/airdrop/`.
- Perform web research *only* for third-party service docs explicitly required by the examples (e.g., Notion API). Any external claims must be cited.

**Not allowed**
- Do not change source code except minor non-functional doc-only samples in a `docs/` or `examples/` folder (only with explicit instruction).
- Do not invent product features or endpoints that are not present in the repo or in the referenced third-party docs.
- Do not change infra (CI, package manifests) unless explicitly asked.

---

## Required Pre-read
Before writing, agents MUST read:
- This `AGENTS.md`
- Fumadocs component docs:  
  - https://fumadocs.dev/docs/headless/components  
  - https://fumadocs.dev/docs/ui/components
- Notion developer docs (for Notion cookbook): https://developers.notion.com/  
(Agent should perform live web research on Notion to understand auth and major API flows; cite sources.)

---

## Documentation Rules & Style
- Output format: **Fumadocs-compatible MDX** files with frontmatter (`title`, `description`).
- Visible content must start at **H2**.
- Voice: developer-first, active, concise, corporate but blunt.
- Provide runnable, minimal examples. Show where to run commands, what to expect, and how to verify.
- Preserve exact API signatures, config keys, filenames and repo-derived constants. If missing, leave a TODO with file path references.
- Use Fumadocs components where appropriate: `<Steps>`, `<Tabs>`, `<Files>`, `<Mermaid>`, callouts, etc.
- All code blocks must declare language and include expected output context.

---

## Deliverables (minimum)
Place in `content/docs/airdrop/`:

1. `index.mdx` — Intro, why airdrops, high-level architecture overview.
2. `quickstart.mdx` — Minimal steps to run the template locally (init, configure, run).
3. `your-first-airdrop.mdx` — Full codelab: scaffold → implement → test → verify.
4. `cookbook/todo-connector.mdx` — Cookbook example implementing a Todo connector (simple local or Todoist).
5. `cookbook/notion-connector.mdx` — Cookbook example integrating Notion (auth, read/write basics).
6. `concepts.mdx` — Key concepts: seats, recipients, batching, idempotency, errors, telemetry.
7. `api-reference.mdx` — Extracted reference snippets (config shape, key functions) from `src/`.
8. `examples/` — small runnable snippets referenced by codelabs (if necessary).
9. `README.md` — short authoring notes for maintainers.

Each MDX must have frontmatter and H2-first content.

---

## Process / Execution Flow (how the agent must work)
1. **Scan** the repo: list candidate code files, manifests and example fixtures. Produce a short manifest file `docs-gen-manifest.json` listing what you will document.
2. **Research**: For Notion cookbook, fetch and cite Notion API docs (auth, major endpoints). For Todo example, choose a public Todo API (Todoist) or implement minimal local Todo sample—state your choice and cite URLs if external.
3. **One-file-at-a-time**: Migrate/write one MDX file at a time. After finishing each file, run the validation checklist (below) and commit with a clear message `docs(airdrop): add <file>`.
4. **Validation**: After all files built, run final validation and produce a `docs-health.json` report describing coverage and any TODOs.
5. **Submit**: Create a single batch PR with all files and a short PR description linking to `docs-gen-manifest.json` and `docs-health.json`.

---

## Validation Checklist (per file)
- [ ] Frontmatter present: `title`, `description`.
- [ ] Visible content starts at H2.
- [ ] Uses Fumadocs components where applicable.
- [ ] Code snippets complete and runnable (or marked with TODO if credentials needed).
- [ ] Commands include expected outputs or verification steps.
- [ ] Internal links use relative `.mdx` paths.
- [ ] Any external third-party claims cite the source URL.
- [ ] No invented API endpoints or behavior.

---

## Guardrails & Evidence
- **Ground truth only**: all functional claims must be traceable to file paths in the repo or cited external docs.
- For any decision where the repo is silent, create a TODO and flag for human review — do not guess.
- When referencing code, include a path and optional line range (e.g., `src/connector/notion.ts:32-88`).

---

## Commit & PR policy
- Use one commit per MDX file: `docs(airdrop): add <relative-path>`.
- Final submission: one PR titled `docs(airdrop): initial airdrop docs + cookbooks`.
- Include `docs-gen-manifest.json` and `docs-health.json` in PR root for reviewers.

---

## Success Criteria
- All core docs (index, quickstart, first-airdrop, two cookbooks, concepts, api-reference) present in `content/docs/airdrop/`.
- Each file passes the Validation Checklist.
- `docs-health.json` reports ≥ 90% coverage of public entry points or lists concrete TODOs for gaps.
- PR is ready for review (no speculative content, all external claims sourced).

---

## Notes to Agents
- Be surgical. Focus on documentation quality and traceability, not feature work.
- If you must fetch external docs (Notion/Todoist), include citation lines at the top of the MDX referencing the URLs.
- Leave human-review TODOs for anything requiring infra credentials, private tokens, or assumptions.
