---
title: Model Selection
description: Compare foundation models for a specific use case — pricing, benchmarks, capability risks, and a concrete recommendation
difficulty: beginner
tools_required:
  - check_model_pricing
  - compare_foundation_models
  - get_domination_risk
estimated_steps: 5
placeholders:
  - name: USE_CASE
    description: What you're building and what the model needs to do
    example: "RAG pipeline for legal documents — needs structured output, long context, low cost"
you_will_get:
  - Pricing comparison across providers
  - Side-by-side benchmark comparison of candidates
  - Capability domination risk analysis
  - Web research on latest model updates
  - A concrete recommendation with reasoning
---

## Steps

1. Based on the use case '{{USE_CASE}}', identify which capabilities matter most (e.g., structured output, vision, tool use, long context, code execution). Use `check_model_pricing` to see the full pricing landscape. Filter to models that support the required capabilities. Show me the top 10 candidates sorted by input price, with their capability flags.

2. From the pricing results, pick the top 4-5 candidates that fit the requirements and budget. Use `compare_foundation_models` to get a side-by-side comparison — benchmarks, pricing, capabilities. Identify where the models meaningfully differ vs. where they're interchangeable.

3. For each capability that matters for this use case, use `get_domination_risk` to check the domination landscape. Is this capability commoditized (everyone's good at it, pick the cheapest), differentiated (meaningful quality gaps), or moated (one provider dominates)? This tells you where switching cost is low and where it's high.

4. Search the web for the latest announcements, benchmarks, and user reports for each candidate model. Are any of them about to be deprecated? Has a new version been announced? Are there known reliability or latency issues in production? Look for what the benchmarks don't capture.

5. Synthesize everything into a recommendation. For the use case '{{USE_CASE}}', rank the candidates and recommend a primary model and a fallback. Explain: why this model wins for this use case, what the cost will look like at scale, what the switching risk is (based on domination analysis), and when you should re-evaluate (e.g., "revisit when GPT-5 launches" or "this capability is commoditized, just use the cheapest").

## Tips

- Don't just pick the cheapest model. If a capability is moated (one provider dominates), the switching cost of going cheap now and migrating later might exceed the savings.
- The domination risk analysis is the most underused signal. If a capability is "commoditized," you have leverage — negotiate or switch freely. If it's "moated," you're locked in — factor that into your architecture.
- Run this workflow again whenever a major model launch happens. The landscape shifts fast.
