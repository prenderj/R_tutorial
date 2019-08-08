# Introduction to data analysis in R

R is a statistical software package widely used in bioinformatics and genetics analyses. Due to its large number of available packages, supported statistical analyses and plotting functions it has become very popular. It is also free.

In this tutorial we will go over a basic analysis of the results from an eQTL study. eQTLs are genetic loci linked to the expression of genes, and are generally identified by testing for correlations between a variant's genotypes and the expression level of the gene.

![eQTLs](https://ars.els-cdn.com/content/image/1-s2.0-S0925443914001112-gr1.jpg)

## Dataset
After starting the interactive session the data you need for this session can be copied from */export/data/ilri/bioinformatics/workshop_dnaseq/Session1*. 

```
interactive -c 4
```
We first go to the home directory, then copy the required data and move to this new directory
```
cd
cp -R /export/data/ilri/bioinformatics/workshop_dnaseq/Session1/ ~/
cd ~/Session1
```

