Communication Between Distributed Nodes
=======================================


A distributed web of trust as proposed here will need to be protocol agnostic when it comes to communication of the data which it contains.  That said, there should be some discussion of the protocols presently available and the advantages or disadvantages of using them.

Developers looking to provide an interface between users and node data should pay particular attention to this and aim to implement more than one protocol for the sake of redundancy.

It should be noted that the communications protocols used may open a node to certain types of threats, particularly if the realm this web of trust is being used in requires protecting identities (e.g. civilians in Mexico who need to protect themselves from the drug cartels).  There are, of course, the means to address this through anonymising networks, such as Tor and I2P, so developers should at least provide the ability to access alternative networks through proxy settings (HTTP, HTTPS, FTP and SOCKS5, just as in most browsers).


HTTP/S
------

Expect this to be one of the most common means of serving node data.  Either directly or by providing a compressed archive (.zip, .tar.gz, etc.).  It requires little introduction.


IRC
---

As with version 1 on #bitcoin-irc, information could be checked through queries sent to an IRC bot.  Such a bot could be a private one only used to access the data for a single node or it could be more like the gribble bot on #bitcoin-otc and used to check the entire web of trust either for a single realm or all realms.


SMTP
----

An automated mail gateway could be used to request specific data in much the same way as with an IRC bot.  This may or may not be signed or encrypted using GPG.


Torrents
--------


BitMessage
----------

This is a fairly new protocol which provides a pseudonymous messaging system.  Information is available at https://bitmessage.ch


XMPP
----

This is the open standard instant messaging system more commonly known as Jabber and which supports OTR encryption, though it incorporates SSL connections.
