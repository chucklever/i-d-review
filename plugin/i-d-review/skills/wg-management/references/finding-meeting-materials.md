# Finding Meeting Agendas and Minutes

meetings.md covers publishing a session's record as chair. This
file covers the other direction: retrieving what a WG already
posted — the agenda, minutes, and slides for a past session,
whether the WG is yours or someone else's. Agenda building,
milestone review, and "what did we decide in the room" questions
all start here.

## The procedure

Every retrieval runs in this order; the sections below explain
why each step is there and what goes wrong when it is skipped.

1. Query the document API for the material you want, narrowed
   to the WG and the meeting (query forms under "Enumerate a
   WG's meeting history" below). The API, not any page, is the
   inventory.
2. Query type=chatlog for the same meeting and count the
   results to learn how many sessions the WG held.
3. Take uploaded_filename from each object you want; the
   revision and extension in it are not predictable from the
   document name.
4. Fetch the raw file from the proceedings tree under that
   filename — chatlogs excepted, which the datatracker serves
   instead.

Fetch with curl at every step, the API queries included. A
tool that renders, converts to markdown, or summarizes returns
a paraphrase, and it will drop uploaded_filename out of a JSON
response as readily as it will reword a decision you meant to
quote.

## Enumerate through the API, not the session page

The obvious entry point is the session page:

    https://datatracker.ietf.org/meeting/<num>/session/<wg>/

Use it to orient, but do not treat it as the inventory. It
renders one session, so a WG that met twice can have materials
that never appear on it: httpbis at IETF 122 posted minutes for
both its Tuesday and Friday sessions, and that page links only
the Tuesday one. Concluding "no minutes were posted" from the
session page is the standard way to get this wrong.

The document API is the enumeration of record; the query forms
are under "Enumerate a WG's meeting history" below. Each entry
also has a datatracker document page, which carries revision
history and upload dates but not, for minutes and agendas, the
text:

    https://datatracker.ietf.org/doc/agenda-<num>-<wg>/
    https://datatracker.ietf.org/doc/minutes-<num>-<wg>/
    https://datatracker.ietf.org/doc/slides-<num>-<wg>-<slug>/

Reach these from a name the API gave you. Constructing one by
hand to test whether a material exists reproduces the 404
ambiguity described below.

## What the name tells you

Chatlogs and bluesheets are produced per session and always
carry a session-start timestamp, single session or not. An
agenda is one document per WG per meeting, keeps the bare name
however many times the WG met, and is revised in place; httpbis
met twice at IETF 122 under a single agenda-122-httpbis at
revision 03.

Minutes follow no rule, because the name reflects how the chair
filed them. tls met twice at IETF 122 and filed one document per
session, minutes-122-tls-202503180830 and
minutes-122-tls-202503200230, with bare minutes-122-tls
resolving to nothing. dnsop also met twice at IETF 121 and filed
a single bare minutes-121-dnsop covering both. So the minutes
name does not tell you how many sessions the WG held, and the
session count does not tell you the name. To count sessions,
query type=chatlog or type=bluesheets for the meeting and count
the results.

Timestamps are not comparable across material types either: the
httpbis Tuesday session is minutes-122-httpbis-202503180600 but
chatlog-122-httpbis-202503181300, seven hours apart because they
are recorded in different timezones. Never derive one material's
name from another's; take each from the API.

Nor does a name promise anything about scope. It is the filing
slot, not a description of contents, and this cuts both ways:
both httpbis minutes documents at IETF 122 narrate both days, so
the one filed under the Friday timestamp opens with the Tuesday
session, while dnsop's single bare document carries Session 1
and Session 2 as internal headings. Before reporting a session
unminuted, or quoting a passage as one session's record, read
the document far enough to see which sessions it actually
covers.

A 404 therefore carries two meanings — the name needs a
timestamp suffix, or the material was never posted. Resolve it
against the API rather than by trying variants. Posting minutes
is a chair obligation that is not always met: nfsv4 at IETF 122
has an agenda, five slide decks, and a chatlog, but no minutes.
Missing minutes are a gap in the WG's record, not a failed
search, and the chatlog is sometimes the only account of the
session.

## Fetch the text rather than the viewer

The datatracker /materials/ URL that the session page links
serves an HTML wrapper around the document, not the document.
For the raw file, use the proceedings tree:

    https://www.ietf.org/proceedings/<num>/minutes/<filename>
    https://www.ietf.org/proceedings/<num>/agenda/<filename>
    https://www.ietf.org/proceedings/<num>/slides/<filename>

Chatlogs are not in the proceedings tree at all. They are JSON,
and the datatracker serves them raw because the wrapper applies
only to rendered text:

    https://datatracker.ietf.org/meeting/<num>/materials/<filename>

<filename> carries both a revision and an extension, and
neither is predictable: minutes-124-nfsv4-00.md is markdown at
revision 00, minutes-116-nfsv4-01.pdf is a PDF at revision 01.
Minutes get revised after the WG corrects them, so -00 is not a
safe default. Neither the session page nor the document page
shows an extension; the filename comes from the API's
uploaded_filename field, below.

The extension also decides how to read what you fetched: a .pdf
minute is binary to curl, so run it through pdftotext rather
than reporting the fetch as failed.

This is the fetch a summarizing tool most visibly ruins. A
paraphrased minute is worthless for quoting a decision back to
the WG.

## Reporting what you found

Quote the document verbatim; do not paraphrase a decision back
to the WG. Cite it by document name and by the session its API
title field names ("Minutes IETF122: httpbis: Tue 06:00"),
since the document name alone does not identify a session.
Where a session has no minutes, report that none were posted
and say what does exist for it — an agenda, a chatlog, slides.
That is a different answer from "not found," and the WG's
record turns on the difference.

## Enumerate a WG's meeting history

For a browsable list of every session a WG has held, including
interims, with links to recordings:

    https://datatracker.ietf.org/group/<wg>/meetings/

It gives dates but not session times, and it is a heavy HTML
page; prefer the API below whenever you need to work from the
answer rather than read it.

To pull the whole set of minutes in one query, with the exact
filenames, use the datatracker REST API (one line, no wrapping):

    https://datatracker.ietf.org/api/v1/doc/document/?type=minutes&group__acronym=<wg>&format=json&limit=100

Each object carries name, rev, time, title, and
uploaded_filename. uploaded_filename is the proceedings filename
above, for interims as well as regular meetings; title is what
distinguishes one session from another in human terms
("Minutes IETF122: httpbis: Tue 06:00"), and is the only field
that does. `type=agenda`, `type=slides`, `type=chatlog`, and
`type=bluesheets` behave the same way. Two traps: the default
page size is 20 and the response truncates silently, which is
why the forms here carry limit=100 — check meta.total_count
against what you received and page with offset when a WG has
more; and the API rejects `order_by=time`, so sort on the
client.

To narrow to one meeting, filter on the name rather than
matching the meeting number as a substring — an interim's
YYYYMMDD timestamp contains meeting-number-like digits, so
"123" also matches minutes-interim-2018-quic-01-201801230930:

    ...?type=minutes&group__acronym=<wg>&name__startswith=minutes-<num>&limit=100

## Interims

Interim materials follow a parallel naming scheme keyed to the
interim's own identifier rather than a meeting number:

    minutes-interim-<year>-<wg>-<NN>-<YYYYMMDDHHMM>

and the raw file sits under a matching proceedings directory
(one line, no wrapping):

    https://www.ietf.org/proceedings/interim-<year>-<wg>-<NN>/minutes/<filename>

## Whole-meeting view

When the question spans WGs rather than one session, start from
the proceedings index for the meeting:

    https://datatracker.ietf.org/meeting/<num>/proceedings

The older https://www.ietf.org/proceedings/<num>/ redirects
there.

## When the datatracker has nothing

Minutes and agendas are normally announced on the WG list as
well, and a session's substance continues there afterward. When
the datatracker record is thin, search the list archive — load
the internet-draft skill and read its
references/mailarchive-search.md for the query forms.

Some WGs also keep a materials repository of their own and
treat it, not the datatracker, as the working copy. The
datatracker upload can then lag or hold only a pointer. The
WG's charter page or its posted slides usually name that
repository.

## Currency

The URL forms, field names, and API behavior here were checked
against the live datatracker in July 2026. The page-size
default and the order_by rejection are the parts most likely to
drift; where a response contradicts this file, trust the
response.
