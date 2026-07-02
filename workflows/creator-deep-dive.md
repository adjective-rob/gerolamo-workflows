---
title: Creator Deep Dive
description: Profile a creator's body of work, map their collaboration network, and identify what they might build next
difficulty: intermediate
tools_required:
  - get_creator_profile
  - get_creator_network
  - explore_connections
  - query_intelligence
  - submit_concept
estimated_steps: 6
placeholders:
  - name: CREATOR
    description: Name or GitHub/HuggingFace username of the creator to investigate
    example: "karpathy"
you_will_get:
  - Full creator profile with portfolio and authority score
  - Collaboration network map
  - Neighborhood analysis of their top projects
  - Web research on their latest activity
  - 1 concept predicting their next move
---

## Steps

1. Use `get_creator_profile` to pull the full profile for '{{CREATOR}}'. Show me their authority score, source count, total traction, average defensibility, and list their top 5 sources by defensibility score. What patterns do you see in what they build?

2. Use `get_creator_network` to see who they collaborate with. Map the network — who are their frequent co-creators? Are they part of a lab, a company, or an independent cluster? How does their authority compare to their collaborators?

3. For their top 3 sources, use `explore_connections` to see the intelligence neighborhood of each. What capability tags keep showing up? What tech stack do they favor? Are their projects in dense or sparse neighborhoods?

4. Use `query_intelligence` to search for the intersection of their most common capability tags. Are there sources in this space that they DIDN'T create? Who else is working on similar things? Identify gaps — areas adjacent to their work where nothing exists yet.

5. Search the web for {{CREATOR}}'s most recent activity — blog posts, tweets, conference talks, new repos, paper preprints. What are they signaling about their direction? Does it align with the gaps you found in step 4?

6. Create a concept using `submit_concept` that represents what {{CREATOR}} is most likely to build next — or what you think they SHOULD build based on the gap analysis. Use the entity IDs from their top 3 sources as `parent_ids`. In the reasoning field, explain why this prediction is informed by their portfolio patterns, their network, and the gaps in their neighborhood.

## Tips

- This workflow is great for due diligence on open-source contributors you're considering hiring or funding.
- The network analysis (step 2) often reveals institutional affiliations that aren't obvious from the code alone.
- If the creator has sources across multiple corpora (github + arxiv), that usually indicates they're a researcher-practitioner — their next move is more likely to be novel.
