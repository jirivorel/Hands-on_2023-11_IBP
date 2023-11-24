# **Hands-on course, Institute of Biophysics of the Czech Academy of Sciences, November 2023, Brno**

This readme was created by Jiří Vorel (vorel@cesnet.cz).

Jiří Vorel and Roman Leontovyč lectured the course.

Information given in this course is current as of 30th November 2023.

<p align="center"><img src="./figs/01_logos.jpg"></p>

# Table of contents
* [Introduction](#introduction)
  * [Aims](#aims)
  * [Prerequisites](#prerequisites)
  * [Dedicated resources](#dedicated-resources)
  * [Data and tools](#data-and-tools)
  * [Useful links](#useful-links)
* [Log in to the frontend server](#log-in-to-the-frontend-server)

# Introduction

## Aims

This tutorial, in the brief form of a hands-on course, shows how to process and analyse sequencing data using [MetaCentrum NGI](https://www.metacentrum.cz/en/index.html) (National Grid Infrastructure). Participants will be introduced to the basic usage of MetaCentrum, e.g. how to [log in on the frontend server](https://docs.metacentrum.cz/access/log-in/), how to [manipulate data](https://docs.metacentrum.cz/data/data-within/) properly, how to [start an interactive or batch job](https://docs.metacentrum.cz/basics/jobs/), and how to [display graphical output](https://docs.metacentrum.cz/software/graphical-access/).

In the practical part of the course, we will use publicly available sequencing data (produced by [Illumina](https://www.illumina.com/) and [Oxford Nanopore](https://nanoporetech.com/) platforms) for the hybrid assembly of the bacterial genome - specifically, _Escherichia coli_ strain A0 34/86 (as described in this [paper](https://journals.asm.org/doi/10.1128/mra.00363-23)). Unfortunatelly, processing raw reads, genome assembly and following gene prediction and annotation are processes (especially in the case of larger eukaryotic genomes) that often require time-consuming tuning for optimal parameters and considerable hardware resources.

> [!IMPORTANT]  
> **This course does not aim to create a perfect genome assembly!**
> 
> Due to the time limitation of this course and its primary focus (how to use grid infrastructure as effectively as possible), we will create a very rough genome draft using a few necessary steps.
>
> The proposal of a comprehensive approach for a "perfect" bacterial genome assembly can be seen [here](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1010905).

> [!NOTE]
> Throughout this tutorial, important points will be supplemented with links to documentation with more detailed description and explanation.

## Prerequisites

To get the full potential of this course, each of the participants should be (or should have):
  -  **be a registered user of MetaCentrum** (due to the process involving application approval and propagation of a new account, it is necessary to apply for an account no later than a day before the course).
  -  **know login information - username and password** (which were created during the application process).
  -  **have a laptop with a working internet connection.**
  -  **be able to log in to the remote server (via ssh protocol).**
  
> [!NOTE]
> This course is designed for participants with no command-line (CLI) knowledge. But this knowledge is recommended. All commands and shell scripts used during the course are pasted below and can be directly copied.

> [!NOTE]
> No data and software tools need to be downloaded/installed before the course. Data will be downloaded during the course, and all software tools (freely available for non-commercial usage) are already available for Metacentrum users. 

## Dedicated resources

As is typical for grid computing, all submitted jobs are sorted into specific [queues](https://docs.metacentrum.cz/advanced/queues-in-meta/) (mainly based on the amount of requested resources). The combination of the required resources and the current infrastructure load determines the delay between the submission and the start of the calculation. Very demanding jobs can wait in the queue for several days before all the required resources are free. We will use a special queue `XYZ` reserved only for this course to avoid this delay. This queue is operated by two ida machines (`ida7` and `ida25`), each with 20 CPU cores and 128 GB RAM.

> [!IMPORTANT]  
> Each job submitted during this course needs to target this dedicated queue. As you will see later, interactive jobs will include a parameter `-q XYZ`, and batch jobs will include the line `#PBS -q XYZ`. In both cases, the job scheduler [PBSPro](https://docs.metacentrum.cz/basics/concepts/#pbs-servers) will send jobs to this specified queue.

## Data and tools

The following data and software tools will be used during the course:

 - Illumina paired-end reads (NCBI SRA accession number: [SRX20115911](https://www.ncbi.nlm.nih.gov/sra/SRX20115911[accn])).
 - Oxford Nanopore reads (NCBI SRA accession number: [SRX20115912](https://www.ncbi.nlm.nih.gov/sra/SRX20115912[accn])).
 - [NCBI SRA Toolkit](https://github.com/ncbi/sra-tools) for downloading sequencing data.
 - 

## Useful links
 - [MetaCentrum terms and conditions](https://docs.metacentrum.cz/access/terms/)

> [!NOTE]
> Access to MetaCentrum is granted free of charge only to members (employees and students) of academic/research institutions of the Czech Republic.
   
 - [Documentation](https://docs.metacentrum.cz/)
 - [Monitoring page](https://metavo.metacentrum.cz/en/index.html)
 - [User support contact](https://docs.metacentrum.cz/contact/)
 - MetaCentrum is an activity of the [CESNET](https://www.cesnet.cz/?lang=en) association, part of the [e-INFRA CZ](https://www.e-infra.cz/en) - research and development e-infrastructure.

# Log in to the frontend server

As most computing/data centres, Metacentrum nodes are running on Linux (mostly on [Debian](https://www.debian.org/)). Linux is preferred for its stability, security, speed, adaptability and compatibility. Additionally, scientific tools are primarily designed and optimized for Linux.

> [!WARNING]  
> MetaCentum uses [Kerberos](https://docs.metacentrum.cz/advanced/kerberos/) 

<p align="center"><img src="https://tacc.github.io/ctls2017/resources/hpc_schematic.png"></p>



