---
name: carelink-interpreter
description: Systematically interpret a Medtronic CareLink or MiniMed 780G Daily Review download in a structured 6-step clinical workflow — covering Time in Range, insulin delivery, day/night patterns, hypo and hyperglycemia root causes, and a prioritised action plan. Trigger when a clinician uploads or shares a CareLink report, MiniMed download, 780G Daily Review, pump download, or asks to review a patient's CGM or insulin pump data.
---

# CareLink / MiniMed 780G Report Interpreter

## BEFORE YOU BEGIN

When a CareLink file is uploaded, read it carefully. Identify:
1. **Report type** — Daily Review (780G/770G) vs classic CareLink (Therapy Management Dashboard, Episode Summary, Sensor & Meter Overview)
2. **Device** — MiniMed 780G (SmartGuard Auto Mode = closed-loop), 770G, 640G, or older open-loop pump
3. **Date range** — How many days of data?
4. **Units** — mg/dL or mmol/L (multiply mmol/L × 18.0182 to convert)

> **For MiniMed 780G Daily Review:** The report shows TDD, Total Basal %, Total Bolus %, food bolus, Auto Correction bolus, and daily glucose traces with Time in Range (TIR) bars on the right. This is the primary format for current closed-loop pump users.

---

## STEP 1 — TIME IN RANGE SCORECARD (Start here. Always.)

### Extract from the report:
- % time in range (70–180 mg/dL / 3.9–10.0 mmol/L)
- % time above range (>180 mg/dL)
- % time very high (>250 mg/dL / >13.9 mmol/L)
- % time below range (<70 mg/dL / <3.9 mmol/L)
- % time very low (<54 mg/dL / <3.0 mmol/L)

### Targets (ADA/International Consensus 2019):

| Metric | Target (T1D / insulin-treated T2D) | Flag if... |
|---|---|---|
| TIR (70–180) | ≥70% | <70% needs action |
| Time above 180 | <25% | >25% = hyperglycaemia problem |
| Time above 250 | <5% | >5% = significant problem |
| Time below 70 | <4% | >4% = hypoglycaemia problem |
| Time below 54 | <1% | **ANY value is urgent** |

> Adjust target to ≥50% TIR for elderly or high-risk patients.

**Report findings:** State overall TIR, whether targets are met, and on which days control was best vs worst. Note day-to-day variability — consistent vs erratic patterns have different causes.

---

## STEP 2 — INSULIN DELIVERY ANALYSIS

### For MiniMed 780G Daily Review, extract per day:
- **TDD** (Total Daily Dose in Units)
- **Total Basal %** and units
- **Total Bolus %** and units → broken into:
  - **Food Bolus** (user-initiated, meal-related)
  - **Auto Correction** (SmartGuard-delivered without user input)

### Interpret:

**TDD trend:**
- Rising TDD over days → insulin needs increasing, or carbohydrate intake rising
- Falling TDD → improving control, less Auto Correction needed, or reduced eating
- Marked day-to-day variability → erratic eating or lifestyle variation

**Basal/Bolus ratio:**
- Normal in closed-loop: ~30–40% basal, 60–70% bolus
- Basal >50% → check if SmartGuard is compensating for under-bolusing, or if basal rate is set too high
- Basal <25% → may suggest frequent manual suspends, or aggressive food bolusing

**Auto Correction bolus (780G only):**
- Auto Correction <20% of total bolus → SmartGuard managing minor corrections ✓
- Auto Correction 20–35% → system working reasonably, watch for patterns
- **Auto Correction >35%** → system compensating heavily → likely meal boluses are too small, ICR needs adjustment, or meal timing is off
- High Auto Correction with still-high TIR → system is coping; if TIR is poor, ICR or basal target needs review

---

## STEP 3 — PATTERN ANALYSIS (Read the glucose traces)

Work through the day in four segments. For each segment note: glucose level, trend direction, and what insulin was active.

