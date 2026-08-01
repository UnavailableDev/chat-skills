---
name: ponder
description: Handles the /ponder command. When a paragraph in the user's message is prefixed with /ponder, that paragraph contains a claim, fact, or assumption the user is personally unsure of and wants checked — not just accepted at face value. Always use this skill whenever a message contains "/ponder", regardless of what else is in the prompt or what other skills are also active. Trigger on the literal token /ponder anywhere in the message, even mid-message or on just one paragraph among several.
---

# Ponder

## What /ponder means

The user marks a paragraph with `/ponder` to flag: "I'm not fully confident this is correct — check it rather than just running with it."

`/ponder` is not a standalone command with its own response format. It's an inline annotation inside a larger prompt. The rest of the message should be handled normally (following whatever task, format, or other skills the prompt calls for). The ponder-marked paragraph just gets extra scrutiny along the way.

## What to do

1. **Identify the claims.** Read the /ponder-marked paragraph and pull out the factual assertions, assumptions, or claims it makes (there may be more than one).

2. **Check them.**
   - If a claim is checkable against something Claude already knows confidently, evaluate it directly.
   - If a claim is about current events, specific figures, recent developments, or anything where Claude's knowledge could be stale or thin, use web search to verify before responding.
   - If a claim is a matter of opinion, prediction, or judgment call rather than fact, note that it's not a "verify against a source" kind of claim — say so rather than forcing a true/false verdict.

3. **Flag, don't derail.** Fold the finding into the response naturally rather than writing a separate isolated fact-check section:
   - If correct: briefly confirm it's accurate (a short aside is enough — no need to belabor it) and move on.
   - If wrong or shaky: flag it clearly and correct it, then continue using the corrected version for the rest of the task. Don't silently swap it in — call out that this is a change from what the user wrote.
   - If mixed/partially right: say specifically what holds up and what doesn't.
   - If unverifiable or a judgment call: say so plainly instead of inventing false certainty.

4. **Keep proportion.** How much space this gets depends on the surrounding prompt, not a fixed template — a quick aside in a longer answer, or the main focus if the /ponder paragraph *is* most of the message. Don't let fact-checking overwhelm the rest of the task the user actually asked for.

## Contradictions with earlier context

Sometimes the /ponder-marked paragraph doesn't just contain a checkable fact — it contradicts something the user themselves said or requested earlier in the conversation (not itself marked with /ponder). Treat this as its own case, separate from fact-checking:

- Point out the contradiction explicitly rather than quietly picking one version or the other. Name both what was said before and what the /ponder paragraph now says.
- Don't assume which one is "right." Ask, or make a reasonable working assumption and clearly flag it as an assumption, depending on how much the rest of the task depends on resolving it.
- Then proceed with the task using whichever version makes sense (the clarified one if the user responds, or the most recently stated one with a flagged assumption if not), rather than stalling entirely.

This is different from a false factual claim: a contradiction isn't necessarily "wrong," it may just mean the user changed their mind, misremembered, or is testing something — so the tone should be clarifying, not corrective.

## Example

User message:
> Can you help me write a short pitch for my startup?
>
> /ponder We're the first company doing on-device AI for translation earbuds — nobody else has done this before.
>
> It should be punchy, under 100 words, aimed at investors.

Handling:
- Treat this as a pitch-writing task (the main request).
- Because of /ponder, check the "first company / nobody else" claim — this is an empirical, checkable claim about the market, so search for existing on-device AI translation earbud products.
- If competitors exist, flag that clearly to the user before or alongside the draft pitch, and write the pitch without the false "first ever" claim (or reframe it accurately, e.g. "one of the first").
- Still deliver the punchy <100-word pitch as asked — the fact-check informs it, it doesn't replace the task.