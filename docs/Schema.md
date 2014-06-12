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
** Other Nodes
*** Node1
*** Node2
** Received
*** Contracts
*** Ratings
** Shared Authority

The base directory contains files identifying the node, a copy of the OpenPGP public key, an index or toc and optionally a history of when files were added or changed.

The Archive directory contains previous versions of documents from the base, Authority or Shared Authority directories for comparison.  Data in this directory might be compressed.  If so then should use individual file compression (gzip, bzip2, xz) rather than collective compression (zip or tarball).  Archived files should have their timestamp appended to the filename.  The Received documents are likely to be recorded here too.

The Authority directory contains documents for which the node is the sole issuing authority.  This will likely be ratings documents in all probability.

The Other Nodes directory contains data and directories obtained from other nodes with each external node being assigned its own subdirectory.  The directory name should include the long key ID of the GPG key of the node in question as this will prevent name or username conflicts.  Data obtained from other nodes should at least include the base, Authority and Shared Authority directories.  Keeping the Archive directory is advisable (as is keeping one's own record independently of the Archive directories).  Keeping the Other Nodes directory of an external node is entirely optional.

The Received directory contains copies of documents directed to that node, in particular ratings from other nodes.  This makes the documents easier to locate in the future.

The Shared Authority directory contains documents for which the node is one of a number authorising it.  The most common example being a contract between two or more parties.  This directory might be subdivided into additional directories, such as for different realms.


Node Identification
-------------------

File:  node.xml
Location:  base directory

Contains complete data about a node and those documents it holds for which it is authoritive or one of a number of authoritive hosts.  See the example-node.xml file in the xml directory for the sort of thing which ought to be found in the node.xml file.

Depending on the number of files served, it may be preferable to create a separate index file.


Index File
----------

File:  index.xml
Location:  base directory

See the example-index.xml file in the xml directory for what this file should contain.  File paths should be relative to the base directory.

Should contain the realm data from node.xml and the authority data (including a detached signature).


OpenPGP/GPG Public Key
----------------------

Files:  openpgp.xml, pubkey.asc
Location:  base directory

This file should be available as a standard ASCII armoured GPG or PGP file, but may also be available encased in XML in order to be read into some programs.  If only one of these is used then it should be the ASCII armoured file.  A node may choose to include the public key in non-ASCII armoured form (e.g. pubkey.gpg) in addition to either or both of the standard files.


Rating Documents
----------------

Filename format:  name_keyid-timestamp.xml
Location:  Authority directory

The filename is constructed of the user's name or node name, the long form OpenPGP key ID and the timestamp of the rating (which makes it easier to move when superceded by a later rating).

The file should contain additional identifying information, including the fingerprint of the rated node's public key, numerical rating values, any additional notes, a raw text copy of the rating and an ASCII armoured detached signature of that raw text notes and rating.  Alternatively the raw text could be signed and ASCII armoured to create a block of what appears to be ciphertext.

The file should include references to any previous ratings in the Archive directory.


Contract Documents - Type 1
---------------------------

Filname format:  name_keyid-timestamp.xml
Location:  Authority directory


Contract Documents - Type 2
---------------------------

Filname format:  name_keyid-timestamp.xml
Location:  Other Nodes directories


Contract Documents - Type 3
---------------------------

Filname format:  name1_keyid1-name2_keyid2-timestamp.xml
Location:  Shared Authority directory


