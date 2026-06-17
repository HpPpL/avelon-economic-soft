# Sanitization checklist

This repository still contains historical binary artifacts in the base branch. They should be removed or replaced before the repository is made public. This cleanup is documented separately because some PR/review tools reject binary diffs such as deleted `.xls`, `.xlsx`, `.docx`, or `.png` files.

## Required before public visibility

- Remove or replace tracked Excel workbooks: `*.xls`, `*.xlsx`, `*.xlsm`.
- Remove or replace tracked Word/PDF business documents: `*.docx`, `*.pdf`.
- Remove generated report/chart exports under `EconomicProject/Report/Results/` and `EconomicProject/Report/Charts/`.
- Remove local IDE metadata under `.idea/`.
- Remove tracked Python cache files under `__pycache__/`.
- Re-run a keyword and file-extension audit after cleanup.
- Make the repository public only after the binary and sensitive-file audit passes.

## Suggested cleanup command set

Use these commands in an environment that supports binary file changes in commits/PRs:

```bash
find . -type f \( -name '*.xls' -o -name '*.xlsx' -o -name '*.xlsm' -o -name '*.docx' -o -name '*.pdf' -o -name '*.png' -o -name '*.pyc' \) -print
find . -path '*/.idea/*' -print
rg -n "(password|secret|token|api[_-]?key|client|клиент|ООО|ИП)" . -g '!/.git/**'
```

If the results are expected cleanup targets, remove them in a binary-capable workflow and keep only synthetic/demo-safe inputs such as `demo_data/synthetic_project_input.csv`.
