---
title: Cross-Domain Intersection
description: Discover underexplored intersections between tracked domains, synthesize cross-cutting ideas, and generate a production-ready build spec
difficulty: advanced
tools_required:
  - get_tracked_topics
  - query_intelligence
  - submit_molecule
  - submit_meta_molecule
  - compose_molecules
estimated_steps: 7
placeholders: []
you_will_get:
  - Full map of tracked domains with stats
  - Top 3 molecules from each selected domain
  - New molecules submitted from intersection research
  - 2 meta molecules (one cross-domain concept, one concrete implementation)
  - 1 build composition designed as a production open-source project
---

## Steps

1. Use `get_tracked_topics` to see all domains Gerolamo currently tracks. List them with their entity counts and average defensibility scores.

2. Analyze the topics and identify an underexplored intersection between two or more domains that could produce something genuinely novel. Don't pick the obvious combinations — look for domains that nobody would naturally put together but where the intersection could unlock a real capability. Explain your reasoning for why this intersection is interesting.

3. Search the Gerolamo corpus for molecules in each of the domains you identified. Use `query_intelligence` for each domain. Show the top 3 results from each.

4. Search the web for the most recent research at the intersection of these domains from the last 30 days. If you find papers or repos not in the corpus, submit them using `submit_molecule`. Summarize what you found.

5. Create a meta molecule using `submit_meta_molecule` that represents a cross-domain capability that doesn't exist yet — synthesized from the corpus results and external research. Use the IDs from the most relevant molecules across all domains as `parent_molecule_ids`. The reasoning field should explain why this cross-domain idea is defensible and what makes it different from anything in either domain alone.

6. Create a second meta molecule that takes the cross-domain idea and makes it concrete — a specific implementation, system, or tool that could be built. Use the first meta molecule's ID as a parent.

7. Use `compose_molecules` to create a 'build' composition combining the real molecules from step 3 and both meta molecules. Add `user_context`: 'Design this as a production-ready open source project with a clear README, installation guide, and API surface. Focus on the novel cross-domain aspects that make this different from existing tools in either domain.'

## Tips

- Step 2 is the creative core — the agent picks the intersection. Let it think before you intervene.
- The best intersections combine a mature domain (lots of tools) with an emerging one (few tools, high defensibility).
- If the agent picks an obvious combo (e.g., "LLMs + code generation"), push back and ask for something less explored.

## Example intersections the agent might find

- Quantum error correction + cybersecurity AI
- Robot manipulation + privacy-preserving ML
- Mixture of experts + edge deployment for drones
