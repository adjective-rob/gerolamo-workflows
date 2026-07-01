---
title: Domain Discovery
description: Deep-dive a single domain — search the corpus, find gaps via web research, synthesize novel ideas as concepts, and generate a build spec
difficulty: intermediate
tools_required:
  - query_intelligence
  - submit_source
  - submit_meta_molecule
  - trace_lineage
  - compose_molecules
estimated_steps: 6
placeholders:
  - name: DOMAIN
    description: The domain or technology area to explore
    example: "privacy-preserving machine learning"
you_will_get:
  - Top 5 corpus results for your domain
  - New sources submitted from recent research
  - 2 concepts (one concept, one refinement)
  - 1 build composition with a concrete spec
  - Full lineage trace showing how ideas connect
---

## Steps

1. Use Gerolamo MCP to search for '{{DOMAIN}}'. Show me the top 5 results.

2. Search the web for the most recent academic papers or blog posts on {{DOMAIN}} from the last 30 days. Find something that isn't already in the Gerolamo corpus. If you find papers or repos not in the corpus, submit them using the `submit_source` MCP tool so they get ingested in the next batch run. Summarize what you found and explain what's different about it compared to the corpus results.

3. Create a concept using `submit_meta_molecule` that synthesizes the external research with the corpus results. It should represent something that doesn't exist yet — not a copy of a paper, not a recombination of existing tools, but a new idea informed by both. Use the IDs from the top 3 corpus results as `parent_ids`. Explain in the reasoning field why this is different from what already exists in the corpus.

4. Use `trace_lineage` to show the ancestors of the concept you just created. Direction: ancestors.

5. Create a second concept using `submit_meta_molecule` that builds on the first one — take the idea further, make it more concrete, or address a limitation you see. Use the first concept's ID as a parent.

6. Use `compose_molecules` to create a 'build' composition combining the real sources from step 1 (use their `entity_ids`) and both concepts (use their `concept_ids`). Add `user_context` describing what you'd want the final output to be — a library, a service, a framework — based on what makes sense for the idea. And save it.

## Tips

- Be specific with `{{DOMAIN}}`. "autonomous agents" works better than "AI".
- Step 2 is where the magic happens — the web search finds what the corpus doesn't have yet.
- The second concept (step 5) should be more concrete than the first — think implementation, not concept.

## Example

Replace `{{DOMAIN}}` with something like:
- `AI Voice and Distributed Hard-to-access Hardware like Space systems`
- `privacy-preserving machine learning`
- `real-time robot manipulation planning`
