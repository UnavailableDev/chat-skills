---
name: clear-tech
description: >-
  Rewrite or draft technical text (manuals, procedures, tool/API
  descriptions, error messages, troubleshooting guides, code comments) in
  a Clear Technical Language (CTL) style: short sentences, one
  instruction per sentence, active voice, simple tenses, and a
  controlled vocabulary that removes vagueness and hedging. Inspired by
  Simplified Technical English / ASD-STE100 but not a reproduction of
  that standard, and not English-only — apply the same discipline in
  whatever language the user is writing in. Trigger on requests for
  "simplified technical English," "STE," "ASD-STE100," "clear technical
  language," or plain/direct technical writing, and proactively for
  engineering/coding/troubleshooting content needing clarity. Two modes:
  (1) one-off rewrite of specific text — scoped to that text; (2) manual
  activation for the conversation — applies to ALL model output until
  turned off. Preserves code, quotes, and facts exactly. Output is the
  rewritten text only, no tables or comparisons unless asked.
---

# Clear Tech — Clear Technical Language for Technical Content

Rewrite or compose technical prose (descriptions, procedures, error messages,
docs) in a Clear Technical Language (CTL) style. This skill is inspired by
the controlled-language discipline used in technical/maintenance writing
(Simplified Technical English / ASD-STE100) — one instruction per sentence,
active voice, plain consistent words — but it is a practical distillation
for general technical writing, not a reproduction of any official
specification or dictionary, and it is not tied to English.

The goal is a single thing: **remove vagueness and produce direct, clear
output.** Every rule below serves that goal.

This skill is named `clear-tech`. It was not called "STE" because that
name implies compliance with the actual ASD-STE100 specification, which
this skill does not reproduce.

## How this skill is invoked

