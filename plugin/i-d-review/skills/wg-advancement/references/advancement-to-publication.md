# From Submission to RFC

What happens after the chair submits a WG document for
publication, and what the chair (as shepherd) still has to do.
The document-readiness properties a participant can check
(references to unpublished I-Ds, downref classification,
mandatory sections, BCP 14 boilerplate) live in the
`internet-draft` skill's `references/review-workflow.md`; this
file covers the chair's submission gates and the process
downstream.

## Initiation and submission

A standards action is initiated by the WG's recommendation to
its responsible Area Director (RFC 2026 §6.1.1). The chair
submits the publication request with the shepherd write-up
(references/shepherd-writeup.md). The AD then evaluates the
document and may return it to the WG for changes before
proceeding.

## IETF Last Call

The IESG issues an IETF Last Call by email to the IETF-Announce
list (RFC 2026 §6.1.2). The minimum period is:

- **two weeks** when the action was initiated by an IETF
  working group;
- **four weeks** when it was not (individual or non-WG
  submissions).

This is a different event from WG Last Call and reaches the
whole community. IETF-stream publication requires IETF rough
consensus, which IETF Last Call is the mechanism to confirm
(RFC 8789).

### Downrefs

A normative reference from a Standards-Track or BCP document to
a lower-maturity document (Informational, Experimental, or a
document at a lower standards level) is a downref. Under BCP
97, the need for the downref should be called out in the IETF
Last Call notice (RFC 3967 §3). RFC 8067 relaxed this: the
call-out is strongly recommended but not required, and whether
to repeat the Last Call for a downref found late is at the
IESG's discretion. RFC 4897 adds a "note and move on" path for
downrefs whose targets are themselves Standards-Track or BCP.
Enumerate the downrefs in the shepherd write-up so the AD can
handle them at Last Call.

## IESG evaluation

The IESG ballots on a telechat. Positions include Yes, No
Objection, DISCUSS, and Abstain. A DISCUSS is blocking and must
be resolved before approval; the DISCUSS criteria are an IESG
statement, not an RFC. The shepherd follows up on each position
with the AD who raised it (RFC 4858 §3.3).

### The Proposed Standard bar

Most WG standards-track documents target Proposed Standard. The
standards track has two maturity levels — Proposed Standard
and Internet Standard (RFC 6410); the former Draft Standard
level is gone, so do not expect it. The current
characterization of Proposed Standard (RFC 7127 §3.1, which
updates RFC 2026 §4.1.1) is that the document is stable, has
resolved known design choices, has received significant
community review, appears to enjoy enough community interest to
be considered valuable, and has no known technical omissions.
Implementation is not required, though it is desirable. (RFC
2026 §4.1.1 is the superseded original wording; quote RFC 7127
for the current bar.)

## Approval and publication

On approval, the IESG sends notification to the RFC Editor with
instructions to publish (RFC 2026 §6.1.3). The document enters
the RFC Editor queue, is edited, and reaches AUTH48 — the
final author approval step before publication. AUTH48 is an RFC
Editor process step, documented on rfc-editor.org and not
defined in a process RFC; the RFC Editor Model itself is RFC
9280. The shepherd coordinates author responses through AUTH48.

## Appeals

A participant who believes an objection was wrongly overridden
can appeal. The chain runs WG chair, then responsible Area
Director, then the IESG as a whole, then the IAB, whose
decision is final (RFC 2026 §6.5.1). A written consensus
determination that named the objection and explained the
disposition (references/consensus-determination.md) is the
chair's defense at every step.
