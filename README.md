## Microbial food-web recovery following warming

Code and data supporting analyses of how experimental top-down and bottom-up food-web structure shapes microbial community responses to warming and subsequent cooling.

## Overview

This repository contains the complete analysis workflow for a laboratory microbial food-web experiment. The experiment manipulates temperature, predator identity/richness, and algal presence, and evaluates responses in:

- bacterial abundance
- bacterial Shannon diversity
- bacterial community composition
- algal abundance

The analysis uses flow cytometry to characterize bacterial phenotypic groups, Bayesian models to estimate treatment-specific trajectories, and posterior predictions to calculate a stable-treatment-corrected Reversibility Index.

## Repository structure

```text
data/
  raw/                  Raw flow-cytometry data and manually gated algae-reference files
  processed/            Algae-removed and bacterial-clustered datasets
  model_fits/           Saved Bayesian model fits

scripts/
  01_data_preparation/  Algae removal and bacterial phenotypic clustering
  02_bayesian_models/   Bayesian models for each response variable
  03_figures/           Code used to create manuscript Figures 2–5

output/
  figures/              Rendered manuscript figures
```

## Analysis workflow

Run the Quarto documents in numerical order:

1. `01_remove_algae.qmd`  
   Identifies algal events from manually gated reference files and removes them from the full flow-cytometry dataset.

2. `02_cluster_bacteria.qmd`  
   Log-transforms flow-cytometry variables, removes outliers, performs principal component analysis and Gaussian-mixture clustering, removes a noise cluster, and exports the final bacterial phenotypic-group dataset.

3. `03_algae_abundance.qmd`  
   Fits Bayesian models of algal abundance.

4. `04_bacterial_abundance.qmd`  
   Fits Bayesian models of bacterial abundance.

5. `05_bacterial_shannon_diversity.qmd`  
   Calculates bacterial Shannon diversity and fits Bayesian models.

6. `06_bacterial_composition.qmd`  
   Calculates Bray–Curtis dissimilarity, conducts NMDS ordination, and fits Bayesian models of bacterial community composition.

7. `07_figure_2_base_model.qmd`  
   Creates Figure 2 for the base model.

8. `08_figure_3_bottom_up.qmd`  
   Creates Figure 3, evaluating bottom-up effects of algal presence.

9. `09_figure_4_top_down.qmd`  
   Creates Figure 4, evaluating top-down effects of predator identity.

10. `10_figure_5_combined_models.qmd`  
    Creates Figure 5, evaluating combined top-down and bottom-up effects.

## Software requirements

Analyses were conducted in R using Quarto documents. Key packages include `brms`, `mclust`, `vegan`, `tidyverse`, `data.table`, `tidybayes`, `bayesplot`, `posterior`, `loo`, and `patchwork`.

## Reproducibility

All data, code, and saved model objects required to reproduce the analyses and figures will be publicly available in this repository. Scripts should be run in the order listed above.

## Citation

Citation information will be added when the associated manuscript is published.

## License

A license will be added before the repository’s final release.