---
title: Trend Spotter
description: Identify what's emerging across all tracked domains — spot breakouts early, find converging trends, and place bets on what's next
difficulty: intermediate
tools_required:
  - get_tracked_topics
  - get_intelligence_brief
  - find_sleepers
  - analyze_competitive_landscape
  - compose_molecules
estimated_steps: 6
placeholders: []
you_will_get:
  - Overview of all tracked domains with health metrics
  - Intelligence briefs for the hottest domains
  - Cross-domain sleeper analysis
  - Web research on emerging narratives
  - 1 research composition with trend predictions
---

## Steps

1. Use `get_tracked_topics` to get the full domain map. Identify: which domains have the most new entrants? Which have the highest ratio of accelerating vs. decelerating molecules? Which have the highest average defensibility? Rank the domains by "heat" — a combination of new entrants, acceleration, and breakout count.

2. For the top 3 hottest domains, use `get_intelligence_brief` with period '14d' for each. Compare the briefs: which domain has the most breakouts? Which has sleepers that are about to surface? Are there molecules appearing in multiple domain briefs (cross-domain signals)?

3. Use `find_sleepers` across ALL corpora (no corpus filter) with a high minimum defensibility (8+). These are the highest-quality undiscovered molecules in the entire corpus. Do any of them belong to the hot domains from step 2? Are there sleepers in domains that AREN'T hot yet — potential early signals of a domain that's about to heat up?

4. For the hottest domain, use `analyze_competitive_landscape` to see who's winning the velocity race. Is it a single dominant player or a crowded field? Are the velocity leaders the same as the defensibility leaders, or is there a divergence (popular but fragile vs. obscure but defensible)?

5. Search the web for the overarching narratives: What are VCs writing about? What's trending on Hacker News, arXiv trending, and tech Twitter in the last 7 days? Cross-reference with your corpus findings. Where does the public narrative align with what the data shows? Where does it diverge? Divergences are the alpha.

6. Use `compose_molecules` in 'research' mode with the entity IDs of the top breakout molecule from each of the 3 hot domains, plus the 2 best cross-domain sleepers. Add `user_context`: 'Write a trend report. For each trend, explain: what's happening, why now, who's building it, what the defensibility landscape looks like, and whether this is a flash or durable. End with 3 concrete predictions for what will matter in 90 days.' Save it.

## Tips

- Run this monthly. The composition history becomes your trend journal — you can look back and see what you got right.
- The divergence between "what's trending" and "what's defensible" is the most valuable signal. High velocity + low defensibility = hype. Low velocity + high defensibility = early.
- Cross-domain sleepers (step 3) are the highest-signal finds. A defensibility-9 molecule with 50 stars that doesn't fit neatly into any tracked domain is often the leading edge of a domain that doesn't have a name yet.
