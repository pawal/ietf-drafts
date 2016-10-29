%%%

    Title = "DNS Copyright and License prefixes"
    abbrev = "DNS Copyright"
    category = "info"
    docName = "draft-wallstrom-dnsop-copyright-prefix-01"
    ipr= "trust200902"
    area = "ops"
    workgroup = "dnsop"
 
    date = 2016-10-29T12:00:00Z
 
    [[author]]
    initials="P."
    surname="Wallstrom"
    fullname="Patrik Wallstrom"
    organization="IIS"
        [author.address]
        email="pawal@iis.se"
 
%%%

.# Abstract

The content of a typical zone file is lacking information on the copyright
and license from which the content of the zone file is available. The
typical use is to make a zone file available after an agreement on use
(license) has been made. When the zone file is publicly available through
DNS, there is no way of signalling the copyright ownership or any end user
license of the content. Other means of distributing the zone file allows
this, such as using comments in a zone file distributed over other
channels. This document describes two prefixes for handling this using the
TXT RR type, _copyright and _license.

{mainmatter}


# Introduction

A zone file is typically not available to an end user in its entirety,
but rather accessed only through DNS lookups. AXFR and other methods for
accessing the complete content of the zone file is often prohibited.

For clients and applications that wish to use the zone file for purposes
other than DNS lookups, adding the copyright and license information
to the zone file itself is useful.

This document describes two prefixes for handling this using the TXT RR
type, _copyright and _license. A client that looks up these records in a
zone can determine the copyright owner and the license of the content of a
zone.

The use of an underscore prefix is based on the work on
[@?I-D.ietf-dnsop-attrleaf].

## Reserved Words

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [@?RFC2119].


# The _copyright prefix

The _copyright record is published in the zone using the DNS TXT resource
record type.

The RDATA for the _copyright resource record is textual in format using the
following template:

_copyright IN TXT "Copyright (C) YEAR Your Name or Organization"

The copyright applies to the specific zone of where the _copyright TXT RR
is found. The copyright itself is a sui generis database right that covers
the complete zone content, or larger portions of it where this type of
copyright law applies.


# The _license prefix

The _license record is published in the zone using the DNS TXT resource
record type.

The RDATA for the _license resource record is textual in format and is
a HTTP URL leading to the full license text represented in either plain
text or HTML. Example:

_license IN TXT &quot;https\://www.example.com/license.txt&quot;

The _license record can be omitted if there is no license given to the
client, of written as "All rights reserved." if no use rights are given.


# Security Considerations

This document has no security considerations.


# IANA Considerations

The prefixes described in this document might be published by the IANA
registry described in [@?I-D.ietf-dnsop-attrleaf].


# Acknowledgements

Thanks go to Dave Crocker, John R Levine, Roger Murray and Jakob Schlyter
for input on the content of this document.

{backmatter}
