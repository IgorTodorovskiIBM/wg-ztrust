This folder holds all PKI root certificates in the ZTRUST collection
in armored or PEM-encoded format.

The file `pki-bundle.pem` one level up from here is a concatenation
of all of these PEM files.

The collection includes root certificates which chain to leaf certs
of any kind, including web servers and email encryption, but especially
for code signing.

## Naming

PEM-encoded certificates (armored) have a file type extension of `.crt`.

DER-encoded certificates (that is, binary) are not recommended here.

Human readable "text" form certs found here have a file type extension
of `.txt`. The PEM-encoded certificate itself will be found at the end
of such a file. These human readable forms are easily generated with ...

    openssl x509 -text -in rootcert.crt > rootcert.txt

Detached PGP signatures have a file type extension of `.asc`
indicating that they are ASCII-armored. The full extension is `.crt.asc`.
PGP-signed root PKI certificates can be verified with ...

    gpg --verify rootcert.crt.asc

You will, of course, need the signing key in your local PGP/GPG keyring.
See the PGP collection found in this repository.

## Rationale

These root certificates exist to fill the gap where Z community
contributions cannot be supported by the usual CA-provided root certs.


