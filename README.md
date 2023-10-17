# transcriptome_analysis
Pipeline for the analysis of transcriptomic data in the context of a Spatio-temporal study on Heifer that aims to Identify Molecular Features Associated with Fertility
<img width="1244" alt="Screenshot 2023-10-13 at 11 47 46" src="https://github.com/ydamergi/transcriptome_analysis/assets/114066873/df5da355-6f61-480a-a895-a5438eed81ef">


### get_count_data: <br>
Reads and prepares count data for a weighted gene co-expression network analysis.
Performs the following steps:
Read the count data. 
Filter the count data: removes genes with low expression levels and samples with low reads generated.
Merge the count data with sample information. 
Extract the genes of interest: protein-coding genes, lncRNAs, and pseudogenes.
Write the filtered count data to a file.<br>

### co_expression_analysis : <br>
Performs a weighted gene co-expression network analysis using the [WGCNA R package]([https://gaganpreetkaurkalsi.netlify.app/](https://cran.r-project.org/web/packages/WGCNA/index.html)) . Allows to identify groups of genes that are co-expressed, (correlated expression levels). These groups of genes are called modules, they are likely to be involved in the same biological processes.
Performs the following steps:<br>
Filter and normalize the count data. <br>
Construct the co-expression network.<br>
Identify gene modules. <br>
Calculate module eigengenes.<br>
Correlate module eigengenes with traits.<br>
Identify driver genes.<br>
