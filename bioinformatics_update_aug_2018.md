# Bioinformatics at MetaSUB

This document outlines the state of Bioinformatics at MetaSUB following the 2018 MetaSUB meeting in Brazil. It is largely based off of the discussion at the bioinformatics round table. 

At the round table many expressed interest in listing all MetaSUB-Bioinformatics resources, projects, and policies in a single place. This document addresses all of these topics and this repo provides a centralized point for management and discussion.

MetaSUB is a peer led organization. Everyone should feel free to ask questions, make suggestions, and contribute. The best way to start a discussion (if your topic does not relate to a specific codebase) is to use a GitHub Issue.

Thank you,
David Danko 

## Code Availability

We use a number of programs for bioinformatics at MetaSUB. All code is available on GitHub. Everyone in MetaSUB is welcome to contribute to any relevant codebase including filing issues.

Except for Figure Generation (which includes some unpublished data) all code is public.

### Data Analysis

[The Core Analysis Pipeline](https://github.com/MetaSUB/MetaSUB_CAP)

[The Core QC Pipeline](https://github.com/MetaSUB/MetaSUB_QC_Pipeline)

[The Core Assembly Pipeline (WIP)](https://github.com/MetaSUB/MetaSUB_assembly_CAP)

[Data Table Generator](https://github.com/dcdanko/capalyzer)

[Figure Generators (private, contains unpublished data, ask for access)](https://github.com/dcdanko/metasub-packetizer)

[Macrobial Abundance Estimation](https://github.com/MetaSUB/macrobial-genomes)

### Utilities

[Bioinformatics Management, Policies, and Communications](https://github.com/MetaSUB/bioinformatics_management)

[Uncategorized Utility Scripts](https://github.com/MetaSUB/metasub_utils)

[Metadata Clean Up and Collation](https://github.com/dcdanko/MetaSUB-metadata)

[Pipeline Compiler (ModuleUltra)](https://github.com/dcdanko/ModuleUltra)

[Pipeline Organization and Structure (DataSuper)](https://github.com/dcdanko/DataSuper)

[Abandoned Package Manager for Biological Data (PackageMega)](https://github.com/dcdanko/PackageMega)

## Data Analysis

### The Core Analysis Pipeline

The Core Analysis Pipeline is being run on all MetaSUB samples at Weill Cornell Medical. Due to the complexity of this pipeline it is not feasible to split computation across multiple sites. Results will be made directly available as soon as possible.

### Assemblies

Assembly of MetaSUB data is being performed using the XSEDE Project's supercomputing resources. The intention is to assemble all MetaSUB samples using MetaSPAdes. No quality control is performed before assembling reads.

Additional compute resources for assembly are welcome. Please contact David Danko to coordinate.

## Data Availability and Storage

### SFTP Server

Andre Kahles currently maintains an SFTP server at ETH Zurich. We are working to update this server to 
- [ ] include analyzed MetaSUB data
- [ ] include human-free data
- [ ] include assembled contigs
- [ ] match the file structure outlined below

Please contact Andre Kahles for a username and password.

### MetaGenScope

[MetaGenScope](www.metagenscope.com) is available for automated visualization MetaSUB data. It is possible to create arbitrary sample groups. Please contact David Danko for access and questions.

### Making Data Public

There are no plans to make the data publicly available until after the consortium has published a manuscript. Any data published will have human sequence scrubbed. 

## How the Data is Stored

### File and Naming Structure

All source files (raw, unedited fastqs) are stored in a 'library' directory. Each source file receives a globally unique name based on an ID shared only with its mate pair (if applicable). 

The unique names used to store source files typically are not scientifically useful. __This is an intentional design decision and will not be changed__. Throughout the course of the MetaSUB project there have been instances where a single sample was split over multiple files, where samples were assigned incorrect names, and where names were simply missing. Using a globally available and unique name obviates the need to perform time consuming and error prone migrations.

__Scientifically relevant names will still be supported__. However, these names will be maintained by symlinking to source files rather than storing directly. Map files from unique source names to relevant names will also be available.

The scientifically relevant name format is as follows `<metasub project id>-<city code>-[<optional subproject id>]<sample number>` (e.g. CSD16-OFA-070 or CSD17-OSL-AS16). Valid project codes, city codes, and subproject codes are listed in the metadata git repo. Since samples may be split over multiple source files files with metasub names will also include the source filename with the format `<metasub name>.<source id>.<ext>`.

### Hudson Alpha Files

The vast majority of MetaSUB samples were sequenced at Hudson Alpha. These are stored in a directory name `hudson_alpha_library`.

Each sample sequenced at Hudson Alpha was sequenced as part of a hudson alpha project (e.g. haib17CEM5241) on a particular flowcell (e.g. HMCMJCCXY). 

Each tube we sent to Hudson Alpha received an 'SL' name (e.g. SL336201), usually an SL name shows up in exactly one flowcell in one project but a few SL names (288 as of aug 22, 2018) appear multiple times in different flowcells (unclear if the same SL name can occur across hudson alpha projects).

To avoid collisions each source file is stored with a name in this format `<hudson alpha project id>_<flowcell number>_<SL number>_[1,2].fastq.gz` (e.g. haib18CEM5453_HMC2KCCXY_SL336821). This is referred to as the hudson alpha unique id (`hauniq` for short)

For convenience the `hudson_alpha_library` directory is subdivided into directories for hudson alpha projects which are themselves divided into directories for flowcells. As such the complete path for a given file looks like this `hudson_alpha_library/haib18CEM5453/HMC2KCCXY/haib18CEM5453_HMC2KCCXY_SL336821.fastq.gz`.

Source files from the same sample are never concatenated in the standard processing pipeline. This is because 1) such instances are rare, 2) technical replicates provide useful quality control, 3) managing such events is likely to lead to larger issues with organization. Of course custom analyses may concatenate as they see fit.

## Potential Projects

We discussed several potential projects at the MetaSUB meeting
- Sandboxes to facilitate data analysis
- Kmer countign in the CAP (in progress)
- Batch Normalization of Samples
- Sequence search against MetaSUB data (in progress by Andre Kahles)
- Uncertainty in taxonomic Assignments
