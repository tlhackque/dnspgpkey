# dnspgpkey

Utiltity to generate DNS OPENPGPKEY records from GPG keyring entries

Copyright (C) 2018 Timothe Litt


## Usage:
       dnspgpkey [options] email [email ...]

 Options:
-   `-n`     Format record on one line (nsupdate-compatible)
          Default is zone file format (mult-line rdata)
-   `-t:n`   Specify TTL for record

Specify the e-mail address(es) for which OPENPGPKEY records are
to be generated.  The keys must be on your GPG keyring.

Valid records on stdout (can feed to nsupdate or zone file).
Errors on stderr.

## Bugs
Use the issue tracker on https://github.com/tlhackque/dnspgpkey

## Notes:

The mailbox name is case sensitive.

If multiple records are generated, the email addresses should all be in the same
zone (usually domain).  This is not enforced.

The e-mail address is output as comment with each record.

The zone MUST be protected by DNSSEC, however the consumer is still responsible
for trust decisions using the web of trust or manual verification.

See https://tools.ietf.org/html/rfc7929

## Dependencies:
- Perl
- Email::Address::XS
- Digest::SHA
- gpg (on PATH or export GPG=/path/to/gpg)