### Overnight (12AM – 6AM):
- Flat, in-range trace → basal adequate ✓
- **Rising overnight** → basal too low, or dawn phenomenon (common 3–6AM rise)
- **Falling overnight / lows** → basal too high, or residual insulin from late correction
- In Auto Mode (780G): look for auto-basal activity (pink shading). Persistent overnight highs despite active auto-basal → consider raising SmartGuard glucose target

### Morning fasting / breakfast period (6AM – 10AM):
- Glucose at target on waking → overnight basal correct ✓
- **Waking high** → overnight basal insufficient OR dawn phenomenon
- **Post-breakfast spike >180** lasting >2 hours → breakfast ICR too low, or bolus given too late
- Check carb entry vs food bolus: are carbs consistently entered?

### Daytime / lunch / afternoon (10AM – 6PM):
- Post-meal peaks >250 mg/dL → review ICR for that meal period
- Correction boluses clustering at the same time each day → systematic ICR problem at that meal
- **Bolus overrides (negative correction)** → patient is reducing recommended bolus; counsel on trust in Bolus Wizard
- Delayed site change flag (>3.5 days between cannula fills) → check infusion site as cause of hyperglycaemia

### Evening / dinner / overnight transition (6PM – 12AM):
- Post-dinner spike → dinner ICR or portion size
- Late correction boluses → risk of overnight stacking; counsel on active insulin time
- **Nocturnal lows (11PM–5AM)** → review evening correction bolus doses and overnight basal

---

## STEP 4 — HYPOGLYCAEMIA ASSESSMENT

**If time below 70 is ≥4% or any time below 54 is present — address this before anything else.**

### Identify timing:
- **Nocturnal (11PM–5AM)** → overnight basal too high; counsel on evening bolus timing; in 780G, check if suspend-before-low is active
- **Post-meal (<3 hours after bolus)** → food bolus too large; ICR needs adjusting; counsel on bolus timing with meals
- **Fasting / between meals** → basal too high
- **Post-exercise** → counsel on temp basal or reduced bolus before activity

### CareLink Episode Summary hypo event types (if available):
| Event | Action |
|---|---|
| Basal Rate Increase | Review basal settings, including temp basals |
| Rapid Falling Sensor Rate | Counsel patient to act on falling CGM arrows |
| Bolus with Falling Sensor Rate | Reduce bolus when SG is already falling |
| Bolus Wizard Food Bolus | Review ICR and carb counting accuracy |
| Nocturnal Hypoglycaemia (11PM–5AM) | Review overnight basal; counsel on evening boluses |
| Multiple Correction Boluses | Educate on insulin stacking risk |
| Manual Bolus | Encourage Bolus Wizard use |

### 780G Auto Mode: check suspend events
- Suspend Before Low events → protective, expected ✓
- Suspend on Low → actual hypoglycaemia reached; more aggressive prevention needed
- Total suspend duration >2 hours/day → review overnight basal settings

---

## STEP 5 — HYPERGLYCAEMIA ASSESSMENT

### Identify dominant pattern — when does the glucose go high?

**Fasting / overnight high:**
- Dawn phenomenon (3–7AM rise) → increase overnight basal rate or raise SmartGuard target for that period
- Post-midnight high → insufficient evening correction or high-carb late meal

**Postprandial highs (consistent meal period):**
- Breakfast high every day → breakfast ICR too low, or bolus given after eating
- Lunch high → lunch ICR; check carb entry
- Dinner high → dinner ICR; consider dual/square bolus for higher-fat meals

**Site-change-related highs:**
- Glucose consistently rises 3–4 days after last set change → infusion site degrading; counsel on ≤3-day site rotation
- Glucose improves after set change → site occlusion confirmed

**Auto Correction clustering (780G):**
- Heavy Auto Correction at the same time each day → systematic meal bolus gap; adjust ICR for that period

