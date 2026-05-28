# GMAT3 Relative Valuation

Projeto valuation relativo (Trading Comps) para a Grupo Mateus (`GMAT3.SA`), comparando com alguns pares listados na B3:

- Assai (`ASAI3.SA`)
- GPA / Pao de Acucar (`PCAR3.SA`)

A ideia e organizar os dados financeiros, puxar precos de mercado e montar uma comparacao por EV/EBITDA.

## Estrutura

```text
data/
  raw/
    peer_financials.csv
  processed/
    validated_peer_financials.csv
    master_valuation_dataset.csv

notebooks/
  01-data-validation.ipynb
  02-relative-valuation.ipynb

outputs/
  current_market_positioning.csv
  gmat3_relative_valuation_scenarios.csv
```

## Notebooks

`01-data-validation.ipynb`

Valida os dados brutos, busca os precos atuais e gera a base principal em `data/processed/master_valuation_dataset.csv`.

`02-relative-valuation.ipynb`

Usa a base processada para calcular os multiplos e criar cenarios de valuation para GMAT3.

## Como rodar

Crie e ative um ambiente virtual, depois instale as dependencias:

```bash
pip install -r requirements.txt
```

Depois abra os notebooks:

```bash
jupyter notebook
```

Rode primeiro o notebook `01-data-validation.ipynb` e depois o `02-relative-valuation.ipynb`.

## Saidas

Os principais arquivos gerados ficam em `outputs/`:

- `current_market_positioning.csv`
- `gmat3_relative_valuation_scenarios.csv`

Obs: a pasta `.venv/` fica fora do Git.
