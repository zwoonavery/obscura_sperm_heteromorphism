# Perform Multigenome RNA-seq Alignment
The goal of this workflow is to perform RNA-seq alignment to multiple genomes and get a list of differentially expressed genes. The paths and variables in the config file are able to be replaced to allow for any relevant input for processing.

## Multigenome Alignment
The multigenome alignment was performed with a Snakemake workflow. All environments will be created with conda as necessary for each rule, as specified in the Snakefile.

## Differential Expression Analysis
The output of the multigenome alignment is a raw counts table that must be processed for downstream analysis. Both normalization for the gene expression of all species as well as differential expression for the *D. pseudoobscura* mutant was performed in (`R_process_rnaseq_zwa.ipynb`). All required packages for this analysis are in (`multigenome_analysis.yaml`).

## Output
This workflow creates two final analyses. One is the normalized reads for the gene expression in all species. The other is a table of genes with their logFC in each comparison within *D. pseudoobscura*.
