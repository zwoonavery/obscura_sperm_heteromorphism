# Gene Annotation
The goal of this pipeline is to assign gene ontology terms to genes through homology analysis and function prediction. This annotation is facilitated through the tool Trinotate that consolidates the results from multiple tools. Trinotate and the other tools used in this analysis require individual download, as described below. To convert these results into a comma-separated file, additional processing is required as performed in (`R_convert_go_zwa.ipynb`). All packages required to run this processing notebook are included in (`annotation_analysis.yaml`).

## Create Trinotate Environment
The Trinotate package is no longer supported on conda so the package must be installed in another way. 

Following the Trinotate wiki, this can be achieved either through directly downloading the files or installing it with Singularity. 
For the uses in this Snakemake workflow to maintain reproducibility and reliability, I suggest using the Singularity method. For this pipeline, Trinotate version 4.0.2 was used following the Trinotate wiki setup instructions (https://github.com/Trinotate/Trinotate/wiki/TrinotateViaSingularity).

## Download Additional tools
This pipeline involves the local downloading of additional scripts: HMMer (v3.4), RNAMMer (v1.2), SignalP (v4.1), and TMHMM (v2.0c). They will need to be initialized for use by Trinotate as described in the Trinotate wiki.
