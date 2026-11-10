# Single Cell Analysis
The goal of this workflow is to analyze the single cell analysis from He *et al.* 2026 through tissue clustering and differential gene expression analysis. Through the successful annotation of the cells, genes differentially expressed across tissue types were identified.

## Cell Annotation
The cells were clustered using Seurat and these clusters were annotated based on the expression pattern of tissue associated genes discovered in He *et al.* 2026. Then, using the MAST algorithm, differentially expressed genes between clusters were identified. All analyses performed are included in (`R_scrnaseq_zwa.ipynb`) and all required packages are included in (`scrnaseq_analysis.ipynb`).

## Output
The output for this workflow is a list genes that are differentially expressed between tissue types, including their logFC.
