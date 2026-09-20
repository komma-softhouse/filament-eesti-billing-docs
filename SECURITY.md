# Security Policy

## Supported versions

| Version | Supported |
| --- | --- |
| 1.x | ✅ |

Security fixes land on the latest 1.x release. Older tags are not patched.

## Reporting a vulnerability

Report privately, never in a public issue: open a
[security advisory](https://github.com/komma-softhouse/filament-eesti-billing/security/advisories/new)
on this repository, or write to **security@kommasofthouse.com**.

Please include the affected version, the steps to reproduce it, and what an
attacker could obtain or alter. A proof of concept helps, but a clear
description is enough.

What to expect:

- Acknowledgement within 3 working days.
- An assessment, with severity and a fix window, within 10 working days.
- Credit in the release notes when the fix ships, unless you prefer not to
  be named.

Please give us a reasonable window to release a fix before disclosing
publicly.

## Scope

This package issues invoices, builds the returns a company files with the
Estonian Tax and Customs Board, sends e-invoices and signs documents with
qualified certificates. Reports of the following are especially welcome:

- Anything that lets a completed document, its number, its VAT regime or
  its VIES proof be altered or deleted outside the guards that freeze it.
- Anything that lets a KMD, VD or OSS file be built from documents the
  user is not allowed to see, or for an issuer they do not manage.
- Anything that exposes Smart-ID or Mobile-ID relying-party credentials,
  e-invoice operator credentials, OCR API keys or print agent tokens, in
  storage, logs or responses.
- Anything that lets a signature be finished with a value that does not
  match the hash the signer was shown, or a signed container be altered
  after signing.
- Authentication or authorisation bypasses on the public routes: customer
  repair tracking, print agent pairing and dispatch, the signing endpoints.
- Injection or path traversal reachable from uploaded documents, OCR input,
  template branding files or the Business Register lookup.

Out of scope: findings that require an already-compromised host or
privileged access to the database, denial of service through resource
exhaustion, and vulnerabilities in e-MTA, VIES, the Business Register or
SK ID Solutions' own services.