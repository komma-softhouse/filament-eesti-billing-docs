# Changelog

All notable changes to `komma-softhouse/filament-eesti-billing` are documented here. The format follows Keep a Changelog and the project follows SemVer.

## [1.2.0] - 2026-09-24

### Removed

- The runtime licence check: the daily call to the licence server, the licence banner, the grace period and the pause in issuing. The licence is enforced where it is sold — access to the private Composer repository, which gates every install and update.
- The `eesti_license_state` table, dropped by a new migration, and `PermissionGate::LICENSED_ABILITIES`.
- The licence line in `eesti:selftest`.

### Deprecated

- `eesti:license` does nothing and exits successfully, so schedules that call it keep running. `LicenseExpiredException` is no longer thrown. Both are removed in 2.0.

## [1.1.1] - 2026-09-20

### Fixed

- `migrate` on a host without spatie/laravel-settings no longer fails: the plugin creates the `settings` table when it is missing, before its settings migrations run.

## v1.1.0 - 2026-09-20

### What's Changed

* Signing settings page, register lookup, masked inputs, series preview by @edeoliv in https://github.com/komma-softhouse/filament-eesti-billing/pull/4
* 1.1.0 docs and screenshots by @edeoliv in https://github.com/komma-softhouse/filament-eesti-billing/pull/5

**Full Changelog**: https://github.com/komma-softhouse/filament-eesti-billing/compare/v1.0.1...v1.1.0

## [1.1.0] - 2026-09-20

### Added

- Signing settings page in the panel: ways offered, Smart-ID and Mobile-ID relying-party credentials stored encrypted, demo or production environment, a test-connection button per service, and the trust services (time-stamp, OCSP). The configuration file remains a fallback.
- The Web eID JavaScript library ships as a plugin asset; the sign dialog checks the secure context and the extension before asking for the card, validates the personal code and the phone, and names what is missing.
- Business Register lookup reads the public company page as a second source: address, city and postal code parsed from the Estonian format, e-mail, phone, website, VAT number and whether the company receives e-invoices.
- Input masks on registry codes, VAT numbers, IBAN, BIC, postal codes, phones and personal codes: characters that can never be valid are refused while typing and cleaned on paste.
- Live preview on numbering series of the next number and the payment reference it will carry.
- Estonian and international carriers on delivery notes and repair orders: Omniva, DPD, Smartpost, Venipak, DHL, UPS, FedEx, GLS.
- Slide-over help on customers and issuers.

### Changed

- Customer and issuer forms rebuilt with sections, descriptions, grids and toggle buttons.
- The print agent token is generated when the issuer is selected, not at the first download.
- `eesti:selftest` checks that the Web eID library is published and that the panel is served over HTTPS.

### Fixed

- Dashboard widget errors from the expense ledger.
- Sign action hidden by an operator-precedence bug.
- A stray copy of the register client under `src/EestiBilling` is removed.

## v1.0.1 - 2026-09-19

### What's Changed

* Fix migration order and the repair-tables migration by @edeoliv in https://github.com/komma-softhouse/filament-eesti-billing/pull/3

**Full Changelog**: https://github.com/komma-softhouse/filament-eesti-billing/compare/v1.0.0...v1.0.1

## v1.0.0 - 2026-09-19

### What's Changed

* Full scope for 1.0.0: complete Estonian fiscal document engine by @edeoliv in https://github.com/komma-softhouse/filament-eesti-billing/pull/2

**Full Changelog**: https://github.com/komma-softhouse/filament-eesti-billing/compare/v0.1.0...v1.0.0

## [1.0.0] - 2026-09-17

### Added

- Document cycle: quote, order, delivery note, proforma, invoice, receipt and credit note; drafts complete into numbered, immutable documents and convert forward; recurring documents; catalog items; merge into invoice.
- VAT regime decided at completion by customer, with the VIES consultation number stored on the document; reduced 13 % and 9 % rates per line.
- Estonian payment reference (viitenumber, 7-3-1) per invoice or per customer; ISO 11649 RF reference; IBAN validation for any country with several accounts per issuer.
- Due date from the payment term and late interest per day, on the issuer, the customer or the document.
- Customer directory with Business Register lookup, VIES check and the regime the engine would apply today.
- Returns: KMD with INF A and B, VD and OSS, as the XML files e-MTA imports; VAT position widget.
- E-invoices in EN 16931 UBL and e-arve 1.2; delivery through Finbite or a Peppol access point; check of the customer's e-invoice recipient status in the Business Register.
- Digital signing with ID-kaart (Web eID), Smart-ID and Mobile-ID into ASiC-E containers, with download and validation.
- Template designer for A4 and receipt paper with live preview, watermark, colours and labels; document language Estonian, English, Russian or Spanish.
- PDF through mPDF or Gotenberg, chosen explicitly; ESC/POS receipts and the print agent; Z/X reports and movements.
- Received invoices and expenses, by hand or from a photo (OCR), feeding input VAT and INF B.
- Audit trail, permissions per action with Gate override, licence guard, self-test command.

### Removed

- Everything Spain-specific from the 0.1.0 line: the standalone invoice resource is replaced by the document cycle.

## [0.1.0] - 2026-09-17

### Added

- First release: VAT regime resolver, VIES client, sequential numbering, locked invoices with PDF and EN 16931 XML, credit notes, Issuer page and Invoices resource.
