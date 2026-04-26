---
title: Stack Audit
description: Evaluate a technology stack's defensibility, find weak links, discover better alternatives, and produce a migration plan
difficulty: beginner
tools_required:
  - score_stack
  - explain_score
  - find_alternatives
  - compose_molecules
estimated_steps: 5
placeholders:
  - name: STACK
    description: Comma-separated list of technologies, libraries, or frameworks to audit
    example: "langchain, chromadb, fastapi, openai"
you_will_get:
  - Weakest-link defensibility analysis of your stack
  - Full scoring reasoning for the weakest components
  - Alternative candidates for each weak link
  - 1 comparison composition with adopt/watch/skip verdicts
---

## Steps

1. Use `score_stack` with the following dependencies: {{STACK}}. Show me the full results — overall stack score, individual scores, and identify which components are the weakest links. Flag anything with a defensibility score below 5.

2. For each component that scored below 6, use `explain_score` to understand why. Is it a frontier risk problem (big labs will replace it)? A moat problem (no differentiation)? A traction problem (might not survive)? Summarize the real risks in plain language.

3. For each weak component, use `find_alternatives` to discover potential replacements. Show the top 3 alternatives for each, with their defensibility scores and how they compare. Note if any alternatives are sleepers (high score, low traction) — those might be your best bets.

4. Search the web for the latest on each weak component and its top alternatives. Are any of the alternatives gaining momentum? Has the weak component announced improvements? Are there migration guides available? This context matters for the final recommendation.

5. Use `compose_molecules` in 'compare' mode with the entity IDs of your current weak components AND their best alternatives. Add `user_context`: 'Compare my current stack components against their alternatives. For each pair, give me an adopt/watch/skip verdict with a concrete migration difficulty estimate. Factor in ecosystem maturity, not just defensibility scores.' Save the composition.

## Tips

- Start with your actual production stack — the results are more actionable when they're real.
- A low defensibility score doesn't always mean "replace immediately" — if the component works and has high traction, the ecosystem support matters.
- Pay attention to the `find_alternatives` results that share capability tags with your weak component but score higher — those are the most drop-in replaceable.
