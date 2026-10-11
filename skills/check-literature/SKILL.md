---
name: check-literature
description: Run a full literature and manuscript check using the specialist agents (citations and references, writing quality, literature coverage, claims vs sources, internal consistency) and compile one combined report. Use when the user asks to check, review, or audit their paper, thesis, manuscript, or literature review.
---

# Check literature

Arguments (optional): a file path and/or a list of checks to run, e.g. `/check-literature thesis.docx citations claims`.

## 1. Find the manuscript
- Use the path the user gave. Otherwise Glob the working directory for `*.docx`, `*.pdf`, `*.tex`, `*.md`, and `*.bib`, and ask if it is ambiguous which file is the manuscript.
- Note any accompanying files: a `.bib` or reference export, a folder of cited PDFs, and author guidelines.
- Ask once, briefly, only if useful and not already stated: the target journal and citation style.

## 2. Choose the checks
Default to all five unless the user names specific ones:

| Check | Agent |
|---|---|
| citations / references | `citation-checker` |
| writing / grammar / style | `writing-quality-reviewer` |
| coverage / missing papers | `literature-coverage-analyst` |
| claims / fact-check | `claims-verifier` |
| consistency / formatting / submission | `consistency-checker` |

## 3. Run the agents in parallel
Launch all selected agents in a **single message** with the Agent tool. Give each one:
- the absolute path to the manuscript and to any supporting files (.bib, PDFs folder, guidelines)
- the target journal and citation style, if known
- the instruction: "Return your full markdown report as your final message."

## 4. Compile the report
Write `literature-check-report.md` next to the manuscript, containing:
1. **Executive summary**: an overall verdict, then the **top 10 fixes** across all checks, ranked by impact (fabricated or retracted references and unsupported central claims first).
2. One section per check, containing that agent's report. Lightly de-duplicate issues reported by more than one agent.
3. **Action checklist**: `- [ ]` items the author can tick off.

Then tell the user the top 5 issues in chat and link the report file. Never modify the manuscript itself unless the user explicitly asks you to apply fixes.
