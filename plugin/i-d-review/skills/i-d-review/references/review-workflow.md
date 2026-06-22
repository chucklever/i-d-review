# Reviewing an Internet-Draft

Reviewing and authoring share the same reference shelf but
differ in sequence and emphasis. This file covers the
review workflow.

## Orientation pass

Before diving into body text, establish:

- The draft's title block: title, author list, date,
  Intended status, Obsoletes/Updates relationships.
- The document's relation to other drafts and RFCs named
  in the title block or Abstract.
- The table of contents. Scan section titles for the
  mandatory sections (Introduction, Conventions, Security
  Considerations, IANA Considerations, References).
- The authoring toolchain (mmark vs kramdown-rfc) if source
  is available. Useful when suggesting edits.

## Front-matter hygiene check

Apply the checklist in document-structure.md's "Front-matter
hygiene" section (BCP 14 boilerplate verbatim, section
titles free of stray punctuation, Obsoletes/Updates headers
consistent with body text, TOC section numbers match body).
For BCP 14 deviations specifically, see normative-language.md.

## Citation pass

For each reference entry:

- Fetch the referenced document into `~/Documents/rfcs/` if
  not already cached (see CLAUDE.md for the download
  procedure).
- Verify title, authors, and date against the cached text.
- Verify any in-text section citations (e.g., "see §9 of
  [X]") by reading the referenced section in the cached
  RFC. Section numbers change between revisions; do not
  trust the draft's section reference without checking.
- Check "Obsoleted by" / "Updated by" lines on the cached
  RFC. Cite the current document unless there is a
  documented reason to cite the predecessor.
- Internet-Draft references: verify the version string is
  current, and that the draft has not been superseded by an
  RFC.

For classification:

- Every reference classified informative should be one an
  implementer can actually skip. A reference that the body
  text describes as the source of mechanism, motivation for
  extensions, or derivation of content is normative in
  function. Flag misclassifications.
- Every normative reference to a Standards Track RFC is
  safe. Every normative reference to an Informational,
  Experimental, or Historic RFC is a downref requiring
  IESG approval (BCP 97). Every normative reference to an
  Internet-Draft is a publication blocker.

**Companion-document cross-reference pattern.** When a
draft has a companion document developed in parallel, check
each cross-reference to the companion against the specific
sentence that contains it. A sentence that compares or
contrasts the two documents ("this attribute governs X,
while the companion governs Y") is informative regardless
of where the reference is classified. Classify the
reference by what the body text actually requires, not by
the companion relationship. Also verify that section
headings and opening sentences have not been copied from the
companion with subject-matter details left unreplaced — a
section titled for one attribute whose first sentence
describes a different attribute is a common copy-paste
defect in companion-document pairs.

## Body-section review

- Does each section do what its heading says it does?
- For any use of BCP 14 keywords in the body, is the
  requirement genuinely an interoperability requirement, or
  is the uppercase form decorative?
- Are new terms introduced with definitions or references?
- Are internal section cross-references (§X.Y) valid after
  the current edits?

## Security and IANA Considerations

- For a draft that introduces new protocol surface (new
  operations, attributes, callbacks, codepoints), a
  Security Considerations section that delegates
  wholesale to another document is suspect. Identify what
  new surface the draft adds and check whether that surface
  has corresponding security text somewhere reachable.
- Same for IANA Considerations when new codepoints,
  registries, or bitmaps are defined.

## Post-WGLC readiness checklist

Before a WG chair submits a document to the AD for IESG processing,
the following must all be true. Use this checklist when a review is
explicitly framed as a WGLC advancement assessment.

**Publication blockers (any one fails the checklist):**

- No normative references to Internet-Drafts. Every normative
  reference must be a published RFC or a document at a maturity
  level that the IESG will accept at publication time.
- No unresolved downrefs without prior IESG approval (BCP 97 /
  RFC 3967). A normative reference from a Standards Track document
  to an Informational or Experimental RFC requires explicit IESG
  approval or an entry in the downref registry.
- All mandatory sections present (Abstract, Security Considerations,
  IANA Considerations, References). "None" must be stated explicitly
  rather than the section being absent.
- BCP 14 boilerplate verbatim and consistent with keyword usage in
  the body (boilerplate present iff uppercase keywords appear).

**Issues that attract IESG feedback (fix before submission):**

- IANA Considerations claim "no actions" when a new codepoint,
  attribute number, or registry entry is defined — verify against
  the actual IANA registry for the relevant protocol family. Some
  protocol families (e.g., NFSv4 attribute numbers) manage
  namespaces through WG coordination rather than an IANA registry;
  in that case "no IANA actions" may be accurate, but the section
  should briefly explain how the number was assigned and how
  collisions are avoided. Silence on both points will draw an IESG
  question regardless of whether a registry exists.
- Security Considerations delegates wholesale to another document
  for new protocol surface introduced by this draft.
- Normative keyword usage that is decorative rather than an
  interoperability requirement.
- SHOULD/MUST layering ambiguity (see normative-language.md).
- Citations in the Abstract (RFC 7322 §4.3).
- Informative I-D references to personal (non-WG) drafts that
  serve as attribution for content the draft adapts — flag for
  the shepherd to confirm currency before AD submission.

**Shepherd write-up items to flag explicitly:**

- Any identifier (codepoint, attribute number, etc.) whose
  namespace is managed by WG coordination rather than an IANA
  registry — note the coordination evidence.
- Any informative I-D reference whose RFC publication is needed
  before or concurrent with this document.

## Mailing list consensus review

When a review is framed as a WGLC advancement assessment,
read the mailing list record in addition to the document
text. The archive for most WGs is at
mailarchive.ietf.org/arch/browse/<wgname>/. Search for
the draft name and any WGLC or last-call subject lines.

**Rough consensus standard (RFC 2026 §6.1).** Consensus is
not unanimity and does not require a vote, but it requires
more than the absence of response. A chair declaring rough
consensus must be able to show that the group considered
and genuinely weighed objections — not merely that no
further messages arrived.

**Identifying sustained objections.** A substantive
objection is one that challenges the document's motivation,
correctness, or scope rather than proposing editorial
improvements. Mark it as sustained if:
- The same concern was raised in at least two separate
  messages from the same reviewer, or repeated by more
  than one reviewer; and
- The most recent version of the document has not resolved
  it to the reviewer's stated satisfaction.

An objection is resolved only when the reviewer explicitly
withdraws it or accepts the author's response. Silence
after a follow-up is not withdrawal.

**Distinguishing process from substance.** Procedural
objections (wrong draft version under review, insufficient
review period, late submission) are separable from
technical ones. Resolve procedural issues first; they do
not substitute for addressing substantive objections, and
addressing substantive objections does not render
procedural defects moot.

**WGLC version tracking.** If a new revision is posted
during an open WGLC window, establish which version
actually governs the review. Reviews against a superseded
version are not void, but they must be checked against the
new version before the chair can call consensus. Flag any
WGLC where the version under review changed mid-window.

**What a chair must do to override an objection.** A chair
may call rough consensus despite a sustained objection, but
only by issuing an explicit consensus determination on the
list that: (a) names the objection, (b) describes how the
WG considered it, and (c) explains why the objection was
not adopted. A "final call" notice that does not address
open objections is not a consensus determination.

**Affirmative support matters.** Note whether any WG
participant other than the author expressed support for
advancement. Rough consensus in favor of a document
normally requires some affirmative voice; a record
consisting entirely of objections and silence, with no
expression of support, does not establish consensus even
if the deadline passes.

## Context-specific workflows

Depending on the review purpose, layer in additional
material:

- **Adoption-call assessment**: apply the RFC 7221 §2.2
  criteria (see wg-adoption.md), pull WG charter and
  milestones from datatracker, run the IPR check.
- **Bis-document review**: apply the scope-appropriateness
  framework (see bis-documents.md) and identify any
  WG-specific extension-rules RFC.
- **Pre-submission author review**: run idnits and fix
  whatever it flags before posting.

## Tools

- **idnits**: https://author-tools.ietf.org/idnits — surface
  conformance lint. Standard pre-submission bar.
- **bib.ietf.org**: pre-built XML reference entries.
- **datatracker.ietf.org**: WG charters, milestones, IPR
  disclosures, draft version history.
- **rfc-editor.org/errata**: errata for published RFCs.
  Worth consulting when a draft claims to correct an
  erratum.

## Reporting review findings

When reporting findings, distinguish:

- **Confirmed real** issues with cited evidence.
- **Likely issues** that need author confirmation.
- **Questions** where the draft's intent is unclear.

Do not silently paper over a cited section number that
turns out to be wrong, a reference classification that
looks inverted, or boilerplate that deviates from BCP 14.
Flag each discrepancy explicitly. See CLAUDE.md's "Code
Review Guidelines" for the labeling convention.
