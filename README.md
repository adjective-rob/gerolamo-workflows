# gerolamo-workflows

Agent workflows for [Gerolamo](https://gerolamo.org) — the competitive intelligence engine for open-source technology.

Workflows are multi-step prompt templates that chain [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) tools into complete intelligence operations. They work with any MCP-capable agent — Claude, Cursor, Windsurf, GPT, or anything else that speaks MCP.

## How it works

This repo is the **open-source contribution surface**. The Gerolamo API is the **runtime**.

```
gerolamo-workflows (this repo)        gerolamo API (database)
    ┌──────────────┐                   ┌──────────────────┐
    │  workflows/   │ ── seed script ──>│  workflow table   │
    │  *.md files   │                   │  (source of truth)│
    │               │                   └────────┬─────────┘
    │  Community PRs│                            │
    │  & iteration  │                   ┌────────┴─────────┐
    └──────────────┘                   │  MCP tools        │
                                        │  list_workflows() │
                                        │  get_workflow()   │
                                        └────────┬─────────┘
                                                 │
                                        ┌────────┴─────────┐
                                        │  Any MCP agent    │
                                        │  discovers &      │
                                        │  executes the     │
                                        │  workflow          │
                                        └──────────────────┘
```

**The agent IS the runtime.** Gerolamo doesn't execute workflows — it serves them. Your agent reads the steps and executes them using the existing MCP tools, thinking and adapting between each step. That's the whole point: the LLM brings judgment, the workflow brings structure.

## Using workflows

### Option 1: Through your agent (recommended)

If you have [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) configured, your agent can discover and run workflows directly:

```
"Show me available Gerolamo workflows"
→ agent calls list_workflows()

"Run the Domain Discovery workflow for autonomous agents"
→ agent calls get_workflow("domain-discovery")
→ agent reads the steps
→ agent executes each step using MCP tools, thinking between steps
```

The agent fills in placeholders, handles errors, and makes creative decisions at each step. Two agents running the same workflow will produce different results — that's a feature.

### Option 2: Copy-paste

Browse `workflows/` in this repo, copy the steps, paste into your agent. Same result, just manual.

## What's in a workflow

Each workflow is a markdown file with YAML frontmatter:

```markdown
---
title: Domain Discovery
description: Deep-dive a single domain and synthesize novel ideas
difficulty: intermediate
tools_required:
  - query_intelligence
  - submit_molecule
  - submit_meta_molecule
  - trace_lineage
  - compose_molecules
estimated_steps: 6
you_will_get:
  - Top 5 corpus results for your domain
  - New molecules submitted from web research
  - 2 meta molecules (concept + refinement)
  - 1 build composition with a concrete spec
  - Full lineage trace
placeholders:
  - name: DOMAIN
    description: The domain or technology area to explore
    example: "privacy-preserving machine learning"
---

## Steps

1. Use Gerolamo MCP to search for '{{DOMAIN}}'...
```

### Fields

| Field | Purpose |
|-------|---------|
| `title` | Human-readable name |
| `description` | One-line summary — what the agent sees in `list_workflows()` |
| `difficulty` | `beginner` / `intermediate` / `advanced` — signals how many steps and how much agent judgment is needed |
| `tools_required` | Which MCP tools the workflow calls — agents can check they have access before starting |
| `estimated_steps` | How many steps the agent will execute |
| `you_will_get` | Concrete deliverables — what exists in your Gerolamo account after the workflow completes |
| `placeholders` | Variables the user fills in — `{{NAME}}` in the prompt body |

## Available workflows

| Workflow | What it does | Difficulty | You get |
|----------|-------------|------------|---------|
| [Domain Discovery](workflows/domain-discovery.md) | Deep-dive a domain: corpus search, web research gap analysis, meta molecule synthesis, build spec | Intermediate | 2 meta molecules, 1 composition, submitted molecules |
| [Cross-Domain Intersection](workflows/cross-domain-intersection.md) | Find novel intersections between tracked domains, synthesize cross-cutting ideas, generate production spec | Advanced | Domain map, 2 meta molecules, 1 composition |
| [Sleeper Hunt](workflows/sleeper-hunt.md) | Find high-quality under-the-radar projects, explore their neighborhoods, and build something from hidden gems | Intermediate | Deep analysis of 3 sleepers, 1 meta molecule, 1 composition |
| [Stack Audit](workflows/stack-audit.md) | Evaluate your tech stack's defensibility, find weak links, discover alternatives, produce migration plan | Beginner | Weakest-link analysis, alternatives for each weak component, 1 comparison composition |
| [Creator Deep Dive](workflows/creator-deep-dive.md) | Profile a creator's work, map their network, and predict what they might build next | Intermediate | Creator profile, network map, gap analysis, 1 predictive meta molecule |
| [Investment Thesis](workflows/investment-thesis.md) | Generate a data-backed investment thesis — market dynamics, defensible players, frontier risks, buy/watch/pass | Advanced | Intelligence brief, landscape analysis, cluster map, 1 research composition |
| [Model Selection](workflows/model-selection.md) | Compare foundation models for a specific use case — pricing, benchmarks, domination risk, recommendation | Beginner | Pricing comparison, benchmark comparison, domination analysis, concrete recommendation |
| [Trend Spotter](workflows/trend-spotter.md) | Spot what's emerging across all domains — breakouts, converging trends, and 90-day predictions | Intermediate | Domain heat map, cross-domain sleepers, 1 trend report composition |

## Why this exists

Gerolamo tracks thousands of molecules (repos, papers, models) across dozens of domains. The MCP gives you 25+ tools to search, analyze, compose, and create. But the tools alone don't tell you *what to do with them*.

Workflows are opinionated sequences that solve specific problems:

- **"I want to understand a new domain"** → Domain Discovery
- **"I want to find a novel project idea"** → Cross-Domain Intersection
- **"I want to evaluate my tech stack"** → Stack Audit
- **"I want to write an investment memo"** → Investment Thesis
- **"I want to find hidden gems"** → Sleeper Hunt
- **"I want to pick a foundation model"** → Model Selection
- **"I want to know who's building what"** → Creator Deep Dive
- **"I want to see what's emerging"** → Trend Spotter

Each workflow chains 5-7 MCP tool calls with web research and creative synthesis in between. The steps are specific enough to be repeatable but open enough that the agent brings its own judgment. Run the same workflow twice and you'll get different (equally valid) results.

## Architecture decisions

**Why not API endpoints?** We considered `POST /api/v1/workflows/run/domain-discovery`. But that means building an orchestration engine — timeouts, partial failure handling, LLM cost management. The agent already handles all of that. Serving the recipe and letting the agent cook is simpler and more powerful.

**Why not just MCP tools?** We considered a single `run_domain_discovery(domain)` compound tool. But that hides the steps, removes agent judgment between them, and makes the workflow a black box. The agent should see what it's doing and adapt.

**Why a database?** Workflows are seeded from this repo but served from the Gerolamo database. This means:
- Workflows can be updated without redeploying the MCP
- Usage analytics (which workflows get requested, which steps fail most)
- Future: users save their own custom workflows
- Future: `suggest_workflow()` recommends workflows based on your user profile

**Why this repo?** The database is the runtime, but the repo is the contribution surface. Community members can browse, fork, improve, and submit new workflows via pull request. Accepted PRs get seeded into the database on the next deploy.

## Prerequisites

- A [Gerolamo](https://gerolamo.org) account (free tier works for most workflows)
- [gerolamo-mcp](https://www.npmjs.com/package/gerolamo-mcp) configured in your agent
- For workflows that use `compose_molecules`: Pro or BYOK tier

## Contributing

We welcome new workflows. The best ones solve a specific problem that requires chaining multiple tools with human-level judgment in between.

### To contribute:

1. Fork this repo
2. Create a new `.md` file in `workflows/`
3. Follow the frontmatter format (see any existing workflow as a template)
4. Include the `you_will_get` field — be specific about what the user ends up with
5. Test it by running it with an MCP-capable agent at least once
6. Open a PR with a description of what problem the workflow solves

### What makes a good workflow:

- **Specific outcome** — "generate an investment thesis" not "explore stuff"
- **5-8 steps** — enough structure to be useful, not so many that it's rigid
- **Creative steps** — at least one step where the agent has to think, not just call a tool
- **Web research** — the best workflows combine corpus data with fresh external research
- **Concrete artifacts** — meta molecules, compositions, submitted molecules — things that persist

## License

MIT
