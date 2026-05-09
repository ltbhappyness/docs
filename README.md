# Vedam design artifacts (tracked)

**Repository:** [github.com/ltbhappyness/docs](https://github.com/ltbhappyness/docs) — published specs for implementers; complements [`ltbhappyness/vedam`](https://github.com/ltbhappyness/vedam).

| File | Purpose |
|------|---------|
| [templates/technical_document.docx](templates/technical_document.docx) | Word template |
| [vedam.docx](vedam.docx) | **Vedam v0.1-draft** technical design (yellow paper) |
| [vedam_requirements.xlsx](vedam_requirements.xlsx) | Requirements, modules, glossary, decisions, open questions (JIRA-friendly) |

**Regenerating** (optional — figures are high-res PNG embedded for clarity):

```bash
docs/build/.venv/bin/python docs/build/build_docs.py
docs/build/.venv/bin/python docs/build/build_xlsx.py
```

Raw figures and the Python venv live under `docs/figures/` and `docs/build/.venv/` and are **gitignored**; keep them locally if you rebuild.
