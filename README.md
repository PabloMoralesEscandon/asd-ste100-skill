# ASD-STE100 Skill — Simplified Technical English for Agent Output

A Claude Code skill that rewrites dense, ambiguous English into [ASD-STE100 Simplified Technical English](https://www.asd-ste100.org/) (STE) — the controlled-language standard the aerospace and defense industry built so aircraft maintenance instructions cannot be misread.

This skill repurposes that same discipline for a different reader: an **AI agent** parsing another agent's output, a tool description, an error message, or an inter-agent instruction, with no human in the loop to resolve ambiguity.

## Why STE, and Why for Agents

STE exists because a misread instruction on an aircraft can kill people, and the intended readers were often not native English speakers with no author to call for clarification. The standard's fix: one meaning per word, active voice, simple tenses, one instruction per sentence, short sentences, no dropped words.

An LLM agent parsing another agent's output is in a strikingly similar position — no back-channel, no way to ask "did you mean X or Y?" The same rules that keep a mechanic from misreading a torque spec keep a downstream agent from misreading a tool description or an inter-agent message.

## Before / After

| Before | After |
|---|---|
| "This tool will attempt to synchronize state across the various backends that have been configured, and if a conflict is detected it may resolve it automatically depending on the strategy that has been set, or otherwise it will surface the conflict for manual review." | "The tool attempts to synchronize state across the configured backends. If the tool detects a conflict, it checks the configured strategy. If the strategy permits automatic resolution, the tool may resolve the conflict automatically. Otherwise, the tool reports the conflict for manual review." |
| "An error may have occurred while processing your request due to a possible mismatch in the expected data format, which could be caused by an outdated client version." | "An error may have occurred while processing the request. A possible mismatch with the expected data format may have caused the error. An outdated client version could have caused the mismatch." |

## What This Skill Does

[`SKILL.md`](SKILL.md) is the compact entry point. It contains the activation rules, mode routing, workflow, and semantic invariants. Detailed writing and compliance rules are separated under [`references/`](references/) and are loaded only when the selected mode or task requires them.

1. Picks a mode — **Agent/Strict** for system and agent instructions, tool and function descriptions, error and status messages, and other machine-consumed text; **STE Compliance** only when ASD-STE100 or STE compliance is explicitly requested or required by the surrounding system.
2. Reads the input English text for meaning, including its facts, conditions, scope, negation, uncertainty, and modality.
3. Loads only the applicable reference material. Agent-facing work usually uses the [Agent/Strict writing rules](references/agent-writing-rules.md). STE Compliance work uses the [STE writing rules](references/ste-writing-rules.md) and, when required, the dictionary, part-of-speech, and compliance-checking references.
4. Rewrites the text without dropping or inventing facts, conditions, scope qualifiers, causes, requirements, or uncertainty. If a language rule conflicts with semantic preservation, meaning wins and the unresolved compliance issue can be reported.
5. Returns the format the user or consuming system requested. Ask for the reasoning ("show the diff", "which rules did it break") to get an explanation or compliance details.

Generic technical subject matter, complex prose, or ordinary human-facing documentation does not automatically select STE Compliance mode. It also does not activate the skill by complexity alone.

The structural rules it checks are mechanical — you can point at the word or punctuation mark that breaks each one. Exact STE vocabulary compliance also depends on the applicable official dictionary and the organization's approved project terminology.

It does **not** reproduce ASD's official ~900-word approved dictionary. The standard is free to obtain but not free to redistribute: Issue 9 permits reproduction only with ASD's written authority, or by eight listed categories of organisation that this project does not belong to. For exact lexical verification or an STE compliance claim, use the official standard and the applicable project terminology.

The supporting references cover [dictionary access](references/dictionary-access.md), [part-of-speech analysis](references/pos-analysis.md), and the final [STE compliance checklist](references/compliance-checklist.md).

## Installation

### Claude Code

```bash
git clone https://github.com/PabloMoralesEscandon/asd-ste100-skill ~/.claude/skills/asd-ste100
```

### Codex

```bash
git clone https://github.com/PabloMoralesEscandon/asd-ste100-skill ~/.agents/skills/asd-ste100
```

Codex detects skills in `~/.agents/skills` automatically. If the skill does not appear, restart Codex.

## Usage

Agent/Strict mode activates for agent-facing or machine-consumed text. For example:

```
Disambiguate this tool description
Rewrite this error message so an agent can't misparse it
Make this inter-agent instruction deterministic
```

STE Compliance mode activates only when compliance with ASD-STE100 or STE is explicit. For example:

```
Apply ASD-STE100 to this instruction
Check this procedure for STE compliance
Rewrite this text in compliant Simplified Technical English
```

An explicit request for “controlled English” also activates the skill; if it does not explicitly require STE compliance, the skill uses Agent/Strict mode. A generic request such as “simplify this technical explanation” does not by itself activate the skill or select STE Compliance mode.

You get the requested rewritten text back. To see which rules were applied, add "show the diff" or "explain the changes" to the request. For a formal compliance report, request one explicitly and provide the applicable official dictionary and project terminology.

## Scope

Built for: agent-to-agent messages, tool/function descriptions, error messages, system prompts, inter-agent instructions — any English text a machine or non-native reader has to parse without a human to ask. It also supports STE-controlled documentation when compliance is explicitly requested or required.

Not built for: creative writing, marketing copy, or anything where voice and nuance are the point — STE is deliberately flat and literal by design. Ordinary human-facing prose does not activate the skill merely because it is technical or complex.

One limit worth stating up front: this fixes the form of a text, not its substance. A paragraph with nothing to say comes out short, clean, and still empty.

## Sources

- [ASD-STE100 official site](https://www.asd-ste100.org/)
- [ASD-STE100 — About STE](https://www.asd-ste100.org/about_STE.html)
- [ASD Europe — Simplified Technical English](https://www.asd-europe.org/standards-specifications/simplified-technical-english/)
- [Simplified Technical English — Wikipedia](https://en.wikipedia.org/wiki/Simplified_Technical_English)
- [TechScribe — ASD-STE100 Simplified Technical English](https://www.techscribe.co.uk/techw/asd-simplified-technical-english.htm)

## License

MIT — see [LICENSE](LICENSE).
