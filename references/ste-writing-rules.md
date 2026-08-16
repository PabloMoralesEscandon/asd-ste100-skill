# STE Compliance Writing Rules

Use these rules for STE Compliance mode. The official ASD-STE100 specification and its dictionary remain authoritative. This summary supports drafting and review but does not replace the official standard.

## Contents

- Compliance Boundary
- Approved Vocabulary
- Verbs and Voice
- Tense and Modality
- Sentences
- Noun Phrases and References
- Paragraphs, Lists, and Punctuation
- Difficult and Ambiguous Language
- Consistency Rules
- Sources

## Compliance Boundary

Full compliance requires all of these sources:

- The applicable official ASD-STE100 issue.
- The official approved-word dictionary for that issue.
- The organization's approved technical names, technical verbs, and terminology decisions.

If an authoritative dictionary is unavailable, apply the structural rules and label lexical compliance as unverified. Never claim full compliance from this summary alone.

Treat an agent review as drafting and quality-control assistance. Complete any professional or organizational review that the document's assurance process requires before making a formal compliance claim.

Semantic preservation remains mandatory. If a compliant construction would change a fact, condition, scope, or uncertainty, keep the source meaning and record the unresolved compliance issue.

## Approved Vocabulary

- Use an approved word only with its approved meaning and part of speech.
- Use one word for one meaning. Do not rotate synonyms for stylistic variety.
- Use approved alternatives only when they preserve the source meaning.
- Use a technical name or technical verb only under the standard's terminology rules and the applicable project dictionary.
- Do not assume that a familiar or simple word is approved.
- Do not infer approval from examples in this repository.

Read [dictionary-access.md](dictionary-access.md) when exact vocabulary must be verified. Read [pos-analysis.md](pos-analysis.md) when grammatical role or dictionary use is uncertain.

## Verbs and Voice

- Use the approved verb for an action instead of a nominalized action.
- Use active voice for instructions and procedures.
- Identify the actor when the actor affects correct execution.
- Use passive voice in descriptive text only when the actor is unknown or irrelevant and the applicable standard permits it.
- Avoid phrasal verbs. Select a single approved verb that preserves the meaning.
- Use only verb forms permitted by the applicable official issue.
- Prefer the imperative for direct procedures when it preserves the source requirement strength.
- Do not change a recommendation into a command merely to obtain an imperative sentence.

Example:

> Before: Do an inspection of the filter.
>
> After: Inspect the filter.

The rewrite preserves one required action and removes the nominalization. Verify `inspect` in the applicable dictionary before claiming lexical compliance.

## Tense and Modality

- Prefer simple approved tenses and constructions.
- Remove an unnecessary compound tense only when the simple tense has the same temporal meaning.
- Preserve modal meaning and uncertainty even when the resulting form needs a documented departure.
- Do not convert `may`, `might`, `could`, `should`, or a probability qualifier into certainty.

Example:

> Before: The valve may have failed during the test.
>
> Meaning-preserving result: The valve may have failed during the test.

Do not write `The valve failed during the test.` The second sentence changes an uncertain statement into a fact. If the original construction is not permitted, record the issue instead of changing the claim.

## Sentences

- Write one instruction per sentence.
- A condition and the single instruction that it controls can occur in one sentence.
- Keep all necessary subjects, verbs, articles, conditions, and objects.
- Prefer a direct subject-verb-object structure in descriptive text.
- Separate independent actions into separate sentences.
- Avoid long subordinate-clause chains.
- Keep procedural sentences at 20 words or fewer.
- Keep descriptive sentences at 25 words or fewer.
- If a length limit conflicts with semantic preservation, divide the sentence. If division cannot preserve the relationship, keep the meaning and report the exception.

Example:

> If the pressure is more than 50 kPa, stop the pump. Notify the supervisor.

The condition controls only `stop the pump`. The notification is a separate instruction. Do not attach the condition to both instructions unless the source does so.

## Noun Phrases and References

- Do not use noun clusters longer than three words.
- Expand a complex noun cluster with prepositions or a relative clause.
- Keep articles and other sentence parts that prevent ambiguity.
- Repeat the applicable noun when a pronoun has multiple possible antecedents.
- Do not use an omitted subject or verb to save words.

Example:

> Before: Inspect the engine fuel pump pressure switch.
>
> After: Inspect the pressure switch on the engine fuel pump.

Verify the boundaries of each technical name before changing a noun cluster. Do not split an approved technical name incorrectly.

## Paragraphs, Lists, and Punctuation

- Keep one topic in each paragraph.
- Use no more than six sentences in a paragraph.
- Use a vertical list for a sequence or a complex set of conditions.
- Use a numbered list when order matters.
- Do not use semicolons.
- Use punctuation to expose structure, not to join unrelated actions.
- Put a safety instruction before the action or condition that creates the hazard.

## Difficult and Ambiguous Language

- Prefer common approved words over unnecessarily difficult alternatives.
- Remove decorative wording that does not add technical meaning.
- Avoid vague modifiers and undefined frequency terms.
- Avoid ambiguous pronouns and words with multiple possible meanings.
- Keep a difficult technical term when replacing it would reduce precision. Define the term through the approved terminology process.

## Consistency Rules

- Use the same term, spelling, capitalization, and unit format for the same concept.
- Use parallel grammar for parallel instructions.
- Keep warnings, cautions, notes, and procedural steps in the required document format.
- Do not treat variation as a style benefit. Strict controlled English values repeatability over variety.

## Sources

- [ASD-STE100 official site](https://www.asd-ste100.org/)
- [Official ASD-STE100 downloads](https://www.asd-ste100.org/STE_downloads.html)
- [ASD Europe: Simplified Technical English](https://www.asd-europe.org/standards-specifications/simplified-technical-english/)
