# Finding RFCs and Archived Drafts

Citation verification (citations.md) assumes you can already
obtain the referenced document. This file covers the step
before that: locating an RFC or an Internet-Draft — including
an expired one — when you hold a title keyword or a
sub-series label rather than a document number.

## Fetch a document you can already name

- Published RFC, plain text:

    https://www.rfc-editor.org/rfc/rfc<NNNN>.txt

- RFC metadata in one view — status, stream, which STD or
  BCP it belongs to, "Obsoleted by" / "Updated by", and
  errata links:

    https://www.rfc-editor.org/info/rfc<NNNN>

- Errata for a published RFC:

    https://www.rfc-editor.org/errata/rfc<NNNN>

Prefer the /info/ page over reading the .txt header when you
need status or sub-series membership: RFCs from the v3
(xml2rfc) toolchain omit the old header block, and sub-series
membership never appears in the body at all.

## Resolve a sub-series label (BCP / STD / FYI)

A BCP, STD, or FYI number is not an RFC number, and the
RFC(s) it maps to change over time — BCP 79 is RFC 8179
today, was RFC 3979 before. Never hardcode the mapping from
memory; resolve it:

    https://www.rfc-editor.org/info/bcp<NN>
    https://www.rfc-editor.org/info/std<NN>

The page lists the current member RFC(s); fetch those by
number for the actual text. This matters throughout IETF
work: BCP 14, BCP 79, BCP 97, and the rest are cited by
sub-series label but must be read as their current RFCs.

## Search when you do not have the number

The datatracker document search covers RFCs and drafts,
active and expired, in one query:

    https://datatracker.ietf.org/doc/search/?name=<terms>

`name=` matches against the document name and title, not the
body text: a term that never appears in a title returns
nothing, so search with words you expect in the title rather
than an arbitrary topic. URL-encode spaces in <terms> (%20).
Add the document-type toggles; the expired one is off by
default:

- `rfcs=on` — published RFCs.
- `activedrafts=on` — current Internet-Drafts.
- `olddrafts=on` — expired, replaced, and withdrawn drafts.
  Omit it and an expired draft never appears in the results.

Results link to each document's page (`/doc/<name>/`,
`/doc/rfc<NNNN>/`). Confirm the exact title and status on
that page, then pin the match to an RFC number or a full
versioned draft name before fetching text; when several
same-titled documents remain, disambiguate through the
document page and its history rather than guessing. For an
RFC-only search by title, author, stream, or status, the RFC
Editor's form is at

    https://www.rfc-editor.org/search/rfc_search.php

## Retrieve a specific archived draft version

Every posted revision, including long-expired ones, is
retrievable by full versioned name. The version number is
part of the filename; a bare draft name is ambiguous:

    https://www.ietf.org/archive/id/draft-<name>-<NN>.txt

For example, draft-ietf-nfsv4-minorversion2-01.txt returns
the April 2011 revision. To enumerate every version of a
draft, see which became an RFC, and see what it replaced or
replaces, use the datatracker document page and its history:

    https://datatracker.ietf.org/doc/<draft-name>/
    https://datatracker.ietf.org/doc/<draft-name>/history/

The unversioned datatracker page redirects to the latest
revision; the archive/id URL always needs the version number.

## Pre-built reference XML

For a reference entry rather than document text, take the
citation-library XML from bib.ietf.org rather than
hand-building it. A published RFC's entry is at

    https://bib.ietf.org/public/rfc/bibxml/reference.RFC.<NNNN>.xml

Internet-Draft and sub-series (BCP/STD) entries live under
sibling bibxml directories on the same host. When you do not
know the sibling path, hand-build the reference from the
/info/rfc<NNNN> metadata (title, authors, date, status)
rather than guessing the path.
See citations.md for when a URI may accompany a reference and
when a versioned draft cite is required.
