# Searching the IETF Mail Archive

Working-group discussion happens on the WG mailing list, and
the list archive is the record you must read before judging
WG consensus or citing what a participant said. The archive
lives at mailarchive.ietf.org. Browsing and searching are
different operations on different endpoints; do not conflate
them.

## The procedure

1. Find the list name and its archive from the WG's
   datatracker page.
2. Keyword-search that list for the draft and the discussion
   you need (if the search endpoint is blocked, fall back to a
   `site:mailarchive.ietf.org` web search).
3. Open a hit and copy its message permalink; fetch the
   permalink, not the search URL.
4. Cite the permalink (or the thread) as the record.

Each step is detailed below.

## Find the right list first

A message went to a mailing list, not to a working group. The
list name is usually the WG acronym — nfsv4@ietf.org is
archived under the list `nfsv4` — but not always, and some
WGs run more than one list. Confirm the exact list name and
its archive URL from the WG's datatracker page:

  https://datatracker.ietf.org/wg/<wgname>/about/

which shows the mailing-list address and a direct "List
archive" link. Use that list name in the URLs below.

## Browse vs. search

Two endpoints, two jobs. Browsing lists one WG's traffic in
date or thread order:

  https://mailarchive.ietf.org/arch/browse/<list>/

Use it to read a thread you can already place by date, or to
skim recent traffic. It is not a keyword search: typing a
draft name into the browse page filters nothing.

Searching is full-text keyword lookup:

  https://mailarchive.ietf.org/arch/search/?email_list=<list>&q=<terms>

`q=` carries the query; `email_list=<list>` scopes it to one
list, and omitting it searches every list. Use search when
you know what was discussed but not when.

The `q=` query is full-text with AND as the default: several
bare terms all have to match. Double-quote an exact phrase,
`OR` with parentheses builds alternatives, a leading `-`
excludes a term, a trailing `*` wildcards it, and a
`from:`/`to:`/`subject:`/`msgid:` prefix scopes one term to a
header field. The full syntax is at
mailarchive.ietf.org/arch/help/.

Both views accept the same refinements as URL parameters:

- `qdr=d|w|m|y` — restrict to the past day, week, month, or
  year.
- `gbt=1` — group by thread instead of by individual message.
- `page=N` — page through results; the Subject, From, Date,
  and List columns are sortable.

For queries scoped by sender, subject, or an explicit date
range, use the Advanced Search form rather than hand-building
the query string:

  https://mailarchive.ietf.org/arch/advsearch/

It composes the URL for you, and that URL is stable enough to
paste into a review. Fall back to it, too, when a hand-built
query is rejected or returns implausibly few hits: a mistyped
field prefix or parameter fails silently, and an empty result
must never be read as an empty record.

## Cite messages, not searches

A search URL is a query, not evidence: its results shift as
the archive grows. When you cite the record, cite the
message. Every message has a stable permalink:

  https://mailarchive.ietf.org/arch/msg/<list>/<hash>/

Open the message from the results list and copy that URL. To
show a whole exchange, cite the thread (the `gbt=1` thread
view) and name the messages within it.

## Worked example

Reading the nfsv4 WG Last Call record for the Multiple NFSv4
Domain Namespace draft (later RFC 8000):

1. Search the list for the draft topic:

     https://mailarchive.ietf.org/arch/search/?email_list=nfsv4&q=%22Multiple+NFSv4+Domain%22

2. Open a hit from the WGLC thread and copy its permalink:

     https://mailarchive.ietf.org/arch/msg/nfsv4/ofSZW8-wqSfEwt9EFGMJWEPkGxo/

3. Fetch that permalink — not the search URL — and cite it as
   the record ("Cite messages, not searches", above).

## Retrieval caveats and fallbacks

The archive is a JavaScript-assisted application, and it does
not hand its full contents to every automated fetcher:

- The `/arch/search/` results endpoint may return HTTP 403 to
  a naive fetch. Individual `/arch/msg/<list>/<hash>/`
  permalink pages render as plain content and are reliably
  fetchable — resolve to a permalink, then fetch that.
- Export (mbox, maildir, or a message-URL list) requires an
  IETF datatracker login. Do not rely on it in an
  unauthenticated session.

When a direct fetch is blocked, fall back to:

- A web search scoped to the archive host:
  `site:mailarchive.ietf.org <list> <terms>`. Its result
  links are the `/arch/msg/` permalinks you want anyway.
- The document's datatracker page,
  https://datatracker.ietf.org/doc/<draft>/, which links
  related Last Call and mailing-list activity.

State plainly when the archive could not be retrieved rather
than inferring a thread's contents from memory.

## What to search for in a consensus review

When reading the record for a WG Last Call or adoption call:

- Search both the adopted name (`draft-ietf-<wgname>-...`)
  and any earlier personal name (`draft-<author>-...`);
  pre-adoption discussion is filed under the old name.
- Add the Last Call subject terms — "WGLC", "WG Last Call",
  "Last Call" — which the chair's call message usually
  carries.
- Search the specific issue keywords when chasing whether a
  named objection was ever answered on the merits.

The record is adequately covered once the adopted- and
personal-name searches, the Last Call thread, and each raised
objection have each been read to a resolution or to an
explicit non-answer. Distinguish "no message resolved this
objection" from "the archive could not be searched": report
which, and never present an unsearched record as silent
consensus.

Reading the record is one step; judging it is another. For
the participant's read of consensus see review-workflow.md's
"Mailing list consensus review"; for the chair's
determination see the wg-advancement skill's
references/consensus-determination.md.
