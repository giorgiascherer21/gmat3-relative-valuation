# GMAT3 Relative Valuation

Professional relative valuation pipeline for Grupo Mateus (`GMAT3.SA`) using Brazilian listed peers:

- Grupo Mateus (`GMAT3.SA`)
- Assai (`ASAI3.SA`)
- GPA / Pao de Acucar (`PCAR3.SA`)

The project is structured as an institutional-style equity research workflow. The first notebook validates raw financial inputs, collects market data, standardizes units, and creates a processed dataset for later trading comparable analysis.

## Repository Structure

```text
gmat3-relative-valuation/
├── data/
│   ├── raw/
│   │   └── peer_financials.csv
│   └── processed/
├── notebooks/
│   └── 01-data-validation.ipynb
├── outputs/
├── charts/
├── reports/
├── README.md
├── requirements.txt
└── .gitignore
```

## Methodology

The current pipeline focuses on relative valuation / trading comparables. Raw company fundamentals are kept separate from calculated outputs. All monetary statement inputs are stored in BRL millions.

The first notebook calculates initial enterprise value and annualized EV/EBITDA signals, but it does not calculate a target price or final valuation conclusion.

## Running the Notebook

```bash
pip install -r requirements.txt
jupyter notebook notebooks/01-data-validation.ipynb
```

Then run:

```text
Restart Kernel -> Run All
```

The notebook exports the processed dataset to:

```text
data/processed/master_valuation_dataset.csv
```
