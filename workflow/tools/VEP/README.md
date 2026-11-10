# Variant Effect Prediction
The goal of this workflow is to call variants relative to a constructed reference genome and predict the effect of these variants. Because the progenitor of the mutant is the Sex Ratio of *Drosophila pseudoobscura*, a new reference genome had to be constructed from the DNA-seq reads before calling the variants in the mutant with GATK. These effect of these variants were then predicted with VEP.

## Set Up Environment
The software required for variant calling and data processing are included in the (`variant_analysis.yaml`), including GATK version 3.8. VEP must be downloaded from the github as described on the ensembl webpage https://jun2026.archive.ensembl.org/info/docs/tools/vep/script/vep_download.html. All analyses were performed with version 113.1.

## Call Variants and Predict Variant Effect
Variants in the *D. pseudoobscura* mutant were called against a reference genome constructed from the sex ratio mutant DNA-seq reads. The results were then processed and effects were predicted with VEP, predicting all possible effects ((`--everything`)). All of these steps were performed with command line tools and, as such, all commands run for this process are outline in (`gatk_reference_steps.txt`). This code was run with the (`variant_analysis.yaml`) environment.

## Output
The final output of this workflow is a list of variants in the mutant relative to the progenitor as well as the predicted effect of these mutants.
