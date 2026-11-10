# Motif Discovery from Upstream Regions
The goal of this workflow is to identify motifs that are enriched among upstream regions of differentially expressed genes. First, a list of genes as well as the controls must be determined. STREME was run on the commandline while the web-user interface was used for TomTom to identify motifs in the target regions and the factors associated with those motifs, respectively. 

## Extract Promoters from Genes of Interest and Controls
Differentially expressed genes between the mutant and the progenitor were identified from the analysis in (`../../analysis/R_analysis_zwa.ipynb`). The fasta and GFF of the reference genome were used along with these list of differentially expressed genes to extract the upstream regions with the (`R_extract_promoters_zwa.ipynb`) notebook. All required packages are included in the (`promoter_analysis.yaml`) environment. Using this analysis, the region 1,000 base pairs upstream of the transcription start site of each gene was extracted and then a fasta file of all of these sequences was compiled for each gene list.

## Identify Motifs with STREME
STREME version 5.5.8 in the MEME suite was used to identify motifs enriched in the compiled fasta files, as is available in the (`promoter_analysis.ipynb`) environment. Along with the target sequences and the control sequences, the patience was increased to 1,000,000 to increase the number of motifs searched.

## Identify Associated Factors of Motifs with TomTom
The output of the STREME results was then put into the TomTom web-based interface version 5.5.9 at https://meme-suite.org/meme/tools/tomtom. All of the base parameters were used to search the enriched motifs against the combined Drosophila databases.
