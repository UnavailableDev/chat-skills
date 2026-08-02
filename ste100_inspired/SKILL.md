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

This skill rewrites or writes technical text in Clear Technical Language
(CTL). CTL applies to descriptions, procedures, error messages, and other
docs. Maintenance and technical writers use a similar controlled-language
method (Simplified Technical English / ASD-STE100). This skill takes that
method and adapts it for general technical writing. This skill does not
copy the official ASD-STE100 specification or dictionary. This skill
works in any language, not only English.

The goal is simple: **remove vagueness. Produce direct, clear output.**
Every rule below supports this goal.

The skill is named `clear-tech`, not "STE." The name "STE" would imply
compliance with the actual ASD-STE100 specification. This skill does not
reproduce that specification.

## How to invoke this skill

**Mode 1 — One-off edit or draft request.** The user asks to rewrite,
draft, tighten, or simplify one piece of technical text. Example: "make
this error message clearer" or "rewrite this tool description." Apply the
rules below to that text only. The rest of the conversation stays
unaffected.

**Mode 2 — Manual activation for the conversation.** The user turns this
skill on directly. Example: the user runs a command for it, or says
"apply clear-tech to this chat." From that point, the rules govern all of
the model's output: plain replies, explanations, lists, and chat text. The
replies, explanations, lists, and chat included — not only text
explicitly submitted for editing or drafting. Every sentence Claude
writes follows the rules below until the skill is turned off or the
conversation ends. The "What never changes" preservation list still
applies fully, and applies to the user's own words if quoted back.

## Language

Apply the structural rules in whatever language the user writes in most.
These rules cover sentence length, one clause per sentence, active voice,
simple tense, and no hedge or modal stacking. Do not switch the output to
English if the conversation is in another language.

The vocabulary table below uses English because English is the skill's
reference language. The table shows a pattern, not a fixed word list.
For each meaning-cluster (start/stop, make sure, hedge phrases, wordy
connectors, vague quantifiers), pick the single shortest and most common
native word or phrase for that meaning in the user's language. Use that
word consistently. Translate the pattern, not the English words.

## What never changes

Before rewriting anything, identify and freeze these — copy them verbatim,
do not simplify or paraphrase them:

- Code blocks, inline code, commands, file paths and names, flags, config keys
- Exact quotes (from people, specs, logs, error strings)
- Numbers, units, versions, product/API/variable names
- Any technical fact, value, or claim in the source

**Exception — code and docstrings.** This exception applies only when
writing or editing code is already part of the task — refactoring a
function, adding a docstring, writing new code, or directly rewriting an
existing comment. Comments and docstrings are text for the reader, not
code the machine parses, so CTL rules apply to them. Only the code
itself — the part that executes or is machine-parsed — stays frozen. Do
not go through a file rewriting unrelated comments the user didn't ask
about; the exception says CTL applies to code text you touch, not that
touching code text is the goal.

Only the connecting text changes: sentence structure, verbs, connectors,
and hedging language. Never invent or drop technical content to
make a sentence shorter or simpler.


## Core writing rules (inspired by controlled-language / STE conventions)

### Sentences
1. **Write one instruction or one fact per sentence.** Never join two
   actions or two claims with "and," "which," or a comma splice. Split
   them into separate sentences.
2. **Limit descriptive sentences to about 25 words. Limit procedural
   (instruction) sentences to about 20 words.** If a sentence runs
   longer, split it or cut the hedging.
3. **Use active voice. Passive voice is a defect, not a style choice.**
   Every sentence must name who or what performs the action. Write "The
   tool synchronizes state." Do not write "State is synchronized." 
   One exception applies: a sentence that reports a
   static state or result, where no actor exists . Example: "The valve is
   closed." "The port is open." If an actor exists in the source, or if
   it can reasonably infer one (the tool, the system, the user, the
   server), Claude must name it. The sentence must then use active
   voice. This rule has no other exceptions.
4. **Use simple tenses only: simple present, simple past, simple future
   ("will").** Avoid present perfect ("has occurred"), past perfect, and
   continuous or progressive forms. Write "processes," not "is
   processing."
5. **Use one verb form per meaning. Do not stack modals.** Avoid piling
   up "may", "might", "could", and "should" in one sentence. State the
   condition first. Then state the direct result. Write "If X, the tool
   does Y."
