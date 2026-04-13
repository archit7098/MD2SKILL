---
name: nhs-genomic-test-finder
description: >
  Look up NHS England genomic tests for rare and inherited diseases. Use this skill whenever a clinician asks
  what genetic test to order for a condition, which genes are covered for a specific diagnosis, what commissioning
  category a genomic test falls under (Core, Specialised, or Highly Specialised), or which tests belong to a
  specialty group (Neurology, Cardiology, Endocrinology, etc.). Also trigger for questions like what panel is
  used for a condition, whether there is an NHS test for something, what the R number is for a condition, or
  whether anything has changed in the genomic test directory. Source: NHS England National Genomic Test Directory
  for Rare and Inherited Disease v9.0 (April 2026).
---

# NHS Genomic Test Finder

This skill provides lookup and search over the NHS England National Genomic Test Directory for Rare and Inherited Disease (v9.0, April 2026, 2026/27 commissioning year).

The data lives in a CSV reference file alongside this skill. Always read it before answering.

## Reference Data

File: `references/genomic-test-directory.csv`

Columns:
- `indication_id` — Clinical indication code (e.g. R14, R133)
- `test_id` — Specific test code (e.g. R14.1, R133.1) — one indication may have multiple tests
- `clinical_indication` — Full name of the condition/indication
- `target_genes` — Panel name with gene count, or specific gene(s) tested
- `test_method` — e.g. WGS, Small panel, Single gene sequencing >=10 amplicons, MLPA, Microarray
- `commissioning_category` — Core | Specialised | Highly Specialised | Core/Specialised | Newborn screening programme
- `specialist_group` — e.g. Neurology, Cardiology, Endocrinology, Haematology, Metabolic, Prenatal
- `eligibility_section` — Section of the NHS eligibility criteria document
- `changes_since_last_version` — What changed vs May/July 2025 publication

## Query Types and How to Handle Each

### 1. Condition/Indication Search
*"What test do I order for Brugada syndrome?"*

- Search `clinical_indication` column (case-insensitive, partial match)
- Return all matching rows
- For each match, present: Test ID → Indication → Genes/Panel → Method → Commissioning category
- If multiple test IDs exist for one indication, list all (they may differ by method or scope)

### 2. Gene / Panel Search
*"Is BRCA2 tested in this directory?" / "What tests cover the RASopathy panel?"*

- Search `target_genes` column for the gene or panel name
- Return indication(s) that include it, with test details

### 3. Specialty Browse
*"What Neurology tests are available?"*

- Filter by `specialist_group`
- Group by indication, list Test IDs and methods
- Note commissioning categories across the group

### 4. R-Code Lookup
*"What is R391?" / "Tell me about R14.1"*

- Match on `indication_id` or `test_id` exactly
- Return full row details

### 5. Commissioning Category Check
*"Is this test Core or Specialised?"*

- Return the commissioning category for the matched test
- Clarify: Core = available through any NHS genomics lab; Specialised = requires referral to specialist centre; Highly Specialised = rare, specific centres only

### 6. What's New / Changed
*"What's changed since the last version?"*

- Filter where `changes_since_last_version` ≠ "No change"
- Group by type of change (new CI, amended scope, added genes, amended name, etc.)
- List affected Test IDs and what changed

---

## Output Format

Always structure results clearly. For a single test lookup:

```
R-Code:        R133.1
Indication:    Arrhythmogenic right ventricular cardiomyopathy
Genes/Panel:   Arrhythmogenic cardiomyopathy panel (134 genes)
Test Method:   Small panel
Commissioning: Specialised
Specialty:     Cardiology
Changes:       No change since May/July 2025
```

For multi-result searches, use a brief table or numbered list. If more than 10 results match, summarise by specialty or category and ask if the user wants to narrow the search.

---

## Clinical Guardrails

- **This directory covers NHS England only** — does not apply to Scotland, Wales, Northern Ireland, or private testing
- **Commissioning categories determine referral pathway** — Core tests can be requested via local genomics labs; Specialised and Highly Specialised require appropriate clinical referral
- **Check eligibility criteria** — the directory lists available tests but not patient eligibility. The full eligibility criteria document should be consulted for indications/thresholds
- **Multiple test IDs for one condition** — some indications have .1, .2, .3 variants (e.g. different methods for different clinical scenarios). Present all and flag the differences
- **Version currency** — this is v9.0, April 2026. Always note the version when providing lookup results so clinicians can verify currency

---

## Source

NHS England National Genomic Test Directory for Rare and Inherited Disease, v9.0, 8 April 2026 (2026/27 commissioning year)
© NHS in England 2026/27. All rights reserved.
