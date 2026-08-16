---
name: asd-ste100
description: Rewrite or author English for unambiguous agent and machine use, or apply ASD-STE100 controlled English. Use when the user explicitly requests STE, ASD-STE100, Simplified Technical English, or controlled English, or when the output is a system prompt, tool or function description, error or status message, inter-agent instruction, or other machine-consumed message. Do not trigger only because ordinary human-facing prose is complex or technical.
---

# ASD-STE100 Writing

## Activation Boundary

Use this skill in either of these cases:

- The user explicitly requests STE, ASD-STE100, Simplified Technical English, or controlled English.
- The output is for an agent, tool, function, system prompt, error channel, parser, or other machine consumer.

Do not apply this skill automatically to ordinary human-facing prose. Complexity alone does not activate it.

## Modes

- **Agent/Strict mode:** Use for system and agent instructions, tool and function descriptions, error and status messages, inter-agent communication, and other machine-consumed text. Optimize for deterministic interpretation and reliable parsing.
- **STE Compliance mode:** Use only when the user explicitly requests compliance with ASD-STE100 or STE, or when the surrounding system explicitly requires STE compliance. Apply the official STE constraints as rigorously as the available dictionary and project terminology permit.

Use Agent/Strict mode for a generic controlled-English request that does not explicitly require STE compliance. Technical subject matter alone does not select STE Compliance mode.

## Nonnegotiable Requirements

1. Preserve the original meaning, facts, conditions, scope, relationships, negation, and uncertainty.
2. Do not invent a fact, cause, action, frequency, requirement, or guarantee.
3. Do not convert an uncertain statement into a certain statement.
4. Preserve the force of requirements. Do not interchange `must`, `should`, `may`, and `can` unless the source authorizes that change.
5. Preserve literal identifiers, placeholders, code, commands, paths, field names, enum values, units, error codes, and required formats unless the user asks to change them.
6. Prefer active voice, simple sentence structures, one instruction per sentence, and one term for each concept.
7. Avoid ambiguous pronouns, unnecessary synonyms, complex noun clusters, and unnecessarily difficult language.
8. In Agent/Strict mode, optimize the output for reliable machine and agent parsing, not for stylistic variety.

If a language rule conflicts with semantic preservation, preserve the meaning. In Agent/Strict mode, report an unresolved rule only when the user requests details. In STE Compliance mode, always report unresolved departures and verification limitations. Do not make a compliance claim that hides an unresolved item.

## Workflow

1. Identify the consumer and select the mode.
2. Extract the source claims, actors, actions, conditions, exceptions, scope, modality, and protected literals.
3. Load only the references required for the selected mode and task.
4. Rewrite or author the text with explicit actors, conditions, and stable terminology.
5. Compare the result with the source. Reject any change to meaning, negation, certainty, requirement strength, or scope.
6. If the input requires no changes under the completed checks, say so. Do not force changes onto the text.
7. Run the applicable checks. Return the requested format or the default format below.

## Output Format

Follow an explicit format from the user or consuming system.

By default, return the rewritten text and nothing else. Do not add a preamble, mode announcement, violation count, change summary, rule table, or closing offer to explain the result. If no changes are necessary, return `No changes are required.`

In STE Compliance mode, append a `Departures:` list when unresolved departures or verification limitations exist. Use one bullet for each item and state the affected text or location, the unresolved rule or limitation, and the reason. Do this even when the user did not request an explanation. Do not add this list when there are no unresolved items. In Agent/Strict mode, report retained language or unresolved rules only when the user requests details.

When the user asks to "show the diff," "explain the changes," identify broken rules, or provide a before-and-after comparison, return this table instead of the default bare rewrite:

| Source sentence | Rule | Revised text | Change |
|---|---|---|---|
| Original sentence | Applicable rule | Rewritten sentence | Concise description of the change |

Add the selected mode after the table. Identify any wording that remains unchanged because a rewrite would alter the meaning. In STE Compliance mode, also include every unresolved departure and verification limitation.

## Reference Routing

- Read [references/agent-writing-rules.md](references/agent-writing-rules.md) when producing or revising agent-facing or machine-consumed English.
- Read [references/ste-writing-rules.md](references/ste-writing-rules.md) when STE Compliance mode applies or the user asks about a detailed STE grammar or vocabulary rule.
- Read [references/pos-analysis.md](references/pos-analysis.md) only when a word's part of speech or approved use is ambiguous, or when the user requests a lexical or part-of-speech audit.
- Read [references/dictionary-access.md](references/dictionary-access.md) when exact approved vocabulary, an official compliance claim, or project-specific terminology must be verified.
- Read [references/compliance-checklist.md](references/compliance-checklist.md) for a final STE compliance audit or when the user requests a compliance report.

Do not load all references by default. For Agent/Strict mode, the agent-writing rules are usually sufficient. For STE Compliance mode, load the STE writing rules, then load dictionary and checklist material only as the verification scope requires.
