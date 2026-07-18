# i-d-review

A Claude Code plugin for authoring, reviewing, and chairing IETF
Internet-Drafts.

## Skills

### `internet-draft`

Activated automatically when working on files matching `draft-*.md`,
`draft-*.xml`, or `draft-*.txt`, or when discussing RFC submissions,
xml2rfc, kramdown-rfc, mmark, idnits, BCP 14, WG adoption, or bis
documents.

Covers:

- **Normative language** — BCP 14 keyword usage, boilerplate, and
  common deviations
- **Citations** — normative vs. informative classification, downrefs,
  Internet-Draft references, and citation-verification procedure
- **Document structure** — mandatory sections, Security/IANA
  considerations, front-matter hygiene
- **Authoring toolchains** — mmark vs. kramdown-rfc, xml2rfc v3
  validation, idnits pre-submission lint
- **Review workflow** — end-to-end orientation, front-matter, citation
  pass, body review, and reporting findings
- **WG adoption** — RFC 7221 §2.2 criteria, charter and milestone
  verification, IPR check
- **Bis documents** — RFC 2026 §6.3, defect correction vs. new feature,
  WG-specific extension rules

### `wg-advancement`

Activated when acting as a working-group chair to advance a document.
Covers running adoption calls and WG Last Calls, judging and declaring
rough consensus (RFC 2418, RFC 7282, RFC 8789), the document shepherd
write-up (RFC 4858), and tracking a draft through IETF Last Call and IESG
evaluation to publication (RFC 2026, RFC 7127, BCP 97).

### `wg-management`

Activated for standing chair operations not tied to one document: charter
scope and rechartering (RFC 2418), milestones, IPR disclosure polls
(BCP 79, RFC 6702), meetings, and mailing-list moderation including posting
suspensions and PR-actions (RFC 3934, RFC 3683).

## Installation

```
/plugin install i-d-review
```

## License

MIT
