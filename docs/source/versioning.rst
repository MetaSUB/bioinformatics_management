Data Governance
==============

This page outlines how data is handled at MetaSUB. It is concerned twith the practical issues of maintaining a large database for a scientific consortium.

This section details:
-   How version numbers are assigned for MetaSUB data
-   The management principles guiding new releases
-   Specific policies for data lifecycle management

Principles for High Quality Data
-------------------------------

Correctness > Stability > Convenience

Correctness
~~~~~~~~~~~

It is critical that the information we provide be correct, this trumps all other considerations. Even though it's embarrasing to admit a mistake it's better than allowing it to propagate. Whenever possible formats should be general such that correcting a mistake does not force programs to be rebuilt, however if it is not possible to correct a mistake without changing a format the format should be changed.

Stability
~~~~~~~~~

Every time something is released users can build off of it. If the format of what is released changes users must modify their work. As such it is more important to maintain existing formats than it is to make formats easy to use. Appending new items is typically fine and should be preffered to editing existing items.

Convenience
~~~~~~~~~~~

Releases should be as easy to access as possible. Data formats should be clear and standard and tooling should be provided for easy access. Releases should aim for a balance between useful information and clutter. Releases should always include a README explaining how the release work.

Versioning
----------

We use a form of Semantic Versioning meaning that each release is versioned by a triple of the form v1.2.3. These numbers are reffered to as major.minor.patch. Releases should contain documentation specifying what is in the release and the version of the release.

Changes to the documentation that improve clarity do not require a version bump. All changes that modify the version should include a changelog.

Patch versions are used to guarantee correctness. They can be used if the following criteria are met:
- A change corrects a specification error [1] without changing format
- A change adds a new object that does not interfere with old objects

Minor versions are used to add new data and guarantee correctness. They can be used if the following criteria is met:
- A change corrects a data error [2] without *substantially* changing format
- A change adds new data (append only). Note that changing a value from <null> -> <not null> for an existing sample is considered a patch. 

Major versions cover any and all changes not covered by Minor and Patch updates. Principally these are used for format changes or to reflect major changes in underlying sources.


[1] Defined as an error where the specification called for something other than what was present
[2] Defined as an error where the data given was incorrect, even if it was properly formatted

Data Flow
---------

Data follows a defined path from induction to release.

Induction -> Raw Data -> Processed Data -> Tabulated Data -> Release

Data Induction Policy
~~~~~~~~~~~~~~~~~~~~~

Data Induction should follow these steps:
1. Make a staging directory `staging/<proj>/<flowcell>` (bash)
2. download unconcatenated files to staging dir (H.A. utils)
3. concatenate files (H.A. utils)
4. rename files to HA-Uniq IDs (metasub utils)
5. move to main data dir (bash)
6. health check files and add to file spec (llps)
7. upload files to wasabi (llps)