# TEffectR
This repo is a R package. It is developped by Nazmiye Arslan. 
Email : nzmye.arslan01@gmail.com 
### What does this package use for ? 


#### What are the dependencies for TEffectR ?
1. [R](https://www.r-project.org/) version should be version 3.5+
2. While using r programming we suggest you to use [Rstudio](https://www.rstudio.com/products/rstudio/download/) which is the R statistical computing environment to use and understand functions TEffectR well.
3. [Bedtools](https://bedtools.readthedocs.io/en/latest/content/installation.html) is required on your local computer.
4. [devtools](https://cran.r-project.org/web/packages/devtools/readme/README.html) is required to install TEffectR.
5. TEffectR uses these R packages so you have to install all of them. How can you install them eaisly, please visit websites:
    - [dplyr](https://dplyr.tidyverse.org/)
    - [GenomicRanges](https://bioconductor.org/packages/release/bioc/html/GenomicRanges.html)
    - [biomaRt](https://bioconductor.org/packages/release/bioc/html/biomaRt.html)
    - [biomartr](https://cran.r-project.org/web/packages/biomartr/readme/README.html)
    - [Rsamtools](https://www.bioconductor.org/packages//2.10/bioc/html/Rsamtools.html)
    - [edgeR](https://bioconductor.org/packages/release/bioc/html/edgeR.html)
    - [limma](https://bioconductor.org/packages/release/bioc/html/limma.html)
    - [rlist](https://renkun-ken.github.io/rlist/)
    - [stringr](https://github.com/tidyverse/stringr)

### How to install this R package ?
> library(devtools)
> devtools::install_github("karakulahg/TEffectR")

### How does it work?

1. Load the library :

> library(TEffectR)


2. For repeat annotation download [repeatmasker](http://www.repeatmasker.org/genomicDatasets/RMGenomicDatasets.html)

3. Read your repeat annotaion and format it. This example for hg38:

> rm <- rm_format(filepath = "~/Downloads/hg38.fa.out.gz" )

4. To Read gene or transcript expression file :

> x<-read.csv("gene_count_matrix.csv", row.names = 1, header=T, stringsAsFactors = F)

5. For filter gene annotation from Biomart :

    - The URL option which you use annotation release is a link. you can these from [this link](https://www.bioconductor.org/packages/devel/bioc/vignettes/biomaRt/inst/doc/biomaRt.html) or you can list by this R code:
    
    > biomaRt::listEnsemblArchives()
    
    - ID.type can be ensembl_gene_name, ensembl_transcript_id, ensembl_transcript_id_version, ensembl_gene_id_version, ensembl_gene_id.
    
    - For this example :

> genes <- get_intervals(x = rownames(x), organism="hg38", ID.type = "ensembl_gene_id", URL="dec2014.archive.ensembl.org" ) 

