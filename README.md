# GMAT3 Relative Valuation

Projeto de valuation relativo para Grupo Mateus (`GMAT3.SA`), com foco em varejo alimentar e atacarejo. A análise combina pares brasileiros listados, referências operacionais e empresas LatAm de food retail para estimar uma faixa de valor justo por múltiplos.

- Assai (`ASAI3.SA`)
- GPA / Pao de Acucar (`PCAR3.SA`)
- Carrefour Brasil / Atacadao (`CRFB3.SA`) como referencia operacional delistada
- Walmex (`WALMEX.MX`)
- Chedraui (`CHDRAUIB.MX`)
- Soriana (`SORIANAB.MX`)
- Cencosud (`CENCOSUD.SN`)

A análise organiza dados financeiros, preços de mercado, qualidade do peer group e cenários de valuation por EV/EBITDA e P/L.

## Estrutura

```text
data/
  raw/
    peer_financials.csv
    peer_universe.csv
    peer_exclusion_rationale.csv
    external_peer_multiples.csv
    source_log.csv
  processed/
    validated_peer_financials.csv
    master_valuation_dataset.csv
    normalized_valuation_base.csv

notebooks/
  01-data-validation.ipynb
  02-relative-valuation.ipynb
  03-valuation-charts.ipynb
  04-ltm-comparison.ipynb

outputs/
  current_market_positioning.csv
  expanded_peer_multiples.csv
  expanded_peer_stats.csv
  gmat3_relative_valuation_scenarios.csv
  ltm_methodology_valuation_check.csv
  multiple_adjustment_bridge.csv
  pe_comparison.csv
  source_log.csv
```

## Notebooks

`01-data-validation.ipynb`

Valida os dados brutos, busca os precos atuais e gera a base principal em `data/processed/master_valuation_dataset.csv`.

`02-relative-valuation.ipynb`

Usa a base processada e o universo expandido de peers para calcular EV/EBITDA, P/L, separar peers core de peers distressed/delistados e criar cenarios de valuation para GMAT3.

`03-valuation-charts.ipynb`

Gera graficos para o relatorio: comparacao EV/EBITDA, spread contra a mediana saudavel, P/L, preco justo por cenario, upside/downside, football field e boxplot de outliers.

`04-ltm-comparison.ipynb`

Testa a sensibilidade metodologica entre a anualizacao do 1T26 e uma leitura LTM/trailing disponivel.

## Como rodar

Crie e ative um ambiente virtual, depois instale as dependencias:

```bash
pip install -r requirements.txt
```

Depois abra os notebooks:

```bash
jupyter notebook
```

Rode primeiro o notebook `01-data-validation.ipynb`, depois `02-relative-valuation.ipynb`. Os notebooks `03` e `04` usam os outputs gerados nas etapas anteriores.

## Saidas

Os principais arquivos gerados ficam em `outputs/`:

- `current_market_positioning.csv`
- `expanded_peer_multiples.csv`
- `expanded_peer_stats.csv`
- `gmat3_relative_valuation_scenarios.csv`
- `multiple_adjustment_bridge.csv`
- `pe_comparison.csv`
- `ltm_methodology_valuation_check.csv`
- `gmat3_valuation_research_workbook.xlsx`

Obs: Carrefour Brasil / Atacadao entra como referencia operacional, mas nao como trading comp atual, pois CRFB3 deixou de ser uma acao negociada na B3 apos o processo de delisting.
