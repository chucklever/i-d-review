# Determining and Declaring Rough Consensus

This is the chair's core adjudication task, shared by adoption
calls and WG Last Calls. It governs how the chair judges the
result of a call and how the chair writes the determination
that goes on the record.

## What rough consensus is

Working groups decide by rough consensus, not by voting (RFC
2418 §3.3). It is up to the chair to determine whether rough
consensus has been reached. Rough consensus is not unanimity:
a determination can stand even over the continued objection of
the person who raised an issue (RFC 7282 §3). It is also not a
majority — "51% of the working group does not qualify as
rough consensus" (RFC 2418 §3.3).

For IETF-stream documents, IETF rough consensus (confirmed
later at IETF Last Call, not just WG consensus) is required
before publication (RFC 8789). The WG determination is the
first gate, not the last.

## An objection is not disposed of by silence

The determinative question is whether an open technical issue
has been addressed, not how many people spoke. "It is the
existence of the unaddressed open issue, not the number of
people, which is determinative" (RFC 7282 §6). An objection
met with silence has not been answered; an objector who later
disappears from the thread still leaves the issue open until
it is engaged.

"Addressed" means the objection was engaged on its technical
merits and either accommodated or explicitly judged not to
require accommodation, with the reasoning stated. A deadline
passing is not an answer.

## Sustained vs resolved objections

Read the mailing-list archive, not just the message count.
Mark an objection as **sustained** if:

- the same substantive concern was raised in at least two
  separate messages from one reviewer, or by more than one
  reviewer; and
- the current revision has not resolved it to the reviewer's
  stated satisfaction.

An objection is **resolved** only when the reviewer explicitly
withdraws it or accepts the response. Silence after a
follow-up is not withdrawal.

A substantive objection challenges the document's motivation,
correctness, or scope. Separate these from procedural
objections (wrong version under review, insufficient review
time, late submission): resolve the procedural issues first,
but addressing them does not dispose of the substantive ones,
and vice versa.

## Affirmative support matters

Note whether any participant other than the authors spoke in
favor of advancement. Rough consensus in favor of a document
normally requires some affirmative voice. A record consisting
entirely of objections and silence does not establish
consensus even if the deadline passes.

## The version under review

If a substantive revision is posted while a call is open, the
WG never actually called that text. Establish which version
governs. Reviews against a superseded version are not void,
but they must be checked against the new text before the chair
can call consensus. When the change is material, run a short
confirming call on the new revision rather than declaring on
text the group did not review.

## Overriding a sustained objection

A chair may call rough consensus despite a sustained
objection, but only by posting an explicit determination to
the list that:

1. names the objection,
2. describes how the WG considered it, and
3. explains why it was not adopted.

A "final call" notice that does not address the open objection
is not a consensus determination. The written determination is
the record the group — and, on appeal, the AD, IESG, and IAB
(RFC 2026 §6.5) — will test. It also feeds the shepherd
write-up's consensus question (references/shepherd-writeup.md).

## Writing the determination

Post a chair message to the list that states: the outcome,
which document version it applies to, how each sustained
objection was resolved or why it does not block, and the
next step. This message becomes part of the permanent record.
