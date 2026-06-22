# i-d-review

A Claude Code plugin for authoring and reviewing IETF Internet-Drafts.

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

## Installation

```
/plugin install i-d-review
```

## License

MIT
