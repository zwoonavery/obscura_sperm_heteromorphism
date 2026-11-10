# Model Gene Expression Across Phylogeny
This workflow describes the steps to model gene expression changes across a phylogeny using the command line tool CAGEE. First, the reads output from the bulk RNA-seq pipeline must be reformatted to fit the expected input structure for CAGEE. Then, CAGEE is ran on these reads as well as provided phylogenetic tree. Finally, the output of CAGEE is processed to extract the genes with high confidence modeled changes at branches of interest.

## Gene Expression Read Pre-Processing
CAGEE expects an input where the first column is a description of the gene, the second column is the gene name, and each subsequent column is the expression of said gene in each species. Thus, the count matrix output from the RNA-seq pipeline in (`../../multigenome_rnaseq/`) needs to be reformatted. This processing was performed in the (`R_reformat_reads_zwa.ipynb`) Jupyter Notebook with all required packages in the (`phylogenetic_analysis.yaml`) environment.

## Running CAGEE
Using CAGEE version 1.2 with the (`phylogenetic_analysis.yaml`) environment, gene expression was modeled against the phylogenetic tree from Kim *et al.* 2024 with varying parameters to determine the model with the highest likelihood. First, a null model was performed where only the read input file and phylogenetic tree was provided such that sigma would be consistent across the tree. Then, three separate sigma trees were produced: all tips were assigned one of three discrete categories based on the species' parasperm content (high, medium, or low) and each internal node was assigned a category as well based on the assumption that the ancestor either contained high, medium, or low parasperm content. Thus, three distinct trees were produced based on these three potential histories.

## Branch Changes Extrapolation
To determine the model with the highest likelihood, chi-squared was calculated for each sigma model relative to the null hypothesis. This calculation is included in (`R_cagee_zwa.ipynb`) and all required packages are in (`phylogenetics_analysis`). The model with the highest likelihood was then used to identify genes with credible changes at branches with predicted changes in parasperm content.

## Output
The final output is a comma-separated file with a column for gene name, a column with the modeled expression change at each branch of interest, as well as a column for which branch changes are credible.
