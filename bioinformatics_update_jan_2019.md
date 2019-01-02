# Update January 2019

A record of new bioinformatics tools and features for MetaSUB.

## Big Things

### v1.0.1 Metadata for Sequenced Samples

We have a v1.0.1 metadata table for all sequenced samples. This table includes, at a minimum, city of origin and project for 4,495 samples*. Typically far more metadata is available in this table.

This table represents the v1.0.0 MetaSUB data freeze. 

*PathoMap is not included in this total

### v1.0.0 Data Packet

We have collated the results of the CAP into a set of data tables for the v1.0.0 data release. This packet is available on Dropbox and GitHub (private repo) and includes a detailed README

### All Sequenced Data on Wasabi Hot Storage

All sequenced data is available for download from Wasabi Hot Storage (an S3 clone). See [the utilities](https://github.com/MetaSUB/metasub_utils) and [this file](https://github.com/MetaSUB/bioinformatics_management/blob/master/data_storage.md) for more information.

Some members of the consortium have expressed interest in maintaining an SFTP mirror. We are exploring this possibility.


## Small Things

### Utilities

The [MetaSUB Utilities Repo](https://github.com/MetaSUB/metasub_utils) has been updated significantly. It now uses a microlibrary architecture with Continuous Integration and automated code review. This will make the codebase easier to maintain and extend. The version of the on the utilities on PyPi has been updated. This tool is used to download raw data from Wasabi Hot Storage

### Installing the CAP

Installing the CAP is getting easier. Several of the most problematic dependencies for the CAP (ModuleUltra, DataSuper) have been updated. We're continuing to work on ways to make the CAP easier to use.

### MetaGenScope

City specific pages on MetaGenScope have been updated with new data and metadata.

MetaGenScope will be receiving a facelift in January and there may be brief outages.

## Tiny Things

The `metasub-scripts` repo is deprecated in favor of the `metasub_utils` repo.

The `capalyzer` repo is about to be deprecated in favor of the `metasub_utils` repo.


