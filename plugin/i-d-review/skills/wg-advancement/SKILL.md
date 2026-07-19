---
name: wg-advancement
description: Load when acting as an IETF working group chair to advance a WG document — issuing or judging an adoption call or WG Last Call, writing a rough-consensus determination, deciding whether an objection blocks advancement, producing a document shepherd write-up, requesting publication, submitting to the AD, or tracking a draft through IETF Last Call and IESG evaluation to RFC. Covers RFC 2418, RFC 7221, RFC 7282, RFC 8789, RFC 4858, RFC 2026, RFC 7127, and BCP 97. This is the chair's adjudication and process role; to review a draft's technical content as a participant, use the internet-draft skill.
invocation_policy: automatic
---

# Advancing a WG Document (chair)

This skill covers the chair's role in moving a working group
document from adoption through publication as an RFC: running
adoption calls and WG Last Calls, judging and declaring rough
consensus, writing the shepherd write-up, and submitting the
document for IETF Last Call and IESG evaluation. Reference
material lives in `references/`; load the file whose topic
matches the task.

Reviewing a draft's technical content, citations, and
structure is participant work — use the `internet-draft`
skill for that. Keep the two hats separate: this skill is
about the chair's determination and the process, not your own
technical opinion of the draft.

## Operating principles

The chair adjudicates consensus; the chair does not decide the
outcome. Your own technical position on the content carries no
special authority — the chair's view of the content has no
more standing than any other participant's (RFC 7221 §2.2).
Assess what the group concluded, not what you would conclude.

Rough consensus is neither a vote nor the mere absence of
objection. It is up to the chair to determine whether rough
consensus has been reached (RFC 2418 §3.3), and a raised
technical objection is not disposed of by silence,
non-response, or a head count (RFC 7282 §6). Never read a
passed deadline as consensus over an unanswered objection.

Do not guess about process mechanics — Last Call durations,
who issues what, appeal chains, maturity-level bars. Verify
against the cached RFCs in `~/Documents/rfcs/` (download
procedure in CLAUDE.md) or the datatracker. A confident wrong
statement about process costs the chair credibility. To
resolve a BCP/STD label to its current RFC or fetch a
specific document, see the internet-draft skill's
references/finding-rfcs-and-drafts.md.

Adjudicate on the actual record. If the mailing-list thread or
document state under judgment is not already in your context,
retrieve it first — the list archive at mailarchive.ietf.org and
the document's history and ballot state at
datatracker.ietf.org/doc/<draft>/ — then judge on what you find.
For how to search the list archive and cite messages from it,
see the internet-draft skill's
references/mailarchive-search.md. If the record is already
supplied, use it; do not re-fetch.

A session's minutes are part of that record, but they do not
close a question on their own. A decision reached in a room on
something the list has not discussed, or departing
significantly from a consensus the list already reached, MUST
be reviewed on the list (RFC 2418 §3.2); where a face-to-face consensus is being
verified on the list, the agreement expressed in the room is
taken into account (§3.3). So cite minutes to establish what
was raised and answered, and the list to establish what the WG
agreed. To retrieve them, load the wg-management skill and read
its references/finding-meeting-materials.md.

## The advancement pipeline

Each gate, who acts, and where the detail lives:

1. Adoption call — chair runs, WG decides.
   (references/adoption-call.md)
2. WG development, then WG Last Call — chair issues.
   (references/wg-last-call.md)
3. Rough-consensus determination — chair writes.
   (references/consensus-determination.md)
4. Shepherd write-up and publication request — the shepherd
   (usually a chair) writes it and submits to the responsible
   Area Director. (references/shepherd-writeup.md)
5. AD evaluation, IETF Last Call (issued by the IESG), IESG
   ballot, approval, RFC Editor, publication.
   (references/advancement-to-publication.md)

The chair's job does not end at submission: the shepherd
fields Last Call comments, tracks IESG DISCUSS positions, and
coordinates author responses through AUTH48.

## Task-specific material

Load the file whose topic matches the task. Do not
pre-emptively load all of them.

- Running an adoption call (issuing the call, the IPR poll,
  declaring the result, change-control transfer):
  references/adoption-call.md.
- Issuing a WG Last Call (contents, duration, tracking the
  version under review): references/wg-last-call.md.
- Writing a rough-consensus determination (sustained vs
  resolved objections, overriding an objection, affirmative
  support): references/consensus-determination.md.
- Producing a document shepherd write-up (RFC 4858 structure,
  what each item asks): references/shepherd-writeup.md.
- What happens after submission (IETF Last Call, downrefs,
  IESG evaluation, maturity level, publication):
  references/advancement-to-publication.md.

## Decision shortcuts

Recognize the trap; the canonical rule, wording, and citations
are in references/consensus-determination.md.

- Objection still open at Last Call close — it blocks.
  "Addressed" means engaged on the merits, not "the objector
  went quiet."
- Substantive revision posted mid-Last-Call — the WG never
  Last-Called that text; confirm the review still applies or
  run a short confirming call.
- Objections plus silence, no affirmative support — not
  consensus, even past the deadline.
- Advancing over a sustained objection — allowed only with a
  written determination naming the objection and why it does
  not block; it is the chair's defense on appeal (RFC 2026
  §6.5).
