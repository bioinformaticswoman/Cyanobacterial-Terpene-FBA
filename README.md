# Cyanobacterial-Terpene-FBA
Flux Balance Analysis workflow to model Terpene Precursor production in Synechocystis.

This project uses genome-scale metabolic modeling and Flux Balance Analysis (FBA) to study terpene precursor biosynthesis in *Synechocystis sp. PCC 6803*, a model cyanobacterium used in synthetic biology and sustainable biotechnology.

The workflow is designed for Google Colab and uses COBRApy to load a BiGG genome-scale metabolic model, run baseline growth simulations, identify terpene-related reactions, optimize flux toward isoprenoid precursor production, and predict gene knockout targets that may redirect carbon flux toward the terpene pathway.

## Project Context

Cyanobacteria are photosynthetic microorganisms that can convert light and carbon dioxide into valuable bioproducts. This makes them attractive hosts for sustainable production of terpenes and other industrially relevant molecules.

Sesquiterpenes are produced from isoprenoid precursors such as isopentenyl diphosphate (IPP), dimethylallyl diphosphate (DMAPP), geranyl diphosphate (GPP), and farnesyl diphosphate (FPP). In cyanobacteria, these precursors are generated through the MEP/DXP pathway.

This project computationally investigates how metabolic flux in *Synechocystis* can be redirected toward terpene precursor biosynthesis.

## Objectives

The main objectives of this project are:

1. Load a genome-scale metabolic model of *Synechocystis sp. PCC 6803*.
2. Run baseline Flux Balance Analysis to estimate wildtype growth.
3. Search the model for terpene and isoprenoid pathway reactions.
4. Set terpene precursor production as a new metabolic objective.
5. Simulate single gene knockouts across the model.
6. Identify knockout candidates that improve terpene-related flux while preserving growth.
7. Visualize and export the final candidate gene knockout results.

## Tools and Libraries

This project uses the following Python libraries:

- `cobra` for constraint-based metabolic modeling and FBA
- `pandas` for data handling and result tables
- `matplotlib` for plotting
- `numpy` for numerical operations
- `escher` for metabolic map compatibility and optional visualization

The project is intended to run fully in Google Colab.

## Model Used

The requested model is `iSyn811`. If this model is not directly available from BiGG Models, the notebook uses the closest available BiGG model for *Synechocystis sp. PCC 6803*, such as:

- `iJN678`

This fallback is included because public model availability can vary across BiGG endpoints.

## Workflow Overview

The notebook is divided into eight sequential blocks.

### Block 1: Install and Import Libraries

Installs all required Python packages and imports them into the notebook.

### Block 2: Load the Genome-Scale Model

Loads a *Synechocystis* genome-scale metabolic model from BiGG using COBRApy.

### Block 3: Run Baseline FBA

Runs Flux Balance Analysis using the model's default objective, usually biomass production.

### Block 4: Identify Terpene-Related Reactions

Searches reaction and metabolite names for keywords related to the MEP/DXP and isoprenoid pathways.

### Block 5: Optimize Terpene Precursor Production

Uses a terpene-related metabolite, such as IPP or a close proxy, as the new objective.

### Block 6: Single Gene Knockout Simulation

Simulates deletion of each gene and ranks knockouts based on terpene-related flux and growth preservation.

### Block 7: Visualize Knockout Results

Creates bar charts comparing candidate gene knockouts.

### Block 8: Save Results

Exports the final knockout candidate table as a CSV file.

## Biological Interpretation

The results help identify genes whose deletion may redirect metabolic flux toward terpene precursor biosynthesis. These genes can be considered computational candidates for metabolic engineering.

However, FBA predictions are theoretical. Experimental validation is required before drawing final biological conclusions. Important real-world factors such as enzyme regulation, pathway kinetics, toxicity, photosynthetic efficiency, and genetic stability are not fully captured by standard FBA.

## Expected Output

The notebook produces:

- A loaded *Synechocystis* metabolic model
- Model summary statistics
- Baseline growth prediction
- Top flux-carrying reactions
- Terpene-related reaction and metabolite search results
- Maximum theoretical terpene precursor flux
- Ranked gene knockout candidates
- Bar chart visualizations
- A downloadable CSV file of final results


Project Relevance
This project is relevant to metabolic engineering, synthetic biology, and sustainable biotechnology. It supports the design of cyanobacterial strains that may be optimized for production of terpene-derived compounds using light and carbon dioxide as inputs.

Author
Prepared as part of a Master's-level project in Genome Biology and AI in Life Sciences.

License
This project is intended for academic and educational use.


## Repository Structure

```text
cyanobacterial-terpene-fba/
│
├── README.md
├── Cyanobacterial_Terpene_FBA.ipynb
└── results/
    └── synechocystis_terpene_gene_knockout_results.csv
