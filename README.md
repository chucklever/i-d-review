# i-d-review

A [Claude Code](https://claude.ai/code) plugin for authoring and reviewing
IETF Internet-Drafts.

## What it does

The plugin provides an `internet-draft` skill that loads automatically when
Claude Code detects you are working on Internet-Draft source files
(`draft-*.md`, `draft-*.xml`, `draft-*.txt`) or when the conversation touches
IETF-specific topics such as xml2rfc, kramdown-rfc, mmark, idnits, BCP 14,
WG adoption, or bis documents.

The skill covers:

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

Once installed, the `internet-draft` skill activates automatically when you
open an Internet-Draft source file or discuss IETF topics. No manual
invocation is required.

## License

MIT
