# coding exercise using TCGA immune infiltration data

### Overview
The Cancer Genome Atlas (TCGA) project is probably one of the most well-known large-scale cancer sequencing project. 
It sequenced ~10,000 treatment-naive tumors across 33 cancer types. Different data including whole-exome, whole-genome, copy-number (SNP array), 
bulk RNAseq, protein expression (Reverse-Phase Protein Array), DNA methylation are available.

Helpful links: 
* TCGA barcode system https://docs.gdc.cancer.gov/Encyclopedia/pages/TCGA_Barcode/
* TCGA code table report: https://gdc.cancer.gov/resources-tcga-users/tcga-code-tables
  
### Task

The task is to explore the immune infiltration differences between different EGFR mutants and wild type samples.
Specifically, you need to compare the different immune cell abundance in EGFR wild type, Exon20 insertion mutation
and Exon19 deletion mutation, pL855R mutation and other misssense mutations.

### Step 1 Download the immune infiltration data estimated by CIBERsort using RNAseq data

Go to https://gdc.cancer.gov/about-data/publications/panimmune

The two files you need are in the Cellular Fraction Estimates section.

* Leukocyte Fraction - `TCGA_all_leuk_estimate.masked.20170107.tsv`
* CIBERSORT immune fractions - `TCGA.Kallisto.fullIDs.cibersort.relative.tsv`
You can also download from this github repository.

1. demonstrate that `TCGA.Kallisto.fullIDs.cibersort.relative.tsv` is relative immune cell abundance (Hint, all the immune cell type fractions sum up to 1)
2. calculate the absolute immune infiltration by using the `Leukocyte Fraction` using `TCGA_all_leuk_estimate.masked.20170107.tsv`.
when joining the two tables:
   
* make sure you explore the two data tables to understand the TCGA barcode and identify the unique keys to combine the two datasets.
* There are some duplicated rows in the `TCGA.Kallisto.fullIDs.cibersort.relative.tsv` file, make sure you spot them.

3. group similar immune cell types together and calculate the absolute immune infiltration for  B_cells, T_cells, NK_cells, Monocytes, Macrophages, DCs, Mast, Eosinophils and  Neutrophils

4. plot the immune infiltration of T cells across all cancer types in a boxplot and order the box by the median level of T cell infiltration from high to low.

5. Get the median level of immune infiltration of B_cells, T_cells, NK_cells, Monocytes, Macrophages, DCs, Mast and Eosinophils per cancer type and plot them in a heatmap

### Step 2 Get the mutation data 

Download the mutation data for LUAD (lung adenocarcinoma) from TCGA. (you choose a resource that you want to get this information).
Now, use the mutation data to stratify the patients in the `TCGA.Kallisto.fullIDs.cibersort.relative.tsv` based on the EGFR mutation status: EGFR wildtype, Exon20 insertion mutation, Exon19 deletion mutation, pL855R mutation and other misssense mutations.

Note the mutation file may not tell you the exon number for the mutations. You will need to cross check the mutation position (chr, start, end) with the gene model anntoation (e.g., gtf file).

### Step 3 data visualization

plot the absolute infiltration level for B_cells, T_cells, NK_cells, Monocytes, Macrophages, DCs across different EGFR mutants for LUAD.

Use a notebook either with Rmarkdown or Jupyter notebook; document how you performed the analysis.

### Time to completion

It may take you 1-2 days for this task depending on your coding experiences and familarity with the genomics data.
