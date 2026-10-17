# OpenAlex plugin for Claude

This plugin connects Claude (chat, Cowork and Claude Code) to [OpenAlex](https://openalex.org), the free and open
index of the world's scholarly research: papers, books, datasets and preprints across every field, with their authors, institutions, journals, funders
and citations. Ask about the literature in plain language and Claude finds, counts and checks papers for you, and shows
the exact query behind each answer so you can rerun or cite it.

It has two parts:

- **The OpenAlex connector**: OpenAlex's remote MCP server (`https://mcp.openalex.org/mcp`), the same one listed in
  Claude's connector directory, so people who have both see one set of tools. The first time Claude uses it, you sign
  in with a free OpenAlex account. Nothing to install or run locally.
- **Skills** that teach Claude how to use it well:
  - `literature-search`: find papers on a topic, preview and tune the search, and report the works with the exact
    query, the total count and what the search left out.
  - `check-references`: check a bibliography or citations, flag the ones that don't exist, don't match or were
    retracted, and offer corrected citations.
  - `research-landscape`: map who works on a topic (authors, institutions, countries, journals, funders) and how
    output has grown, with the counts and the search behind them.

## Install

```text
/plugin marketplace add ourresearch/openalex-claude-plugin
/plugin install openalex@openalex
```

## What you can ask

- Find papers on a topic, filtered by year, open access, type, field or institution.
- Check a reference list: which citations exist, and which DOIs are wrong.
- Find the papers that cite a work, or that it cites.
- Profile a researcher, institution, journal or funder.
- Count and compare research output, for example open-access share by year.
- Claim and fix your own OpenAlex author profile.

## Help

Docs: [help.openalex.org/access/connector](https://help.openalex.org/access/connector/). Everything else OpenAlex can
do: [help.openalex.org/llms.txt](https://help.openalex.org/llms.txt). Questions and bugs: support@openalex.org.

OpenAlex data is CC0. This plugin is MIT-licensed.
