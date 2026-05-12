# Requirements traceability

> **Status:** skeleton — Markdown conversion of the requirements spreadsheet is pending.

For now, the authoritative requirements artifact is the JIRA-friendly spreadsheet:

- [vedam_requirements.xlsx](../vedam_requirements.xlsx)

Sheets in that file (per pre-2026 lock-in):

- **Requirements** — REQ IDs, statements, priority, status.
- **Modules** — module list and per-module intent (kept in sync with `vedam/modules/*/README.md`).
- **Glossary** — duplicated here in [14_glossary.md](./14_glossary.md) for browser-friendly reading.
- **Decisions** — duplicated here in [decisions.md](./decisions.md).
- **Open questions** — duplicated here in [12_open_questions.md](./12_open_questions.md).

---

## Roadmap to Markdown

When the spreadsheet stabilises, this page will be replaced by:

- A YAML or JSON requirements bank under `requirements/` (REQ IDs as keys).
- Generated Markdown tables in this file from that bank.
- A small Python or Node script in a new `tools/` directory to re-render the tables.

Conversion is deferred until requirements are settled enough that round-trip churn is not painful. The spreadsheet remains the source of truth in the meantime.
