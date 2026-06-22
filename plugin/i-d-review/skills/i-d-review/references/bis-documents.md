# Bis Documents: What Can and Cannot Appear

"Bis" is IETF community shorthand for a successor document
that obsoletes its predecessor. The term is convention, not
a formally defined document class. Common intuition holds
that a bis should contain only editorial changes plus
deprecation of unimplemented or unimplementable protocol
elements; that intuition is a community *habit*, not a
codified IETF rule.

## What the published rules actually say

**BCP 9 / RFC 2026 §6.3 "Revising a Standard"** is the
authoritative text. It is short and permissive:

> A new version of an established Internet Standard must
> progress through the full Internet standardization process
> as if it were a completely new specification.

No scope restriction is imposed. The rule is procedural:
the new version re-enters the Standards Track and goes
through Last Call, IESG evaluation, and publication like
any other new document. That procedure implicitly permits
new material, since a revision treated as "a completely new
specification" is not constrained to a subset of its
predecessor's content.

**draft-ietf-procon-2026bis** is the active PROCON WG
successor to RFC 2026. Its revision text carries the same
permissive language forward (as §8.3 in recent revisions).

**draft-roach-bis-documents** proposed formal scope limits
on bis documents — specifically that changes "must not
constitute the majority of the document" and that bis
documents should avoid "spurious changes (such as
reformatting)." It is an expired, unadopted personal draft.
Its failure to progress is itself informative: the
community considered codifying scope limits and chose not
to. Do not cite it as authority.

## WG-specific extension-rules documents

Some WGs publish their own extension-rules RFC that defines,
for that protocol, what a revision may contain and how
corrections are to be carried. These are on-point where
they exist and take precedence over general convention.

Check for a WG-specific extension-rules document before
ruling on scope. Examples:

- **NFSv4: RFC 8178** "Rules for NFSv4 Extensions and Minor
  Versions". §9 "Correction of Existing Minor Versions and
  Features" expressly authorizes XDR extensions to correct
  protocol defects, carried in a document obsoleting the
  RFC that defined the minor version. §§9.2-9.4 require
  explicit interoperability analysis for such corrections.
  §9.1 imposes the hard constraint that "existing XDR
  structures may not be modified or deleted."
- **HTTP/TLS/QUIC** have their own versioning and extension
  conventions carried across multiple RFCs; check the WG's
  reference shelf.

When a WG-specific rule applies:

- The bis document is permitted to include material the
  general convention would exclude, if the WG rule
  authorizes it.
- The WG rule usually imposes its own constraints (e.g.,
  XDR stability for NFSv4, wire-format stability for HTTP
  header fields). These constraints are real even when the
  general IETF rules are silent.

## Reviewing a bis document for scope appropriateness

The practical review question is not "does this draft
contain new content?" — almost all bis documents do — but
"is the new content of a kind the applicable rules permit?"

Steps:

1. Identify the applicable rules: the general RFC 2026 §6.3
   procedural rule, plus any WG-specific extension-rules
   document.
2. For each substantive addition in the bis, identify
   which rule permits it:
   - Editorial clarification: always permitted.
   - Errata corrections: permitted; cite the erratum ID.
   - Defect correction via new feature (under an extension
     rule like RFC 8178 §9): permitted only if the specific
     defect is named and cited, and the interoperability
     analysis required by the extension rule is present.
   - New feature unrelated to defect correction: generally
     belongs in a separate extension draft, not a bis.
3. Flag any addition that cannot be cleanly placed in one
   of the above categories.

## The "is it really a defect correction?" question

When a bis document invokes a WG-specific correction
pathway (RFC 8178 §9 for NFSv4, or an analogous mechanism
elsewhere), the load-bearing claim is that each added
feature corrects an identifiable defect in the predecessor.
Verify that claim item by item:

- Is the defect named in the bis document or in a cited
  companion document?
- Can the defect be tied to specific text in the
  predecessor RFC, an erratum, or a documented WG finding?
- Is the correction structured per the extension rule's
  requirements (for NFSv4, OPTIONAL versus REQUIRED
  feature handling per §§9.2-9.3; interoperability
  analysis per §9.4)?

A bis document that asserts "these changes correct defects"
without naming defects is asserting the conclusion. Ask for
the underlying defect list before accepting the framing.
