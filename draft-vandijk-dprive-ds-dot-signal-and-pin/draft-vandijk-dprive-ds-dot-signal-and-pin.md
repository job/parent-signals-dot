%%%
title = "Signalling Authoritative DoT support in DS records with key pinning"
abbrev = "ds-dot-signal-and-pin"
docName = "draft-vandijk-dprive-ds-dot-signal-and-pin-00"
category = "std"

ipr = "trust200902"
area = "General"
workgroup = "dprive"
keyword = ["Internet-Draft"]

[seriesInfo]
name = "Internet-Draft"
value = "draft-vandijk-dprive-ds-dot-signal-and-pin-00"
stream = "IETF"
status = "standard"

[pi]
toc = "yes"

[[author]]
initials = "P."
surname = "van Dijk"
fullname = "Peter van Dijk"
organization = "PowerDNS"
[author.address]
 email = "peter.van.dijk@powerdns.com"
[author.address.postal]
 city = "Den Haag"
 country = "Netherlands"

[[author]]
initials = "R."
surname = "Geuze"
fullname = "Robin Geuze"
organization = "TransIP"
[author.address]
 email = "robing@transip.nl"
[author.address.postal]
 city = "Delft"
 country = "Netherlands"

%%%


.# Abstract

This Internet-Draft specifies a way to signal the usage of DoT, and the pinned keys for that DoT usage, in authoritative servers.
This signal lives on the parent side of delegations, in DS records.
To ensure easy deployment, the signal is defined in terms of DNSKEY.

{mainmatter}

# Introduction

Even quite recently, DNS was a completely unencrypted protocol, with no protection against snooping.
In recent years this landscape has shifted.
The connections between stubs and resolvers are now often protected by DoT, DoH, or other protocols that provide privacy.


# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 [@!RFC2119] [@RFC8174]
when, and only when, they appear in all capitals, as shown here.

DS record
: as defined in [@!RFC4034]

# Background

To enable the signaling of DoT a new DNSKEY algorithm type [X] is added.
If a recursor encounters a DS record with the DNSKEY algorithm type [X] it MUST connect to the authoritative servers for this domain via DoT if it supports it.
It should use the hashes attached to the DS records with DNSKEY algorithm type [X] to check whether the public key supplied by the authoritative nameserver is valid.
If DoT connection is unsuccessful or the public key supplied the server does not match one of the DS digests name resolution should fail.

The pseudo DNSKEY record MUST contain DER encoded SubjectPublicKeyInfo as defined in RFC5280 4.1.2.7.
Since the cert provided by the TLS server over the wire is already DER encoded this makes for easy validation.
The pseudo DNSKEY algorithm type [X] is algorithm agnostic, like the TLSA record, since the DER encoded data already contains information about the used algorithm.
Algorithm support SHOULD be handled at the TLS handshake level, which means a DNS application SHOULD NOT need to be aware of the algorithm used outside its SSL library.
The pseudo DNSKEY record MUST NOT be present in the zone.
The procedure for hashing the pseudo DNSKEY record is the same as for a normal DNSKEY as defined in RFC4034.

The pseudo DNSKEY type can be used in CDNSKEY and CDS, as defined in RFC7344, records as well. These MAY be present in the zone.

# Use Cases {#usecases}


## First use case

Some text about the first use case. (And an example of using a second level
heading.)

## Second use case

This example includes a list:

- first item
- second item
- third item

And text below the list.

## Third use case

This use case includes some ascii art.  The format for this art is as follows:

~~~ ascii-art
        0
       +-+
       |A|
       +-+
~~~

# Security Considerations

As outlined earlier in (#usecases), there could be security issues in
various use cases.

# IANA Considerations

This document has no IANA actions.

{backmatter}

