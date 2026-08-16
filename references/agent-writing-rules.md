# Agent/Strict Writing Rules

Use these rules for English that an agent, tool, parser, or automated system will consume. Apply the semantic safeguards in `SKILL.md` before these rules. If a writing rule conflicts with those safeguards, the safeguard wins.

## Sentence Construction

- Prefer active voice when the source identifies the actor. Do not invent an actor to remove passive voice.
- Apply the core one-instruction rule atomically. One sentence can contain one condition and the single action that it controls.
- Put each condition immediately before its controlled action.
- Separate alternative branches and state the condition for each branch.
- Prefer subject-verb-object order.
- Use positive commands when they preserve the constraint. Keep negation when a positive rewrite would change the boundary.
- Split long sentences, but do not shorten text past the point of precision.
- Avoid semicolons and parenthetical instructions. Use separate sentences or lists.

Use:

> If the file exists, the agent reads the file. If the file does not exist, the agent returns `not_found`.

Do not use:

> Read it if available; otherwise, handle the issue appropriately.

The second version has an unclear pronoun and an undefined action.

## Terminology

- Assign one term to each concept and use that term consistently.
- Do not rotate synonyms for variety or use one term for different concepts.
- Repeat a noun when a pronoun has more than one possible antecedent.
- Replace a complex noun cluster with a clause or prepositional phrase.
- Use the least difficult word that preserves the technical meaning.
- Do not replace a precise domain term with a broader plain-language term.
- For new text, define a necessary domain term when the consumer might not know it.
- For a rewrite, add a definition only when the source or user supplies it. Otherwise, keep and flag the term.

Use:

> The scheduler sends the task to the worker. The worker returns the task result to the scheduler.

Do not use:

> The scheduler sends the job to the worker, which returns its result to it.

The second version rotates `task` and `job` and has ambiguous pronouns.

## Instructions and Logic

- Use a numbered list when order matters.
- Use bullets for independent requirements or alternatives.
- State whether all conditions or any condition must be true. Avoid `and/or`.
- State defaults and precedence rules explicitly when they affect behavior.
- Use parallel grammar for parallel branches.
- Put a warning before the action that can cause harm.
- Do not infer causation from temporal sequence.
- For new text, replace vague actions such as `handle the error` with defined behavior.
- For a rewrite, preserve a vague qualifier that carries meaning. Flag the ambiguity instead of deleting or defining it.

For new normative text, use modal verbs consistently:

- `must`: mandatory requirement
- `must not`: prohibition
- `should`: recommendation with permitted exceptions
- `may`: permission
- `can`: capability

Express possibility explicitly, for example, `It is possible that the request failed.` Do not use one modal for permission and possibility in the same instruction set. When rewriting, preserve the source force. If modal ambiguity affects execution and the intended meaning cannot be determined from context, preserve the ambiguity and report it to the caller.

## Machine-Sensitive Output

- Treat code spans, quoted literals, identifiers, placeholders, paths, enum values, and protocol tokens as opaque unless the task explicitly changes them.
- Preserve case, spelling, delimiters, and whitespace when the consuming format makes them significant.
- Keep a protected value in the same syntactic role. Do not translate or normalize it as prose.
- Do not reformat a machine-readable schema unless the user requests a schema change.
- Keep delimiters and required labels stable.
- Do not add a preamble, explanation, Markdown, or closing text when the consumer expects a bare value or fixed structure.
- Prefer explicit repeated fields over stylistic variation when repetition improves parsing.

## Final Scan

Before delivery, verify that:

- each pronoun has one clear antecedent;
- each instruction has one action;
- each condition controls an explicit action;
- each alternative has an explicit outcome;
- negation and exceptions keep their original logical reach;
- each concept has one stable name;
- no rewrite changes causality; and
- the output matches the required format exactly.

