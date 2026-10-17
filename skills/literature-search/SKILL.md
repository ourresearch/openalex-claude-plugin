---
name: literature-search
description: Find scholarly papers on a topic with OpenAlex and report them with the exact query behind them. Use when the user asks for papers, studies, evidence or prior work on a topic, a reading list, the most influential or most recent work, or "what does the research say about" something.
---

# Literature search with OpenAlex

Search like a careful librarian: say exactly what you searched, how many works matched, and what you left out.

## Steps

1. **Split the topic into facets**, the two to four ideas every result must have (for "microplastics in drinking
   water and human health": microplastics, drinking water, health effects). Give each facet its synonyms. Ask the user
   only when the scope is truly unclear, such as a field, a year range or a study type that changes the answer.
2. **Preview before reading.** Call `search_works` with the facets as a Boolean query (`AND` between facets, `OR`
   between synonyms, quoted phrases) plus any filters (`from_year`, `types`, `open_access_only`), and `preview=true`.
   Read the count and the sample. Too many off-topic hits: tighten the synonyms or add a facet. Too few: add
   synonyms. Use `preview_sample=random` to judge precision across the whole set, not just the top.
3. **Go thorough when the user wants everything** (a review, a systematic search, "all the papers on"): call
   `find_keywords` for the topic, then `keyword_search` with one facet per idea and only the keywords that really
   mean it. Check the keyword-only sample before trusting what keywords added. List the results with
   `search_works(oql=...)` using the combined query `keyword_search` returned. Don't write query syntax by hand; if
   you must, check it first with `check_oql` (syntax: `read_docs`).
4. **Rank for the question.** Default relevance (reranked) for "papers on X". For "most influential", sort by
   `cited_by_count` or `fwci` and drop any top result whose title isn't about the topic. For "latest", sort by
   `publication_date`.
5. **Verify what you quote.** Call `get_work` for any paper you summarize beyond its title. Retracted works are hidden
   by default; never present one as evidence.

## What to reply

- One or two sentences answering the question, then the works: title, first author et al., year, venue, one line
  on why it's relevant, and a link (the DOI, else the OpenAlex URL), plus the open-access link when there is one.
- The total number of matching works and the `reproduce_url`, so the user can rerun or cite the search.
- What the search did not cover: the years, types or languages you filtered out, and that you read only the top N
  of the total.

Never cite a paper from memory or invent one; every work you list comes from a tool result. Don't paste raw tool
output.

More on what OpenAlex can do: https://help.openalex.org/llms.txt
