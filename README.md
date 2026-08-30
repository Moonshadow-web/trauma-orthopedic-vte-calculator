# Trauma Orthopaedic Perioperative DVT Risk Calculator

A bedside web calculator for predicting perioperative **deep vein thrombosis (DVT)** risk in trauma orthopaedic inpatients with lower-limb fractures, based on a temporally validated model combining the **Caprini score** with the **thrombus coagulation index (TCI = TAT + TM)**.

## Model

```
logit(P) = -3.8238 + 0.2469 × Caprini + 1.6019 × I(TCI > 24.23)
risk     = 1 / (1 + exp(-logit))
```

- **TCI** (thrombus coagulation index) = TAT + TM, dichotomised at the Youden-optimal cut-off of 24.23
- Equivalently in standardised form: `logit(P) = -2.0233 + 0.5563 × (Caprini − 7.29)/2.25 + 1.6019 × I(TCI > 24.23)`

## Features

- Enter Caprini score (0–20), TAT (μg/L) and TM (TU/mL)
- Returns the individualised DVT probability and a risk stratum:
  - **Low** <20%
  - **Intermediate** 20–30%
  - **High** >30%
- Bilingual (English / 中文), works fully offline (single `index.html`, no dependencies)

## Development / Validation

- Derivation cohort: n = 130, 32 DVT events (24.6%), AUC 0.790
- Temporal validation cohort: n = 109, 27 DVT events (24.8%), AUC 0.801
- The model is for **risk assessment only** and does not constitute a treatment recommendation.

## Usage

Open `index.html` in any modern browser. No server or internet connection required.

## License

MIT © 2026 Civil Aviation General Hospital, Beijing, China