### CareLink Episode Summary hyperglycaemia event types (if available):
| Event | Action |
|---|---|
| Rising Sensor Rate Without Bolus | Patient missing meal boluses; counsel on pre-meal bolus |
| Delayed Site Change | Reinforce ≤3-day infusion site rotation |
| Basal Rate Decrease | Review basal settings |
| Dawn Phenomenon (3AM–7AM) | Increase overnight basal or adjust SmartGuard target |
| Overcorrection of Hypoglycaemia | Counsel on appropriate low treatment amounts |
| Pump Suspends >60 min | Assess if suspend limits are set appropriately |

---

## STEP 6 — ADHERENCE & ENGAGEMENT FLAGS

Check these in the Adherence Report or Daily Review:

| Flag | Threshold | Action |
|---|---|---|
| Sensor wear | <5 days/week readings | Counsel on CGM wear benefits |
| BG readings (fingerstick) | <4/day | Discuss calibration/confirmation needs |
| Bolus Wizard use | <67% of boluses | Encourage Bolus Wizard for all meals |
| Bolus override (negative) | Frequent | Counsel on following Bolus Wizard |
| Manual boluses (no Bolus Wizard) | Present | Educate on Bolus Wizard accuracy |
| Infusion site interval | >3.5 days average | Counsel on ≤3-day rotation |
| Basal/Bolus ratio skewed | Basal >55% | Likely under-bolusing for meals |

---

## OUTPUT FORMAT — CLINICAL SUMMARY

After working through Steps 1–6, present findings as:

**Patient / Date Range:**

**GLYCAEMIC CONTROL SNAPSHOT**
- Overall TIR: X% (target ≥70%) — [Met / Not Met]
- Time above range: X% — [Met / Not Met]
- Time below range: X% — [Safe / Needs Attention]
- Best day: [date, TIR%] | Worst day: [date, TIR%]

**KEY FINDINGS**
1. [Most important pattern — e.g. "Consistent post-breakfast hyperglycaemia on all days"]
2. [Second finding — e.g. "High Auto Correction (avg 38%) suggests meal boluses are underestimating carbs"]
3. [Third finding — e.g. "No hypoglycaemia — lows <1%"]

**PRIORITISED ACTION PLAN**
1. ✅ Safety first: [Address any hypoglycaemia]
2. 🔧 Primary fix: [Biggest contributor to time out of range]
3. 📋 Counselling: [Behavioural/adherence point]
4. 🔄 Review in: [Timeframe — usually 2–4 weeks after any change]

---

## CLINICAL GUARDRAILS

- **Never adjust more than one insulin setting per review cycle.** Sequential changes allow attribution of effects.
- **In SmartGuard Auto Mode (780G):** the system compensates for basal errors with auto corrections. A high auto correction % often points to meal bolus gaps rather than basal problems.
- **Set change timing matters:** a glucose trace that is good days 1–2 after a set change but deteriorates by day 3–4 almost always points to infusion site degradation, not an insulin dose problem.
- **Sensor errors (interrupted traces, calibration flags)** can produce spurious glucose readings — always cross-check sensor data with fingerstick BG if in doubt.
- **Day-to-day variability** is normal. Look for patterns across ≥3 days before making any dose changes.
- **Do not interpret glucose excursions on sick days or travel days in isolation** — contextual events explain transient outliers.
- **CGM does not replace clinical judgment.** Download data supports decision-making but does not replace the full clinical picture (HbA1c, renal function, hypoglycaemia awareness, lifestyle context).

---

## SOURCE
- Medtronic CareLink™ Software Report Reference Guide (M995150AOU1_A, 2019)
- Medtronic CareLink Pro Report Reference Guide
- Petrovski G & Zivkovic M. "Five-step approach to interpreting Medtronic CareLink therapy management data." *Journal of Diabetes Science and Technology*, 2017. DOI: 10.1177/1932296817726553
- International Consensus on Time in Range. *Diabetes Care* 2019;42:1593–1603
