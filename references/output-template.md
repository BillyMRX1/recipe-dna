# Standard Recipe Lineage Output Template (`recipe-dna`)

Use this exact Markdown structure in **Step 5** of [`SKILL.md`](../SKILL.md) when presenting the reconstructed **Family Recipe Lineage Record** to the user.

---

```markdown
# Family Recipe Lineage Record: <Dish Name>

> **Provenance Notice**: This record was reconstructed strictly from authorized files on your UGREEN AI NAS. Variations, conflicting instructions, and uncertain extractions are preserved side by side to honor each source without inventing compromise measurements. This record documents historical family variations and does not guarantee recreating the exact taste of any original dish.

## 1. Inspected NAS Source Inventory

| Source ID | NAS File Path | Modality & Agent Used | Documented Date / Metadata | Attribution (Evidence-Based) | Extraction Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `v1 (Baseline)` | `<exact_path_1>` | `<Document / Photo / Audio>` (`<agent>`) | `<Date / EXIF>` | `<Attribution or Neutral Label>` | `<Complete / Partial OCR / Uninspected>` |
| `v2` | `<exact_path_2>` | `<Document / Photo / Audio>` (`<agent>`) | `<Date / EXIF>` | `<Attribution or Neutral Label>` | `<Complete / Partial OCR / Uninspected>` |
| `v3 (Oral/Note)` | `<exact_path_3>` | `<Audio / Note>` (`<agent>`) | `<Date / mtime>` | `<Attribution or Neutral Label>` | `<Transcribed / Transcription Unavailable>` |

---

## 2. Ingredient Lineage Matrix (Baseline vs. Generational Variations)

| Ingredient | `v1 (Baseline)` (`<filename_1>`) | `v2` (`<filename_2>`) | Oral / Family Variations (`<filename_3>`) | Lineage Category & Notes |
| :--- | :--- | :--- | :--- | :--- |
| `<Ingredient 1>` | `<Exact quantity + unit>` | `<Exact quantity + unit>` | `<Quoted adjustment or N/A>` | `<Original / Later Change / Family-Specific Variation / Uncertain Quantity>` |
| `<Ingredient 2>` | `<Exact quantity + unit>` | `<Exact quantity + unit>` | `<Quoted adjustment or N/A>` | `<Category>` |

---

## 3. Preparation Step Evolution & Cooking Method Comparison

### Baseline Preparation Flow (`v1`) with Version Deltas
1. **Stage 1 — `<Stage Name>`**
   - **`v1` (`<filename_1>`)**: `<Step description>`
   - **`v2` (`<filename_2>`)**: `<Step description or [SAME AS v1] or [MISSING IN v2]>`
   - **Oral / Family Note (`<filename_3>`)**: `"<Exact quote>"`
   - **Classification**: `<Original / Different Cooking Method / Missing Step / Conflicting Instruction>`

---

## 4. Contradictions, Missing Quantities & Uncertain Extractions Alert

| Issue Type | Affected Item / Step | Source(s) Involved | Exact Evidence / Raw Token | Resolution Status |
| :--- | :--- | :--- | :--- | :--- |
| `<Conflicting Instruction / Uncertain Quantity / Missing Step>` | `<Item or Step>` | `<file_path(s)>` | `"<Verbatim quote or OCR token>"` | **Unresolved by design** — requires human cook's choice or visual inspection of original file |

---

## 5. Uninspected or Unsupported Sources (If Any)

- `<file_path>`: `<Reason, e.g., Audio transcription unavailable or unsupported binary format>`

---
*Would you like to save this Family Recipe Lineage Record as a new Markdown file on your NAS? Please confirm the destination folder before anything is written.*
```
