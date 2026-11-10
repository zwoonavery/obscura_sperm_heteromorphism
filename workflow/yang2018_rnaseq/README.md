# Tissue Specificity Analysis
The goal of this workflow is to process the reads from Yang *et al.* 2018 (BioProject PRJNA388952) to identify genes with tissue specific expression through the calculation of tau. First, the reads for each tissue must be processed and mapped to the reference genome using the Snakemake pipeline. This produces a file with gene expression count that is then processed in a Jupyter notebook to calculate tau for each gene.

## Gene Expression Count
Before running the pipeline, update the variable paths in the config to specify the location of the data for processing, location for results, as well as desired parameters. Otherwise, all required dependencies will be downloaded in the relevant conda environment for each rule by the Snakemake pipeline during running.

## Tau Calculation
The Jupyter notebook (`R_tau_dpse_zwa.ipynb`) processes the output of the RNA-seq pipeline to calculate tissue specificity for each gene. All packages required to run this code is in the environment created by (`tau_analysis.yaml`).

## Output
The output includes the gene, tau calculation, organ with the highest expression, as well as the assignment of the tau tissue. In other words, if tau is significant, the tau tissue is the tissue with the highest expression. If tau is not significant, than the expression of the gene is ambiguous.
