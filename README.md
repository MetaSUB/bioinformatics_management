# Bioinformatics at MetaSUB

This repo tracks policies, management and communication for MetaSUB Bioinformatics.

This is an appropriate place to ask questions and make suggestions. Please use GitHub's issue feature to do so.

## Programs and Resources

We use a number of programs for bioinformatics at MetaSUB. Everyone in MetaSUB is welcome to contribute to any relevant codebase including filing issues.

### Public

[Metadata for Sequenced Samples](https://github.com/dcdanko/MetaSUB-metadata), A fully reproducible metadata table for all sequenced samples.

[The Core Analysis Pipeline](https://github.com/MetaSUB/MetaSUB_CAP), A pipeline for analysis of short read metagenomic data.

[The Core QC Pipeline](https://github.com/MetaSUB/MetaSUB_QC_Pipeline), A pipeline to perform quality control of samples.

[Data Table Generator](https://github.com/dcdanko/capalyzer), A tool to build data tables from the output of the CAP

### Private

_Figure Generators_, code to generate figures and tables for publication and exploration. Available as a private GitHub repo

_MetaSUB Data Packet_, raw data tables from running the CAP on MetaSUB samples. Available on Dropbox and as a private GitHub repo.


### Utilities

[Bioinformatics Management, Policies, and Communications](https://github.com/MetaSUB/bioinformatics_management)

[Utility Scripts](https://github.com/MetaSUB/metasub_utils), Used for managing metasub data, transferring storage, and handling analysis. Serves as a catch all for small programs.


## Data Availability and Storage

### Data Packets

We provide the results of the CAP as a set of data tables that can be easily analyzed using tools like Python, R, and Excel. These data tables include information on taxonomy, functional profiles, and resistomes for MetaSUB Samples. The data packet can be accessed via Dropbox or on GitHub (private repo), please contact David Danko or Chris Mason for access.

#### Teaching Packet

The MetaSUB data packet includes a curated subset of the data useful for teching or demos. This packet includes 8 samples from each of 16 cities with complete metadata and results.

### Wasabi Cloud Storage

We are storing the MetaSUB data on Wasabi Storage, a service that is functionally identical to Amazon S3. We have a single bucket on Wasabi that contains:

- Raw Sequence Data
- CAP Outputs
- Assemblies
- Data Packet

We maintain [utilities](https://github.com/MetaSUB/metasub_utils) to download data from this service. Please contact David Danko for API keys.

See [this file](https://github.com/MetaSUB/bioinformatics_management/blob/master/data_storage.md) for more information on how MetaSUB's data is stored.

### MetaGenScope

[MetaGenScope](www.metagenscope.com) is available for automated visualization MetaSUB data. All MetaSUB cities with sufficient data have been visualized and may be accessed with appropriate credentials.

It is possible to create arbitrary sample groups. Please contact David Danko for access and questions.

### Making Data Public

There are no plans to make the data publicly available until after the consortium has published a manuscript. Any data published will have human sequence scrubbed. 
