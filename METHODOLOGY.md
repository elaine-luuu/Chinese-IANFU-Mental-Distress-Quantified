# Methodology and Data Analysis Framework (updated Nov. 3)

## 1. Corpus
- Qiu, Su & Chen (2013): 12 narratives from 100+ cases (use Chinese source text where available; the English translation measures the translator as much as the survivor).
- Zhang Shuangbing, 《炮楼里的女人》 (2011): Shanxi survivors. Confirm N (reports range 48–123).
- Su & Chen, 《日军"慰安妇"全史》 (2025): direct testimony only; separate authorial narrative.
- Interviewer is part of the data: record collector, translator and editor for each passage.
- To verify before citing: Qiu, Su & Chen 2013; Kleinman; Soh 2008; Chinese emotion lexicon; DUTIR. Confirm N per source and how much of the 全史 is testimony.

## 2. Unit of analysis and design
- Unit: passage (segment), nested in survivor, nested in source/collector. 1,000 passages are not 1,000 independent observations.
- Tags: speaker (survivor/collector), life phase (prewar, capture, captivity, postwar, redress), survivor attributes, collector, edition/translation status.
- Results are patterns within a selected population (survivors who spoke), not prevalence for all victims.

## 3. Codebook (symptom-based, not polarity)
Intrusion, avoidance, shame/self-blame, fear of men, somatic complaint (incl. TCM terms), social exclusion (marriage, childbearing, village stigma).
- Avoidance markers (refusals, fragments, silence notes by collectors, flat delivery) are coded as data.
- Cross-map each code to DSM-5 PTSD clusters and ICD-11 (C)PTSD, with an "unmapped" category for culturally specific distress (H2/H3).

## 4. Measurement pipeline (H1)
1. OCR, clean, segment, tag.
2. Baselines: Chinese emotion lexicon (DUTIR) and generic sentiment.
3. Symptom classifier: fine-tuned Chinese transformer, or few-shot LLM prompting.
4. Validation: ~150 human-coded passages, two+ coders, Cohen's κ (target ≥ 0.6), accuracy, macro-F1 (target ≥ 0.7). Compare symptom classifier vs. baselines; show that sentiment misses flat-affect passages.
5. Check for known off-the-shelf sentiment classifier problems (cf. Holocaust-testimony precedents: Blanke et al. 2020; Gagnier 2026).

## 5. Statistical models
Outcome: presence/count of each symptom code per passage (and total distress index).
- M1 (H1): agreement metrics with bootstrap CIs; paired comparison of classifier vs. lexicon.
- M2 (life phase, H1/H3): mixed-effects logistic/Poisson regression, `distress ~ phase + attributes + (1 | survivor) + (1 | source)`; expect postwar > captivity.
- M3 (collector effect): survivors in multiple collections (e.g., Wan Aihua); `(1 | survivor)` + fixed collector effect; within-survivor comparison.
- M4 (H2): per-survivor coverage of DSM-5 clusters and ICD-11 CPTSD domains; compare proportion matched, with CIs.
- M5 (H3): share of passages coded somatic/social/unmapped; compare to emotion-word share.
- Small N: Bayesian multilevel models or cluster-robust/bootstrap by survivor; report effect sizes with intervals; multiple-comparison correction.

## 6. Robustness
- Chinese originals vs. translation; excluding collector-authored text; alternative codebook thresholds; leave-one-source-out; leave-one-survivor-out.

## 7. Optional extension: press coverage
Contingent on archive access (apply for fellowship if paid archives needed).
- Count testimony articles by outlet/year, normalized by volume; interrupted time series around independently coded triggers (code triggers separately from coverage).
- KWIC and collocates around 慰安妇.
- Represented distress via DUTIR and fine-tuned transformer; define "represented distress" explicitly.
- Frame classification: victimhood, survivor distress, state responsibility, denial rebuttal, compensation/legal, diplomacy/nationalism.
- Validate on ~100 human-coded articles (accuracy, F1). Treat low coverage cautiously (censorship vs. disinterest).

## 8. Limitations
Flat affect hides distress from text measures; testimonies are edited and translated; small, selected, nested sample; archive access unconfirmed.