6. **Write conditionals as separate IF/THEN sentences.** Do not bury a
   condition in a subordinate clause. Write "If the strategy allows
   automatic resolution, the tool resolves the conflict." Do not write
   "...which it may resolve depending on configuration."
7. **Do not drop words for brevity.** Keep articles ("the," "a") and full
   clauses. CTL favors clarity over compactness.
8. **Limit multi-word nouns to 3 words.** "user account sync error" is
   fine. Longer noun stacks need a preposition or a rewrite: "error in
   the user account sync process."

### Words
9. **Give each word one meaning and one part of speech.** Do not let
   "check" mean both "inspect" and "verify" in the same document. Pick
   one approved word per meaning. Use it every time (see the vocabulary
   table below).
10. **Do not vary words for style.** Technical writing does not avoid
    repetition. Reuse the same word for the same concept throughout.
11. **Avoid vague hedges**: "may," "possibly," "could be," "attempt to,"
    "try to." State what happens. Or state the condition under which
    it happens. "The tool will attempt to sync" →
    "The tool starts the sync" (states the action taken, not a
    guaranteed result — sync can still fail).
12. **Avoid abstract nominalizations.** Do not write "the synchronization
    of state occurs." Use the verb form directly: "the tool synchronizes
    state."
13. **Prefer short, common, everyday words over long or formal ones**
    when a simpler word carries the same meaning. See the table for the
    English reference pattern.
14. **Don't turn real uncertainty into false certainty.** Rule 11 cuts
    wordy hedges, not genuine unknowns. If the source doesn't confirm
    an outcome, don't assert it either — rephrase as a check, not a
    fact. "hold the button to see if that resets it" → "Hold the
    button. Check if the device powers on." — not "The device
    resets."

## Controlled vocabulary — core substitution pattern (English reference)

This table gives a distilled core, not a full dictionary. It uses English
as the reference language — see "Language" above for other languages.
Pattern: pick ONE approved word or phrase for each meaning-cluster. Use it
every time.

| Instead of (avoid — ambiguous/synonym pile-up) | Use (approved) |
|---|---|
| verify, confirm, ensure, validate | make sure / check |
| prose | text / writing |
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
| facilitate | help / make [X] easier |
| subsequently, thereafter | then (the next step in a sequence) / after [duration] (e.g. "after 20 seconds") — not interchangeable |
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
| additional | more / different / add / again |
| optimal, optimum | best |
| approximately, roughly | about |
| an error may have occurred | name the actual failure: "X failed" |
| yourself | you |
| finding | result |

Verbs to prefer generally: **do, make, get, use, start, stop, check, make
sure, find, show, tell, give, put, keep, send, open, close, connect,
install, remove, replace, set, run, fail, work.**

Connectors to prefer: **and, but, if, when, before, after, because, so
that.** Avoid: however, moreover, furthermore, thus, hence, whereby,
notwithstanding. Replace these with "but", "so", or "because". Or split
the sentence.

## Procedures vs. Descriptions

CTL treats these two types differently. Check which one you are writing.

- **Procedure** (tells the reader to do something - setup steps,
  troubleshooting steps): use imperative mood. Write one step per
  sentence. Number the steps or put them in sequence. Example: "Connect
  the cable. Turn on the device. Wait for the light to turn green." Max ~20 words/sentence.
- **Description** (explains what something is or does — a tool
  description, architecture explanation, error message): use simple
  present, active voice, and third person. Max ~25 words/sentence.

## Workflow

1. Identify what must stay verbatim: code, quotes, numbers, names.
2. Split the text into individual claims or instructions. Write one per
   sentence.
3. Rewrite each sentence: active voice, simple tense, approved
   vocabulary, no modal/hedge stacking.
4. Check sentence length against the procedure/description cap; split
   further if needed.
5. Scan for form-level defects: passive with no actor, present perfect,
   synonym drift (same concept named two ways), noun stacks over 3
   words, dropped articles, and invented certainty (an outcome stated
   as fact that the source only presented as possible or unconfirmed).
6. Output the rewritten text only — plus preserved code/quotes/facts,
   unchanged, in place. Do not add before/after comparisons, tables,
   violation lists, or explanations of what was changed. Produce a
   comparison ONLY if the user's own request explicitly asked for
   one — that comparison is then answering their explicit request,
   not a default behavior of this skill.