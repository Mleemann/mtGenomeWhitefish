# mtGenomeWhitefish

This repository contains all scripts used to assemble a Alpine whitefish mitochondrial reference genome and to create a mitochondrial phylogeny of 97 whitefish individuals. 

## Workflow of the project

1. Assembly of mitochondrial reference genome using NOVOPlasty and COXI gene of common whitefish _Coregonus lavaretus_ (NC_002646.1) from Illumina reads of one whitefish individual.
   --> run novoplsty.lsf  

2. Annotation of the mitogenome using MitoFish webtool (http://mitofish.aori.u-tokyo.ac.jp/)

3. Illumina read mapping of 97 whitefish individuals to the mitochondrial reference genome using bwa-mem, filtering out low quality reads using Sambamba, and remove duplicates using Picard-tools. 
   --> run bwa_array.lsf
   
4. Variant calling of each BAM file using freebayes keeping variant and invariant sites.
   --> run freebayes_array.lsf
   
5. Merge all VCF files to one single VCF file and perform DP filtering and remove indels.
   -- > merge_vcfs.txt, filter_vcf.txt
   
6. Convert VCF file to PHYLIP file using vcf2phylip.
   --> vcf2phylip.txt
   
7. Run IQ-TREE to produce phylogenetic tree.
   --> run_iqtree.txt
