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
 email = "robinFIXME@transip.nl"
[author.address.postal]
 city = "FIXME"
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

This is some background text

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
