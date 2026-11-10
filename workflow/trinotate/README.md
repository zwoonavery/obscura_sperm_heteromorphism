# Gene Annotation
The goal of this pipeline is to assign gene ontology terms to genes through homology analysis and function prediction. This annotation is facilitated through the tool Trinotate that consolidates the results from multiple tools. Trinotate and the other tools used in this analysis require individual download, as described below. To convert these results into a comma-separated file for downstream use, additional processing is required as performed in (`R_convert_go_zwa.ipynb`). All packages required to run this processing notebook are included in (`simple_analysis.yaml`).

## Create Trinotate Environment
For the uses in this Snakemake workflow to maintain reproducibility and reliability even though the Trinotated conda package is no longer supported, a Trinotate singularity image version 4.0.2 was create as following the Trinotate wiki setup instructions (https://github.com/Trinotate/Trinotate/wiki/TrinotateViaSingularity).

Additionally, this analysis involves the local downloading of additional tools as follows: HMMer (v3.4), RNAMMer (v1.2), SignalP (v4.1), and TMHMM (v2.0c). They will need to be initialized for use by Trinotate as described in the Trinotate wiki. The path for both the Trinotate Singularity as well as the location of these tools must be updated in the config file before running the Snakemake script.
