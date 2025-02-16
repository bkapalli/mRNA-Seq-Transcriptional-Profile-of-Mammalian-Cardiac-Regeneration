# RNA-Seq Analysis  

## Transcriptional Profile of Mammalian Cardiac Regeneration with mRNA-Seq  

This analysis is based on data from the study:  
O’Meara et al. *Transcriptional Reversion of Cardiac Myocyte Fate During Mammalian Cardiac Regeneration.* Circ Res. Feb 2015. PMID: 25477501  

The focus is specifically on data from the first figure of the paper, which includes samples from P0, P4, P7, and adult mouse heart ventricle cells. While the analysis incorporates more up-to-date strategies and tools compared to the published methods, the workflow aims to capture and recreate the core biological signals observed in the original study.  

## Methods  

RNA sequencing data from biological samples ('AD', 'P0', 'P4', 'P7') with replicates ('rep1', 'rep2') was processed using a Snakemake pipeline. The GRCm39 reference genome and GTF annotation file were obtained from the Gencode database (release M34).  

- Quality control analysis of raw sequencing data: FastQC (v0.12.1)  
- Read alignment to the reference genome: STAR aligner (2.7.11b)  
- Gene expression quantification at the exon level: Verse (v1.0.5)  
- Aggregation of FastQC results: MultiQC  
- Parsing gene annotation, generating a counts matrix from exon-level expression data, and filtering the counts matrix: Custom Python scripts  

All analysis methods are integrated into the `rna_seq.snake` file for reproducibility and workflow automation. Further analysis, including differential expression and gene set enrichment analysis, is conducted in the `differential_expression.Rmd` file.  

