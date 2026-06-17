# Avelon Economic Tooling

> Archived early freelance/client-work project for internal economic analysis and report automation. The code is preserved as historical portfolio work; original client data, reports, and business documents must be audited before public release, with synthetic examples provided for safe portfolio review.

## Project summary

Avelon Economic Tooling is a Python-based economic modeling utility originally built to help analyze investment scenarios for resource-production projects. It read structured spreadsheet assumptions, calculated project economics, ran sensitivity and Monte Carlo-style simulations, and generated Excel/Word-style reporting artifacts for internal review.

This repository is intentionally presented as an archived portfolio snapshot rather than a modern production package. The goal is to show the problem, architecture, and implementation approach while avoiding disclosure of private client information.

## Client-work context

This was an early freelance/internal tooling engagement. The user workflow was spreadsheet-first: domain experts maintained input assumptions in Excel templates, and the Python scripts automated repeated economic calculations and report generation.

Sanitization plan for the public-ready version:

- Treat existing `.xls`, `.xlsx`, `.docx`, generated report, chart, and local IDE/cache artifacts as private cleanup targets before making the repository public.
- Keep this PR text-only so hosting tools that reject binary diffs can still review the portfolio documentation changes.
- Added a small synthetic CSV in `demo_data/` to document the kind of input data the model expected.
- Added `.gitignore` rules to keep future local exports, reports, spreadsheets, documents, caches, and secrets out of the repository.

## Problem statement

Manual evaluation of economic scenarios was slow and error-prone because analysts had to repeatedly update spreadsheet assumptions, calculate financial metrics, compare project variants, and prepare reporting outputs. This tool automated the repeated calculation/reporting steps around an existing spreadsheet model.

## Implemented functionality

The historical code includes modules for:

- Reading named spreadsheet sheets and mapping them into model objects.
- Modeling production profiles, market assumptions, CAPEX, OPEX, taxes, and credits.
- Calculating cash flows, discounted cash flows, NPV, IRR, payback periods, and related efficiency metrics.
- Running Monte Carlo simulations over model inputs.
- Generating Excel and Word overview reports from calculated results.
- Batch-processing multiple example workbooks in the original internal workflow.

## Tech stack

- Python 3.x
- pandas, NumPy, SciPy
- openpyxl, xlrd, XlsxWriter
- matplotlib
- python-docx and docxcompose

## Repository structure

```text
.
├── EconomicProject/
│   ├── Models/          # Economic domain models and financial calculations
│   ├── Operations/      # Monte Carlo simulation logic
│   ├── ReaderWriter/    # Spreadsheet reading and Excel report writing helpers
│   ├── Report/          # Historical Word/Excel overview generation scripts
│   ├── Units/           # Unit conversion helpers and variable definitions
│   ├── Examples/        # Batch-processing script retained without private workbooks
│   ├── Program/         # Historical single-run entry point retained without private workbooks
│   └── requirements.txt # Historical dependency pins
├── demo_data/           # Synthetic, non-client data shape example
├── .gitignore           # Portfolio-safe ignore rules
└── README.md
```

## Running locally

This repository is archived/demo-only while it is being sanitized for portfolio use. The original runnable workflow depends on Excel templates and generated Word/Excel report templates; review `docs/sanitization-checklist.md` before making the repository public.

You can still inspect the code and install the historical dependencies:

```bash
cd EconomicProject
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

The old entry points are:

```bash
python Program/Programm.py
python Examples/MultyExamples.py
```

However, they will require rebuilding a compatible Excel workbook/template layout before they can run end-to-end. See `demo_data/synthetic_project_input.csv` for a safe sample of the assumptions represented by the original spreadsheets.

## Demo data

`demo_data/synthetic_project_input.csv` contains invented yearly assumptions for production volumes, prices, CAPEX, OPEX, and tax rate. It is provided to explain the model inputs at a high level and does not represent any real company, project, field, contract, or client report.

## Limitations and historical status

- Archived early project: code style and packaging reflect the original timeframe and client constraints.
- Not production-ready: no modern CI, typed public API, or reusable package interface has been added.
- Binary cleanup is tracked separately in `docs/sanitization-checklist.md` because this PR intentionally avoids binary deletions that some review tools cannot render.
- Public visibility should only be enabled after confirming the repository remains free of private documents, generated reports, and credentials.

## Suggested GitHub metadata

- Repository name: `avelon-economic-tooling`
- Description: `Internal economic tooling developed as an early freelance/client project.`
- Topics: `client-work`, `freelance`, `internal-tool`, `economic-analysis`, `automation`, `data-processing`, `portfolio`, `archived-project`
