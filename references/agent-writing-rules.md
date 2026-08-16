# Agent/Strict Writing Rules

Use these rules for text that another agent, tool, parser, or automated system will consume. These rules prioritize semantic stability and deterministic interpretation. They do not by themselves establish ASD-STE100 compliance.

## Contents

- Priority and semantic stability
- Sentence construction and terminology
- Instructions, logic, and modal verbs
- Machine-sensitive content
- Final scan

## Priority Order

Apply rules in this order:

1. Preserve meaning and protected literals.
2. Preserve conditions, exceptions, scope, and uncertainty.
3. Make actors, actions, inputs, outputs, and failure states explicit.
4. Use stable terminology and simple syntax.
5. Reduce length only when reduction does not remove information.

## Semantic Stability

- Keep every fact and logical relationship from the source.
- Keep qualifiers such as `only`, `unless`, `except`, `at least`, and `at most`.
- Keep probability and uncertainty markers such as `may`, `might`, `can`, `could`, `likely`, and `sometimes`.
- Keep requirement strength. `Must`, `should`, `may`, and `can` are not synonyms.
- Do not add a remedy, cause, sequence step, fallback, or success claim that the source does not contain.
- Do not infer that temporal sequence means causation.
- Keep identifiers and syntax tokens exact when another component depends on them.

Correct:

> The request may have failed because the client and server formats differ.

Incorrect:

> The request failed because the client is outdated.

The incorrect version removes uncertainty and invents a cause.

## Sentence Construction

- Prefer active voice when the source identifies the actor. Do not invent an actor to remove passive voice.
- Use one instruction per sentence.
- Put a condition immediately before the instruction that it controls.
- Separate alternative branches. State the condition for each branch.
- Prefer subject-verb-object order.
- Use positive commands when they express the same constraint. Keep a negative command when changing it would alter the boundary.
- Use short sentences, but do not treat length as more important than precision.
- Avoid semicolons and parenthetical instructions. Use separate sentences or lists.

Use:

> If the file exists, the agent reads the file. If the file does not exist, the agent returns `not_found`.

Do not use:

> Read it if available; otherwise, handle the issue appropriately.

The second version has an unclear pronoun and an undefined action.

## Terminology

- Assign one term to each concept and use that term consistently.
- Do not rotate synonyms for variety.
- Do not use one term for two different concepts.
- Repeat a noun when a pronoun can have more than one antecedent.
- Replace a complex noun cluster with a clause or a prepositional phrase.
- Use the least difficult word that preserves the technical meaning.
- For new text, define a necessary domain term before first use when the consumer might not know it.
- For a rewrite, add a definition only when the source or user supplies it. Otherwise, keep and flag the term.
- Do not replace a precise domain term with a broader plain-language term.

Use:

> The scheduler sends the task to the worker. The worker returns the task result to the scheduler.

Do not use:

> The scheduler sends the job to the worker, which returns its result to it.

The second version rotates `task` and `job` and has ambiguous pronouns.

## Instructions and Logic

- Make each instruction atomic. One sentence can contain one condition and one controlled action.
- Use a numbered list when order matters.
- Use bullets for independent requirements or alternatives.
- State whether all conditions or any condition must be true. Avoid `and/or`.
- State defaults and precedence rules explicitly when they affect behavior.
- Use the same grammatical pattern for parallel branches.
- Put warnings before the action that can cause harm.
- For new text, do not use vague references such as `as needed`, `appropriate`, `normally`, or `handle the error` unless the text defines them.
- For a rewrite, preserve a vague qualifier that carries meaning. Flag the ambiguity instead of silently deleting or defining it.

## Modal Verbs

For new normative text, use these meanings consistently:

- `must`: mandatory requirement
- `must not`: prohibition
- `should`: recommendation with permitted exceptions
- `may`: permission
- `can`: capability

Express possibility with an explicit construction such as `It is possible that`. Do not use one modal for both permission and possibility in the same instruction set.

When rewriting existing text, preserve the source force even if it differs from this convention. Ask the author to resolve a genuinely ambiguous modal when the ambiguity affects execution.

## Machine-Sensitive Content

- Preserve placeholders such as `{user_id}` and `${TASK_ID}` exactly.
- Preserve keys, enum values, flags, commands, code spans, paths, URLs, units, and error identifiers exactly.
- Do not reformat a machine-readable schema unless the user requests a schema change.
- Keep delimiters and required labels stable.
- Do not add preambles, explanations, Markdown, or closing text when the consumer expects a bare value or fixed structure.
- Prefer explicit repeated fields over elegant variation when repetition improves parsing.

## Final Scan

Before delivery, verify that:

- each pronoun has one clear antecedent;
- each instruction has one action;
- each condition controls an explicit action;
- each concept has one stable name;
- no rewrite changed certainty, obligation, scope, or causality;
- no protected literal changed; and
- the output matches the required format exactly.
