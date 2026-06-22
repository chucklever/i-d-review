# Document Structure

A typical Internet-Draft contains:

1. Abstract (no citations)
2. Status of This Memo / Copyright Notice (boilerplate)
3. Introduction
4. Conventions and Definitions (BCP 14 boilerplate)
5. Protocol / mechanism specification sections
6. Security Considerations (mandatory)
7. IANA Considerations (mandatory, even if "none")
8. References (Normative / Informative)
9. Appendices (optional)
10. Acknowledgments (optional)

Security Considerations and IANA Considerations sections are
required even when the draft has no security or IANA
implications; state this explicitly rather than omitting the
section.

## Security Considerations

Address at minimum:

- Threats introduced or altered by the mechanism defined in
  this document.
- Trust boundaries and assumptions about the deployment
  environment.
- Interaction with existing security mechanisms (TLS,
  authentication, access control).

If the document genuinely introduces no new security
considerations, state the reason explicitly. A one-line
delegation to another document ("See the Security
Considerations section of [X]") is a red flag when the draft
under review introduces new mechanisms, new optional
features, or new callbacks. Delegation is acceptable only
when the delegating document truly adds no new surface.

## IANA Considerations

Same pattern: mandatory section, explicit "none" rather than
omission, and a one-line delegation to another document is
suspect if the draft defines new codepoints, bitmaps, or
registries.

**Verifying "no IANA actions" claims for new identifiers:**

When a draft assigns a new protocol identifier — a codepoint,
attribute number, operation code, flag bit, or similar — and the
IANA Considerations section claims "no IANA actions," do not
accept that claim without checking:

1. Does an IANA registry exist for this identifier type? Search
   https://www.iana.org/assignments/ for the protocol family
   name. (For NFSv4, the named-attribute registry exists but
   numbered file attributes are assigned through the standards
   publication itself, not through a separate registry action.)
2. If a registry exists, an IANA registration action is required
   and the section must describe it. Flag the omission.
3. If no registry exists, the claim may be correct. Note in your
   review how the identifier namespace is managed — through WG
   coordination, through the RFC publication itself, or through
   some other mechanism — so the shepherd can address it in the
   write-up.

The verification can require checking the IANA Considerations
sections of the base protocol RFCs to understand what registries
were created and what policy governs additions to them.

## Cross-reference hygiene

After adding or removing sections, verify all internal
section references remain correct. Use section numbers, not
page numbers (RFC 7322 §4.8.6).

## Front-matter hygiene

Common front-matter defects worth checking on every review:

- Section titles do not contain stray quotation marks,
  colons, or other punctuation artifacts from editor tools.
- BCP 14 boilerplate is present and verbatim (see
  normative-language.md).
- Obsoletes / Updates / Intended status header lines in the
  title block are consistent with the body text.
- Table of Contents section numbers match the body.
