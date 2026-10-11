# Academic Writing Toolkit

A Claude Code plugin with 9 agents and 2 commands for writing and checking academic papers.

## Install

In Claude Code:

```
/plugin marketplace add shahparth189-commits/academic-writing-toolkit
/plugin install academic-writing-toolkit@shahparth-tools
```

This repository is private, so the computer you install on must be signed in to GitHub with access to it.

## Commands

### `/write-paper [stage]` — write a paper step by step

| Stage | Agent | Produces |
|---|---|---|
| `plan` | paper-planner | `paper-plan.md`: research question, gap, contribution, detailed outline |
| `literature` | literature-synthesizer | `evidence-matrix.md`, `drafts/literature-review.md` |
| `draft <section>` | section-drafter | `drafts/<section>.md` |
| `check` | the checking agents | `literature-check-report.md` |
| `review-response` | reviewer-response-writer | `response-to-reviewers.md`, `revision-checklist.md` |

Suggested order: plan → literature → Methods & Results → Discussion → Introduction → Abstract & title → check → revise.

### `/check-literature [file] [checks]` — check a manuscript

Runs these agents in parallel and compiles `literature-check-report.md`:

| Agent | Checks |
|---|---|
| citation-checker | References exist, details are correct, citations match the reference list, citation style, retractions |
| writing-quality-reviewer | Structure, flow, clarity, tone, grammar |
| literature-coverage-analyst | Missing key, recent, or contradicting papers; outdated sources |
| claims-verifier | Each claim is actually supported by its cited source |
| consistency-checker | Numbers, abbreviations, terminology, figure/table references, journal requirements |

Example: `/check-literature thesis.docx citations claims`

## Supported files

Word (.docx), PDF, LaTeX (.tex), BibTeX (.bib), Markdown/text, and reference-manager exports (RIS, CSV, XML).

## Principles

- Agents never fabricate data, results, or citations. Missing items are marked with placeholders such as `[CITATION NEEDED]`.
- Your manuscript is never overwritten. Drafts go into `drafts/`.
- Check your journal's or university's policy on AI-assisted writing, and disclose its use where required.
