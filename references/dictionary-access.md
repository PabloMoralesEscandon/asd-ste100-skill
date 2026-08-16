# Dictionary Access and Vocabulary Verification

Use this procedure when STE Compliance mode requires exact approved vocabulary or when the user asks for a formal lexical compliance claim.

## Authority

Use the dictionary in the applicable official ASD-STE100 issue as the authority for general vocabulary. Use the organization's approved terminology source for technical names and technical verbs.

This repository does not reproduce the official approved-word dictionary. Do not reconstruct, memorize, or redistribute the dictionary from unofficial copies. Obtain the standard through the [official ASD-STE100 downloads page](https://www.asd-ste100.org/STE_downloads.html) and follow its license terms.

## Required Inputs

Before a lexical compliance check, identify:

- the applicable ASD-STE100 issue;
- the authorized official dictionary for that issue;
- the project or organization dictionary;
- the document domain and intended audience; and
- any required terminology, identifiers, units, and product names.

If an input is unavailable, state the limitation. Continue with structural review only when that still helps the user.

## Verification Procedure

1. Build a list of each distinct content word in the text.
2. Keep the sentence context for every occurrence.
3. Separate protected literals, product identifiers, symbols, and code from prose vocabulary.
4. For each general word, find the exact official dictionary entry.
5. Verify the approved meaning and part of speech in every occurrence.
6. For a word that is not approved general vocabulary, determine whether it qualifies as an approved technical name or technical verb.
7. Check each technical term against the project dictionary and its definition.
8. Replace an unapproved use only with a verified construction that preserves meaning.
9. Check the revised sentence again. Do not assume that a suggested alternative is correct in every context.
10. Record words that remain unverified or require terminology approval.

Use [pos-analysis.md](pos-analysis.md) for a word whose grammatical role is unclear.

## Dictionary Decision Rules

- A matching spelling is insufficient. Meaning and part of speech must also match.
- An approved word in one entry is not approved for all senses.
- A dictionary alternative is not permission to change technical meaning.
- A common word is not necessarily approved.
- A technical word is not automatically a valid technical name or technical verb.
- Product names, code, paths, field names, and identifiers are protected literals. Do not silently rewrite them as prose.
- Use the same approved term for the same concept throughout the applicable scope.

## Project Terminology

For each project term, record:

- the exact term and spelling;
- its category as a technical name or technical verb;
- one definition;
- its permitted forms;
- any prohibited synonyms; and
- the approving source or owner.

Do not create a project term merely to avoid an official vocabulary restriction. The term must represent necessary domain meaning.

## Reporting Status

Use one of these statuses:

- **Lexically verified:** Every general word and project term was checked against authorized sources.
- **Structurally reviewed; lexical verification incomplete:** Structural rules were checked, but one or more dictionary inputs or entries were unavailable.
- **Not compliant:** At least one verified use violates an applicable rule and remains unresolved.

Lexical verification is only one part of compliance. Do not use `STE compliant` when only automated checks, memory, secondary summaries, or plain-language judgment support the result.
