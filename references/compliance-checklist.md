# STE Compliance Checklist

Use this checklist for a final review in STE Compliance mode or when the user requests a compliance report. Complete the semantic checks before the language checks.

## 1. Scope and Sources

- [ ] Record the applicable ASD-STE100 issue.
- [ ] Confirm access to its official dictionary.
- [ ] Identify the applicable project terminology source.
- [ ] Identify the document type, audience, and required output format.
- [ ] Protect identifiers, code, units, product names, and required labels.

## 2. Semantic Preservation

- [ ] Preserve every source fact and relationship.
- [ ] Preserve all conditions, exceptions, thresholds, quantities, and scope limits.
- [ ] Preserve uncertainty, probability, and frequency.
- [ ] Preserve requirement strength and permission.
- [ ] Preserve causal and temporal relationships without adding an inference.
- [ ] Add no action, remedy, cause, guarantee, or warning that the source does not contain.

Fail the rewrite if any semantic item changes. Do not trade accuracy for a clean compliance result.

## 3. Vocabulary and Terminology

- [ ] Verify each general word against the official dictionary.
- [ ] Verify each use in its approved meaning.
- [ ] Verify each use in its approved part of speech.
- [ ] Verify each technical name and technical verb against project terminology.
- [ ] Use one term for one concept.
- [ ] Remove unnecessary synonyms and difficult alternatives.
- [ ] Define or escalate each necessary unapproved term.

## 4. Grammar and Sentences

- [ ] Use active voice for each instruction.
- [ ] Make the actor explicit when the actor matters.
- [ ] Use one instruction in each sentence.
- [ ] Put each condition next to the instruction that it controls.
- [ ] Use permitted verb forms and tenses.
- [ ] Preserve modal meaning.
- [ ] Remove nominalized actions when an approved verb preserves the meaning.
- [ ] Remove phrasal verbs when a verified single verb preserves the meaning.
- [ ] Keep necessary subjects, verbs, objects, and articles.
- [ ] Resolve each ambiguous pronoun.

## 5. Length and Structure

- [ ] Keep each procedural sentence at 20 words or fewer.
- [ ] Keep each descriptive sentence at 25 words or fewer.
- [ ] Keep noun clusters at three words or fewer, except where an applicable terminology rule controls the term.
- [ ] Keep one topic in each paragraph.
- [ ] Keep each paragraph at six sentences or fewer.
- [ ] Use vertical lists for sequences and complex conditions.
- [ ] Use numbered lists when order matters.
- [ ] Remove all semicolons.
- [ ] Put safety information before the hazardous action.

## 6. Consistency and Output

- [ ] Use consistent spelling, capitalization, terminology, and units.
- [ ] Use parallel grammar for parallel items.
- [ ] Keep required warnings, cautions, notes, and labels in their required format.
- [ ] Match the user's or consuming system's output schema exactly.
- [ ] Add no unrequested preamble or commentary to machine-consumed output.

## 7. Final Comparison

Compare the final text against the source sentence by sentence.

- [ ] Every source claim appears in the result.
- [ ] Every result claim has support in the source.
- [ ] Each condition has the same logical reach.
- [ ] Each modal has the same force.
- [ ] Each protected literal is unchanged.
- [ ] Each documented exception is accurate.

## Result Labels

Use only a label supported by the review:

- **STE compliance checks passed:** All applicable structural, lexical, terminology, and format checks passed against authorized sources, and all required professional or organizational review is complete.
- **Agent review passed, formal review pending:** The agent found no unresolved issue, but required professional or organizational review is not complete or not verified.
- **Compliant except for documented departures:** All unresolved departures are listed, and none is hidden.
- **Structurally reviewed, lexical compliance not verified:** Structural checks passed, but dictionary or terminology verification is incomplete.
- **Not compliant:** One or more applicable checks failed.

## Exception Record

For each unresolved item, record:

| Location | Source text | Rule or check | Reason retained | Required resolution |
|---|---|---|---|---|
| Section and sentence | Exact text | Applicable rule | Meaning or source limitation | Author, dictionary, or terminology decision |
