# GMAT3 Relative Valuation

Projeto de valuation relativo (trading comps) para Grupo Mateus (`GMAT3.SA`), combinando pares brasileiros listados, referencias operacionais e peers LatAm de food retail.

- Assai (`ASAI3.SA`)
- GPA / Pao de Acucar (`PCAR3.SA`)
- Carrefour Brasil / Atacadao (`CRFB3.SA`) como referencia operacional delistada
- Walmex (`WALMEX.MX`)
- Chedraui (`CHDRAUIB.MX`)
- Soriana (`SORIANAB.MX`)
- Cencosud (`CENCOSUD.SN`)

A ideia e organizar os dados financeiros, puxar precos de mercado, documentar qualidade de peers e montar cenarios de valuation por EV/EBITDA.

## Estrutura

```text
data/
  raw/
    peer_financials.csv
    peer_universe.csv
    external_peer_multiples.csv
  processed/
    validated_peer_financials.csv
    master_valuation_dataset.csv

notebooks/
  01-data-validation.ipynb
  02-relative-valuation.ipynb

outputs/
  current_market_positioning.csv
  expanded_peer_multiples.csv
  expanded_peer_stats.csv
  gmat3_relative_valuation_scenarios.csv
```

## Notebooks

`01-data-validation.ipynb`

Valida os dados brutos, busca os precos atuais e gera a base principal em `data/processed/master_valuation_dataset.csv`.

`02-relative-valuation.ipynb`

Usa a base processada e o universo expandido de peers para calcular multiplos, separar peers core de peers distressed/delistados e criar cenarios de valuation para GMAT3.

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
- `expanded_peer_multiples.csv`
- `expanded_peer_stats.csv`
- `gmat3_relative_valuation_scenarios.csv`

Obs: Carrefour Brasil / Atacadao entra como referencia operacional, mas nao como trading comp atual, pois CRFB3 deixou de ser uma acao negociada na B3 apos o processo de delisting.
