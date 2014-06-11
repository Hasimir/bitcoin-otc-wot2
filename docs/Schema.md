Information Schema
==================

This document describes the data types to be included within the schema and does so utilising the base data format of XML.  XML has been chosen so that there is no requirement for additional software to maintain the files of a node, though that might be beneficial.  The schema is intended to be a framework which provides the ability to enhance or expand upon any aspect of it in the future.


Directory Structure
-------------------

Storing these files within a specific directory structure is useful, both for classifying types of data and preventing naming conflicts with certain files.

The basic structure should be as follows:

* Base directory
** Archive
** Authority
** Shared Authority
** Other Nodes
*** Node1
*** Node2

The base directory contains files identifying the node, a copy of the OpenPGP public key, an index or toc and optionally a history of when files were added or changed.

The Archive directory contains previous versions of documents from the base, Authority or Shared Authority directories for comparison.  Data in this directory might be compressed.  If so then should use individual file compression (gzip, bzip2, xz) rather than collective compression (zip or tarball).  Archived files should have their timestamp appended to the filename.

The Authority directory contains documents for which the node is the sole issuing authority.  This will likely be ratings documents in all probability.

The Shared Authority directory contains documents for which the node is one of a number authorising it.  The most common example being a contract between two or more parties.

The Other Nodes directory contains data and directories obtained from other nodes with each external node being assigned its own subdirectory.  The directory name should include the long key ID of the GPG key of the node in question as this will prevent name or username conflicts.  Data obtained from other nodes should at least include the base, Authority and Shared Authority directories.  Keeping the Archive directory is advisable (as is keeping one's own record independently of the Archive directories).  Keeping the Other Nodes directory of an external node is entirely optional.


Node Identification
-------------------

File:  node.xml
Location:  base directory

Contains complete data about a node and those documents it holds for which it is authoritive or one of a number of authoritive hosts.  See the example-node.xml file in the xml directory for the sort of thing which ought to be found in the node.xml file.

Depending on the number of files served, it may be preferable to create a separate index file.


Index File
----------

File index.xml
Location:  base directory

