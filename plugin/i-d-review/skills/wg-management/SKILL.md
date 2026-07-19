---
name: wg-management
description: Load when acting as an IETF working group chair on standing WG operations not tied to one document's advancement — deciding whether work is in charter scope, rechartering, setting and tracking milestones, running IPR disclosure reminders and polls, building meeting agendas and minutes, requesting sessions or interims, and moderating the WG mailing list including posting suspensions and PR-actions. Also load, chair or not, to retrieve a past session's minutes, agenda, slides, chatlog, or bluesheets from the datatracker or IETF proceedings, or to find what a WG decided at a numbered IETF meeting or interim. Covers RFC 2418, BCP 79 / RFC 8179, RFC 6702, BCP 78, BCP 83 / RFC 3683, and RFC 3934. To advance a specific document, use the wg-advancement skill; to review a draft's technical content, use the internet-draft skill. Do not load for non-IETF group governance or general project management.
invocation_policy: automatic
---

# Running a Working Group (chair)

This skill covers the chair's standing operational tasks that
are not tied to advancing one specific document: charter scope,
milestones, IPR polls, meetings, and the mailing list.
Reference material lives in `references/`; load the file whose
topic matches the task.

Advancing a particular document — adoption calls, WG Last
Call, consensus determinations, shepherding — is the
`wg-advancement` skill. Reviewing a draft's technical content
is the `internet-draft` skill.

## Operating principles

The chair runs the group with wide discretion in the conduct of
WG business (RFC 2418 §6.1), but that discretion operates
inside the charter and the IETF process. Scope questions,
charter changes, and milestones are settled with the
responsible Area Director, not by the chair alone.

Do not overstate obligations. Several duties commonly attributed
to the chair are actually personal duties of participants (IPR
disclosure) or are best practice rather than a rule (polling for
disclosures). State which is which; the difference matters when
a chair acts on it. Verify against the cached RFCs in
`~/Documents/rfcs/` or the datatracker before asserting a
process rule.

## Task-specific material

Load the file whose topic matches the task. Do not
pre-emptively load all of them.

- Deciding whether work is in charter scope, and rechartering
  when it is not: references/charter-and-scope.md.
- Setting milestones, judging their realism, and handling
  overdue ones: references/milestones.md.
- IPR and copyright: whose duty it is, and when a chair should
  poll: references/ipr.md.
- Meeting agendas, sessions and interims, minutes:
  references/meetings.md.
- Retrieving a past session's agenda, minutes, or slides from
  the datatracker: references/finding-meeting-materials.md.
- Mailing-list moderation, posting suspensions, and PR-actions:
  references/list-admin.md.

## Decision shortcuts

These are quick copies of the rules developed in the
references; when detail or an edge case matters, the
referenced file is authoritative.

- Proposed work is close to but not clearly in scope? That is
  an AD conversation, not a chair-only call. Read the charter
  generously with AD agreement, recharter, or decline — do not
  quietly adopt out-of-scope work
  (references/charter-and-scope.md).
- Asked to move a milestone date? That is routine AD
  coordination, not rechartering; only a change to the WG's
  *scope* triggers the full recharter review
  (references/milestones.md).
- Someone asks the chair to "require" an IPR disclosure? The
  disclosure duty is personal to the contributor (BCP 79); the
  chair polls and confirms as best practice (RFC 6702), and
  cannot file another party's disclosure for them
  (references/ipr.md).
- Disruptive participant on the list? Warn, then suspend
  posting for up to 30 days after consulting the AD (RFC 3934);
  a longer removal is a PR-action requiring the IESG (RFC
  3683). The person still receives list mail either way
  (references/list-admin.md).
