# The Document Shepherd Write-Up

After WG Last Call, a document shepherd — usually a WG chair,
sometimes another appointed participant — takes the document
through to publication and writes the shepherd write-up that
accompanies the publication request to the AD. RFC 4858
defines the role and gives the write-up's structure. The
questionnaire text itself is maintained externally (the IESG
section of the IETF web site) and changes over time, so pull
the current template from the datatracker — the write-up form
on the document's page at datatracker.ietf.org/doc/<draft>/ —
rather than relying on a remembered version (RFC 4858 §3.1).

## What the write-up contains

Two parts (RFC 4858 §3.1):

1. **Process questions** giving the responsible AD insight
   into how the WG handled the document. They cover:
   - the shepherd's own review and its depth;
   - the breadth and adequacy of WG review, and whether
     broader review (security, operations, internationaliza-
     tion, etc.) is still needed;
   - specific concerns the shepherd has, and the state of IPR
     disclosures;
   - how solid the WG consensus is — this is where the
     rough-consensus determination goes
     (references/consensus-determination.md);
   - any threat of appeal or extended discontent;
   - ID-nits and formal-review criteria;
   - the normative/informative reference split and any
     downrefs, per RFC 3967
     (references/advancement-to-publication.md);
   - the IANA Considerations;
   - validation of any formal language (ABNF, MIB, YANG, XML).

2. **The Document Announcement Write-Up** (RFC 4858 §3.1 item
   1.k), with four sections: Technical Summary, Working Group
   Summary, Document Quality, and Personnel.

## What the questions are really asking

- The consensus question wants the *determination*, not "the
  WG agreed." State how broad the review was, who supported
  advancement, and how each sustained objection was resolved.
- The IPR question wants confirmation that each author and
  contributor was polled and responded, not a general "no IPR
  known" (see the `wg-management` skill's
  `references/ipr.md`).
- The downref question wants each normative reference to a
  lower-maturity document named, so the AD can call it out in
  the IETF Last Call notice
  (references/advancement-to-publication.md).

## Shepherding after submission

- **AD Evaluation** (RFC 4858 §3.2): read and relay the AD's
  comments to the editors and the WG list, iterate until the
  issues are resolved, and mediate any editor/WG disagreement
  with the AD.
- **IESG Evaluation** (RFC 4858 §3.3): follow up on each
  ballot position with the AD who raised it. A DISCUSS is
  blocking and must be resolved; a COMMENT is non-blocking.
  Keep the responsible AD copied.