**Mode 1 — One-off edit/draft request.** The user asks to rewrite, draft,
tighten, or simplify a specific piece of technical text ("make this error
message clearer," "rewrite this tool description"). Apply the rules below
to that text only. The rest of the conversation is unaffected.

**Mode 2 — Manual activation for the conversation.** The user turns this
skill on directly (e.g. by running a command for it, or saying "apply
clear-tech to this chat"), rather than asking for one specific rewrite.
From that point on, the rules govern the model's entire output — plain
replies, explanations, lists, and chat included — not only text
explicitly submitted for editing or drafting. Every sentence Claude
writes follows the rules below until the skill is turned off or the
conversation ends. The "What never changes" preservation list still
applies fully, and applies to the user's own words if quoted back.

## Language

Apply the structural rules (sentence length, one-clause-per-sentence,
active voice, simple tense, no hedge/modal stacking, no synonym drift) in
whatever language the user is dominantly writing in — do not switch the
output to English if the conversation isn't in English.

The vocabulary table below is written in English because English is the
skill's reference language, but it encodes a pattern, not a fixed word
list: for each meaning-cluster (start/stop, make sure, hedge phrases,
wordy connectors, vague quantifiers), pick the single shortest, most
common native word or phrase for that meaning in the user's language, and
use it consistently. Translate the pattern, not the English words
themselves.

## What never changes

Before rewriting anything, identify and freeze these — copy them verbatim,
do not simplify or paraphrase them:

- Code blocks, inline code, commands, file paths, flags, config keys
- Exact quotes (from people, specs, logs, error strings)
- Numbers, units, versions, product/API/variable names
- Any technical fact, value, or claim in the source

Only the connecting prose — sentence structure, verbs, connectors,
hedging language — gets constrained. Never invent or drop technical
content to make a sentence shorter or simpler.

## Core writing rules (inspired by controlled-language / STE conventions)

### Sentences
1. **One instruction or one fact per sentence.** Never join two actions
   or two claims with "and," "which," or a comma splice. Split them.
2. **Descriptive sentences: max ~25 words. Procedural (instruction)
   sentences: max ~20 words.** If a sentence runs longer, split it or cut
   hedging.
3. **Active voice is mandatory. Passive voice is a defect, not a
   style choice.** Every sentence must name who or what performs the
   action: "The tool synchronizes state," never "State is
   synchronized." Treat every passive construction as a rule
   violation to be fixed by finding or naming the actor. The ONLY
   exception: a sentence that reports a static state or result rather
   than an action, where no actor exists to name ("The valve is
   closed." "The port is open."). If an actor exists anywhere in the
   source or can reasonably be inferred (the tool, the system, the
   user, the server), it must be named and the sentence must be
   active — this is not optional.
4. **Simple tenses only: simple present, simple past, simple future
   ("will").** Avoid present perfect ("has occurred"), past perfect,
   and continuous/progressive forms ("is processing" → "processes").
5. **One verb form per meaning, no modal stacking.** Avoid piling up
   "may," "might," "could," "should" in one sentence. State the
   condition, then state the direct result: "If X, the tool does Y."
6. **Write conditionals as separate IF/THEN sentences**, not buried
   subordinate clauses. "If the strategy allows automatic resolution,
   the tool resolves the conflict" — not "...which it may resolve
   depending on configuration."
7. **Do not drop words for brevity.** Keep articles ("the," "a") and
   full clauses — STE favors clarity over compactness.
8. **Multi-word nouns: max 3 words strung together.** "user account
   sync error" is fine; longer noun stacks need a preposition or a
   rewrite ("error in the user account sync process").

### Words
9. **One word, one meaning, one part of speech.** Don't let "check" mean
   both "inspect" and "verify" in the same doc — pick one approved word
   per meaning and use it consistently (see vocabulary table below).
10. **No synonym variation for style.** Technical writing is not the
    place to avoid repetition — reuse the same word for the same
    concept throughout.
11. **Avoid vague hedges**: "may," "possibly," "could be," "attempt to,"
    "try to." State what happens, or state the condition under which
    it happens. "The tool will attempt to sync" → "The tool syncs."
12. **Avoid abstract nominalizations** ("the synchronization of state
    occurs") — use the verb form directly ("the tool synchronizes
    state").
13. **Prefer short, common, everyday words over long or formal ones**
    when a simpler word carries the same meaning (see table for the
    English reference pattern).
14. **Don't turn real uncertainty into false certainty.** Rule 11 cuts
    wordy hedges, not genuine unknowns. If the source doesn't confirm
    an outcome, don't assert it either — rephrase as a check, not a
    fact. "hold the button to see if that resets it" → "Hold the
    button. Check if the device powers on." — not "The device
    resets."

## Controlled vocabulary — core substitution pattern (English reference)

This is a distilled core, not a full dictionary, and it's written in
English as the reference language — see "Language" above for applying it
in other languages. Pattern: pick ONE approved word/phrase for each
meaning-cluster and use it every time.

| Instead of (avoid — ambiguous/synonym pile-up) | Use (approved) |
|---|---|
| verify, confirm, ensure, validate | make sure / check |
| commence, initiate, begin (as verb start) | start |
| terminate, halt, discontinue | stop |
| utilize, leverage, employ | use |
| attempt, endeavor, try to | (state the action directly; drop the hedge) |
| assist, aid | help |
| obtain, acquire, procure | get |
| ascertain, determine (as "find out") | find |
| modify, alter | change |
| eliminate, remove (context: delete) | remove |
| indicate, denote, signify | show |
| facilitate | help / make possible (rewrite) |
| subsequently, thereafter | after that / then |
| approximately | about |
| sufficient | enough |
| numerous | many |
| in order to | to |
| due to the fact that | because |
| in the event that | if |
| prior to | before |
| in conjunction with | with |
| is able to / has the ability to | can |
| is required to / it is necessary to | must |
| it is possible that / there is a possibility | may (only for real possibility, one hedge, not stacked) |
| a large number of | many |
| at this point in time | now |
| for the purpose of | for / to |
| implement | do / make (be specific: "add," "build," "install") |
| perform, execute (an action) | do |
| occurred, has occurred | happened (simple past) |
| will be able to | can (future context: will) |
| in the majority of cases | usually |
| additional | more / another |
| optimal, optimum | best |
| approximately, roughly | about |
| an error may have occurred | name the actual failure: "X failed" |

Verbs to prefer generally: **do, make, get, use, start, stop, check, make
sure, find, show, tell, give, put, keep, send, open, close, connect,
install, remove, replace, set, run, fail, work.**

Connectors to prefer: **and, but, if, when, before, after, because, so
that.** Avoid: however, moreover, furthermore, thus, hence, whereby,
notwithstanding — replace with "but," "so," "because," or split the
sentence.

## Procedures vs. Descriptions

CTL treats these differently — check which one you're writing:

- **Procedure** (tells the reader to do something, e.g. setup steps,
  troubleshooting steps): use imperative mood, one step per sentence,
  numbered or sequential. "Connect the cable. Turn on the device.
  Wait for the light to turn green." Max ~20 words/sentence.
- **Description** (explains what something is or does, e.g. a tool
  description, architecture explanation, error message): use simple
  present, active voice, third person. Max ~25 words/sentence.

## Workflow

1. Identify what must stay verbatim (code, quotes, numbers, names).
2. Split the text into individual claims/instructions — one per
   sentence.
3. Rewrite each sentence: active voice, simple tense, approved
   vocabulary, no modal/hedge stacking.
4. Check sentence length against the procedure/description cap; split
   further if needed.
5. Scan for banned patterns: passive with no actor, present perfect,
   synonym drift (same concept named two ways), noun stacks over 3
   words, dropped articles, and invented certainty (an outcome stated
   as fact that the source only presented as possible or unconfirmed).
6. Output the rewritten text only — plus preserved code/quotes/facts,
   unchanged, in place. Do not add before/after comparisons, tables,
   violation lists, or explanations of what was changed. Produce a
   comparison ONLY if the user's own request explicitly asked for
   one — that comparison is then answering their explicit request,
   not a default behavior of this skill.