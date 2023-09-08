---
layout: post
title: "Where data belongs"
description: "Guidelines for storing and organizing data in the Wallace lab"
about: true
author_handle: ew
tags: [labmanual, newstart]
---
{% include JB/setup %}

# Guidelines for storing and organizing data in the Wallace lab

The principles behind our approach to data are described in [data management plan](data-management-plan); this manual page contains practical guidelines.

All data must be securely stored and backed up, usually to the lab's datastore space `wallace_rna`. 

Data must also be findable, organized, and described, usually with a `README.txt` or `README.md` file that describes the contents of each directory.

**Please ask if there is any doubt at all about any of this.**

* TOC
{:toc}

## Resources on dealing with data

Dealing with data is important and can get complex.
Here are some helpful resources that make it easier to deal with data effectively.
The first two papers are essential reading.

* [Good enough practices in scientific computing, article](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510)
* [Good enough practices in scientific computing, lesson website with links](https://carpentries-lab.github.io/good-enough-practices/)
* [How to Share Data for Collaboration, Shannon E. Ellis & Jeffrey T. Leek](https://doi.org/10.1080/00031305.2017.1375987)
* [Edinburgh's BioRDM team](https://www.ed.ac.uk/biology/research/facilities/research-data-management)
* To be continued...

TODO: make a plan for storing microscopy images.


## README files

It is very helpful to give a brief overview of folders containing data that says "read me first to understand what's here", called a [README file](https://carpentries-lab.github.io/good-enough-practices/05-project_organization.html#readme-files-are-magic). 

Different projects will have different needs, for example there are alternative needs for cloning projects, software projects, manuscript drafts, etc.
The test is, can someone read the README file and know if the directory contains what they need?
Can they find what they need in under 5 minutes?
README files are mutually supportive with the lab notebook.

Edward's default recipe for README file example of a small cloning/lab project is below, certified to prevent him from screaming.

Create a new file called README.md (in markdown plain-text format) in the directory, adapted from:


```
# COPY NAME OF DIRECTORY AS FIRST LINE

This directory contains materials for GOAL OF PROJECT

Materials include DELETE/ADD AS APPROPRIATE
- fasta files with gene sequences
- .txt files with lists of oligos to order
- snapgene files with annotated sequences and plasmid maps
- .svg files with figures describing the designs
- ETC.

This material is also used in/uses  LINK TO LAB NOTEBOOK, OTHER DIRECTORY, ETC
The work was done by YOUR NAME AND THE DATE
(and updated ADD MORE NAMES AND DATES IF USEFUL)

MORE BRIEF EXPLANATION AS NEEDED

# Contents

COPY THE LIST OF SUBDIRECTORIES AND FILES

MAKE SUBDIRECTORIES INTO SUBHEADINGS AND THE FILENAMES INTO BULLET PINTS, WITH 1-SENTENCE EXPLANATION OF EACH

EXAMPLE:

## L0_plasmids SUBDIRECTORY NAME

Level 0 plasmids containing individual parts to use in gene assemblies

- pXX001_L0_NtermGFP.dna - Level 0 plasmid containing N-terminal GFP tag codon-optimised for Cryptofungus
- ETC.


# TO DO next

The next steps of this project are:

- SAY WHAT'S NEXT
- SO THAT WHEN YOU READ THIS AGAIN YOU KNOW WHAT TO DO

```

It's good to ask a colleague to have a quick read over and highlight anything unclear, soon after creating the file.


# wallace_rna on datastore

Most everyday lab data goes in `wallace_rna/data`. 
We have a full list of contents and organisation below (work in progress).

## Datastore Contents

* quota.txt - automatically generated file that keeps track of data usage compared to quota

* admin - lab administration, inventories, etc.
* bigdata - big data like (raw) sequencing and proteomics datasets
* **data** - everyday lab data, images, tables, qPCR, etc etc
* datasync - use for sharing data outside the group with the [datasync dropbox-like service](https://www.ed.ac.uk/information-services/computing/desktop-personal/datasync)
* LabMemberContactNos - emergency contact numbers for people who use the wet lab
* manual - contains a previous version of the lab manual from 2019
* presentations - copies of presentations from lab meetings
* riboviz - data related to the riboviz project [riboviz github](https://github.com/riboviz)

Folder organization and contents are described in detail below.

## wallace_rna/admin/

Administrative material for the lab, including inventories, strain database, and archives.

This folder is currently not very well organised. Please try to use it all the same.
Suggest improvements if any occur to you.

### wallace_rna/admin/Inventories

Inventories of lab strains, equipment and stocks

### TODO: REVISE THESE Guidelines for organising glycerol stock strains in datastore

Information on all Fungal and E.coli strains available in the lab are recorded in an Excel spreadsheet called `Edward Lab Database` within the `Strains_and_Associated_Info` Folder in datastore: `wallace_rna/admin/Inventories`. This spreadsheet is divided up into separate sheets for `Yeast` (ie., S.cerevisiae) , `Cryptococcus` and `Bacteria` (ie., E.coli stocks of plasmids). When you make new strains, full details need to be entered into this spreadsheet, as described in [where lab stuff belongs](where-lab-stuff-belongs).

The `Strains_and_Associated_Info` folder also includes additional folders and files:

- **`JA_chimeras_library_yeast_glycerolstock`** – Jamie’s YeastFab database spreadsheet and platemaps of 96-well storage locations together with explanatory `Readme` files as .pdf or .Rmd documents. This folder also contains a subfolder entitled 'JA_chimeras_snapgene_vector_maps' which contains the snapgene vector maps and sequencing trace files verifying the assemblies.

- **`S_cerevisiae_gRNA_plasmids`** -  Snapgene files of gRNA/Cas9 plasmids already existing in the lab - these are linked by name to the relevant entry of the plasmid stock in the `Bacteria` page of ` Edward Lab Database`.

- **`PrimersToTestYeastDelStrains`** – a list of PCR primer sets from the Yeast Deletion Collection that have been used to test deletion strains we already have, together with the expected sizes of their PCR products.

- **`YeastDeletionCollection_Check Primers_PCR_sizes`** - Full list of Primers and Expected PCR product sizes for all of the Yeast Deletion Collection Strains.

- **`YeastDelStrainsfromFoundryin96WellPlate`** – a spreadsheet with the position of a number of yeast deletion strains we got from the Genome Foundry in a 96-well plate.

- **`egf_strains_catalog`** – a list of yeast strains available from the Genome Foundry 

- **`-80 freezer storage locations`** – a spreadsheet showing where communal and personal frozen stocks are kept in the -76oC Freezer – this still needs to be updated to provide space for Rachael . There is also an explanatory `-80 freezer ReadME` file.

- The **`CramerLabDelStrains PCRCheck Primers`** Folder contains snapgene files for CCR4 and POP2(CAF1) genomic sequences together with PCR check primers.

## wallace_rna/bigdata - big data like (raw) sequencing and proteomics datasets

bigdata directory is for storing large files of high-throughput data.
The kind that need to be returned to again and again.
Mostly this focuses on raw data.
We would usually put analysis of the data somewhere else, for example a github repository.

Including:
- high-throughput sequencing data in .fastq format (RNA-seq, CRAC, etc.)
- proteomics data in .raw , .mzML, etc. format (when we get some)
- large microscopy datasets (e.g. smFISH)

Currently (April 2022) the organisation is, uh, mixed.
Some of it is split by year, and some by type of data.
Contents are described in detail below.

Subdirectories are:

- 2018
- 2019
- 2021
- 2022
- fastq

When we start to collect proteomics data, that will need a separate subfolder here as well.

Full contents are listed in a `wallace_rna/bigdata/README.md`

### fastq directory instructions

This folder contains assorted raw fastq files from multiple experiments.
Some are Wallace lab experiments, some pre-date the opening of the Wallace lab from Edward's postdoc work, some from collaborators.

*All raw sequencing datasets should be placed in `wallace_rna/bigdata/fastq` folder as soon as the facility notifies us that the sequencing is complete.*


1. Download the data to here.
2. If necessary, un-archive a tarball into a directory containing individual .fastq.gz files.
3. Check the data integrity by calculating checksums for the individual `.fastq.gz` files and comparing that with the checksums downloaded. If they don't match, download again.
4. Change file permissions to global read only (e.g. `chmod 444 my_new_data`) to make it harder to delete.
5. Update the README file to include your data, a note about it, and a link to a more detailed description such as a sample sheet.
6. If you are feeling paranoid, backup somewhere else as well - and verify your checksums!

See download instructions at [Downloading high-throughput sequencing data](lab-tips-tricks#downloading-high-throughput-sequencing-data)


## wallace_rna/data - everyday lab data, images, tables, qPCR, etc etc

This folder is organized primarily by date then your name: `yyyy/mm-mmmm/name`.
We use years (e.g. `2021`) and months (e.g. `01-Jan`) to ensure that the contents display in consistent order. 
Please make sure to use a hyphen `-`, so `03-Mar` not `03_Mar` nor `03 Mar`.
Please take care to accurately name the folder according to the month when the data were generated; this should be easy if you backup the data quickly.

For example, the directory `wallace_rna/data/2020/07-Jul/Edward/Ssd1_reportergenes_5UTRonly` contains Edward's data from July 2020 on some Ssd1 reporter genes, where the Ssd1 recognition site is on the 5'UTR.
This folder contains a `README.md` file giving an overview of its purpose and all the contents.

For lab data it is helpful to include the date of data generation in a consistent format in every filename, ideally `yyyy-mm-dd`. Generally, dates are unambiguous. Then it is easy to cross-reference the lab notebook for that day. 

If you have some data that does not easily lend itself to being sorted by months, then please sort it by year and name.
Be sure to add a README file explaining what the contents are, including one sentence on why it is not suitable to being organized by year and month.

Wherever the data are on datastore, it should also be linked to from the relevant lab notebook page in RSpace.

If in doubt as to whether a file should be saved - save it and describe it in the README file.

### About integrating with github

It is ok to have more than one backup copy of data as long as it is unambiguous what is the same and what is different - this is another argument for including a date in every file name.
Version control with git is helpful here.
If you are doing some data analysis in a github repository, it may make sense to clone a copy of the github repository into the relevant `yyyy/mm-mmmm/name` folder on datastore.

If in doubt, ask.


## wallace_rna/datasync - use for sharing data outside the group 

The university's [datasync dropbox-like service](https://www.ed.ac.uk/information-services/computing/desktop-personal/datasync).

## wallace_rna/LabMemberContactNos - emergency contact numbers for people who use the wet lab

Please ensure this is updated with your current phone number

## wallace_rna/presentations - copies of presentations from lab meetings

This contains all the presentations from past lab meetings and external talks (conferences, seminars, ...).
Please upload your presentation as soon as possible.
Please ensure that the filename contains your name, the date, and some note of the occasion, for example `EWallace_Fellowsmeeting_29Jan2021.pptx`.

## wallace_rna/riboviz - data related to the riboviz project 

The project is at [riboviz github](https://github.com/riboviz).

Some of the data are too large for github, so they live here.
