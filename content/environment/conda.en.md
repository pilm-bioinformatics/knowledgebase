---
title: "conda"
date: 2019-06-19
type: "post"
weight: 1
---

### Set up your conda

For macOSX

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -p $HOME/miniconda
export PATH="$HOME/miniconda/bin:$PATH"
```

For Linux

```bash
wget https://repo.continuum.io/miniconda/Miniconda3-3.7.0-Linux-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -p $HOME/miniconda
export PATH="$HOME/miniconda/bin:$PATH"
```

Configure proper channels

```bash
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
```

### Create a conda environment

For instance, if you are interested on genome aligners, you can create an
isolated environment with the following tools:

```bash
conda create -n aligners samtools bamtools star
conda activate aligners
```

start using the tools, then to log off:

```bash
conda deactivate
```