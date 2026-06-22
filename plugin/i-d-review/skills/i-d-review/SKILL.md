---
name: internet-draft
description: Load when authoring, editing, or reviewing IETF Internet-Drafts (files matching draft-*.md, draft-*.xml, draft-*.txt, or discussion of RFC submissions, xml2rfc, kramdown-rfc, mmark, idnits, BCP 14, WG adoption, bis documents). Covers normative language, citation verification against cached RFCs in ~/Documents/rfcs/, document structure, WG adoption criteria, bis-document scope rules, and review workflow. Do not load for general technical writing, non-IETF standards work, or discussions that merely mention an RFC in passing.
invocation_policy: automatic
---

# IETF Internet-Drafts

This skill covers authoring, editing, and reviewing IETF
Internet-Drafts. The main reference material lives in
`references/`; load the file whose topic matches the task.

## Operating principles

Do not guess about normative content. When uncertain whether
a claim requires a citation, whether a cited section number
is correct, or whether a term has a normative definition
elsewhere, consult the cached RFCs in `~/Documents/rfcs/`
(download procedure in CLAUDE.md) or ask the user. A
plausible-sounding citation that is wrong costs more to
untangle later than an up-front question.

When reviewing, verify every bibliographic citation —
including cited section numbers — against the cached text
of the referenced document. Flag discrepancies explicitly;
do not silently pass over them.

When authoring or extending a draft, cite the source for any
protocol mechanism, algorithm, or term of art that
originates outside the document.

Match the surrounding prose. Drafts have a house style
established by earlier revisions and the WG: reference tag
conventions, terminology choices, voice. When editing an
existing draft, conform to its conventions rather than
introducing your own.

## BCP 14 boilerplate (the single most-flagged defect)

Every document that uses MUST/SHOULD/MAY keywords must
include this verbatim:

```
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL",
"SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",
"NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document
are to be interpreted as described in BCP 14 [RFC2119]
[RFC8174] when, and only when, they appear in all capitals,
as shown here.
```

For keyword semantics, when-to-use guidance, and the
catalog of common deviations, see
[references/normative-language.md](references/normative-language.md).

## Formality and tone

- Formal, precise technical prose.
- Passive voice or impersonal constructions where
  appropriate ("the sender transmits", not "you send").
- Define terms before using them, or reference the section
  where they are defined.
- Formal vocabulary; expand contractions; neutral technical
  tone.

## Mandatory sections

Every Internet-Draft must contain Abstract, Introduction,
BCP 14 Conventions (if keywords are used), Security
Considerations, IANA Considerations, and References. The
Security and IANA sections are mandatory even when
empty; state "none" explicitly rather than omitting.

For section-by-section expectations, see
[references/document-structure.md](references/document-structure.md).

## Citations

The obligation to cite is functional, not taxonomic. A
reference is normative if an implementer needs it;
informative if the reader can skip it. Internet-Draft
references may appear only as informative. Normative
downrefs require IESG approval per BCP 97.

For classification rules, reference format requirements, and
the citation-verification procedure, see
[references/citations.md](references/citations.md).

## Task-specific material

Load the file whose topic matches the task. Do not
pre-emptively load all of them.

- Authoring or editing source (mmark vs kramdown-rfc,
  xml2rfc v3 validation, idnits pre-submission lint):
  [references/authoring-toolchains.md](references/authoring-toolchains.md).
- Classifying or verifying references (normative vs
  informative, downrefs, Internet-Draft references,
  citation-verification procedure):
  [references/citations.md](references/citations.md).
- Keyword semantics and BCP 14 deviations:
  [references/normative-language.md](references/normative-language.md).
- Mandatory sections, Security/IANA red flags, front-matter
  hygiene: [references/document-structure.md](references/document-structure.md).
- Reviewing a draft end to end (orientation, front-matter,
  citation pass, body, reporting findings):
  [references/review-workflow.md](references/review-workflow.md).
- Assessing a personal draft for WG adoption (RFC 7221 §2.2
  criteria, charter and milestone verification, IPR check):
  [references/wg-adoption.md](references/wg-adoption.md).
- Reviewing a bis document for scope appropriateness (RFC
  2026 §6.3, WG-specific extension-rules documents like
  RFC 8178 for NFSv4, defect correction vs new feature):
  [references/bis-documents.md](references/bis-documents.md).

## Decision shortcuts

- Citation classification unclear? If an implementer cannot
  complete the implementation without reading the cited
  document, it is normative. Otherwise informative.
- BCP 14 keyword in a sentence reads "decorative"? If
  removing the uppercase does not change what an
  implementation must do, remove the keyword or rephrase.
- Draft claims "this corrects a defect in RFCnnnn"? Require
  the defect to be named and tied to specific text, an
  erratum, or a WG finding before accepting the framing
  (see bis-documents.md).
- Draft has an informative Internet-Draft reference the body
  calls "the basis for" or "the source of"? That is a
  misclassification — treat as normative and flag the
  downstream consequences.
