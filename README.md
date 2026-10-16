# OpenAlex for Claude Code

This plugin connects Claude Code to [OpenAlex](https://openalex.org), the free and open index of the world's scholarly
research: papers, books, datasets and preprints across every field, with their authors, institutions, journals, funders
and citations. Ask about the literature in plain language and Claude finds, counts and checks papers for you, and shows
the exact query behind each answer so you can rerun or cite it.

It adds OpenAlex's remote MCP server (`https://mcp.openalex.org/mcp`), the same one behind the OpenAlex connector in
Claude's directory. The first time Claude uses it, you sign in with a free OpenAlex account. There is nothing to install
or run locally.

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
