# Issuing a WG Last Call

WG Last Call (WGLC) is the chair's readiness signal that a WG
document is believed done and ready to request publication. It
is customary practice, not mandated by RFC 2418; it serves the
same purpose within a WG that IETF Last Call serves in the
broader community (RFC 2418 §7.4). Do not confuse it with IETF
Last Call, which comes later and is issued by the IESG
(references/advancement-to-publication.md).

## Issuing the call

Post a call to the list that states:

- the draft name and the exact version under Last Call;
- the review period (2 weeks is customary; longer for a large
  or complex document);
- where to send comments (the WG list);
- what is being asked: review for readiness to advance, and an
  explicit call for statements of support, not only objections.

Run the IPR poll again at WGLC: confirm every author and
contributor has disclosed known IPR or stated none (RFC 6702
§3.3; see the `wg-management` skill's `references/ipr.md`).

## While the call is open

Track the version under review. If the authors post a
substantive revision mid-call, the WG has not Last-Called that
text — confirm the review still applies or run a short
confirming Last Call (references/consensus-determination.md).

## Closing the call

Judge and declare the result per
references/consensus-determination.md. A clean WGLC produces:
a chair determination on the list, a document version the WG
actually reviewed, and a record of how any sustained objection
was resolved. These become inputs to the shepherd write-up
(references/shepherd-writeup.md).

Before requesting publication, the document must also clear
the participant-level readiness checks (no normative
references to unpublished I-Ds, downrefs identified, mandatory
sections present, BCP 14 boilerplate correct). That checklist
lives in the `internet-draft` skill's
`references/review-workflow.md`; the chair's added gates
(consensus declared, write-up complete, downrefs listed for
the Last Call notice) are in
references/advancement-to-publication.md.
