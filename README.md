# gerolamo-workflows

Agent workflows for [Gerolamo](https://gerolamo.org) — the competitive intelligence engine for open-source technology.

These are composable, copy-pasteable prompt templates that chain [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) tools into multi-step intelligence workflows. They work with any MCP-capable agent (Claude, Cursor, Windsurf, GPT, etc.).

## What's in here

Each workflow is a markdown file in `workflows/` with:

- **Frontmatter** — title, description, required tools, difficulty, what you'll end up with
- **The prompt** — a step-by-step template with `{{PLACEHOLDERS}}` you fill in
- **Example output** — what a good run looks like

## Quickstart

1. Install [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) in your agent
2. Pick a workflow from `workflows/`
3. Copy the prompt, fill in the placeholders, paste into your agent
4. Watch it work

## Workflows

| Workflow | Description | Difficulty | Tools Used |
|----------|-------------|------------|------------|
| [Domain Discovery](workflows/domain-discovery.md) | Deep-dive a single domain: search, find gaps, synthesize new ideas, build a spec | Intermediate | 5 |
| [Cross-Domain Intersection](workflows/cross-domain-intersection.md) | Find novel intersections between tracked domains and synthesize cross-cutting ideas | Advanced | 6 |

## Workflow anatomy

```markdown
---
title: My Workflow
description: What this workflow does
difficulty: beginner | intermediate | advanced
tools_required:
  - query_intelligence
  - submit_meta_molecule
  - compose_molecules
estimated_steps: 6
you_will_get:
  - 2 meta molecules
  - 1 build composition
  - 3 submitted molecules
---

## Steps

1. Use Gerolamo MCP to search for '{{DOMAIN}}'...
```

## Prerequisites

- A [Gerolamo](https://gerolamo.org) account (free tier works for most workflows)
- [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) configured in your agent
- For workflows that use `compose_molecules`: Pro or BYOK tier

## Contributing

We welcome new workflows. To contribute:

1. Fork this repo
2. Create a new `.md` file in `workflows/`
3. Follow the frontmatter format above
4. Include at least one example of what the output looks like
5. Open a PR

## License

MIT
