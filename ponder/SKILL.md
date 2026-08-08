---
name: ponder
description: Handles the /ponder command. When a paragraph in the user's message is prefixed with /ponder, that paragraph contains a claim, fact, or assumption the user is personally unsure of and wants checked — not just accepted at face value. Always use this skill whenever a message contains "/ponder", regardless of what else is in the prompt or what other skills are also active. Trigger on the literal token /ponder anywhere in the message, even mid-message or on just one paragraph among several.
version: 0.2.0
---

# Ponder

## What /ponder means

The user marks a paragraph with `/ponder` to flag: "I'm not fully confident this is correct — check it rather than just running with it."

`/ponder` is not a standalone command with its own response format. It's an inline annotation inside a larger prompt. The rest of the message should be handled normally (following whatever task, format, or other skills the prompt calls for). The ponder-marked paragraph just gets extra scrutiny along the way.

## What to do

1. **Identify the claims.** Read the /ponder-marked paragraph and pull out the factual assertions, assumptions, or claims it makes (there may be more than one).

2. **Use established context first.** If the conversation already establishes specific environment, version, tool, or constraint info, check the claim against *that* context rather than answering generically. Don't give an answer that's technically true in general but wrong or irrelevant for the setup the user actually has.

3. **Check them.**
   - Default toward web search rather than away from it. Only skip search for facts that are genuinely stable and unlikely to have changed (e.g. historical dates, settled science, fixed definitions). If a claim *feels* well-known but actually depends on a version, configuration, timeframe, or specific context — the kind of claim that's easy to over-trust because it "sounds like something I'd know" — search it rather than trusting recall.
   - If a claim is a matter of opinion, prediction, or judgment call rather than fact, don't search — note that it's not a "verify against a source" kind of claim and say so rather than forcing a true/false verdict.

4. **Format the response.** Fold the finding into the response as an inline or block quote (use inline for a short aside, a block quote if it runs more than one sentence), and always start that quote with a glyph indicating the verdict:
   - `✓` correct
   - `✗` wrong
   - `!` partial / mixed / shaky
   - `?` opinion, prediction, or otherwise unverifiable
   - `≠` contradicts something established earlier in the conversation
   - Prepend `🔍` before the verdict glyph whenever web search was used to check the claim (e.g. `🔍✗ ...`). Omit it when the claim was evaluated from existing knowledge without searching.

   Within that quote:
   - If correct: briefly confirm it's accurate — no need to belabor it.
   - If wrong or shaky: flag it clearly and correct it, then continue using the corrected version for the rest of the task. Don't silently swap it in — call out that this is a change from what the user wrote.
   - If mixed/partially right: say specifically what holds up and what doesn't.
   - If unverifiable or a judgment call: say so plainly instead of inventing false certainty.

5. **Keep proportion.** How much space this gets depends on the surrounding prompt, not a fixed template — a quick aside in a longer answer, or the main focus if the /ponder paragraph *is* most of the message. Don't let fact-checking overwhelm the rest of the task the user actually asked for. The quote itself should usually be one to a few sentences — if the explanation is running long, that's a sign to trim it, not to expand the quote into a full section.

## Contradictions with earlier context

Sometimes the /ponder-marked paragraph doesn't just contain a checkable fact — it contradicts something the user themselves said or requested earlier in the conversation (not itself marked with /ponder). Treat this as its own case, separate from fact-checking:

- Point out the contradiction explicitly rather than quietly picking one version or the other, using the `≠` quote format described above. Name both what was said before and what the /ponder paragraph now says.
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
- If competitors exist, flag that clearly using the quote format, e.g.:
  > 🔍✗ A few companies already ship on-device AI translation earbuds, so "first ever" doesn't hold up — worth reframing as "one of the first."
- Write the pitch without the false "first ever" claim (or reframe it accurately), and still deliver the punchy <100-word pitch as asked — the fact-check informs it, it doesn't replace the task.

## Example 2 (context-awareness + search)

User message (earlier in the conversation, a specific Linux distro was already established):
> I want to keep compatibility and seamless integration with KDE. /ponder therefore keep SDDM as the display manager? Walk me through installing GNOME to try it out for the first time.

Handling:
- Apply the context rule: an environment detail (the distro) was already established, so the claim is checked against *that* specific setup rather than answered in the abstract.
- Apply the search-bias rule: is a technical/system-configuration claim (display manager behavior, package dependencies) — the kind that "feels known" but is actually version/config-dependent, so it gets searched rather than answered from memory.
- Respond concisely, e.g.:
  > 🔍✓ Keeping SDDM is right for your setup — it's DE-agnostic, and on [distro] installing the GNOME package group won't replace it unless you explicitly switch.
- Continue directly into the GNOME installation walkthrough — the confirmation shouldn't turn into a multi-paragraph digression on display manager internals.