Data Availability and Storage
=============================

Data Packets
------------

We provide the results of the CAP as a set of data tables that can be easily analyzed using tools like Python, R, and Excel. These data tables include information on taxonomy, functional profiles, and resistomes for MetaSUB Samples. The data packet can be accessed via Dropbox or on GitHub (private repo), please contact David Danko or Chris Mason for access.

Teaching Packet
~~~~~~~~~~~~~~~

The MetaSUB data packet includes a curated subset of the data useful for teching or demos. This packet includes 8 samples from each of 16 cities with complete metadata and results.

Wasabi Cloud Storage
--------------------
We are storing the MetaSUB data on Wasabi Storage, a service that is functionally identical to Amazon S3. We have a single bucket on Wasabi that contains:

- Raw Sequence Data
- CAP Outputs
- Assemblies
- Data Packet

We maintain `utilities <https://github.com/MetaSUB/metasub_utils>`_ to download data from this service. Please contact David Danko for API keys.

See `this file <https://github.com/MetaSUB/bioinformatics_management/blob/master/data_storage.md>`_ for more information on how MetaSUB's data is stored.

MetaGenScope
------------

`MetaGenScope <www.metagenscope.com>`_ is available for automated visualization MetaSUB data. All MetaSUB cities with sufficient data have been visualized and may be accessed with appropriate credentials.

It is possible to create arbitrary sample groups. Please contact David Danko for access and questions.
