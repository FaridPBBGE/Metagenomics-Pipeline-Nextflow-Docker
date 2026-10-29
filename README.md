# Metagenomics Pipeline (Nextflow & Docker)

[![Nextflow](https://img.shields.io/badge/nextflow-%E2%89%A525.10.4-brightgreen.svg)](https://www.nextflow.io/)
[![docker](https://img.shields.io/badge/container-Docker-blue.svg)](https://www.docker.com/)
[![nf-core](https://img.shields.io/badge/nf--core-mag-orange.svg)](https://nf-co.re/mag)

## Overview
This repository contains a containerized, reproducible bioinformatics pipeline for analyzing **metagenomic data** to reconstruct **Metagenome-Assembled Genomes (MAGs)**. The pipeline performs assembly, binning, quality assessment, and taxonomic profiling of complex microbial communities.

---

## Pipeline Architecture (`nf-core/mag`)
1. **Preprocessing & Filtering**: Quality filtering and adapter trimming using **fastp** and host read removal via **Bowtie2**.
2. **Assembly**: Reconstruction of contigs using short-read (**MEGAHIT**, **metaSPAdes**) or long-read (**Flye**) assemblers.
3. **Binning**: Grouping contigs into draft genomes using **MetaBAT2**, **MaxBin2**, and **SemiBin2**.
4. **Bin Quality Control**: Assessing genome completeness and contamination using **BUSCO** and **CheckM2**.
5. **Taxonomic Classification & Annotation**: Assigning lineage to MAGs using **GTDB-Tk** and predicting genes via **Prokka**.

---

## System Requirements & Execution
Optimized for local containerized execution on resource-constrained environments (e.g., 8 GB RAM laptop running WSL2/Docker) using a custom configuration (`laptop.config`).

### Quick Start (Test Profile)
```bash
nextflow run nf-core/mag \
  -profile test,docker \
  -c laptop.config \
  --outdir ./results
```
