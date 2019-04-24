---
title: "bulk RNAseq"
date: 2018-12-29T11:02:05+06:00
type: "post"
weight: 1
---

### Fast RNAseq pipeline

Here we show how to run a NextFlow pipeline for RNAseq from species with well
annotated genes, like human or mouse.

#### Raw data

This is an example using a public dataset.

We got the following links from [sra-explore](https://ewels.github.io/sra-explorer/), a web-based app
that help you to find public datasets and provides a script to download the data.

We use the following files:

```bash
#!/usr/bin/env bash
curl -L ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR307/SRR307897/SRR307897_1.fastq.gz -o SRR307897_GSM758559_CshlLong_RnaSeq_GM12878_cell_longPolyA_1.fastq.gz
curl -L ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR307/SRR307897/SRR307897_2.fastq.gz -o SRR307897_GSM758559_CshlLong_RnaSeq_GM12878_cell_longPolyA_2.fastq.gz
curl -L ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR307/SRR307912/SRR307912_1.fastq.gz -o SRR307912_GSM758566_CshlLong_RnaSeq_H1-hESC_cell_longPolyA_1.fastq.gz
curl -L ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR307/SRR307912/SRR307912_2.fastq.gz -o SRR307912_GSM758566_CshlLong_RnaSeq_H1-hESC_cell_longPolyA_2.fastq.gz
```

* create a folder `raw`
* type `cd raw`
* copy that into a file called `download.sh`
* type `bash download.sh`. 

Wait until is finished, then come back to parent folder `cd ..`.

#### Annotation

We need the transcriptome fasta file as well:

`wget ftp://ftp.ensembl.org/pub/release-96/fasta/homo_sapiens/cdna/Homo_sapiens.GRCh38.cdna.all.fa.gz`

#### Environment

If you are in the PILM-cluster, follow this instructions: [PRIVATE PILM]

If you want to try from scratch, follow these [instructions](/environment/conda) to install
miniconda, and then type:

* `conda -n create -y nf-fastrnaseq nextflow salmon multiqc fastqc` 
* `conda activate nf-fastrnaseq`

#### Get the pipeline

If you are in  the  PILM-cluster, follow this instructions: PRIVATE PILM

If you want to try from scratch, download the pipeline from GitHub: PUBLIC PILM.

Now that you know where the file `paired.nf` is, you can run the following command to get the pipeline working:

`nextflow run paired.nf -w working -name tiny -with-report all-report -with-timeline all-time --outdir results  -qs 6 --reads "raw/*{1,2}.fastq.gz" --transcriptopme Homo_sapiens.GRCh38.cdna.all.fa.gz`



