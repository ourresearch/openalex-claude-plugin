---
name: check-references
description: Check a reference list or citations against OpenAlex and flag the ones that don't exist, don't match, or were retracted. Use when the user pastes a bibliography or citations, asks whether references are real or correct, wants missing DOIs filled in, or is checking citations an AI wrote.
---

# Check references with OpenAlex

Treat every citation as unverified until OpenAlex matches it, and say plainly which ones failed.

## Steps

1. **Collect the references** one per item, as written. Keep DOIs, PMIDs and OpenAlex IDs exactly; keep free-text
   citations whole (authors, year, title, venue).
2. **Resolve them** with `resolve_references`, up to 25 per call, in order. IDs are looked up exactly; free text is
   matched on title with a confidence of exact, likely, uncertain or none.
3. **Look again at the weak ones.** For `uncertain` or `none`, try `search_works` with the title in quotes
   (`search_in=title`), then the first author's surname plus distinctive title words and the year range. A title
   that exists under different authors or a different year is a mismatch, not a match.
4. **Compare the details** of every match with the citation as given: authors, year, title, venue, DOI. Note each
   difference.
5. **Check retractions.** A matched work with `is_retracted: true` must be flagged, whatever else is right.

## What to reply

A table, one row per reference, in the user's order:

| # | Reference as given | Status | Matched work | Issue |
|---|---|---|---|---|

Status is one of: verified, verified with corrections, retracted, not found. Link each matched work by DOI or OpenAlex
URL. Under the table, give the count for each status, and offer corrected citations built from the matched metadata.

"Not found" means OpenAlex has no match, not that the work can't exist: books, reports and very recent papers may be
missing. Say so for those, and don't invent a substitute.

More on what OpenAlex can do: https://help.openalex.org/llms.txt
