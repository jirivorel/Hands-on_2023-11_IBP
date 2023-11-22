# **Hands-on course, Institute of Biophysics of the Czech Academy of Sciences, November 2023, Brno**

This readme was created by Jiří Vorel (vorel@cesnet.cz).

Jiří Vorel and Roman Leontovyč lectured the course.

Information given in this course is current as of 30th September 2023.

<p align="center"><img src="./figs/01_logos.jpg"></p>

# Table of contents
* [Introduction](#introduction)
  * [Aims](#aims)
  * [Prerequisites](#prerequisites)
  * [Dedicated resources](#dedicated-resources)
  * [Useful links](#useful-links)

# Introduction

## Aims

This tutorial, in the brief form of a hands-on course, shows how to process and analyse sequencing data at [MetaCentrum NGI](https://www.metacentrum.cz/en/index.html) (National Grid Infrastructure). Attendants will be introduced to the basic usage of MetaCentrum. E.g. how to [log in on the frontend server](https://docs.metacentrum.cz/access/log-in/), how to [manipulate data](https://docs.metacentrum.cz/data/data-within/) properly, how to [start an interactive or batch job](https://docs.metacentrum.cz/basics/jobs/), and how to [display graphic output](https://docs.metacentrum.cz/software/graphical-access/).

In the practical part of the course, we will use publicly available sequencing data (produced by [Illumina](https://www.illumina.com/) and [Oxford Nanopore](https://nanoporetech.com/) platforms) for the hybrid assembly of the bacterial genome. Unfortunatelly, processing raw reads, genome assembly and following gene prediction and annotation are processes (especially in the case of larger eukaryotic genomes) that often require time-consuming tuning for optimal parameters and considerable hardware resources.

> [!IMPORTANT]  
> **This course does not aim to create a perfect genome assembly!**
> 
> Due to the time limitation of this course and its primary focus (how to use grid infrastructure as effectively as possible), we will create a very rough genome draft using a few necessary steps.

## Prerequisites

To get the full potential of this course, each attendant should be (or should has):
  -  **be a registered user of MetaCentrum** (due to the process involving application approval and propagation of a new account, it is necessary to apply for an account no later than a day before the course)
  -  **know its login information - username and password** (which were created during the application process)
  -  **has a laptop with a working internet connection**
  -  **be able to log in to the remote server (via ssh protocol)**
  
> [!NOTE]
> Basic knowledge of work in a Unix command-line interface (CLI) is not mandatory but is strongly recommended. All commands and shell scripts used during the course are pasted below and can be copied.

## Dedicated resources

As is typical for grid computing, all submitted jobs are sorted into specific [queues](https://docs.metacentrum.cz/advanced/queues-in-meta/) (mainly based on the amount of requested resources). The combination of the required resources and the current infrastructure load determines the delay between the submission and the start of the calculation. Very demanding jobs can wait in the queue for several days before all the required resources are free. To avoid this delay, we will use a special queue named `XYZ` reserved only for this course. This queue is operated by two [ida](https://metavo.metacentrum.cz/pbsmon2/resource/ida.meta.zcu.cz) machines (`ida7` and `ida25`), each with 20 cores and 128 GB RAM.

> [!IMPORTANT]  
> Each job submitted during this course needs to target this dedicated queue. As you will see later, interactive jobs will include a parameter `-q XYZ`, and batch jobs will include the line `#PBS -q XYZ`. In both cases, the job scheduler PBSPro will send jobs to this specified queue.

## Useful links
 - [MetaCentrum terms and conditions](https://www.metacentrum.cz/en/about/rules/)
 - [Registration form](https://metavo.metacentrum.cz/en/application/index.html)

> [!NOTE]
> MetaCentrum is intended only for employees and students of research organisations in the Czech Republic and for research purposes only!
   
 - [Documentation](https://docs.metacentrum.cz/)
 - [Monitoring page](https://metavo.metacentrum.cz/en/index.html)
 - [User support contact](https://docs.metacentrum.cz/contact/)
 - MetaCentrum is an activity of the [CESNET](https://www.cesnet.cz/?lang=en) association, part of the [e-INFRA CZ](https://www.e-infra.cz/en) - research and development e-infrastructure













