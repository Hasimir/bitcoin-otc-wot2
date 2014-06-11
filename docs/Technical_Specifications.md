Technical Specifications
========================


OpenPGP/GPG Recommendations
---------------------------

The master or certification key is used to create all subkeys, this must be the strongest or equal strongest key in the generated structure.  Often a master key will be both a certification key and a signing key, but where a signing subkey is used the signing component of the master key is ignored.  Subkeys provide the ability to separate functions and in doing so improve general security of the entire key.  A separate signing subkey is recommended, but not required.

The minimum key requirements are:

* Master/Certification key:  4096-bit RSA
* Signing subkey:  2048-bit RSA or 3072-bit DSA (DSA-2)
* Encryption subkey:  4096-bit RSA or 4096-bit El-Gamal

The minimum signature requirements are:

* Hashing algorithm:  SHA256

The minimum symmetric encryption requirements are:

* 256-bit algorithms included with GPG.
* AES256 (this is the most common).
* TWOFISH.
* CAMELLIA256.

Please note that elliptic curve algorithms are not yet standard and are not supported in all implementations of the OpenPGP standard.

