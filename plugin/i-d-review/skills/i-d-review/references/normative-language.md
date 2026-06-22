# Normative Language (BCP 14)

The BCP 14 boilerplate itself (verbatim text) is in
SKILL.md. This file covers keyword semantics, when to use
them, and the specific defects to watch for in review.

## SHOULD/MUST layering antipattern

A common drafting pattern uses SHOULD for a general principle and
MUST for a more specific minimum floor covering the same obligation:

> "Implementations SHOULD validate the header before processing.
> At a minimum, implementations MUST check the version field."

This construction is ambiguous: an implementer satisfying the MUST
cannot tell whether that also satisfies the SHOULD. When reviewing,
flag this pattern and ask the authors to choose one of:

- Restructure so the MUST covers the general obligation and SHOULD
  (or MAY) covers optional additional behaviour beyond the minimum.
- If the two-tier intent is deliberate, add an explicit sentence
  such as "Meeting the MUST requirement satisfies the SHOULD; the
  SHOULD is not a separate independent obligation."

The antipattern is most common in protocol extension documents that
layer new requirements on top of existing optional behavior.

## Common non-conformance patterns

- Omitting "NOT RECOMMENDED" from the keyword list.
- Replacing "to be interpreted as described in BCP 14" with
  "to be interpreted as BCP 14". The shorter phrasing is not
  the BCP 14 wording.
- Dropping the "when, and only when, they appear in all
  capitals" clause. Without this clause, lowercase "must"
  and "may" in the body become ambiguous.
- Citing RFC 2119 without also citing RFC 8174. Both are
  required when the draft relies on the capitalization
  clarification.
- Boilerplate present but no uppercase keyword appears in
  the body. The boilerplate should be removed, or the
  missing normative text added.
- Uppercase keyword appears in the body but the boilerplate
  is absent. Add the boilerplate or demote the keyword.
- Keywords in IANA Considerations sections. MUSTs on IANA
  are implicit from the registry procedures; adding them is
  redundant. SHOULDs in IANA Considerations create unwanted
  flexibility in what is meant to be a mandatory action.
  Remove keywords from IANA Considerations text entirely.
- Defensive SHOULD: using SHOULD where MUST is actually
  correct, to soften a requirement and avoid commitment.
  If every conforming implementation is expected to do
  something, write MUST. SHOULD implies a documented reason
  to deviate exists; if no such reason can be named, the
  keyword is wrong. Flag any SHOULD whose rationale for
  allowing deviation is absent from the surrounding text.

SHOULD is appropriate for backward compatibility constraints:
when a newer implementation must interoperate with older
ones that do not support a given behavior, SHOULD (rather
than MUST) signals that deviating implementations exist and
interoperability with them is expected. This use is valid
only when the rationale — "older implementations that do X
exist and must be accommodated" — is explicitly stated in
the surrounding text. A SHOULD without that explanation is
indistinguishable from a defensive SHOULD and should be
questioned.

## Keyword definitions (RFC 2119)

- MUST / REQUIRED / SHALL -- absolute requirement.
- MUST NOT / SHALL NOT -- absolute prohibition.
- SHOULD / RECOMMENDED -- valid reasons may exist to deviate
  in particular circumstances, but the full implications
  must be understood and carefully weighed.
- SHOULD NOT / NOT RECOMMENDED -- valid reasons may exist
  when the behavior is acceptable or useful, but the full
  implications must be understood and the case carefully
  weighed.
- MAY / OPTIONAL -- truly optional. An implementation that
  omits an optional feature must interoperate with one that
  includes it (except for the functionality the option
  itself provides).

## Keywords in non-normative sections

BCP 14 keywords that appear in sections labeled as examples,
discussions, appendices, or figures are suspect. Normative
requirements belong in normative sections; restating them in
uppercase inside an example or discussion section creates
ambiguity about scope and makes the document harder to
implement correctly.

When reviewing, check whether the uppercase keyword in a
non-normative section:

- Restates a requirement already stated elsewhere —
  cross-reference the normative section and remove the
  uppercase form.
- States a new requirement not found in any normative
  section — move the requirement to the appropriate
  normative section and replace the example text with a
  cross-reference or a prose description.

This applies even when the example section is illustrating
correct client or server behavior: the normative statement
of that behavior must live in a normative section.

## When to use keywords

Use these keywords sparingly. Per RFC 2119 Section 6, they
are appropriate only where actually required for
interoperation or to limit behavior with potential for
causing harm. Do not use them to impose a particular
implementation method when interoperability does not depend
on it.

A statement can be normative without containing any
uppercase keywords (RFC 8174); the keywords add clarity and
consistency, not authority. But when a statement does
express a normative requirement, use the uppercase keyword
rather than the lowercase English word. Lowercase "must" is
ambiguous about whether the BCP 14 meaning is intended.

<example type="CORRECT">
A sender MUST include a Content-Length header when the
message body is present.
</example>

<example type="INCORRECT">
A sender must include a Content-Length header when the
message body is present.
<!-- Lowercase "must" is ambiguous. Use either the
     uppercase keyword or rephrase to avoid the word. -->
</example>

<example type="CORRECT">
Implementations typically buffer incoming data before
processing.
</example>

<example type="INCORRECT">
Implementations SHOULD buffer incoming data before
processing.
<!-- Uppercase keyword used for a descriptive observation,
     not an interoperability requirement. -->
</example>
