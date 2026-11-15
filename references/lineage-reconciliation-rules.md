# Lineage Reconciliation & Version Association Rules (`recipe-dna`)

This reference defines the deterministic rules used in **Step 4** of [`SKILL.md`](../SKILL.md) to associate multiple NAS files into a unified **Family Recipe Lineage** without losing provenance or inventing compromise quantities.

---

## 1. Version Association Criteria

Before comparing ingredients or steps, verify whether two candidate sources (`Source_i`, `Source_j`) belong to the same recipe lineage:

1. **Dish Identity Match**:
   - Both sources explicitly name the same dish or a known family alias (e.g., *"Nonna's Ragù"* and *"Sunday Meat Sauce - Grandma"*), OR
   - Both sources share at least 60% of core primary ingredients and produce the same dish category within the same authorized recipe folder.
2. **Distinct Recipe Separation**:
   - If a folder contains recipes for two different dishes (e.g., *Apple Pie Crust* vs. *Apple Cinnamon Muffins*), do **not** merge them into a single lineage. Report non-matching files in the `Excluded / Unrelated Files` note.

---

## 2. Establishing the Baseline (`v1`) and Version Ordering

1. **User Preference First**: If the user specified `baseline_preference` (e.g., *"Use Grandma's 1998 scan as the baseline"*), assign that source as `v1 (Baseline)`.
2. **Documented Date Ordering**: Otherwise, rank sources by the earliest verifiable date in the following priority order:
   - Explicit date written inside the document text (e.g., *"Recorded Dec 1995"*).
   - EXIF capture timestamp (`exif_capture_date` from `photo-agent`).
   - Filesystem creation/modification timestamp (`last_modified_date` from `file-agent`).
3. **Modality Tie-Breaker**: If dates are identical or unavailable, prioritize full written/scanned recipes (`document` or `photo`) as `v1`, followed by secondary written variations (`v2`, `v3`), and attach voice recordings (`audio`) or short text notes (`document`) as **Oral / Marginal Variations** linked to the corresponding steps.

---

## 3. Seven-Category Lineage Classification Rules

Every extracted ingredient, measurement, and preparation step must be classified into one or more of the following seven categories:

| Category | Definition & Trigger Condition | Required Handling in Output |
| :--- | :--- | :--- |
| **1. Original Documented Ingredients** | Ingredients and exact quantities present in the designated `v1 (Baseline)` source. | Display in the Baseline column with exact units as written (do not convert units unless showing a bracketed note alongside the original). |
| **2. Later Changes** | An ingredient present in `v1` whose quantity, unit, or specific type changed in `v2+`, or a new ingredient added/removed in `v2+`. | Preserve both `v1` and `v2+` values side by side (e.g., `v1: 200g flour [grandma-card.jpg]` vs. `v2: 250g flour [mom-recipe.docx]`). |
| **3. Different Cooking Methods** | Differences in cooking vessel, heat source, temperature, or technique across versions (e.g., steaming vs. pan-frying; 180°C vs. 200°C). | Highlight in the **Method Comparison** section with source citations for each method. |
| **4. Family-Specific Variations** | Qualitative adjustments, optional add-ins, or sensory cues tied to a specific family member or voice memo (e.g., *"add extra flour until dough reaches earlobe softness"*). | Record verbatim under **Family & Oral Variations** with attribution to the specific audio/note file. |
| **5. Uncertain Quantities** | Measurements where OCR/handwriting is smudged, cut off, or expressed only as an ambiguous phrase (e.g., *"a handful"*, *"2 [?]sp salt"*). | Tag with `[UNCERTAIN EXTRACTION]` or `[AMBIGUOUS QUANTITY]`. Never replace with a guessed numeric value. |
| **6. Missing Steps** | A preparation stage (e.g., resting dough for 30 minutes, preheating oven, Deglazing pan) that appears in one version but is omitted in another. | Flag as `[MISSING IN vX]` in the step evolution table so the cook sees what was skipped. |
| **7. Conflicting Instructions** | Direct procedural contradictions between two sources (e.g., Source A says *"Do not knead more than 1 minute"* while Source B says *"Knead vigorously for 10 minutes"*). | Flag prominently in the **Contradictions & Conflicts Alert** table; do not resolve in favor of either source. |

---

## 4. Attribution Safeguard Protocol

- **Explicit Evidence Only**: Assign a family member label (such as *Grandmother*, *Mother*, *Aunt Mei*, *Dad*) **only** when the relationship or name appears in:
  1. The document header/body or spoken audio transcript,
  2. The filename or parent directory name (e.g., `grandma_apple_pie.jpg`), or
  3. Explicit user input during Step 1.
- **Neutral Fallback**: When no family attribution exists in the evidence, label the version using its filename and modality (e.g., `Version 2 — Scanned Note (recipe_scan_02.png)`).
