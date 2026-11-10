# ztrust/pki

This is the ztrust/pki folder containing root PKI certificates
of z/OS and z/VM and z/Linux vendors and users.

## Certificates

The mere mention of PKI Certificates carries baggage for many people.
This project attempts to provide a "trust anchor" for the Z community
but also to provide information, explanation, documentation,
and simplification of the topics.

PKI is an acronym for "Public Key Infrastructure".
So-called public key cryptography, in turn, is used not only for
PKI certificates but also for such services as PGP and SSH
as well as countless security tools.

An excellent introduction was presented by Charles Mills
and was recorded and made available online.

https://www.newera.com/INFO/Certificates_2021.mp4

This folder contains a number of "root certificates" which you can use
to verify "leaf certificates" particularly in the Z community.

## Signing

Root PKI certificates are self-signed; they are not "issued" by another
certificate. Root certificates serve as the head of the trust chain.
Other certificates being self-signed, such as a self-signed server certificate,
is generally not best practice. (Though it is sometimes warranted.)
The veracity of a root certificate is indicated by its presence in the
local trust store. Trust stores containing many root PKI certificates
are distributed with the operating system or package.

PKI root certificates found here *may* be signed by PGP keys
(found in the companion "pgp" folder) as *detached* signatures.
A "detached" signature does not change the content of the signed file,
so detached PGP signing does not harm the certificates. It is safe.
A PGP signature on a PKI root certificate is an alternative affirmation
of the veracity of that root certificate.

## Naming

PEM-encoded certificates have a file type extension of `.crt`.

DER-encoded certificates (that is, binary) are not recommended here.

Human readable "text" form certs have a file type extension of `.txt`.
The PEM-encoded certificate will be found at the end of such a file.

Detached PGP signatures have a file type extension of `.asc`
indicating that they are ASCII-armored. The full extension is `.crt.asc`.

## Rationale

The following observation is from Dan Rathbun, CIO/CISO:

*"One of the inherent problems of standard HTTPS is that trust put in
a website is defined by certificate authorities: a hierarchical and
closed set of companies and governmental institutions approved by your
web browser vendor. This model of trust has long been criticized
and proven ... to be vulnerable to attacks ..."*

This trust anchor is intended to remedy that problem
in the context of the System Z mainframe community.


