# Working Group Adoption of Personal Drafts

"Adoption" is the act by which a WG takes ownership of a
personal draft. Before adoption the draft is an individual
submission under the authors' control, filed as
`draft-<lastname>-<wgname>-...`. After adoption the draft is
owned by the WG, filed as `draft-ietf-<wgname>-...`, and
change control transfers to the IETF.

## Relevant documents

- **BCP 25 / RFC 2418** "IETF Working Group Guidelines and
  Procedures". The normative BCP. §7 covers WG documents
  generally; §7.4 covers WG Last Call (post-adoption);
  §7.5 covers submission to the IESG.
- **RFC 7221** "Handling of Internet-Drafts by IETF Working
  Groups". Informational, 2014. Not normative, but widely
  treated as the practical reference. §2 covers the
  adoption sequence, §2.2 lists the adoption criteria, §4
  covers document stability and the change constraints an
  adopted draft inherits from the charter.
- **RFC 8179** (BCP 79) for IPR disclosure obligations.

## Adoption criteria (RFC 7221 §2.2)

Apply these criteria when assessing a personal draft for
adoption. None is a strict pass/fail; they structure the
judgement call.

1. Is there a charter milestone that explicitly calls for
   such a document?
2. Is the topic of the I-D within scope for the WG?
3. Is the purpose of the draft sufficiently clear?
4. Does the document provide an acceptable platform for
   continued effort by the WG?
5. What are the process or technical objections to adoption
   of the draft?
6. Is the draft likely to be completed in a timely manner?
7. Does the intended status of the document seem reasonable
   to the WG?
8. If not already in scope, is a simple modification to the
   charter feasible and warranted?
9. Does the draft carry known intellectual property rights
   issues?
10. Is there strong WG support for working on the draft?

## Adoption pragmatics (RFC 7221 §2.2)

- **Rough consensus.** WG agreement to adopt is not required
  to be unanimous (citing RFC 2418).
- **Initial, not final.** Writing quality is not required to
  be publication-ready, though writing quality can be a
  problem and does need explicit attention. Running idnits
  on a new WG draft is good practice.
- **Adoption, not approval.** The document is not required
  to already contain a complete or sufficient solution.
  Adoption does not guarantee publication.
- **Group, not Chairs.** The Chairs' position on the
  content has no special authority beyond assessing WG
  consensus.

Absent explicit agreement, adopting a document does not
automatically mean the WG has agreed to all of its content.
The adoption process is well served by gathering and
flagging WG concerns about the existing draft.

## Adoption workflow (RFC 7221 §2.1)

When there is interest in adoption, Chairs typically:

1. Remind current draft owners that they are transferring
   change control for the document to the IETF. For
   documents with proprietary interests, this may require a
   formal agreement.
2. Check for known IPR that needs to be disclosed.
3. Obtain WG rough consensus.
4. Choose document editors (Chairs select, though views of
   the WG should be considered).
5. Instruct authors to post the WG I-D.
6. Approve posting.
7. Ensure the non-WG version of the draft is marked as
   replaced by the WG version.

## Editor selection (RFC 7221 §3)

For an existing draft being adopted, the question "are the
same people appropriate for continuing the task?" is
explicit. Sometimes yes; sometimes the WG selects new or
additional editors. The process within a WG can be quite
different from the process that created the personal draft,
and continuing editors should understand that.

## Document stability and change constraints (RFC 7221 §4)

Adoption fixes the starting point, not the latitude the WG
has to change it. The charter sets the role of the basis
document, which can range from a set of ideas offered as
input to WG discussion up to an advanced draft subject only
to minimal changes. RFC 7221 asks that the charter state
this role explicitly; where it does, the adoption
assessment inherits the change constraint from it.

The charter can cast existing material in one of several
roles, each granting a different latitude for revision:

- a set of ideas, to be used or ignored;
- a basic design, with the details still fluid;
- a rough draft, subject to extensive revision;
- a solid specification needing review, refinement, and
  maybe enhancement;
- a deployed technology whose installed base is worth
  protecting, with some tolerance for changes that affect
  interoperability;
- a deployed technology for which protecting the installed
  base is essential, including retention of core
  interoperability.

The constraint tracks the technology's place in its life
cycle. Brand-new technology, prototyped at most, absorbs
significant specification changes without adding much to
development or deployment cost. A mature, widely deployed
technology is the opposite: incompatible changes burden the
installed base and can hinder adoption of the changes
themselves. A solidly deployed technology can still be
unfit at Internet scale, in which case its specification
serves only as a starting point and undermining the
deployed base may be appropriate.

For an adoption-call assessment this sharpens criterion 4
(does the draft provide an acceptable platform for
continued effort?). Weigh the document's life-cycle
position, the needs of any installed base, and the
applicability of its technology, then surface the resulting
change constraints as an explicit finding rather than
leaving them implicit.

Not every WG draft is adopted from an individual
submission. A WG may create a document from scratch within
its charter; the same criteria apply, with the added step
that the Chairs appoint authors or editors before work can
progress. A design team (RFC 2418 §6.5) sometimes produces
the first version.

## Verification steps for an adoption-call assessment

Pulling the WG charter and milestones is a routine step.
The datatracker URL for a given WG is:

  https://datatracker.ietf.org/wg/<wgname>/about/

Check:

- The charter scope text (does it name the relevant protocol
  family or document type?).
- The current milestone list (does any milestone name this
  draft or its topic?).
- Whether the milestone target dates are realistic and
  whether any are overdue.
- Whether related milestones exist that this draft depends
  on (for example, a companion protocol document that must
  progress in parallel).

An IPR search on datatracker for the draft filename and the
authors' names is also routine before an adoption call.

## Common adoption-call findings worth surfacing

- Normative references to Internet-Drafts (publication
  blocker until those drafts progress).
- Informative references that are de-facto normative
  (classification should be corrected).
- Missing or thin Security and IANA Considerations given the
  substantive content of the draft.
- Editorial debt in front matter (malformed BCP 14
  boilerplate, typos, stray punctuation in section titles)
  that is not a blocker but is easy to clean up.
- Dependencies on overdue or stalled related documents that
  affect completion-timeline realism (criterion 6).
