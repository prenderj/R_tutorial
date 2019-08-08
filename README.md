# Introduction to data analysis in R

R is a statistical software package widely used in bioinformatics and genetics analyses. Due to its large number of available packages, supported statistical analyses and plotting functions it has become very popular. It is also free.

In this tutorial we will go over a basic analysis of the results from an [expression quantitative trait loci (eQTL)](https://en.wikipedia.org/wiki/Expression_quantitative_trait_loci) study. eQTLs are genetic loci linked to the expression of genes, and are generally identified by testing for correlations between a variant's genotypes and the expression level of the gene across a group of samples. If a correlation is observed this suggests that a variant at this locus may be involved in regulating the expression of the gene, for example by altering a transcription factor binding motif.

![eQTLs](https://ars.els-cdn.com/content/image/1-s2.0-S0925443914001112-gr1.jpg)

The dataset we will use comes from this [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3918453/) and was originally downloaded from [here](https://www.ebi.ac.uk/Tools/geuvadis-das/). However, the dataset has already been copied to the ILRI server and the instructions for accessing it are below.

## Getting started
First start an interactive session on the ILRI server by typing:

```
interactive -c 4
```
Then go to the home directory, copy the required data and move to this new directory
```
cd
cp -R /export/data/ilri/bioinformatics/workshop_dnaseq/Session1/ ~/
cd ~/Session1
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

## Installing packages and loading data
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
**_Question 1: Have a look at the vignette for the stringr package, that was loaded as part of the tidyverse, to see what it is used for_**
