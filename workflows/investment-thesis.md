---
title: Investment Thesis
description: Generate a data-backed investment thesis for a technology area — market dynamics, defensible players, frontier risks, and a buy/watch/pass verdict
difficulty: advanced
tools_required:
  - get_intelligence_brief
  - analyze_competitive_landscape
  - find_defensible_clusters
  - get_creator_network
  - compose_molecules
estimated_steps: 7
placeholders:
  - name: THESIS_AREA
    description: The technology area or market to evaluate
    example: "vector databases"
you_will_get:
  - Intelligence brief with sleepers, trending, and breakouts
  - Competitive landscape ranked by velocity
  - Defensible cluster map showing who has real moats
  - Creator network analysis of top builders
  - Web research on funding and market signals
  - 1 research composition with buy/watch/pass verdicts
---

## Steps

1. Use `get_intelligence_brief` with topic '{{THESIS_AREA}}' and period '30d'. Show me the full brief — sleepers, trending sources, new entrants, and breakouts. What's the overall narrative? Is this space heating up, cooling down, or consolidating?

2. Use `analyze_competitive_landscape` for '{{THESIS_AREA}}'. Rank the top 15 players by velocity. Who's accelerating? Who's decelerating? Identify the velocity leaders and whether their momentum is sustainable or a spike.

3. Use `find_defensible_clusters` to map the defensibility landscape. Where are the real moats? Are there clusters of high-defensibility sources that share capabilities, or is defensibility scattered? Identify the top 3 most defensible entities and explain what makes them hard to replicate.

4. For the top 3 most defensible entities, use `get_creator_network` for each creator. Are these solo builders or teams? Are they affiliated with companies that might commercialize this? Is there institutional backing? Map the human capital landscape.

5. Search the web for recent funding rounds, acquisitions, partnerships, and product launches in the {{THESIS_AREA}} space. Cross-reference with your corpus findings — are the funded companies the same ones with high defensibility? Or is money flowing to the wrong places? This is where alpha lives.

6. Analyze frontier risk: which of these players are most vulnerable to being obsoleted by a major lab (OpenAI, Google, Anthropic, Meta)? Use the threat profiles from the brief and landscape analysis. Flag anything where a frontier lab has announced or shipped something adjacent.

7. Use `compose_molecules` in 'research' mode with the entity IDs of the top 5 most defensible sources. Add `user_context`: 'Write an investment thesis for the {{THESIS_AREA}} space. Include: market dynamics (growing/consolidating/fragmenting), the 3 most defensible bets and why, the top risks (especially frontier lab obsolescence), and a buy/watch/pass verdict for each of the top 5 entities. Factor in creator networks, velocity trends, and the funding landscape from web research.' Save it.

## Tips

- Run this quarterly on spaces you're tracking — the composition history becomes a time-series of market evolution.
- The gap between "funded" and "defensible" is the most interesting finding. High funding + low defensibility = potential short. High defensibility + no funding = potential opportunity.
- Frontier risk is the most important filter. A defensibility score of 9 means nothing if Google ships the same thing for free next quarter.
