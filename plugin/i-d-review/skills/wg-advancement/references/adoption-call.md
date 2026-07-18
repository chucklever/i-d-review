# Running a WG Adoption Call

"Adoption" transfers a personal draft
(`draft-<name>-<wg>-...`) to WG ownership
(`draft-ietf-<wg>-...`), moving change control to the IETF.
This file covers the chair's task of running and closing the
call. For assessing whether a draft *should* be adopted —
the RFC 7221 §2.2 criteria and the §2.1 chair workflow as an
evaluation lens — see the `internet-draft` skill's
`references/wg-adoption.md`; do not duplicate that assessment
here. For judging and declaring the result, see
references/consensus-determination.md.

## Before the call

- Confirm the topic is within charter scope, or that a charter
  change is feasible and warranted (criteria 2 and 8 of RFC
  7221 §2.2). Scope judgments belong to the `wg-management`
  skill's `references/charter-and-scope.md`.
- Remind the current draft owners that adoption transfers
  change control to the IETF (RFC 7221 §2.1).
- Run the IPR poll. Confirm on-list that every author and
  listed contributor has disclosed any known IPR or has
  stated none. This is best practice at adoption (RFC 6702
  §3.2), not a BCP 79 duty on the chair; the underlying
  disclosure duty is personal to each contributor (BCP 79 /
  RFC 8179, see the `wg-management` skill's
  `references/ipr.md`).

## Issuing the call

Post a call to the list that names the draft and version,
states the review period (2 weeks is customary), and asks a
specific question: does the WG want to adopt this draft as a
starting point for its work? Make clear that adoption is not
approval of the content and does not commit the WG to any
specific solution (RFC 7221 §2.2).

## Judging and closing

Apply references/consensus-determination.md. Adoption needs
rough consensus to adopt, not unanimity, and does not require
the draft to be complete or publication-ready — writing
quality and open technical questions are expected and are
addressed after adoption. Gather and flag WG concerns about
the existing draft as part of the call; adopting a document
does not mean the WG has agreed to all of its content.

## After a successful call

- Post the chair determination (references/consensus-
  determination.md).
- Choose document editors; the chair selects, considering the
  views of the WG, and may retain or replace the original
  authors (RFC 7221 §3).
- Instruct the authors to post the WG version and approve the
  posting.
- Ensure the personal draft is marked replaced by the WG
  version in the datatracker.
