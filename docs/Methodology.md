Methodology
===========


Introduction
------------

The predecessors to this system, the OpenPGP Web of Trust and the Bitcoin OTC Web of Trust both have their roots in the need for a system of recommendation and reputation in order to facilitate a particular technical or otherwise entirely logical goal which did not immediately present the means to address the unpredictable element: the human factor.  In the case of OpenPGP the Web of Trust is essentially a means of introduction and verification that a particular cryptographic keypair belonged to a specific individual.  In the case of the Bitcoin OTC IRC channel the Web of Trust was an attempt to quantify and categorise the qualities of participants in order to facilitate trading in Bitcoins, other crypto-currencies, goods and services.

Within the strict confines of the original intent, the OpenPGP Web of Trust has been a guarded success, though it has not been without criticism.  In particular the lack of consistent key signing policies across all users, confusion regarding the levels attributed to types of signatures and how to address keys belonging to individuals maintaining a pseudonymous, yet consistent persona in their oonline dealings.

The Bitcoin OTC Web of Trust and ratings system has received somewhat more vocal criticism amongst those who have dealt with it, though it should really be considered the first step towards a more adaptable and robust system.  This is the intended successor to that system, hence the references to this one as version 2 and the existing rating system as version 1.  Version 1 has simply been an attempt at providing a means for rating interaction between parties involved with trade.  Unfortunately version 1 was subject to abuse by the vindictive or by unrelated parties, skewing the results and confusing a number of users.

The purpose of this new version is to create a system which is resistant to the types of negative aspects of version 1.  It is also to provide a trust metric or rating system which may be of benefit beyond the realm of Bitcoin trading and possibly beyond purely commercial activities.


Requirements of the System
--------------------------

There are a number of requirements of this new system.  Some of these are inherited from the previous system and some have become apparent as a result of short comings in the previous and other systems.

Essentially the system is a means by which a user or node is able to assign both a numeric and descriptive value of another node in relation to any given interaction.  Applications for this within a commercial context can be quite obvious, but it may also be useful for other types of interaction, from software development to political activity.

Since each user will have their own opinions or values when rating another and since there are plenty of examples of vindictive or abusive use of such systems, there is a need for a system which can withstand such abusive nodes.  The calculation of the trust metric between nodes ought to demonstrate this.


### Requirements of WoTv2 Specification

1. Open standard, clearly documented and free to use, develop or modify.
2. Clear base data packet structure which can be manually modified or edited if necessary.
  1. XML recommended in initial proposal.
  2. Other data storage formats permitted, but must be able to provide data in the base format in order to operate with all other nodes.
3. Communication protocol independent.
  1. The adoption or development of a peer-to-peer protocol for updating data would be beneficial.
  2. Protocol must be able to support updating node data.
4. Nodes to be authoritive for the information issued by them.
  1. Authenticity of node to be established through cryptographic signatures.
  2. Nodes to maintain relevant current data about themselves and their ratings of other nodes.
  3. Nodes to maintain historical record of old data.
5. Nodes to be able to interpret data as user deems fit.
  1. Automatically distrust information from nodes rated poorly.
  2. Set thresholds of trust regarding different classes of information.
  3. Weighted trust favouring nodes rated well or known to user.
  4. Local override (e.g. if a node knows something they're unable or unwilling to share).
  5. Other rules for interpretation of data (e.g. how many steps within the web to trust and to what degree).
6. Distributed data.
  1. Each node maintains their own authoritive data regarding self.
  2. May supply data through multiple locations.
  3. Keeps a local cache of external data in order to calculate trust metrics.
7. Spam and abuse resistance.
  1. Interpretation of ratings by each node should be able to withstand spam, abuse and sock puppet attempts at rigging the system.


### Requirements for Developers

1. Software must be able to provide a minimum level of communication with all other nodes.
  1. Simple method(s) of retrieving data from passive node repositories (e.g. HTTP GET requests).
  2. Must be able to import and export data in base format.
  3. Must NOT conceal some data types from the network as a means to achieve adoption of that software package (no vendor lock-in).
  4. Not even for custom data types specific to that software.
2. Interpretation of data.
  1. Must be able to list numerical ratings and rankings.
  2. Must be able to apply node's own ratings on data received externally.
  3. Must be able to apply local rules or overrides.
  4. Must NOT hard code trusted value for author(s) of the software.
  5. Must be able to display raw data in base data format or with all information types clear (i.e. raw XML or with each tag type clear).
3. Authentication and validation of nodes.
  1. Must be able to call GPG to verify signatures.
  2. Must be able to call GPG to decrypt messages.
  3. Must be able to call GPG to sign messages.
  4. Encryption of messages optional.
  5. Does NOT require a complete OpenPGP implementation, only the ability to use that external program.
  6. GPG passphrase should not be stored, should either be handled by gpg-agent (with GPG 2.0.x) or passed through to a terminal (with GPG 1.4.x).


### Requirements for End Users or Nodes

1. Proof of identity in the form of an OpenPGP (RFC 4880 compliant) key.
  1. Pseudonymous identification on the key is permitted.
  2. Strong key to reduce the risk of impersonation.
  3. See the Technical Specifications document for minimum key requirements.
2. Publicly accessible node data in specified format.
  1. This could be anywhere, as long as the data is accessible by other nodes.
  2. Likely to be web pages.
  3. If a peer-to-peer protocol is used then it may simply be a matter of maintaining local data and a client.


Trust Metric
------------

Essentially this begins with the description in the [Distributed Web of Trust Proposal 2](http://privwiki.dreamhosters.com/wiki/Distributed_Web_of_Trust_Proposal_2#Trust_Metric).  Specifically in that it is essentially a [flow network](http://en.wikipedia.org/wiki/Flow_network) where users are nodes and the relationships between them are edges.

The [straight-up web of trust](http://privwiki.dreamhosters.com/wiki/Distributed_Web_of_Trust_Proposal_2#A_trust_metric:_straight-up_web_of_trust) is the most basic form of calculating a trust metric and the initial one for development.  There is, however, nothing preventing the development of additional methods of calculating or interpreting trust.  Furthermore it is quite possible to utilise multiple trust and rating values, each applying to different realms.  For example, there might be a financial or trading trust value, a social trust value or some other area defined by the nodes in question.  These realm specific metrics may in turn contribute to an overall average or general trust metric.


