---
name: asd-ste100
description: "Rewrites ambiguous English into ASD-STE100 style — one meaning per word, active voice, simple tense, short sentences, no phrasal verbs. Strict mode for procedures and error messages, flavored mode for prose. Use when agent output is hard to parse; triggers: simplify this, STE100 rewrite."
version: 0.2.0
---

# Simplified Technical English (ASD-STE100)

ASD-STE100 is a controlled-language standard built by the aerospace and defense industry (ASD, the AeroSpace and Defense Industries Association of Europe) to stop maintenance technicians from misreading English instructions. The standard removes the two biggest sources of misreading: words with more than one meaning, and sentences with more than one possible structure.

This skill borrows that same discipline for a different reader: an **AI agent or a downstream system** that has to parse an English string — an error message, a tool description, an inter-agent instruction, a status report — without a human in the loop to resolve ambiguity. If a maintenance technician can misread "close the valve" as an adjective ("the valve that is near") instead of a command, so can a language model.

## When to Use This Skill

- An agent's output (explanation, instruction, log message, tool description) reads as dense, jargon-heavy, or ambiguous.
- Text will be consumed by another agent, a translation pipeline, or a non-native English reader, and misparsing has a real cost.
- You are writing a prompt, system message, or tool description and want to remove ambiguity before a model ever sees it.
- You want a **before/after** comparison showing exactly which rule was violated and how the rewrite fixes it.

This skill is not for creative or marketing copy — STE is deliberately flat and literal. Do not apply it to text where voice, nuance, or persuasion is the point.

## Two Modes

Pick a mode before rewriting. If the user does not say which, infer from the text type and state the choice in one line.

**Strict** — procedures, error messages, tool and function descriptions, inter-agent instructions, safety text. Anywhere a wrong reading has a cost. Apply every rule below, including the hard length caps and one-word-one-meaning discipline.

**STE-flavored** — READMEs, PR descriptions, changelogs, explanatory prose. Keep sentence length caps, active voice, simple tenses, no phrasal verbs, no nominalization, no marketing adjectives. Drop the one-word-one-meaning lockdown: prose needs some range, and a strict rewrite of prose reads as a personality transplant rather than a clarification.

## Source and Scope

This skill encodes the **rule categories** of ASD-STE100 Issue 9 (Jan 2025): 53 writing rules across 9 sections covering word choice, grammar, sentence structure, and style, backed by a dictionary of ~900 approved words (one meaning, one part of speech each) and ~1,200 words to avoid with suggested replacements. See `references/writing-rules.md` for the full rule summary and citations.

It does **not** reproduce ASD's ~900-word approved dictionary verbatim — that document is ASD's own free-to-download standard, not something to copy wholesale. Instead, this skill applies the *underlying principle* (pick the plainest, most common word available and use it the same way every time) rather than checking against a fixed word list. When exact ASD-approved wording matters (e.g. actual aircraft maintenance documentation), download the official standard at https://www.asd-ste100.org/ and check word-by-word against the real dictionary.

## Core Rewrite Rules

| Rule | Do | Don't |
|---|---|---|
| One word, one meaning | Pick one verb for one action and reuse it every time (e.g. always "check", never mix "check"/"verify"/"confirm" for the same action) | Rotate synonyms for the same idea across a document |
| One part of speech per word | "Apply oil to the valve" (oil = noun) | "Oil the valve" (oil = verb) — if "oil" is only approved as a noun |
| Active voice | "The agent deletes the file." | "The file is deleted (by the agent)." — unless the actor is genuinely unknown or irrelevant |
| Verb, not noun | "Analyze the log." | "Perform an analysis of the log." — a noun form of an action makes the sentence longer and hides who acts |
| No phrasal verbs | "Remove the panel." / "Start the job." | "Take off the panel." / "Spin up the job." — a two-word verb has meanings the parts do not predict |
| Simple tenses only | "We received the report." (simple past) | "We have received the report." (present perfect) |
| One instruction per sentence | "Open the file. Read line 3." | "Open the file and read line 3, then check if it matches." |
| Sentence length | ≤20 words for instructions/procedures, ≤25 words for descriptions | Long compound/subordinate-clause sentences |
| Sentence joins | Split into separate sentences | Stitch clauses together with semicolons (banned) or em dashes |
| Noun clusters | ≤3 words stacked as a noun phrase ("fuel pump valve") | 4+ word noun stacks ("high pressure fuel pump inlet valve assembly") |
| No ellipsis | Keep the subject, verb, and article explicit even if it reads longer | Drop words to save space ("Files not backed up will be lost" → ambiguous which files) |
| Paragraph limits | One topic per paragraph, ≤6 sentences | Multi-topic paragraphs |
| Lists for sequences | Use a numbered or bulleted list for 3+ steps or conditions | Bury a sequence inside one prose sentence |
| Domain terms | Keep necessary technical nouns/verbs, but define them once if not common English (STE allows a project-specific glossary beyond its base dictionary) | Use jargon without ever defining it |

