---
name: write-paper
description: Guide the user through writing an academic paper end to end with the writing agents — plan (paper-planner), synthesize literature (literature-synthesizer), draft sections (section-drafter), check (the /check-literature agents), and respond to reviewers (reviewer-response-writer). Use when the user wants help writing, drafting, or revising a paper, thesis chapter, or review.
---

# Write paper

Arguments (optional): a stage and/or file(s), e.g. `/write-paper plan`, `/write-paper draft introduction`, `/write-paper review-response comments.pdf`.

## 0. Orient
- Find the user's material in the working directory: notes, data or results, existing draft, `.bib` or reference exports, PDFs of papers, author guidelines, and reviewer comments. Also check for existing `paper-plan.md`, `evidence-matrix.md`, and `drafts/`.
- Identify what stage they are at, and ask briefly (once) only about essentials that are missing: the topic or research question, paper type, target journal, and citation style.

## 1. Stages
Run the stage the user asks for. With no stage given, suggest the next logical one based on what already exists.

| Stage | Agent | Produces |
|---|---|---|
| `plan` | `paper-planner` | `paper-plan.md` — question, gap, contribution, detailed outline |
| `literature` | `literature-synthesizer` | `evidence-matrix.md`, `drafts/literature-review.md` |
| `draft <section>` | `section-drafter` | `drafts/<section>.md` |
| `check` | run the `/check-literature` skill | `literature-check-report.md` |
| `review-response` | `reviewer-response-writer` | `response-to-reviewers.md`, `revision-checklist.md` |

Give each agent the absolute paths of the relevant files, the target journal and style, and any decisions the user has made so far. Independent work (for example drafting Methods and Results) can run in parallel in a single message. Dependent work (plan → draft) runs in sequence.

## 2. Recommended order for a new paper
plan → (user approves the outline) → literature → draft Methods & Results → draft Discussion → draft Introduction → draft Abstract & title → check → revise → submit → review-response.

## 3. After each stage
Summarize in chat: what was produced (with file links), the placeholders or decisions the user must resolve, and the suggested next step. Stop and let the user review before moving on. The user stays the author.

## Integrity
- Drafts never contain fabricated data or citations. Placeholders mark anything missing.
- Never overwrite the user's manuscript unless asked.
- Remind the user once, briefly, to check their journal's or university's policy on AI-assisted writing and to disclose the use of AI if required.
