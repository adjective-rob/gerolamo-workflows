---
title: Sleeper Hunt
description: Find high-quality under-the-radar projects, explore their neighborhoods, and synthesize a build plan from the best hidden gems
difficulty: intermediate
tools_required:
  - find_sleepers
  - explore_connections
  - explain_score
  - submit_meta_molecule
  - compose_molecules
estimated_steps: 6
placeholders:
  - name: CORPUS
    description: Which corpus to search (github, arxiv, huggingface, or omit for all)
    example: "github"
you_will_get:
  - Top 10 sleeper sources (high defensibility, low traction)
  - Deep exploration of the 3 best sleepers with neighborhood context
  - Full defensibility reasoning for each
  - 1 concept synthesizing the sleeper insights
  - 1 build composition leveraging the hidden gems
---

## Steps

1. Use `find_sleepers` to discover high-quality, low-traction sources in the {{CORPUS}} corpus. Show me the top 10 results with their defensibility scores, traction, and core functions. Identify which ones are genuinely novel vs. just unpopular.

2. Pick the 3 most interesting sleepers — the ones with real technical substance that the market hasn't found yet. For each one, use `explore_connections` to see their intelligence neighborhood: similar projects, shared capabilities, creator context. Summarize what makes each one's neighborhood interesting.

3. For each of the 3 sleepers, use `explain_score` to get the full defensibility reasoning. Analyze the explanations — are these scores justified? Is there something the scoring missed? Where are the real moats?

4. Search the web for any recent activity around these 3 sleepers or their core technologies. Are they gaining momentum elsewhere? Has anyone written about them? Is there a community forming? This is your alpha — context the corpus doesn't have.

5. Create a concept using `submit_meta_molecule` that represents a project combining the best ideas from these sleepers into something new. Use the 3 sleeper entity IDs as `parent_ids`. The concept should address a gap you identified in their neighborhoods — something none of them do alone but that becomes possible when you combine their approaches.

6. Use `compose_molecules` in 'compose' mode to create a build spec combining the 3 sleeper sources and your concept. Add `user_context` explaining what kind of project this should be and why the combination of these hidden gems creates something the market doesn't have yet. Save it.

## Tips

- Sleepers with defensibility 8+ and traction under 100 are the sweet spot — genuinely good but undiscovered.
- The `explore_connections` step often reveals why a sleeper is underappreciated — it might be in a sparse neighborhood with no obvious category.
- If a sleeper turns out to be abandoned (check the web research), skip it and pick the next one.
