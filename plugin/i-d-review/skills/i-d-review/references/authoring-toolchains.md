# Authoring Toolchains

Internet-Drafts are authored in Markdown using either the
`mmark` or `kramdown-rfc` toolchain, then converted to RFC
XML (xml2rfc v3) for submission. Write the source document
in Markdown, not raw XML or plaintext.

## Identifying which toolchain a draft uses

Before making any edits to an existing draft, determine
which toolchain it uses. Guessing and mixing conventions
produces source that looks plausible but fails to build.

Signals, in order of reliability:

1. The Makefile or build script at the top of the source
   tree. Look for `mmark` or `kramdown-rfc` invocations.
2. Front-matter style. kramdown-rfc uses a YAML block
   opened and closed by `---`. mmark uses a `%%%` fenced
   TOML-ish header.
3. Reference include syntax. kramdown-rfc uses
   `normative:` / `informative:` YAML maps with RFC
   numbers as keys. mmark embeds `<reference>` XML blocks
   or uses `[@RFCnnnn]` shorthand.
4. Figure and table fencing differ; less reliable as a
   signal because both toolchains accept several forms.

## Before editing an existing draft

- Reuse terminology already defined in the Conventions
  section or body. Do not introduce a synonym for a term
  the draft already defines.
- Continue the existing reference-tag pattern. Drafts
  routinely use mnemonic tags (`[HTTP]`, `[NFSv4.1]`)
  instead of bare `[RFCnnnn]`. Follow whatever the draft
  uses; do not mix styles.
- After adding or removing sections, verify that every
  internal section cross-reference still points at the
  right place. Section renumbering is the single most
  common correctness bug in multi-revision edits.

## Before editing an existing draft

Before modifying an existing draft, examine:

- The terminology already defined in the Conventions
  section or body text; reuse the same terms rather than
  introducing synonyms.
- The existing reference tags; continue the same naming
  pattern. Some drafts use mnemonic tags like `[HTTP]`
  rather than `[RFC9110]`; follow whichever convention the
  draft already uses rather than mixing styles.
- Section numbering and cross-reference consistency; after
  adding or removing sections, verify all internal section
  references remain correct.

## xml2rfc v3 validation

Before submission, run the draft through xml2rfc to surface
schema violations. The most common failures:

- Missing required fields in reference entries (author,
  title, date, series number, DOI).
- Malformed or missing BCP 14 boilerplate block.
- Citations with no matching reference entry, or reference
  entries never cited.
- Duplicate anchor IDs.

## idnits

Run `idnits` (available at
https://author-tools.ietf.org/idnits or the legacy
tools.ietf.org/tools/idnits interface) against the generated
plaintext before submission. idnits checks surface-level
conformance: boilerplate present, line length, obsolete
copyright text, references with no citation and vice versa,
and downref candidates. A clean idnits report is the basic
pre-submission bar.
