# Bioinformatics at MetaSUB

## Code Availability

We use a number of programs for bioinformatics at MetaSUB. All code is available on GitHub. Everyone in MetaSUB is welcome to contribute to any relevant codebase including filing issues.

Except for Figure Generation all code is public.

### Data Analysis

[The Core Analysis Pipeline](https://github.com/MetaSUB/MetaSUB_CAP)
[The Core QC Pipeline](https://github.com/MetaSUB/MetaSUB_QC_Pipeline)
[The Core Assembly Pipeline (WIP)](https://github.com/MetaSUB/MetaSUB_assembly_CAP)
[Data Table Generator](https://github.com/dcdanko/capalyzer)
[Figure Generators (private, contains unpublished data, ask for access)](https://github.com/dcdanko/metasub-packetizer)
[Macrobial Abundance Estimation](https://github.com/MetaSUB/macrobial-genomes)

### Utilities

[Uncategorized Utility Scripts](https://github.com/MetaSUB/metasub_utils)
[Metadata Clean Up and Collation](https://github.com/dcdanko/MetaSUB-metadata)
[Pipeline Compiler (ModuleUltra)](https://github.com/dcdanko/ModuleUltra)
[Pipeline Organization and Structure (DataSuper)](https://github.com/dcdanko/DataSuper)
[Abandoned Package Manager for Biological Data (PackageMega)](https://github.com/dcdanko/PackageMega)



## How the data is stored

### Data Availability and Storage
pp


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
