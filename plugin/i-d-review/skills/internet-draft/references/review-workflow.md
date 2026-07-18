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

- Obtain the referenced document as plaintext: use a local
  cache if you keep one, otherwise fetch it from
  rfc-editor.org or the IETF draft archive.
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
explicitly framed as a WGLC advancement assessment. These are
document-readiness properties a participant can verify; the chair's
own submission gates — consensus declared, shepherd write-up
complete, downrefs enumerated for the Last Call notice — are in the
wg-advancement skill's references/advancement-to-publication.md.

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
  attribute number, or registry entry is defined. Run the "no IANA
  actions" verification in document-structure.md against the
  relevant protocol family; an unexplained claim draws an IESG
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
text. Find the thread by keyword-searching the WG's list
archive; the browse-vs-search endpoints, query parameters,
and message permalinks are in mailarchive-search.md. Search
for the draft name — both the adopted `draft-ietf-` name and
any earlier personal name — and any WG Last Call subject
lines.

This section is the participant's read of that record;
declaring the outcome is chair work, covered by the
wg-advancement skill's references/consensus-determination.md.

**Rough consensus standard (RFC 2418 §3.3, RFC 7282 §6).**
Consensus is not unanimity and does not require a vote, but
it requires more than the absence of response. A raised
objection is not disposed of by silence or a head count; the
determinative question is whether the open issue was
addressed (RFC 7282 §6). For IETF-stream documents, IETF
rough consensus — confirmed later at IETF Last Call, not
just within the WG — is required for publication (RFC 8789).

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

**Overriding an objection is chair work.** A chair may call
rough consensus over a sustained objection, but only with an
explicit written determination that names it and explains the
disposition; the requirements are in the wg-advancement
skill's references/consensus-determination.md. As a reviewer,
flag any "final call" that advances over an unaddressed
objection without such a determination.

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
- **finding a document**: search endpoints, BCP/STD
  resolution, and versioned-draft fetch URLs are in
  finding-rfcs-and-drafts.md.
- **rfc-editor.org/errata**: errata for published RFCs.
  Worth consulting when a draft claims to correct an
  erratum.

## Reporting review findings

Report each finding on two independent axes: how severe it
is, and how confident you are that it is real. A minor issue
you are sure of and a blocking issue you only suspect are
different findings; label them differently.

**Severity** — the tiers IETF reviews already use (Gen-ART
and directorate reviews sort findings into Major / Minor /
Nits; IESG ballots into DISCUSS / COMMENT):

- **Blocking** — must be resolved before the draft advances:
  a normative defect, a missing mandatory section, a citation
  an implementer relies on that is wrong or unverifiable, or
  BCP 14 usage that changes what an implementation must do.
  An IESG DISCUSS.
- **Major** — a substantive problem the author should
  resolve: an ambiguous normative requirement, an unstated
  assumption, a misclassified reference. Not
  advancement-blocking on its own.
- **Minor** — a correctness or clarity problem that does not
  threaten interoperability: an imprecise term, a
  cross-reference to the wrong section, a defensive SHOULD.
- **Nit** — editorial: typo, formatting, non-normative
  wording. Group nits together; do not interleave them with
  substantive findings.

**Confidence**:

- **Confirmed** — verified against a cited source (the RFC
  text, datatracker, the errata list). State the evidence.
- **Likely** — consistent with the evidence but needs the
  author to confirm intent.
- **Question** — the draft's intent is unclear; ask rather
  than assert a defect.

Write each finding as a single scannable line, severity
first so the blocking issues surface at the top of the
report: location (section number, or file:line for source
review), the defect in one sentence, the evidence, and a
concrete recommendation. For example:

    Blocking / Confirmed — §4.2 cites RFC 8446 §4.1.3 for
    the "signature_algorithms" extension, but §4.1.3 is
    "Server Hello"; the extension is defined in §4.2.3.
    Verified against the cached RFC 8446. Correct the
    section number.

Do not silently paper over a cited section number that turns
out to be wrong, a reference classification that looks
inverted, or boilerplate that deviates from BCP 14. Flag each
discrepancy explicitly.
