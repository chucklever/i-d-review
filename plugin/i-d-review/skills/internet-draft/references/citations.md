# Citations and References

## When to cite

The obligation to cite is functional, not taxonomic (RFC
3967; IESG Statement on Normative and Informative
References):

- If an implementer needs another document to understand or
  implement the specification, cite it as a normative
  reference. This includes packet formats, required
  algorithms, data encodings, and protocol mechanisms
  defined externally.
- If a document is mentioned for background, motivation, or
  as one of several possible alternatives, cite it as an
  informative reference.
- Foundational specifications safely assumed known to
  practitioners (e.g., RFC 791 for IPv4) need not be cited
  unless the specification depends on specific details
  within them.
- Use of BCP 14 keywords in their normative sense requires
  citing both RFC 2119 and RFC 8174 as normative references.

## Classification

Classify each reference as normative or informative:

- Normative: the document cannot be implemented without
  reading the referenced specification. Examples: a
  protocol the draft extends, a format it encodes, an
  algorithm it requires.
- Informative: the reference provides background,
  motivation, or alternatives but is not required for
  implementation. Examples: related work, historical
  context, measurement studies.

Place normative references in the "Normative References"
subsection and informative references in the "Informative
References" subsection. When only one type is present, no
subsection is needed; title the section accordingly.

A normative reference from a Standards Track document to an
Informational or Experimental RFC constitutes a downward
reference (downref). Downrefs require IESG approval per BCP
97 (RFC 3967). When a downref is unavoidable, note it
explicitly so reviewers can assess whether prior IESG
approval exists or must be requested. The IETF maintains a
downref registry of pre-approved downrefs at
https://datatracker.ietf.org/doc/downref.

Misclassification is a common review finding. A reference
presented as "informative" that an implementer cannot
actually skip is a de-facto normative reference; call it
out and ask the author either to reclassify or to explain
in the text why the cited material is not required for
implementation.

## Reference format (RFC 7322 Section 4.8.6)

- Use the `[RFCnnnn]` tag format for in-text citations.
  Citation tags must not contain spaces. Enclose all
  citations in square brackets.
- Every in-text citation tag must have a corresponding
  reference entry, and every reference entry must be cited
  in the text.
- The Abstract must not contain citations.
- Cross-references within the document and to other RFCs
  must use section numbers, not page numbers.
- List references in alphanumeric order by citation tag.
- BCP and STD numbers are document series that may comprise
  multiple RFCs. Use the BCP/STD identifier when referencing
  the policy or standard as a whole (e.g., BCP 14 for the
  combined requirements language policy), and use the
  individual RFC number when referencing specific technical
  content within one of the constituent documents (e.g.,
  RFC 8174 for the capitalization clarification). When an
  STD or BCP contains multiple RFCs, the reference entry
  must list all constituent RFCs.
- Each reference entry requires: author(s), title, date,
  series number (RFC nnnn or draft string), and DOI. For
  Internet-Drafts, include "Work in Progress" as the series
  designation. Omitting required fields produces xml2rfc
  validation errors.
- When referencing an Internet-Draft, include the full
  version string (e.g., draft-ietf-nfsv4-rpc-tls-09) and
  the date in the reference entry. A reference to a bare
  draft name without a version is ambiguous because drafts
  change between revisions. Flag any reference to an expired
  draft; either update to the successor RFC or document why
  the expired draft is still the correct reference.
  Internet-Draft references may appear only as informative
  references. A normative reference to an Internet-Draft
  blocks RFC publication until the referenced draft is also
  published.
- URIs in reference entries cannot be the sole information;
  when a dated URI is available, use it.
- Use pre-built XML reference entries from bib.ietf.org
  rather than constructing them manually.

## Citation verification

Before accepting or finalizing each citation, download the
referenced RFC or draft into `~/Documents/rfcs/` if not
already cached (see CLAUDE.md for the download procedure),
then verify against the cached plaintext:

- Exact title, authors, and date match the reference entry.
- Any section number cited in the body text exists in the
  referenced document and says what the draft claims it
  says. Section numbers change between revisions; a
  reference that was accurate against RFC 2616 may not
  hold against RFC 9110.
- The "Obsoleted by:" and "Updated by:" lines in the RFC
  header point to the current document. Cite the current
  document, not its predecessor, unless there is a
  documented reason.
- Internet-Draft references resolve to a non-expired
  revision of the draft, or to the successor RFC if the
  draft has been published.

Correct any discrepancies before proceeding. Flag
discrepancies in review output; do not paper over them.
