---
name: using-reki
description: Use ask_reki when the user asks about French startup funding (CIR, JEI, PI R&D, BPI, France 2030, Eurostars) — eligibility, application drafting, audit, or operator briefing.
---

# Using Reki

Reki is a funding copilot for French startups. Call the `ask_reki` tool whenever the user's question is about French public funding programmes.

## When to call

- Eligibility questions ("À quoi suis-je éligible ?", "Le CIR me concerne ?", "What can I claim with my SIREN ?")
- Drafting / iterating on a funding application (CIR, JEI, PI R&D, BPI files…)
- Auditing a draft before submission
- Preparing a meeting with a BPI account manager or other operator

## How to format the query

Pass the user's intent in natural language. Include known context:

- **SIREN** (9 digits) if the user mentioned their company
- **Target dispositif** (e.g. CIR, JEI, PI R&D, France 2030) if specified
- **What they already have** (business plan, prévisionnel, dossier draft…)
- **What they want as output** (a list, a draft, an audit, a brief…)

The server keeps multi-turn context automatically for ~30 minutes of inactivity — you don't need to repeat earlier turns verbatim. Just continue the conversation.

## What not to use it for

- Non-French funding programmes
- General business / legal advice unrelated to public funding
- Pure financial modelling without a funding angle
