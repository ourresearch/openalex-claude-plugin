---
name: research-landscape
description: Map who works on a research topic with OpenAlex: the leading authors, institutions, countries, journals and funders, and how output has grown. Use when the user asks who publishes most on something, who the experts are (at an institution or anywhere), which journals or funders lead a field, or for a trend or profile of a body of research.
---

# Map a research landscape with OpenAlex

Every number you report is a count of works in OpenAlex for a stated search, so define the search first and show it.

## Steps

1. **Define the set of works.** Build the topic as a Boolean query and filters (years, types), and check it with
   `search_works(preview=true)`: the count should be plausible and the sample on topic. For a named institution,
   funder, journal or person, resolve the name to an ID with `search_entities` first and filter by ID, never by name.
2. **Answer "who" and "where" with `group_works`.** Use `group_by` author, institution, country, source, funder or
   year on the same query and filters. Report counts, not just ranks.
3. **Profile a set in one call with `analyze_works`** when the user wants an overview: totals, open-access share,
   share in the top 10% and 1% most cited, trend by year, and top fields, institutions, countries, sources, funders
   and authors. Ask only for the sections you need.
4. **Find experts at a place with `search_entities`** (`entity_type=authors`, `institution_ids` and `topic_ids`).
   `group_works` by author over an institution's works also counts co-authors from elsewhere, so it is the wrong
   tool for "researchers at X". When names collide, use institutions, h-index and top topics to pick the person.
5. **Compare several groups** (three universities, two countries) with one `group_works` or `analyze_works` call per
   group on the same topic query, so the numbers line up.

## What to reply

- The answer in a sentence or two, then a short table of the top entries with their work counts and OpenAlex links.
- The search behind the numbers (the query, filters and `reproduce_url`) and the total count.
- The caveats that apply: counts include only works in OpenAlex, retracted works are excluded by default, author
  counts depend on profile accuracy, and a topic query that is too broad or too narrow moves every rank.

More on what OpenAlex can do: https://help.openalex.org/llms.txt
