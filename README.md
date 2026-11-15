# RecipeDNA (`recipe-dna`)

**Preserve the recipes, voices, and kitchen knowledge of your family.**

A Uliya AI Skill built for **UGREEN UGOS** (UGREEN Hackathon 2026 — *Bring Memories to Life* / *Understand Your Life*).

## Overview

Family recipes are scattered across typed notes, photographed handwritten recipe cards, and kitchen voice memos on a NAS. Generic AI tools flatten them into one guessed "average" recipe and lose who changed what.

**RecipeDNA** searches user-authorized NAS folders and photo albums, extracts ingredients, steps, and spoken tips verbatim, and produces a source-cited **Family Recipe Lineage Record** that keeps `v1` (Baseline), `v2+` updates, and oral notes side by side across seven difference categories:

- Original Documented Ingredients
- Later Changes
- Different Cooking Methods
- Family-Specific Variations
- Uncertain Quantities
- Missing Steps
- Conflicting Instructions

## Package Structure

```text
.
├── SKILL.md
└── references/
    ├── extraction-and-ocr-safeguards.md
    ├── lineage-reconciliation-rules.md
    └── output-template.md
```

## UGOS Capabilities & Expert Orchestration

- `ug-filesystem` → `file-agent` (read-only file discovery)
- `ug-photo` → `photo-agent` (OCR-text/filename album search, metadata, `vision-ocr`)
- `ug-document` → `document-agent` (structured recipe text extraction)
- `ug-knowledge` → `knowledge-agent` (`audio-transcription`, optional approval-gated `save-text`)

## Safeguards

- Never invents, averages, rounds, or converts quantities.
- Tags unclear handwriting/OCR/speech as `[UNCERTAIN EXTRACTION]` or `[INAUDIBLE / UNCERTAIN AUDIO]`.
- Attributes versions to relatives only when source evidence explicitly names them.
- Read-only by default; treats extracted text as untrusted data.

## Validation Status

- **Static Check**: Passed **Uliya Skill Kit 0.7.3** (`check-skill.mjs` → `static-pass`, 0 errors, 0 warnings).
- **NAS Runtime**: Pending Round 2 testing on an assigned UGREEN AI NAS iDX6011 Pro.

## Disclosures

- **Third-party components and open-source libraries**: None (plain Markdown using registered UGOS experts).
- **Author**: Brilian Ade Putra (`Team Brilian`).
- **AI tools used**: Google Antigravity (Gemini) and Anthropic Claude Code (Claude) assisted with concept refinement, Markdown authoring, and static-check compliance review under human review.
