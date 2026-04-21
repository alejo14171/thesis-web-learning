# Thesis Figures Package

This directory contains all figures used in the Results, Analysis, and Discussion
sections of the XAI-GNN stability thesis (Elliptic AML, 4 architectures ×
4 imbalance scenarios × 3 balancing strategies).

## Package contents

- `results/` — 6 figures (R1–R6) documenting the training quality-gate outcome
- `analysis/` — 10 figures (A1–A10) documenting explainer stability
- `discussion/` — 5 figures (D1–D5) contextualising the results
- `FIGURES.md` — per-figure documentation with interpretation and cross-refs
- Every PNG has a matching `.data.csv` with the raw data used to build it

Total: 21 figures × 2 files each = **42 output files**.

## How to regenerate

```bash
cd /home/penerico/gnns_thesis
uv run jupyter nbconvert --to notebook --execute --inplace \
    notebooks/thesis_figures_package.ipynb
```

The notebook reads from:
- `results_v3/xai-gnn-stability-B-v3.csv`
- `results_v3/xai-gnn-stability-C-v3.csv`
- `results_models_v3/*_meta.json` (48 training metadata files)

## Color palette (consistent across all figures)

| Element | Color |
|---------|-------|
| GCN | `#6366f1` (indigo) |
| GraphSAGE | `#f59e0b` (amber) |
| GAT | `#10b981` (emerald) |
| TAGCN | `#8b5cf6` (violet) |
| Scenario 1:1 | `#6366f1` |
| Scenario 1:10 | `#10b981` |
| Scenario 1:50 | `#059669` |
| Scenario 1:100 | `#ef4444` |
| GNNExplainer | `#10b981` |
| PGExplainer | `#ef4444` (degenerate) |
| GNNShap | `#f59e0b` |

## Figure index

### Results (R1–R6)
- R1 — Pass rate by scenario
- R2 — Pass rate by architecture
- R3 — Pass rate by balancing
- R4 — Val F1 heatmap (arch × scenario)
- R5 — Val F1 vs Val MCC scatter
- R6 — Passing configs summary table

### Analysis (A1–A10)
- A1 — Spearman distribution by explainer
- A2 — Spearman by scenario with error bars (money chart)
- A3 — Spearman by architecture
- A4 — Accuracy vs stability scatter
- A5 — Spearman heatmap (arch × scenario)
- A6 — Jaccard distribution (degeneracy evidence)
- A7 — Kruskal–Wallis boxplot
- A8 — Cohen's d effect sizes
- A9 — PGExplainer universal degeneration
- A10 — Top 10 Spearman configs

### Discussion (D1–D5)
- D1 — State of the art comparison
- D2 — Accuracy × stability quadrants
- D3 — Peak-collapse curve
- D4 — Architecture recommendation matrix
- D5 — Pipeline runtime breakdown

## Key numbers (at a glance)

- 48 configs trained, 17 passed val gate (F1 ≥ 0.30 and MCC ≥ 0.15)
- GNNExplainer Spearman peak: 1:50 × TAGCN × focal_loss → 0.789
- PGExplainer Spearman: 0.0 on every single passing config (degenerate)
- Jaccard = 1.0 on all 34 GNNExplainer+PGExplainer runs (deterministic)
- Accuracy vs stability rank correlation: −0.20 (negative tradeoff)
- Cohen's d (1:1 vs 1:50) ≈ −0.92 (large effect)
- Kruskal–Wallis across scenarios: H = 4.31, p = 0.23 (not significant, small n)

See `FIGURES.md` for full per-figure interpretation.
