---
title: "Pipelines with Nextflow"
date: 2019-06-13
type: "post"
weight: 3
---

## Full pipelines

We use [Nextflow](https://www.nextflow.io/) to run our pipelines.

Our pipelines are in our GitHub repository with the naming: `pipelines-ng-*`. The RNAseq pipeline is here: https://github.com/pilm-bioinformatics/pipelines-nf-rnaseq

For instance, to run the RNAseq pipeline you can do the following (assuming you have nextflow already):

`nextflow pilm-bioinformatics/pipelines-nf-rnaseq -prodile docker,test`

If you want to run the development pipeline:

`nextflow pilm-bioinformatics/pipelines-nf-rnaseq -r pilm-devel -prodile docker,test`

To know the difference, look at the CHANGELONG file: https://github.com/pilm-bioinformatics/pipelines-nf-rnaseq/blob/pilm-devel/CHANGELOG.md

Our pipelines are synchronize with [nf-core](https://nf-co.re/) pipelines, and in the majority of the cases will be the same. We updated a little bit before them but in general, the changes will be merged at some point.

To know the differences, look at the README file.
