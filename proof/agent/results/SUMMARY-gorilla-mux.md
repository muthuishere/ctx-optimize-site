# Headless benchmark — gorilla-mux

Model: `openai/gpt-4o-mini` · via OpenRouter · same model, same questions, one freshly-cloned repo.
Arms: **a** shell-only · **b** ctx-optimize store first · **c** graphify store first.
Tokens and cost are OpenRouter's own accounting (`usage.include=true`), not estimates. Deltas are vs arm a.

| question | arm | wall s | tokens | cost | steps |
|---|---|--:|--:|--:|--:|
| q1 | a shell | 2.85 | 2851 | $0.0003 | 2 |
| q1 | b ctx-optimize | 1.93 | 2823 | $0.0003 | 1 |
| q1 | c graphify | 1.81 | 2446 | $0.0004 | 1 |
| q2 | a shell | 3.48 | 4005 | $0.0007 | 4 |
| q2 | b ctx-optimize | 2.28 | 2840 | $0.0005 | 1 |
| q2 | c graphify | 3.95 | 4707 | $0.0006 | 2 |
| q3 | a shell | 3.93 | 4082 | $0.0007 | 4 |
| q3 | b ctx-optimize | 2.74 | 2963 | $0.0003 | 1 |
| q3 | c graphify | 3.13 | 2559 | $0.0004 | 1 |
| q4 | a shell | 2.3 | 698 | $0.0001 | 2 |
| q4 | b ctx-optimize | 1.62 | 987 | $0.0002 | 1 |
| q4 | c graphify | 6.39 | 8630 | $0.0011 | 4 |

## Totals (4 questions)

| metric | a shell | b ctx-optimize | c graphify | b vs a | c vs a |
|---|--:|--:|--:|--:|--:|
| wall time | 12.6s | 8.6s | 15.3s | **−32%** | **+22%** |
| tokens | 11636 | 9613 | 18342 | **−17%** | **+58%** |
| cost | $0.0018 | $0.0013 | $0.0025 | **−31%** | **+39%** |
| steps | 12 | 4 | 8 | **−67%** | **−33%** |