## Scan Checklist

These six habits cover most of what makes machine-written English hard to parse. Each one is mechanical: you can point at the exact word or punctuation mark that breaks the rule, with no judgment call. Scan for all six before you rewrite anything.

1. **Synonym rotation** — the same thing gets several names in one document ("the user", "the customer", "the client"). The reader cannot tell whether they are one thing or three. Fix: pick one name, use it every time.
2. **Hedge stacking** — helper verbs and qualifiers pile up until the sentence asserts nothing ("it is important to note that this may potentially help to improve"). Fix: state the claim, or delete it.
3. **Nominalization** — an action frozen into a noun ("perform an analysis of", "provides assistance to"). Fix: use the verb ("analyze", "helps").
4. **Marketing adjectives** — words that claim quality instead of showing it: seamless, robust, powerful, cutting-edge, effortless, blazing-fast. Fix: delete, or replace with the measurement that earns the claim.
5. **Run-on sentences** — several ideas joined by semicolons or em dashes. Fix: one idea per sentence.
6. **Soft phrasal verbs** — spin up, reach out, dive into, kick off. Fix: use the single plain verb (start, contact, read, begin).

## Process

1. Pick the mode (Strict or STE-flavored) and say which in one line.
2. Read the input text once for meaning — do not start rewriting before you understand what it must still say afterward.
3. Walk it sentence by sentence. Flag every rule violation from the Core Rewrite Rules table and every habit from the Scan Checklist.
4. Rewrite each flagged sentence to fix the violation while preserving the original meaning exactly. If a rewrite would drop necessary precision (a safety condition, a scope qualifier, a number), keep the longer phrasing and flag it instead of silently simplifying.
5. Produce a before/after table (see Output Format).
6. Count the violations you found and report them per 100 words of the original. This is a rough self-check, not a compliance score: it tells you whether the rewrite was worth doing and gives a target to beat on the next pass.
7. If the input already complies, say so — do not force changes onto compliant text.

## Output Format

```markdown
| Rule violated | Original | Simplified |
|---|---|---|
| Present perfect tense | "We have received your request." | "We received your request." |
| Noun cluster (4+ words) | "the agent task queue priority handler" | "the handler that sets task-queue priority" |

Mode: Strict. 7 violations in 140 words (5.0 per 100).
```

Follow the table with a one-line note on anything you deliberately did **not** simplify, and why (usually: simplifying would lose required precision).

## Boundaries

**Will:**
- Rewrite ambiguous or dense English into short, single-meaning, active-voice sentences.
- Flag exactly which rule a sentence violates before rewriting it.
- Preserve every fact, condition, and scope qualifier in the original.
- Suggest a one-line glossary entry for domain terms that must stay.

**Will not:**
- Reproduce ASD's official ~900-word dictionary as if it were memorized verbatim — always treat the official download as the source of truth for exact approved wording.
- Simplify creative, marketing, or persuasive copy where voice and nuance are the point.
- Silently drop a safety condition, exception, or scope qualifier to shorten a sentence — it will flag the trade-off instead.
- Guarantee an aerospace/defense-grade STE-compliant document; this is a general-purpose clarity tool inspired by STE, not a certified STE authoring tool.
- Make weak content true or useful. STE fixes the *form* of a text, not its substance. A hollow paragraph rewritten under these rules becomes a clean, short, well-punctuated hollow paragraph. If the text has nothing to say, no rewrite fixes that — say so instead of polishing it.
- Shorten past the point of clarity. Cutting words is not the goal. Removing ambiguity is. Over-compression can slow a reader down, and the studies behind STE measure comprehension, not recall — expect text that is easier to understand, not text that is better remembered.

## Additional Resources

- **`references/writing-rules.md`** — fuller summary of the 9 rule sections and dictionary structure, with citations to the official standard and secondary sources.
- **`examples/before-after.md`** — worked examples, including official STE examples and agent-output examples built for this skill.
