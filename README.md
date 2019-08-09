# Introduction to data analysis in R

R is a statistical software package widely used in bioinformatics and genetics analyses. Due to its large number of available packages, supported statistical analyses and plotting functions it has become very popular. It is also free.

In this tutorial we will go over a basic analysis of the results from an [expression quantitative trait loci (eQTL)](https://en.wikipedia.org/wiki/Expression_quantitative_trait_loci) study. eQTLs are genetic loci linked to the expression of genes, and are generally identified by testing for correlations between a variant's genotypes and the expression level of the gene across a group of samples. If a correlation is observed this suggests that a variant at this locus may be involved in regulating the expression of the gene, for example by altering a transcription factor binding motif.

![eQTLs](https://ars.els-cdn.com/content/image/1-s2.0-S0925443914001112-gr1.jpg)

The dataset we will use comes from this [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3918453/) and was originally downloaded from [here](https://www.ebi.ac.uk/Tools/geuvadis-das/). However, the dataset has already been copied to the ILRI server and the instructions for accessing it are below.

## Getting started
First start an interactive session on the ILRI server by typing:

```
interactive
```
Then go to the home directory, make a new directory and download the required data from the web using wget:
```
cd
mkdir R_tutorial
cd R_tutorial/
wget https://www.ebi.ac.uk/arrayexpress/files/E-GEUV-1/EUR373.gene.cis.FDR5.all.rs137.txt.gz
```

In this tutorial we will use R to analyse the data you just copied:
*	R (https://cran.r-project.org/)

R is already installed on the ILRI cluster. To make it available type:
```
module load R/3.3.2
```
Then to start R just type:
```
R
```

## Installing packages
In R anyone can create a new package and make it publically available. Although R comes with various statistical and plotting functions pre-installed, most of the time you will want to install extra packages that come with different functionalities. One of the most widely used collections of packages is called ["the tidyverse"](https://www.tidyverse.org/), which provides functions to simplify analysing datasets. 
If they are not already installed, before you can use packages you first need to install them. To install "the tidyverse" you can type:
```
install.packages("tidyverse")
```
To install other packages you can just specify their name instead. This only needs to be done once, i.e. the next time you load R you wouldn't need to repeat this. 
Once a package is installed you need to remember to load it. If you dont load it its functions will not be available to use. To load it just type:
```
library(tidyverse)
```
You will see that by loading "the tidyverse" various packages have been loaded. For example the tibble package. Generally in R each package comes with a vignette that explains a bit about the package. To view the vignette of the tibble package you can type:
```
vignette("tibble")
```
**_Question 1: Have a look at the vignette for the stringr package, that was loaded as part of the tidyverse. What is it used for?_**

Each package contains functions for performing a given task, for example reading files or plotting data. We have already used some functions such as install.packages. You can find out more about a function by using the question mark symbol:
```
?install.packages
```
This shows what the function is for and importantly how to use it. Most functions will take a range of parameters that govern how the function is run and these are listed on these help pages. Generally at the bottom of these pages there will also be examples of how to use the function.

## Reading and viewing files
We are now going to use a function, read_tsv, from the tidyverse packages to read in the file we copied previously. First have a look at how this function works
```
?read_tsv
```
To use this function to read the file we can type:
```
read_tsv("EUR373.gene.cis.FDR5.all.rs137.txt.gz")
```
As we started R in the directory containing the file we don't need to specify its full path. However, we would need to if the file was in a different folder.
You can hopefully see that the file was successfully read and the top of the file was printed to the screen. We though need to save the data in the file to an object so that we can refer to it later. To do this you can use the left assignment arrow:
```
dat<-read_tsv("EUR373.gene.cis.FDR5.all.rs137.txt.gz")
```
Now the contents of the file will be saved into the _dat_ object. Note we could have called this object anything.
To view the contents of an object you just need to type its name:
```
dat
```
**_Question 2: Can you see how many columns and rows the dataset contains?_**

This file contains information on variants (_SNP_ID_) in the human genome whose genotypes are correlated to the expression of nearby genes (_GENE_ID_). The strength of this corelation is indicated by the rho and P values (_rvalue_ and _pvalue_). The distance between the SNP and the gene's transcription start site is also shown (_distance_). More details on the file's contents can be found [here](https://www.ebi.ac.uk/arrayexpress/files/E-GEUV-1/GeuvadisRNASeqAnalysisFiles_README.txt).

