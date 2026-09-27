# AI Usage Documentation

I used Claude (Claude Code) throughout this project: to generate code, to check
hypotheses and ideas, to analyse the dataset, and to build plots. All text cells in the
notebooks were either generated or edited with Claude. I can't provide a link to the
chat, since Claude was used on a corporate Team plan and chat links can't be generated.
Instead, below is a detailed, day-by-day log of how it was used.

## 2026-09-20 — EDA and setup

- Claude helped set up the project: the initial structure and the data loading code,
  after I found out Kaggle phone verification was blocked and switched to a code-only
  workflow.
- It helped reduce memory usage while loading the raw CSV files, and helped build and
  detail the EDA visualizations in `01_eda`.

## 2026-09-23 — Metrics and validation

- For `02_metrics`, Claude proposed the hypothesis behind the sharp-vs-flat model
  example, used to show that two models with the same ROC-AUC can behave very
  differently.
- In `03_validation`, it hypothesized that a random split lets the model memorize
  clients, and proposed measuring this directly (share of validation fraud coming from
  already-seen fraud clients). The 85% vs 63% numbers came out of that check.

## 2026-09-24/26 — GBDT and neural network

- Claude proposed the client-id hypothesis (`card1 + addr1 + day - D1`) after noticing
  in adversarial validation that `day - D` features were suspiciously informative; I
  asked it to verify this wasn't leaking the label before accepting the feature.
- For the neural network, it suggested the DCN-v2 cross layer and FiLM as candidate
  custom layers, and helped me implement both from scratch as `nn.Module` classes with
  their own `nn.Parameter` weights.

## 2026-09-27 — Course ideas, official data, report

- Claude helped build the two-stage ensemble: the out-of-fold stacking setup, the
  choice of combiner, and the paired bootstrap check that the gain over GBDT alone was
  real.
- It helped evaluate the Kaggle scores after submission: pulling the public score
  through the Kaggle API, and comparing CV, public and private across all submitted
  models.
- It helped generate the final report: structuring it into sections, building the
  tables and figures, and writing it up in LaTeX.
