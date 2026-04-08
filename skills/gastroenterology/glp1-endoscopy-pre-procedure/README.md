# GLP-1 RA Pre-Endoscopy Decision Tool
### AGA 2024 Rapid Clinical Practice Update

5-step pre-procedure decision tool for patients on GLP-1 receptor agonists. Covers symptom screening, fasting adequacy, proceed vs. postpone, aspiration risk modification, and whether to hold the drug.

---

## Files

| File | For |
|---|---|
| `SKILL.md` | Claude · OpenClaw · Perplexity Computer — native skill install |
| `system-prompt.md` | ChatGPT · Gemini · Perplexity Spaces — paste as Instructions |

## How to Use

**Claude:** Drop `SKILL.md` into `.claude/skills/glp1-endoscopy-pre-procedure/`. Auto-triggers when you ask about GLP-1 RA and endoscopy.

**OpenClaw / Perplexity Computer:** Install `SKILL.md` directly via the platform's skill/tool installer.

**ChatGPT Custom GPT:** GPT Builder → Configure → Instructions → paste `system-prompt.md`.

**ChatGPT Projects:** Project → Instructions → paste `system-prompt.md`.

**Gemini:** gem.google.com → Create a Gem → Instructions → paste `system-prompt.md`.

**Perplexity Spaces:** Space → Settings → Instructions → paste `system-prompt.md`.

---

## Example

> "62M T2DM on weekly semaglutide 1mg, scheduled for elective EGD tomorrow. Complaining of nausea today."

→ **Symptomatic patient.** Do NOT hold semaglutide (diabetes indication). Consider postponing + clear liquid diet today. If proceeding, use RSI and ensure airway cover.

---

## Source
Hashash JG, Thompson CC, Wang AY. AGA Rapid Clinical Practice Update on Management of Patients Taking GLP-1 Receptor Agonists Prior to Endoscopy. *Clin Gastroenterol Hepatol* 2024;22:705–707. DOI: [10.1016/j.cgh.2023.11.002](https://doi.org/10.1016/j.cgh.2023.11.002)
