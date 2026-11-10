# Gene Annotation
The goal of this pipeline is to assign gene ontology terms to genes through homology analysis and function prediction. This annotation is facilitated through the tool Trinotate that consolidates the results from multiple tools. Trinotate and the other tools used in this analysis require individual download, as described below. To convert these results into a streamlined file for downstream use, the results from this pipeline underwent additional processing in a Jupyter Notebook.

## Environment Creation
For the uses in this Snakemake workflow to maintain reproducibility and reliability even though the Trinotated conda package is no longer supported, a Trinotate singularity image version 4.0.2 was create as following the Trinotate wiki setup instructions (https://github.com/Trinotate/Trinotate/wiki/TrinotateViaSingularity).

Additionally, this analysis involves the local downloading of additional tools as follows: HMMer (v3.4), RNAMMer (v1.2), SignalP (v4.1), and TMHMM (v2.0c). They will need to be initialized for use by Trinotate as described in the Trinotate wiki. The path for both the Trinotate Singularity as well as the location of these tools must be updated in the config file before running the Snakemake script.

## Additional Processing
To convert the numeric assignment into GO terms, additional processing of the Trinotate output is required as performed in (`R_convert_go_zwa.ipynb`). This processing extrapolates the GO term and assigns the aspect (molecular function, biological process, or cellular component) for downstream analysis. All packages required to run this processing notebook are included in (`simple_analysis.yaml`).

## Output
The final output of this workflow is a comma-separated file with three columns: gene, GO term, and GO category. This file is formatted such that each GO term for each gene has its own row, meaning that each gene may appear multiple times if it had multiple GO terms assigned to it by the pipeline.
