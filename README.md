# transcriptome_analysis
Pipeline for the analysis of transcriptomic data in the context of a Spatio-temporal study on Heifer that aims to Identify Molecular Features Associated with Fertility
<img width="1244" alt="Screenshot 2023-10-13 at 11 47 46" src="https://github.com/ydamergi/transcriptome_analysis/assets/114066873/df5da355-6f61-480a-a895-a5438eed81ef">


### get_count_data: <br>
1. Reads and prepares count data for a weighted gene co-expression network analysis.
2. Performs the following steps:<br>
3. Read the count data. <br>
4. Filter the count data: removes genes with low expression levels and samples with low reads generated.<br>
5. Merge the count data with sample information. <br>
6. Extract the genes of interest: protein-coding genes, lncRNAs, and pseudogenes.<br>
7. Write the filtered count data to a file.<br>

### get_gene_annotation: <br>
Connects to the Ensembl [BioMart](https://bioconductor.org/packages/release/bioc/html/biomaRt.html) database for bovine genes.
1. Retrieves the desired annotation data. The annotation data includes the Ensembl gene ID, gene name, description, HGNC gene symbol, gene biotype, transcript length, chromosome name, start position, end position, and strand.
2. Sorts the gene IDs by transcript length in descending order.
3. Removes any duplicate gene IDs.
4. Includes only transcripts that are at least 400 base pairs long. 
5. Writes the annotation data to files. 

### co_expression_analysis : <br>
Performs a weighted gene co-expression network analysis using the [WGCNA R package](https://cran.r-project.org/web/packages/WGCNA/index.html). Allows to identify groups of genes that are co-expressed, (correlated expression levels). These groups of genes are called modules, they are likely to be involved in the same biological processes.<br>
Performs the following steps:<br>
1. Filter and normalize the count data. <br>
2. Construct the co-expression network.<br>
3. Identify gene modules. <br>
4. Calculate module eigengenes.<br>
5. Correlate module eigengenes with traits.<br>
6. Identify driver genes.<br>
