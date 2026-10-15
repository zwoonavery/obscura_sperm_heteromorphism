#Associating gene expression with sperm heteromorphism across the Drosophila obscura group
This repository contains the bioinformatic workflow and analysis presented in:

This project includes multigenome alignment of RNA-seq (`workflow/multigenome_rnaseq`), functional annotation of genes (`workflow/trinotate`), mutation identification and effect prediction (`workflow/tools/VEP`), phylogenetic gene expression analysis (`workflow/tools/CAGEE`), motif discovery (`workflow/tools/STREME`), as well as single-cell analysis (`workflow/he2026_rnaseq`) and tissue specificity calculations (`workflow/yang2018_rnaseq`). Each workflow has its own folder and pipeline that is able to be run independently as well as notebooks containing any workflow specific processing. The combined analysis of these outputs and the code to generate graphical representations is also included (`analysis`).

##Data
To complete the multigenome RNA-seq, the RNA-seq reads from each species as well as the genome and genome annotation files are required. The genome for each species was downloaded from NCBI. These reference genomes were also used as the input for the gene functional annotation workflow. The read counts from the multigenome analysis were then used as the input for the phylogenetic analysis with the Kim *et al.* 2024 phylogenetic tree.

To identify mutations and predict their effect, the DNA-seq reads from the mutant as well as the genome and genome annotation files of the progenitor are required. The variants were called relative to the *D. pseudoobscura* genome from Fuller *et al.* 2020 using the workflow from the Genome Analysis Toolkit. These variants were then used as the input for the effect prediction. The upstream region of the differentially expressed genes identified from the RNA-seq analysis were extracted using `workflow/tools/STREME/R_extract_promoter_zwa.ipynb` and searched for motif enrichment.

The single cell analysis was performed on the reads from He *et al.* 2026 and the tissue specificity calculation was performed on the reads from Yang *et al.* 2018 (BioProject PRJNA388952).

To run the complete analysis notebook, all of the workflow outputs are required. The data required for each step of the analysis is specified in the relevant section.

##Workflow


##Analysis
