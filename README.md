# i-d-review

A [Claude Code](https://claude.ai/code) plugin for authoring, reviewing, and
chairing IETF Internet-Drafts.

## What it does

The plugin provides three skills that load automatically from context.

### `internet-draft` — authoring and reviewing drafts

Loads when you are working on Internet-Draft source files (`draft-*.md`,
`draft-*.xml`, `draft-*.txt`) or the conversation touches IETF topics such as
xml2rfc, kramdown-rfc, mmark, idnits, BCP 14, WG adoption, or bis documents.
Covers:

- **Normative language** — BCP 14 keyword usage, required boilerplate, and
  common deviations
- **Citations** — normative vs. informative classification, downrefs,
  Internet-Draft references, and citation-verification procedure
- **Document structure** — mandatory sections, Security/IANA considerations,
  front-matter hygiene
- **Authoring toolchains** — mmark vs. kramdown-rfc, xml2rfc v3 validation,
  idnits pre-submission lint
- **Review workflow** — end-to-end orientation, front-matter, citation pass,
  body review, and reporting findings
- **WG adoption** — RFC 7221 §2.2 criteria, charter and milestone
  verification, IPR check
- **Bis documents** — RFC 2026 §6.3, defect correction vs. new feature,
  WG-specific extension rules

### `wg-advancement` — chairing a document from adoption to RFC

Loads when acting as a working-group chair to advance a document: running
adoption calls and WG Last Calls, judging and declaring rough consensus
(RFC 2418, RFC 7282, RFC 8789), producing the document shepherd write-up
(RFC 4858), and tracking a draft through IETF Last Call and IESG evaluation to
publication (RFC 2026, RFC 7127, BCP 97).

### `wg-management` — running the working group

Loads for standing chair operations not tied to one document: charter scope
and rechartering (RFC 2418), milestones, IPR disclosure polls (BCP 79,
RFC 6702), meetings, and mailing-list moderation including posting suspensions
and PR-actions (RFC 3934, RFC 3683).

## Installation

### 1. Add this repository as a Claude Code marketplace

```
claude plugin marketplace add https://github.com/chucklever/i-d-review.git
```

Or from within a Claude Code session:

```
/plugin marketplace add https://github.com/chucklever/i-d-review.git
```

### 2. Install the plugin

```
claude plugin install i-d-review
```

Or from within a Claude Code session:

```
/plugin install i-d-review
```

Restart Claude Code after installation for the plugin to take effect.

## Usage

Once installed, the skills activate automatically from context — the
`internet-draft` skill when you open a draft or discuss IETF document topics,
and the `wg-advancement` and `wg-management` skills when you take on
working-group chair tasks. No manual invocation is required.

## License

MIT
