[![DOI](https://zenodo.org/badge/165985614.svg)](https://zenodo.org/badge/latestdoi/165985614)
# SNP_pipeline.ipynb contains following steps:
## 1. Installing dependencies  
This step will install all software used in this pipeline, assuming python and conda/anaconda already installed
​
## 2. Dictionary of necessary files
SRA files and sample names can be stored in a dictionary, which also may be used for accessing files. SRA numbers for samples of the interest can be obtained from NCBI (https://www.ncbi.nlm.nih.gov/sra)
​
## 3. Getting SRA data
Creating subfolders for SRA files and downloading them using sra-tools
​
## 4. Quality trimming with Trimmomatic
Quality trimming and removing primers and adapters (if there are any)  
- Input files - reads 1 and 2
- Output files - paired and unpaired reads.  
​
Since in this pipeline only paired reads used, optionally input files and unpired output files can be removed to save some space on drive.  
​
## 5. Running FastQC with trimmed and paired files
Quality of trimmed and paired files can be checked using FastQC
- Input files - trimmed and paired reads
- Output files - evaluation files, produced by FastQC
​
## 6. BWA alignment and SNP calling
In this step, it is neceessary:
1. Provide reference sequences for each of the samples
2. bwa alignment - align reads to reference sequence
    - Input files - paired and trimmed reads
    - Output files - aligned files in filename.sam format
3. Convert sam files into bam files
    - Input files - sam files
    - Output files - bam files
4. Sort and index bam files
    - Input files - bam files
    - Output files - sorted and indexed bam files
5. Performing SNP calling using Freebayes
    - Input files - reference and sorted bam files
    - Output files - vcf files with SNP observed
6. If necessary, use vcftools for filtering
​
## 7. SNP ratio
Calculating and extracting the ratio between different variants in called SNPs. If in some of the SNPs one of the variants presented in more than 90% of the reads it will be filtered out during this step (can be easily changed or removed)
​
## 8. SNP for all nematodes, table and barplot
Create barplot for samples of the interest by species and gene regions
- Output files - figure with barplots, indicating the amount of SNP per 50 bp, by species, genes and isolates
​
## 9. SNP heatmapes by species and genes separately
Create heatmaps for species, presented by several isolates to see variability of SNPs within species
- Output files - heatmaps-like figures with SNP positions by genes (regions) and different isolates within species

