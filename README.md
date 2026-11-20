# Elderly-Care Opportunity Analysis — Power BI

A municipality-level decision-support project that identifies and prioritises locations for further investigation as potential elderly-care investment opportunities.

## Business question

**Which municipalities combine strong elderly-care demand, comparatively weak care provision, evidence of service pressure, and a supportive decision context?**

The project does **not** assume that the municipality with the highest ageing index is automatically the best location. It uses a transparent multi-criteria framework and keeps demand, supply, pressure, socioeconomic context, geography, and feasibility conceptually separate.

![Executive dashboard](assets/Executive%20dashboard.png)

## Project scope

- Unit of analysis: municipality
- Working reference year: 2024
- Municipalities analysed: 90
- Main analytical domains:
  - demographic need
  - elderly-care provision
  - service pressure
  - socioeconomic context
  - geographic patterns
  - candidate prioritisation

## Final candidate framework

The final Candidate Score uses four 0–100 components:

| Component | Weight | Purpose |
|---|---:|---|
| Demographic Need | 35% | Measures scale and intensity of elderly-care demand |
| Provision Gap | 35% | Measures weakness of existing elderly-care supply |
| Service Pressure | 20% | Measures utilisation and excess-demand pressure |
| Socioeconomic Context | 10% | Adds vulnerability context without dominating the decision |

The model deliberately assigns **70% of the final score to demand and provision mismatch**.

### Internal component weights

**Demographic Need**
- Elderly population: 50%
- Elderly share: 30%
- Ageing index: 20%

**Provision Gap**
- ERPI capacity per 1,000 elderly: 50%
- Day Centre capacity per 1,000 elderly: 25%
- SAD capacity per 1,000 elderly: 25%

**Service Pressure**
- Within each service: 75% utilisation + 25% excess demand
- Across services: 50% ERPI + 25% Day Centre + 25% SAD

**Socioeconomic Context**
- Unemployment rate: 35%
- RSI rate: 35%
- Weak business density: 30%

## Screening logic

A high score alone is not enough. Municipalities receive a stronger screening status when at least two care-relevant signals are elevated:

- Demographic Need >= 50 and Provision Gap >= 50
- Demographic Need >= 50 and Service Pressure >= 50
- Provision Gap >= 50 and Service Pressure >= 50

This prevents socioeconomic vulnerability alone from creating a high-priority care-home candidate.

## Dashboard highlights

The final executive dashboard summarises 90 municipalities, approximately 527K elderly residents, an elderly share of 26.9%, and 38 municipalities passing the screening logic.

The displayed Top 10 Candidate Scores were:

| Rank | Municipality | Candidate Score |
|---:|---|---:|
| 1 | Ílhavo | 69.60 |
| 2 | Ovar | 68.68 |
| 3 | Oliveira de Azeméis | 65.19 |
| 4 | Mortágua | 63.19 |
| 5 | Vale de Cambra | 62.69 |
| 6 | Estarreja | 62.03 |
| 7 | Lamego | 59.79 |
| 8 | Tondela | 59.77 |
| 9 | Lousã | 59.72 |
| 10 | Águeda | 58.59 |

These rankings are **prioritisation signals, not final investment recommendations**.

## Analytical workflow

1. Data checks and missing-data review
2. Demographic EDA
3. Care-provision EDA
4. Socioeconomic EDA
5. Cross-domain relationship analysis
6. Geographic analysis
7. Candidate scoring and screening
8. Executive dashboard
9. Recommended next validation: sensitivity analysis and site feasibility review

## Repository structure

```text
.
├── README.md
├── assets/
│   ├── executive_dashboard.png
│   ├── socioeconomic_analysis.png
│   ├── relationships_analysis.png
│   ├── geography_analysis.png
│   ├── candidate_ranking.png
│   └── candidate_scoring_validation.png
├── data/
│   └── README.md
├── dax/
│   ├── core_measures.dax
│   └── candidate_scoring.dax
└── docs/
    ├── ANALYSIS.md
    ├── DECISION_LOG.md
    └── METHODOLOGY.md
```

## Important design decisions

- Missing property values remain blank; they are never converted to zero.
- Rates, percentages and €/m² values are not summed.
- Dashboard elderly share is weighted: total elderly population / total population.
- Provision is standardised per 1,000 elderly where relevant.
- Same-year IQR logic is used for outlier diagnostics.
- Outliers are investigated, not automatically removed.
- Hospitals and pharmacies are treated as contextual healthcare-access indicators, not direct substitutes for ERPI, SAD or Day Centre.
- Property value is excluded from socioeconomic vulnerability scoring because it can represent both economic context and investment affordability.
- Ageing index is down-weighted inside the demographic score to reduce double-counting with elderly share.
- Candidate scores are interpreted comparatively, not as probabilities of success.

## Portfolio report

- [Printable PDF report](report/PowerBI_Elderly_Care_Portfolio_Report.pdf)
- [Editable Word report](report/PowerBI_Elderly_Care_Portfolio_Report.docx)

## Portfolio note

This repository is designed to demonstrate the analytical reasoning, Power BI modelling, DAX, visual analysis, decision framework and communication approach. The source dataset and PBIX file are not included in this generated package; add them only if you have the right to publish them.

For a full narrative, see [`docs/ANALYSIS.md`](docs/ANALYSIS.md) and [`docs/METHODOLOGY.md`](docs/METHODOLOGY.md).
