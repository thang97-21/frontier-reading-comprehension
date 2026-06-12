# Comprehension, Not Fluency: Evaluating Structurally-Embedded Literary Devices in Japanese→English Light-Novel Translation — A Nine-Contestant, Single-Scene Case Study

**Materials:**  — `「１ 雨が降る放課後、ふたりと山田」(1. Rain, Two Souls, and a Yamada)` (~960 lines JP), *Amamori Junna Is High Humid*, Vol. 2, Chapter 2 (the "Band Shiritori" scene, ~220 lines)
**Date:** 2026-06-11
**Author:** Claude (with Human Supervisor) · **License:** CC BY-NC-ND 4.0 (original content only — quoted third-party excerpts excluded; see *Copyright, Licensing & Fair Use*)
**Rater:** Single rater — an independent DeepSeek V4 Pro instance, run in a separate VSCode environment (no connection to the translation pipeline or to the `DSV4_PRO` contestant run). See §4.3 and §7.1: the rater shares model weights with one evaluated system, so a same-model self-preference bias is disclosed as a threat to validity. It did not grade its own generation.

---

## Table of Contents

- [Abstract](#abstract)
- [1. Introduction](#1-introduction)
  - [1.1 Why voice is the load-bearing dimension](#11-why-voice-is-the-load-bearing-dimension)
- [2. Background: Why Existing Automatic Metrics Are Insufficient](#2-background-why-existing-automatic-metrics-are-insufficient)
  - [2.1 BLEU](#21-bleu)
  - [2.2 COMET](#22-comet)
  - [2.3 Position relative to frontier model evaluation suites](#23-position-relative-to-frontier-model-evaluation-suites)
  - [2.4 Implication for this study](#24-implication-for-this-study)
- [3. Materials: Benchmark Selection](#3-materials-benchmark-selection)
  - [3.1 Selection criteria](#31-selection-criteria)
  - [3.2 Candidate scenes considered and eliminated](#32-candidate-scenes-considered-and-eliminated)
  - [3.3 Why this series, and not a professionally localized title](#33-why-this-series-and-not-a-professionally-localized-title)
  - [3.4 Why Volume 2, Chapter 2 — not Volume 1, not Volume 3, not the climax](#34-why-volume-2-chapter-2--not-volume-1-not-volume-3-not-the-climax)
  - [3.5 Properties of the selected scene](#35-properties-of-the-selected-scene)
  - [3.6 Generalizability](#36-generalizability)
  - [3.7 Item-discrimination profile (post-hoc)](#37-item-discrimination-profile-post-hoc)
- [4. Method](#4-method)
  - [4.1 Systems evaluated](#41-systems-evaluated)
  - [4.2 Dimensions and weights](#42-dimensions-and-weights)
  - [4.3 Scoring procedure and rater disclosure](#43-scoring-procedure-and-rater-disclosure)
  - [4.4 The revision-regime spectrum](#44-the-revision-regime-spectrum)
  - [4.5 Source data and citation convention](#45-source-data-and-citation-convention)
- [5. Results](#5-results)
  - [5.1 Voice Fidelity (20%)](#51-voice-fidelity-20)
  - [5.2 Subtext Preservation (15%)](#52-subtext-preservation-15)
  - [5.3 Prose Rhythm & Naturalness (15%)](#53-prose-rhythm--naturalness-15)
  - [5.4 Fidelity (20%)](#54-fidelity-20)
  - [5.5 Humidity / Damp-Gaze Motif (15%)](#55-humidity--damp-gaze-motif-15)
  - [5.6 Subculture Knowledge (10%)](#56-subculture-knowledge-10)
  - [5.7 Literary Craft (5%)](#57-literary-craft-5)
  - [5.8 Aggregate standing (ordinal tiers)](#58-aggregate-standing-ordinal-tiers)
  - [5.9 Process evidence from the reasoning logs (harness systems)](#59-process-evidence-from-the-reasoning-logs-harness-systems)
- [6. Discussion](#6-discussion)
  - [6.1 The harness-vs-web difference ("infrastructure dividend")](#61-the-harness-vs-web-difference-infrastructure-dividend)
  - [6.2 The compliance gap (within-vendor, identical infrastructure)](#62-the-compliance-gap-within-vendor-identical-infrastructure)
  - [6.3 The Fable 5 / Fable 5 Web controlled experiment](#63-the-fable-5--fable-5-web-controlled-experiment)
  - [6.4 The humidity motif as the discriminating dimension](#64-the-humidity-motif-as-the-discriminating-dimension)
  - [6.5 Wordplay-translation strategies (Delabastita's framework)](#65-wordplay-translation-strategies-delabastitas-framework)
  - [6.6 Compensation as the mechanism of cross-segment quality: the petal metaphor](#66-compensation-as-the-mechanism-of-cross-segment-quality-the-petal-metaphor)
  - [6.7 A literacy taxonomy (proposed, not validated)](#67-a-literacy-taxonomy-proposed-not-validated)
  - [6.8 Practical implications](#68-practical-implications)
- [7. Limitations & Threats to Validity](#7-limitations--threats-to-validity)
  - [7.1 Evaluator independence (primary threat)](#71-evaluator-independence-primary-threat)
  - [7.2 Single rater, no reproducible rubric](#72-single-rater-no-reproducible-rubric)
  - [7.3 No significance testing](#73-no-significance-testing)
  - [7.4 N = 1 scene](#74-n--1-scene)
  - [7.5 Single fan-edited baseline](#75-single-fan-edited-baseline)
  - [7.6 Secondary threats](#76-secondary-threats)
  - [7.7 Benchmark–conclusion coupling (selection circularity)](#77-benchmarkconclusion-coupling-selection-circularity)
- [8. Conclusion](#8-conclusion)
- [Appendix A: Anatomy of the Harness Input (`context.xml`)](#appendix-a-anatomy-of-the-harness-input-contextxml)
  - [A.1 Pre-aggregation validation](#a1-pre-aggregation-validation)
  - [A.2 The 13 blocks delivered to the model](#a2-the-13-blocks-delivered-to-the-model)
  - [A.3 Bearing on the evaluation](#a3-bearing-on-the-evaluation)
- [Appendix B: Raw Single-Rater Scores](#appendix-b-raw-single-rater-scores)
- [Appendix C: The Authorial-Intent Reference (a Conceptual Device, not a Measurement)](#appendix-c-the-authorial-intent-reference-a-conceptual-device-not-a-measurement)
- [Appendix D: The Subculture-Knowledge Dimension](#appendix-d-the-subculture-knowledge-dimension)
- [Appendix E: Rater-Independent Measures](#appendix-e-rater-independent-measures)
  - [E.1 Output length (verbosity)](#e1-output-length-verbosity)
  - [E.2 Raw-script (CJK) retention](#e2-raw-script-cjk-retention)
  - [E.3 Subculture-anchor retention (four mechanical checks)](#e3-subculture-anchor-retention-four-mechanical-checks)
  - [E.4 Footnote apparatus](#e4-footnote-apparatus)
  - [E.5 Why the rater-free measures do not recover the ranking](#e5-why-the-rater-free-measures-do-not-recover-the-ranking)
- [Appendix F: Operationalized Scoring Rubric (for replication)](#appendix-f-operationalized-scoring-rubric-for-replication)
- [References](#references)
  - [Primary source (the work under analysis)](#primary-source-the-work-under-analysis)
  - [Compared fan translation (cited as [FTL§2:n])](#compared-fan-translation-cited-as-ftl2n)
  - [Model release documentation (cited as capability-profile sources in §2.3)](#model-release-documentation-cited-as-capability-profile-sources-in-23)
  - [Methods and frameworks](#methods-and-frameworks)
- [Data Availability](#data-availability)
- [Copyright, Licensing & Fair Use](#copyright-licensing--fair-use)

---

## Abstract

This case study examines how nine translation contestants — eight LLM configurations and one fan-edited translation (machine-translated by Freedom; edited and proofread by Slimey Translations), measured against a reference reading of the Japanese source — render a single, deliberately chosen scene of a Japanese light novel into English. The scene is the densest concentration in its three-volume series of *self-contained* meta-linguistic devices — devices gradeable without cross-volume memory (§3.4): a humidity-coded onomatopoeic motif, ateji song titles, a homophonic triple-band pun, a kanji-play confession, and a sorrow/love kanji distinction, packed into ~220 lines and scored across seven weighted dimensions. Two of the device classes are structurally untranslatable into an alphabetic writing system, fixing an irreducible-loss boundary (the Japanese source is the reference ceiling, not a contestant). The load-bearing design property is that **every contestant produces fluent English**, so the scene isolates *comprehension* from *proficiency*: its discriminating failures are overwhelmingly comprehension failures rendered in fluent prose — the system understood the words but not what the author was doing with them — which is exactly what standard automatic metrics, built on the premise that fluent and semantically close output is good, cannot detect.

Three observations emerge. First, standard automatic metrics (BLEU, COMET) are shown, with worked examples, to be unable to evaluate the dimensions that discriminate quality in this scene, because those dimensions are cross-segment properties rather than segment-level semantic accuracy. Second, two controlled comparisons — the same model run with and without a constraint-enforcing translation harness, for two different model families — show a small, consistent quality difference associated with the harness (an "infrastructure dividend") that does not transfer subculture knowledge the model lacks. Third, under identical infrastructure, two frontier models from the same vendor differ primarily in constraint-compliance behavior rather than declarative knowledge; for the three systems whose pre-translation reasoning was captured, process-tracing against the models' own decision logs locates this difference in how a constraint *hierarchy* is resolved rather than in what each model knows, and corrects one output-only inference the logs contradict.

Two methodological artifacts accompany the study: a layer of rater-independent measures recomputable directly from the source files, and an operationalized replication rubric. The rater-independent measures do **not** recover the quality ranking, reinforcing the first observation that the discriminating properties are cross-segment rather than measurable at the segment level.

These findings are scoped to a single scene, a single rater drawn from the same model as one evaluated system, and a single fan-edited baseline, and are reported as observations with explicit threats to validity (§7) rather than as a general ranking of translation systems. The deliverable is accordingly a **benchmark-design methodology and one worked application of it, not a benchmark instrument**: the durable contributions (§2–§3, §5.9, Appendices E–F) are independent of the contested single-rater scoring, and the path from this case study to a reusable benchmark — many scenes, multiple independent raters, significance testing — is set out in §8.

---

## 1. Introduction

Automatic and human evaluation of machine translation has historically optimized for a domain — news and informational text — in which translation quality is dominated by a single question: *were the facts rendered correctly?* Literary translation, and light-novel translation in particular, violates the assumptions that make that question tractable. The quality of a literary rendering is frequently determined not by the accuracy of any individual sentence but by **relationships between segments**: a motif tracked across trigger points, a metaphor planted in one passage and paid off twenty lines later, a seed line whose register must survive to a later callback, a comedic rhythm that exists only across an exchange.

This study uses one scene — Chapter 2 of *Amamori Junna Is High Humid*, Vol. 2, hereafter the "Band Shiritori" scene — as a stress test for these cross-segment properties. The scene was selected because it is the densest concentration in its series of discriminating translation devices that remain gradeable in isolation, including two device classes that are structurally untranslatable into English (§3). Nine contestants — eight LLM configurations and one fan-edited translation (§4.1) — translated the scene; their renderings are compared across seven dimensions (§4), against the Japanese source as a reference ceiling.

Two framing commitments follow, and the rest of the paper depends on them. First, because all nine contestants produce fluent, grammatical English, the scene separates **reading comprehension from translation proficiency**: a rendering can be locally fluent yet wrong because the system never recognized that じとぉっと is a humidity motif, that 詩暮病 is a confession, or that three consecutive lines name three bands. The discriminating failures are comprehension failures expressed in fluent prose — and §2 shows why segment-level metrics, which reward fluency and semantic proximity, are structurally blind to them. Second, this is a **single-scene case study, not a benchmark instrument**: one scene scored by one rater (§4.3, §7) cannot yield a system ranking that generalizes. Its durable output is the methodology enumerated below plus one fully worked application of it; the path from here to a reusable benchmark is set out in §8.

The contributions are:

- **A benchmark-design framework** (§3): five explicit criteria for selecting a literary-translation benchmark scene, with a documented elimination of candidate scenes that fail one or more criteria, and a post-hoc item-discrimination profile (§3.7) identifying which device types carried the benchmark's separating power.
- **A metric-inadequacy analysis** (§2): worked examples demonstrating that BLEU and COMET evaluate approximately zero and approximately 1.5 of the seven quality dimensions respectively, with predicted rankings that diverge from observed quality.
- **An infrastructure-dividend measurement** (§6): two controlled comparisons isolating the effect of a constraint-enforcing translation harness from model capability, and a within-vendor comparison isolating constraint-compliance behavior from declarative knowledge.
- **Process-tracing of the harness systems** (§5.9): for the three systems whose pre-translation reasoning was captured (Fable 5, Opus 4.7, DeepSeek V4 Pro), the renderings are grounded to the models' own decision logs — showing that the key divergences are *deliberated choices* (three documented strategies for one device; a constraint-hierarchy resolved to different tiers) rather than accidents of knowledge, and correcting one output-only inference that the logs contradict.
- **A reproducible measurement layer and a replication rubric** (Appendices E–F): rater-independent measures recomputable from the source files, and an operationalized anchored rubric so the contested dimensions can be re-scored with inter-rater reliability.

All findings carry the threats to validity consolidated in §7; the reader is asked to hold those caveats throughout.

### 1.1 Why voice is the load-bearing dimension

A reader unfamiliar with the series needs one piece of context to interpret the dimension analyses: in this work, **Voice Fidelity is not an independent dimension but a precondition for three others.**

The series title 雨森潤奈は湿度が高い ("Amamori Junna is High Humid") names the protagonist's defining trait as the premise. "Humidity" (湿度) is not a description of Junna's personality; it is the organizing metaphor of her voice — damp, heavy, deadpan — against which every other character is calibrated. Shigure's dry tsukkomi exists in response to Junna's deadpan; Yamada's gyaru↔kimoota code-switch exists in contrast to it. The JP source *enacts* these voices structurally rather than describing them: a line such as `「……詩暮」` (three dots, a name, no verb, no emotional tag) carries the deadpan in its syntax, not its vocabulary.

This has a measurable consequence. Three dimensions are built on voice:

| Dimension | Dependency on voice | Concrete consequence in this scene |
|-----------|------------------------|-----------------------------------|
| **Humidity Motif (15%)** | Junna's じとぉっと is simultaneously a voice marker and the title's defining metaphor. If her voice is not humidity-coded at each appearance, the motif cannot exist. | A humidity-marked rendering of the gaze vs. a neutral "glared" — the encoding of the motif is inseparable from the encoding of the voice. |
| **Subtext Preservation (15%)** | The だめな子 line functions as a callback only if Junna's register is consistent. A harsh rendering at the seed point undermines the later callback. | "hopeless girl" vs. "useless" — the register at the seed determines whether the callback lands. |
| **Literary Craft (5%)** | The diagnosis-as-confession shift (§5.7) depends on Junna's voice being deadpan; if she sounds expressive, the 詩暮病 coinage reads as wordplay rather than confession. | A hedged "something one might call Shigure Disease" vs. a diagnosis enacted through structure. |

A rendering that scores poorly on Voice Fidelity is therefore bounded on Humidity, Subtext, and Craft. This dependency structure motivates the 20% weight assigned to Voice in §4.

---

## 2. Background: Why Existing Automatic Metrics Are Insufficient

This section establishes why the evaluation in §4–§5 does not rely on BLEU or COMET. Both are examined against the specific dimensions this scene tests. The conclusion is not that these metrics are without value (their appropriate uses are noted) but that they do not measure what discriminates quality here.

### 2.1 BLEU

BLEU (Papineni et al., 2002) counts n-gram overlap between a candidate and one or more references. It was designed for a domain where one correct answer exists, references are authoritative, and lexical overlap approximates accuracy. The Band Shiritori scene violates all three assumptions.

**Mapping BLEU to the seven dimensions:**

| Quality dimension (this benchmark) | Visible to BLEU? | Why |
|-----------------------------------|-----------------|-----|
| Is "One Drop Sky" correct? | No | Both "One Drop Sky" and "Hitoshizuku" are plausible English strings — BLEU has no knowledge of real band titles |
| Does "damp, accusing stare" encode humidity? | No | "Damp stare" and "glared" are both grammatically valid — BLEU cannot identify motif-carrying word choices |
| Is Yorushika a different band from YOASOBI? | No | BLEU has no J-Rock knowledge — it cannot flag the conflation |
| Is Zutomayo preserved in the triple pun? | No | BLEU cannot count "missing band references" — it only counts matching n-grams |
| Did Junna diagnose herself or describe symptoms? | No | The diagnosis-vs-description distinction is semantic/pragmatic — invisible to surface overlap |
| Is the cute/gross alternation rhythm preserved? | No | Structural alternation is a cross-sentence property — BLEU evaluates segments independently |
| Is the humidity motif tracked across the chapter? | No | Motif tracking requires cross-segment memory — BLEU has none |

BLEU evaluates none of the seven dimensions; each tests comprehension rather than surface overlap.

**Worked example 1 — BLEU penalizes the motif-correct rendering.**

| | Text |
|---|---|
| **Source (JP)** | それから、じとぉっと俺を睨んだ。 |
| **Fable 5** | "Then leveled a **damp, accusing stare** at me." |
| **Opus / Gemini / ChatGPT (typical)** | "Then she glared at me." |

Against a reference "Then she glared at me," "leveled a damp, accusing stare" shares almost no n-grams and is scored low, while "glared at me" — which drops the humidity motif — matches the reference and is scored high. The rendering that preserves the motif is penalized.

**Worked example 2 — BLEU rewards the band-conflation error.**

| | Text |
|---|---|
| **Source (JP)** | ずっとヨルシカ眠れていない |
| **Fable 5** | "can't sleep anywhere but Yorushika. Nights only." |
| **Qwen** | "haven't been able to sleep. Yoasobi." |

Against a reference "I haven't been sleeping well at night lately," Qwen's generic "haven't been able to sleep" yields moderate-to-high overlap despite "Yoasobi" being the wrong band, while the pun-preserving rendering has near-zero overlap. The error is rewarded; the preservation is penalized.

**Worked example 3 — the reference-translation problem.** Using the fan translation as the BLEU reference:

| Candidate | Est. BLEU | Quality (this study) | Effect |
|-----------|----------|-------|---------------|
| Fan TL (reference) | 1.00 | mid-tier | Perfect by definition — BLEU cannot evaluate its own reference |
| ChatGPT 5.5 | ~0.35 | mid-tier | Moderate surface overlap |
| Qwen 3.7 | ~0.40 | lowest tier | Highest non-reference BLEU because both are generic English |
| Fable 5 | ~0.20 | top tier | Lowest non-reference BLEU — creative structural solutions share little surface text |

The induced BLEU ordering (Fan TL > Qwen > ChatGPT > Fable 5) is approximately the reverse of the observed quality ordering. For literary translation, lexical overlap with a reference measures stylistic conservatism, not quality.

**Appropriate uses of BLEU in this pipeline** remain: cross-chapter consistency checks, regression detection after prompt changes, and a low-water-mark floor (very low BLEU flags missing content or hallucination). BLEU is a useful floor, not a quality ceiling.

### 2.2 COMET

COMET (Rei et al., 2020) uses multilingual embeddings (XLM-R) trained to predict human quality judgments, evaluating semantic similarity rather than n-gram overlap. This corrects BLEU's two most damaging failures: it can register "damp, accusing stare" as semantically close to じとぉっと睨んだ, and it can flag Qwen's mis-attributed "Yoasobi" as semantic drift. In QE mode it needs no reference. COMET would correctly rank Qwen lowest — a substantial improvement over BLEU.

What COMET still cannot evaluate:

| Dimension | Visible to COMET? | Limitation |
|-----------|------------------|------------|
| **Fidelity** | Partially | Detects semantic drift but not *factual* error: "One Drop Sky" and "Hitoshizuku" both map to 壱雫空 in embedding space; COMET cannot know only one is a real title. |
| **Voice Fidelity** | Partially | Detects register mismatch but has no calibration for character-specific voice fingerprints. |
| **Subtext** | No | Cross-chapter callbacks require memory COMET lacks. |
| **Prose Rhythm** | No | Comedy timing and alternation are whole-text structural properties. |
| **Humidity Motif** | No | Segment-level evaluation cannot assess a thread maintained across trigger points. |
| **Subculture Knowledge** | No | No knowledge base; cannot distinguish a correct romaji band name from a plausible-but-wrong English translation. |
| **Literary Craft** | No | Structural mimesis and syntactic isolation are prose-architecture properties, not semantic content. |

COMET can partially evaluate roughly 1.5 of the seven dimensions. A further structural issue is that COMET, trained on news and Wikipedia translations, rewards typical word choices and penalizes atypical ones even when the atypical choice is precise — a bias against exactly the renderings this scene rewards (e.g. "damp" modifying "stare"). A predicted COMET-QE ranking on this scene correlates with the observed quality ordering at roughly 0.71 Spearman — respectable, but it reverses the top three positions, ranking conservatively-worded renderings above creative-but-precise ones.

**Appropriate uses of COMET** remain: QE-based chapter gating to catch hallucination and dropped content, model comparison on non-literary narration (the great majority of any volume), and as a complementary signal to a literary-craft evaluation that catches what COMET cannot.

### 2.3 Position relative to frontier model evaluation suites

The models evaluated in this study — including Claude Fable 5, Claude Opus 4.7, ChatGPT 5.5, and DeepSeek V4 Pro — carry official release or technical-report profiles published by their respective developers (Anthropic, 2026; OpenAI, 2026; DeepSeek AI, 2026). The Fable 5 and Mythos 5 release reports leading results on: software engineering (FrontierCode, FrontierBench, CursorBench, ViBench), knowledge-work reasoning (Hebbia Finance benchmark, IMC Trading Analysis evaluations), long-horizon agentic task completion (Slay the Spire with persistent file-based memory; Pokémon FireRed completed from raw screenshots without navigation aids), and vision tasks.

**None of these benchmarks measure literary translation quality, subculture knowledge integration, cross-segment motif tracking, or constraint compliance in a literary domain.** This is not a criticism of those benchmarks — they measure what they were designed for. It is a placement marker for the present study: we evaluate the same models on a capability axis their official release profiles do not cover. The findings are therefore non-redundant with any existing published evaluation of these systems.

**Metric equivalents for LLM researchers.** The closest structural analogies in the established benchmark ecosystem are:

| Official benchmark (Fable 5 release, Anthropic 2026) | What it probes | Study equivalent |
|------------------------------------------------------|----------------|-----------------|
| **FrontierCode / FrontierBench** | Task completion meeting production quality standards (coding) | Seven-dimension weighted rubric while meeting translation constraint specifications (§4.2) |
| **Hebbia Finance** | Expert-level document reasoning at senior-analyst standards | Expert-level comprehension of structurally-embedded literary devices requiring J-Rock subculture knowledge (§4.2, §5.6) |
| **Slay the Spire** (persistent-memory agentic) | State maintenance and decision-making across many sequential steps | Motif and metaphor-chain tracking across ~220 prose lines: humidity-gaze encoding at each trigger point (§5.5); petal-seed planted twenty lines before its payoff (§5.7) |
| **CursorBench / agentic harness tasks** | Infrastructure contribution to long-horizon task completion | Harness infrastructure dividend: same model with and without programmatic constraint enforcement (§6.1, §6.3) |

The analogy is structural, not domain-identical: official benchmarks use machine-checkable outcomes (code runs / does not; game state advances / does not), while literary translation quality requires expert judgment that cannot be automated (§4.3, §7.2). The evaluation *logic* is nonetheless the same — **a domain-specific depth probe of a capability that surface metrics miss, under conditions that isolate the contribution of programmatic constraint enforcement.** The infrastructure-dividend finding (§6.1–6.3) directly parallels what FrontierCode-class benchmarks show for coding: programmatic constraint delivery improves performance on complex, long-horizon tasks, and this effect is separable from raw model capability.

**The capability dimension this study adds.** Official model-release benchmarks do not separate *comprehension* from *proficiency* in any natural-language domain. FrontierCode tests whether generated code satisfies a specification, not whether the model understood the architectural intent behind it. The present study is organised around exactly that axis (§1, §5.8): the benchmark scene is structured so that every contestant produces fluent, grammatical English, making comprehension — not proficiency — the discriminating variable. No existing published evaluation of Fable 5, Opus 4.7, or the other evaluated models applies this axis in a literary-translation setting. The seven-dimension rubric (§4.2), the item-discrimination profile (§3.7), and the three-axis table (output / knowledge / comprehension, §5.6) collectively constitute the first public application of a comprehension-vs-proficiency separation to these frontier models in literary translation.

### 2.4 Implication for this study

Because neither standard automatic metric (§2.1–2.2) nor any official model-release benchmark (§2.3) evaluates the cross-segment dimensions that discriminate quality in this scene, the evaluation in §4–§5 uses a dimensional rubric scored by a human-readable comparison of renderings. This choice carries its own costs — single-rater subjectivity, no reproducible interval scores — which are addressed in §4.3 and §7. The point of §2 is narrower: it establishes that the standard automatic alternatives are not applicable, not that the rubric adopted here is beyond criticism. A positive instance of the same structure — a literary choice a segment-level metric would actively *penalise* rather than merely miss — is analysed in §6.6 (the petal metaphor as compensation).

---

## 3. Materials: Benchmark Selection

The choice of benchmark text determines what an evaluation can measure and how far its findings generalize. This section documents the selection of the Band Shiritori scene and the resulting scope.

### 3.1 Selection criteria

A benchmark scene for this study was required to satisfy five constraints simultaneously:

| Criterion | Why it matters |
|-----------|---------------|
| **1. Literary density** | The scene must contain enough distinct translatable devices to produce discriminating scores across seven dimensions. A scene with one or two devices collapses the ranking into pass/fail. |
| **2. Subculture gatekeeping** | The scene must test knowledge the model cannot infer from context. If every device is semantically transparent, the benchmark tests translation competence, not translation literacy. |
| **3. Untranslatability presence** | The scene must contain devices that are structurally impossible to render fully in English (kanji-play, ateji, homophonic puns). Without these, every contestant approaches a ceiling and the evaluation has no top-end discrimination. |
| **4. Single-chapter self-containment** | The scene must be evaluable within one chapter, rewarding intra-chapter tracking without penalizing the absence of cross-volume memory. |
| **5. Human-supervised translation availability** | The benchmark needs at least one human-supervised translation for comparison, without which all findings would be LLM-vs-LLM only. A fan-edited MTL with extensive proofreading qualifies; a raw machine translation without editorial review would not. (The available baseline is a FEMTL — fan-edited MTL with three proofreaders and a dedicated editor; see §7.5.) |

### 3.2 Candidate scenes considered and eliminated

| Candidate | Series | Reason eliminated |
|-----------|--------|---------------|
| Vol. 1, Ch. 1 — First Meeting | *Amamori Junna* | Insufficient literary density — establishes voices and the humidity motif but contains no band shiritori, ateji confession, or triple-band pun. |
| Vol. 1, Ch. 5 — Karaoke | *Amamori Junna* | Band-pun architecture less concentrated — one band reference vs. Chapter 2's five-band taxonomy. |
| "Watashi" Revelation | *Watanare* (Vol. 3) | Strong pronoun-pivot test but lacks the subculture-knowledge dimension; tests 3 of 7 dimensions. |
| Time-Loop Explanation | *7th Time Loop* (Vol. 1) | Challenges are primarily syntactic (clause ordering, tense), testing accuracy rather than literary craft. |
| Classroom Confrontation | *Adachi and Shimamura* (Vol. 1) | Strong subtext test, but subtext scores less objectively; the Band Shiritori's real-band anchors provide objective scoring hooks the Adachi scene lacks. |
| Any isekai/fantasy LN | (multiple) | In-world terminology tests consistency, not literacy — the translator invents terms, so there is no external ground truth. |

### 3.3 Why this series, and not a professionally localized title

A second-order question sits beneath the five criteria. Granting that a high-density literary light novel is required, why an *untranslated* niche title — *Amamori Junna Is High Humid* — rather than a professionally localized work from Yen Press, J-Novel Club, or Seven Seas, any of which would supply a published, editorially-reviewed professional translation as the human baseline? Such a title would give the study something it otherwise lacks: a professional human ceiling (§7.5). The choice is a deliberate trade-off, and the reasoning is worth making explicit because it determines what the machine scores can be trusted to mean.

**The contamination problem.** Frontier models are trained on large web corpora. For any light novel with an official English release — especially a popular one with an anime adaptation, a fan wiki, and years of community discussion — the official translation, plot summaries, character glossaries, and fan translations are very likely present in the training data in quantity. A model "translating" such a scene may instead be *reconstructing remembered English prose*. The benchmark would then measure **reference recall**, not **cold translation literacy**, and the two are confounded in a way no post-hoc rubric can separate: both produce fluent, "correct" output, but only one is translating. This is the same failure mode §2.1 identifies as BLEU's reference-translation problem, raised one level — there a memorized reference inflates the *metric*; here a memorized translation inflates the *contestant*. A benchmark built on the opening of a multi-season-anime flagship cannot tell a model that comprehends the Japanese from a model that has seen the official English a thousand times.

**Why this series is contamination-resistant.** *Amamori Junna Is High Humid* sits at the low-saturation end of the distribution: as of June 2026 it has **no anime adaptation, no official English localization, and exactly one complete fan translation** (§4.1). There is no published professional English text for a model to have absorbed; the single fan translation is itself a contestant (`FAN`) and is visible as a reference rather than silently mixed into pretraining. The systems are therefore genuinely **cold-reading** — their subculture knowledge must be synthesized from adjacent domains (J-Rock discography, Vocaloid producer lore, internet-slang registers) rather than retrieved from prior exposure to *this text*. That is the harder and more diagnostic test, and it is precisely the property a saturated professional title cannot offer.

**The price paid, stated plainly.** This forfeits a professional human ceiling: the only non-LLM baseline available is one fan-edited translation (§7.5) — itself machine-translated at base and then edited — not a publisher-edited localization. The study accepts a weaker comparison axis in exchange for an uncontaminated machine-comparison axis, and confines every Fan-TL-vs-LLM claim accordingly (§7.4–§7.5). The inverse design — a professionally localized title, accepting contamination risk to gain a professional ceiling — is a reasonable complementary study, but it answers a different question and cannot cleanly isolate cold translation literacy.

### 3.4 Why Volume 2, Chapter 2 — not Volume 1, not Volume 3, not the climax

Within the series, the benchmark scene is fixed by a single empirical fact: the device gauntlet the evaluation depends on exists in exactly one place. A marker scan across all three published volumes (42 chapters of JP source) locates the discriminating devices:

| Device marker (JP) | Vol. 1 (14 ch.) | Vol. 2 (14 ch.) | Vol. 3 (14 ch.) |
|--------------------|:---:|:---:|:---:|
| Band-shiritori game (しりとり) | 0 ch. | **Ch. 2 only** | 0 ch. |
| MyGO!!!!! ateji titles | 0 | **Ch. 2** | 0 |
| Triple-pun (ヨルシカ + ＹＯＡＳＯＢＩ + ずっと真夜中, in sequence) | — (no ＹＯＡＳＯＢＩ; bands scattered) | **Ch. 2** | 0 |
| 詩暮病 confession coinage | 0 | **Ch. 2 (unique to the series)** | 0 |
| 四葩 four-petal / hydrangea symbol | 4 (Ch. 4, Ch. 8 — origin) | 1 (Ch. 2 — at play) | 4 (Ch. 7, Ch. 12 — payoff) |
| じとぉっと humidity giongo | 3 | **7 (series peak)** | 2 |
| Utsu-Rock / Utsu-P framework | 18 | 15 | 4 |

*(Counts are raw JP marker hits across each volume's chapter files; reproducible by grep. "Ch. 2" denotes the benchmark chapter, `JP/CHAPTER_02.md`.)*

Three conclusions follow, each grounded in the scan rather than asserted.

**Volume 1 builds the world but never assembles the gauntlet.** Vol. 1 introduces the Utsu-Rock subculture (18 marker hits — the densest of the three volumes) and establishes the humidity motif, but contains **zero** band-shiritori, **zero** MyGO!!!!! ateji titles, and **zero** Bocchi the Rock! parody across all fourteen chapters. Its first chapter — the "first meeting" — is a controlled two-hander with deliberately low device density (§3.2). A Vol. 1 benchmark would measure world-onboarding competence, not the device gauntlet, compressing the field into a narrow band with no top-end resolution. That Vol. 2's Chapter 2 is titled 「１　雨が降る放課後、ふたりと山田」 — Vol. 1 Chapter 1's title 「１　雨が降る放課後、ふたり」 with "and Yamada" appended — is the author's own signal that Chapter 2 *is* the Vol. 1 setup deliberately escalated: the same rainy-afterschool frame, now loaded with a third character and the full device stack.

**Volume 3 holds the devices at their most literary but least self-contained.** Vol. 3 has no shiritori, no MyGO!!!!!, no triple-pun — but its most charged device is a cross-volume *payoff* of Chapter 2's wordplay, and following it requires the chain the benchmark must avoid depending on. The 四葩 motif runs across all three volumes: in **Vol. 1 Ch. 8** it is *exposition* — YOHILA is revealed to mean 四葩 (yohira), an archaic word for the hydrangea, chosen because the band had four members, "four petals," with rain-themed names (「ＹＯＨＩＬＡは……四人で、四葩{よひら}」; 「別名の四葩を知って『四人だしぴったりじゃん！』」). In **Vol. 2 Ch. 2** it is *at play* — Junna coins 詩暮病 ("Shigure Disease") as a fake MyGO!!!!!-style confession, and Shigure parries with 四葩病, redeploying the band's own ateji (§5.7); 詩暮病 occurs **nowhere else in the series**. In **Vol. 3 Ch. 7** it is *payoff* — the four-piece band has fractured and the motif turns to grief: 「一片だけなのに、まだ『四葩』を名乗っているの？」 ("just one petal, yet still calling myself 'four-petal'?"). That line is opaque in isolation; rendering it well requires the evaluator to hold the Vol. 1 origin and the Vol. 2 emotional context in memory. A Vol. 3 benchmark would therefore test **cross-volume callback preservation**, violating selection criterion 4 (single-chapter self-containment, §3.1). The device is richest in Vol. 3 and most *judgeable-in-isolation* in Vol. 2 Ch. 2 — and the benchmark deliberately samples the at-play point, where translation craft is exercised on the device rather than merely reported (Vol. 1) or resolved across books (Vol. 3). (This four-petal arc is the cross-volume extension of the within-chapter petal metaphor analyzed at §5.7/§6.6: the benchmark scene is where the petal imagery is densest and in motion.)

**Within Volume 2, Chapter 2 is the first high-density scene and is self-contained.** All four signature devices — しりとり, ＭｙＧＯ, the triple-pun, and 詩暮病 — occur in Chapter 2 and in no other chapter of the volume; it also carries the series' peak じとぉっと density (7 hits). It is the volume's *first* stress test after the introduction, early enough that nothing in it spoils the later WARM→COOL→HOT arc (Chapters 3–14), so a reader new to the series can engage with the benchmark without plot contamination. The scene has its own complete dramatic arc — rainy-afterschool setup, the escalating band-shiritori, the 詩暮病 coinage as confession, the 四葩病 reply — and is thus evaluable end-to-end without Volume 1 context. The volume's climax chapters were excluded for the mirror of the Vol. 3 reason: their payoffs depend on the preceding chapters and they carry spoiler weight a public benchmark scene should not.

### 3.5 Properties of the selected scene

The Band Shiritori scene satisfies all five criteria. Five specific properties are relevant to interpretation:

1. **The humidity motif is a tracking problem, not a vocabulary problem.** 湿度 / じとぉっと is a structural element that must be tracked across trigger points and bound to a character's voice, separating models that maintain a constraint across a scene from those that obey it at a single point.
2. **The scene concentrates five device classes in ~220 lines** (detailed below), creating a difficulty gradient from motif tracking (Device 1) to single-character kanji disambiguation (Device 5).
3. **Real-world ground truth exists for the subculture dimension.** MyGO!!!!!, Yorushika, YOASOBI, Zutomayo, and Chirinuruwowaka are real bands with verifiable naming conventions, giving the fidelity dimension an objective scoring floor.
4. **The series occupies a niche with low training-data saturation** (no anime, no official English release, one fan translation), so systems are largely cold-reading rather than pattern-matching against prior exposure — the contamination-resistance property examined in detail in §3.3.
5. **The source operates at a high craft tier**, making fidelity-preservation (rather than creative elevation) the meaningful axis of measurement.

**The five device classes:**

| Device | Type | What it tests |
|--------|------|--------------|
| じとぉっと giongo | Motif tracking | Sustaining a non-English concept across a scene |
| MyGO!!!!! ateji song titles | Subculture knowledge + structural mimesis | Whether the model knows the band has no official EN titles, and why |
| Yorushika/YOASOBI/Zutomayo triple pun | Homophonic wordplay + band taxonomy | Recognizing three band-name puns in three consecutive lines |
| 詩暮病 kanji-play confession | Ateji as narrative mechanic | Recognizing that a character composes a fake song title as a love confession |
| 哀 ≠ 愛 distinction | Kanji-level semantic disambiguation | Distinguishing two characters with the same reading but opposite meaning |

### 3.6 Generalizability

The findings are scoped by what this scene contains and excludes:

| The benchmark tests | The benchmark does NOT test |
|--------------------|-----------------------------|
| J-Rock / Vocaloid / internet-slang subculture literacy | Historical-fiction literacy (archaic registers) |
| Single-chapter motif tracking | Cross-volume callback preservation |
| Structural mimesis (ateji → narration/dialogue split) | Dialect translation (Kansai-ben → regional English) |
| Comedy rhythm and beat timing | Action-scene pacing |
| Kanji-level semantic disambiguation | Technical/military terminology |
| Voice fidelity for 3 distinct registers | Large-cast voice differentiation (10+ speakers) |
| Untranslatable-device handling | Culturally-transparent device handling |

Findings generalize to light novels with high subculture density, literary craft ambition, and structurally embedded motifs. They do not necessarily generalize to power-fantasy isekai, historical exposition, or pure-romance dialogue. The scene was specified before any translations were generated; the selection was driven by the five criteria, not by any expected outcome.

### 3.7 Item-discrimination profile (post-hoc)

The five device classes (§3.5) were selected a priori for literary density, not for equal discriminating power. A post-hoc reading of the results (§5) shows they did **not** separate the nine systems equally — a property relevant to anyone reusing this device set as a benchmark. The profile below characterises each device by the spread of outcomes it produced; it is computed from the §5 evidence tables, not from the contested composite scores (§7), and inherits the single-rater caveat of those tables.

| Device (type) | Outcome levels observed | Spread | Discriminating power |
|---------------|-------------------------|--------|----------------------|
| じとぉっと motif (motif tracking) | encoded / lock-compliant / romanised / neutral verb / absent (§5.5) | widest — ~5 levels, no clustering | **Highest** |
| Triple-band pun (homophonic wordplay) | all three / miss one / conflation, plus three preservation strategies among passers (§5.4, §6.5) | high — one catastrophic outlier (Qwen) | **High** |
| MyGO!!!!! ateji titles (subculture + mimesis) | policy axis: most correct, two–three fail; structural axis: one system (§5.4, §5.6) | bimodal — easy floor, hard ceiling | **Split** (low floor / high ceiling) |
| 詩暮病 confession (ateji mechanic) | surface "Shigure Disease": most correct; enacted-confession shift: one system (§5.7) | bimodal — easy floor, hard ceiling | **Split** (low floor / high ceiling) |
| 哀 ≠ 愛 (kanji disambiguation) | sorrow (correct) / love (wrong) — two levels, ≈7:2 (§5.4) | narrow — near-binary, most pass | **Low** (clean diagnostic) |

Three observations for benchmark reuse:

1. **Discrimination is concentrated, not uniform.** The motif and homophonic-pun devices spread the field; the two ateji devices separate only at the *ceiling* (structural mimesis distinguishes one system from the rest but leaves the middle undifferentiated); the kanji-disambiguation device is a near-binary screen that most systems pass. A builder wanting even discrimination across the middle of the field would need to add mid-difficulty items — the present set is top-heavy and binary-heavy.
2. **Device type predicts the shape of the spread.** Tracking and homophonic-pun devices produce graded spreads (multiple distinguishable levels); ateji/structural devices produce bimodal spreads (a wide-pass floor and a one-system ceiling); minimal-pair disambiguation produces a binary. This is a reusable heuristic for assembling a discriminating literary-MT scene: include at least one tracking device for graded separation, and reserve minimal-pair items for cheap screening rather than top-end ranking.
3. **The benchmark's separating power rests heavily on its single highest-discrimination device.** Because the motif device produced by far the widest spread, it carries a disproportionate share of the aggregate standing. That concentration is the reason the motif dimension is interpreted at length in §6.4 and flagged as the result's main exposure to the evaluator conflict in §7.1; it is not re-argued here. The point of this subsection is narrower — that the benchmark's discriminating power, by construction, loads onto one device, which is what makes those two cautions load-bearing rather than peripheral.

---

## 4. Method

### 4.1 Systems evaluated

| # | System | Interface | Code |
|---|--------|-----------|------|
| ★ | Mizushiro Mizuki (JP original) | Authorial source text | `JP_SRC` |
| 1 | Claude Opus 4.7, Max Reasoning Effort (Anthropic) | API, constraint-enforced harness, Adaptive Thinking | `OPUS` |
| 2 | Claude Fable 5, Max Reasoning Effort (Anthropic) | API, constraint-enforced harness, Adaptive Thinking | `FABLE` |
| 3 | ChatGPT 5.5 Extended Thinking (OpenAI) | Web | `CHATGPT` |
| 4 | DeepSeek V4, with Deep Thinking enabled (DeepSeek) | Web | `DEEPSEEK` |
| 5 | Gemini 3.1 Pro, with Extended Thinking (Google) | Web | `GEMINI` |
| 6 | Qwen 3.7 Max with Thinking enabled (Alibaba) | Web | `QWEN` |
| 7 | Fan-edited translation (Slimey Translations, ~2025) | MTL (Freedom) + editorial/proofreading | `FAN` |
| 8 | Claude Fable 5 Extra Thinking (Anthropic) | Web + agent config + `context.xml` | `FABLE_WEB` |
| 9 | DeepSeek V4 Pro, Max Reasoning Effort (DeepSeek) | API, constraint-enforced harness, 32k thinking budget | `DSV4_PRO` |

The JP source (★) is not a translation and does not compete; it serves as an authorial-intent reference (see §4.4 and Appendix C). `OPUS`, `FABLE`, and `DSV4_PRO` ran inside a constraint-enforcing infrastructure (canonical rendering locks, voice profile system, cross-pass consistency feed, emotional-temperature calibration, self-revision loop, canonical term registry; see Appendix A). The five web systems received the same translation policy and `context.xml` as prompt context only, without programmatic enforcement. The design supports two controlled comparisons: `FABLE` vs. `FABLE_WEB` (same model, harness present/absent) and `DSV4_PRO` vs. `DEEPSEEK` (same model family, harness present/absent), analyzed in §6.

### 4.2 Dimensions and weights

Each rendering was evaluated on seven dimensions, weighted by literary significance for this scene:

| Dimension | Weight | What it measures |
|-----------|--------|-----------------|
| 1. Voice Fidelity | 20% | Per-character speech fingerprints (Junna's deadpan, Shigure's tsukkomi, Yamada's code-switch) |
| 2. Subtext Preservation | 15% | The unspoken rain constraint, だめな子 callback chain, "not yet" relationship architecture |
| 3. Prose Rhythm & Naturalness | 15% | Fragment deployment, dialogue flow, comedy beat timing |
| 4. Fidelity | 20% | Factual accuracy: band names, song titles, kanji readings, negation wordplay |
| 5. Humidity/Damp-Gaze Motif | 15% | じとぉっと, 湿度, damp/rain imagery as emotional climate |
| 6. Subculture Knowledge | 10% | J-Rock authenticity, anime references, LN honorific conventions |
| 7. Literary Craft | 5% | Metaphor extension, structural solutions to untranslatable wordplay, prose elevation at peaks |

Five passages serve as litmus tests: **P1** じとぉっと (JP ~715, motif retention); **P2** だめな子 (JP ~71, voice-seed callback); **P3** MyGO!!!!! song titles (JP ~225–255, subculture knowledge); **P4** Yorushika/YOASOBI/Zutomayo (JP ~195–205, structural wordplay); **P5** 詩暮病 / 四葩病 (JP ~245–260, meta-textual craft).

### 4.3 Scoring procedure and rater disclosure

Scoring was performed by a **single rater**, applying the dimensional rubric through human-readable comparison of renderings against the JP source. **The rater was an independent DeepSeek V4 Pro instance, run in a separate environment with no connection to the translation pipeline or to the `DSV4_PRO` contestant run (#9); it did not grade its own generation, but it shares model weights with one contestant.** This same-model self-preference risk is treated as a primary threat to validity (§7.1). No operationalized, reproducible rubric was published that would allow an independent rater to reproduce the numeric subscores; for this reason the body of this report presents results as **ordinal tiers with an explicit uncertainty band** (§5.8) rather than as interval scores. The original per-dimension numeric judgments are retained, unaltered, in Appendix B and labeled as single-rater judgments.

### 4.4 The revision-regime spectrum

The contestants were evaluated under asymmetric revision conditions. It is tempting to frame this as a binary — "single-pass machines vs. a proofread human" — but the honest picture is a three-level spectrum, because the harness systems occupy a middle position:

| Contestant(s) | Revision regime | What it means |
|---------------|-----------------|---------------|
| **Web LLMs** (#3 ChatGPT, #4 DeepSeek-Web, #5 Gemini, #6 Qwen, #8 Fable-Web) | One forward token stream | True single-pass sight-translation: comprehend on first reading, emit finished English, no look-back. |
| **Harness LLMs** (#1 Opus, #2 Fable, #9 DSV4_PRO) | Single API call + automated self-revision loop | One model invocation, but a programmatic critique/consistency pass runs *within* it — more than one internal look, though not a human editing cycle. |
| **Fan TL** (#7, MTL + edited) | Machine-translated; multi-pass editorial review | MTL draft (Freedom) → edited (Slimey) → proofread (Crash, Jack74593, Slimey) → final, with post-hoc footnotes. |

The LLMs perform sight-translation: comprehend on first reading and produce finished English without a human edit. The Fan TL was machine-translated then passed through multiple human editorial and proofreading cycles. This means LLM errors are partly first-pass artifacts (some would not survive a second pass), while the Fan TL's errors are hardened (they survived the editorial review); the Fan TL's score is therefore closer to that team's ceiling, while the LLM scores are closer to their floor. The harness systems' internal revision loop is the reason the binary framing is misleading — they are not strictly single-pass, which is precisely why the §6.1/§6.3 controlled pairs (the *same* model with the harness and without it) are needed to isolate what the harness contributes. The study therefore measures comprehension-deployment under *near*-single-pass conditions, a stricter test than multi-pass quality, with the harness tier held as an explicit variable rather than assumed away. These implications are revisited in §7.

### 4.5 Source data and citation convention

Every rendering quoted in §5–§6 is reproduced verbatim from the system's actual single-pass output file and cited inline as [CODE:line]. The JP source lines are cited [JP:line] against `JP/CHAPTER_02.md`.

| Code | System | Source file |
|------|--------|-------------|
| FABLE | Claude Fable 5 (harness) | `CLAUDE_FABLE_5_MAX.md` |
| FABLE_WEB | Claude Fable 5 Web | `CLAUDE_FABLE_5_EXTRA_WEB.md` |
| OPUS | Claude Opus 4.7 (harness) | `CLAUDE_OPUS_4.7_MAX.md` |
| EN | DeepSeek V4 Pro (harness) = DSV4_PRO | `DEEPSEEK_V4_PRO_HARNESS.md` |
| GEMINI | Gemini 3.1 Pro | `GEMINI_3.1_PRO_EXTENDED_THINKING_WEB.md` |
| CHATGPT | ChatGPT 5.5 | `CHATGPT_5.5_EXTENDED_THINKING.md` |
| DEEPSEEK | DeepSeek V4 Web | `Deepseek_V4_Thinking.md` |
| QWEN | Qwen 3.7 Max | `QWEN_3.7_MAX_THINKING.md` |
| FTL§2 / FTL§3 | FEMTL (Slimey team) | `FAN_TRANSLATION_SLIMEY_FULL_CHAPTER_02.md` |

The DSV4_PRO run is the pipeline's production output for this chapter; it was confirmed as DeepSeek V4 Pro via `translation_log.jsonl` (`"model": "deepseek-v4-pro"`) and is cited as [EN:line]. The eight LLM files render the same scene with near-identical line alignment (all open with the Bocchi outburst), so cited line numbers are directly comparable. The Fan TL is a machine-translated, multi-pass edited fan release distributed as an EPUB; its prose is split across two section files and uses translator footnotes, cited [FTL§2:line] / [FTL§3:line]. The JP source is the original, not a translation, and is quoted only as the device anchor.

**Reasoning logs (harness systems).** Three of the nine systems ran inside the MTLS constraint-enforcing harness (Appendix A): **Fable 5** (`FABLE`), **Opus 4.7** (`OPUS`), and **DeepSeek V4 Pro** (`DSV4_PRO`/`EN`). For each, the harness persisted the model's pre-translation reasoning (`reasoning_content`) to a per-chapter thinking log. These logs are primary process records — the model's own decision narrative, written before the rendered output — and are used in §5.9 and §6 to ground claims about *why* a rendering took the form it did. They are cited [CODE-TK:line]:

| Reasoning-log code | System | Source file |
|--------------------|--------|-------------|
| FABLE-TK | Fable 5 (harness) | `chapter_02_THINKING_FABLE.md` |
| OPUS-TK | Opus 4.7 (harness) | `chapter_02_THINKING_OPUS.md` |
| DSV4-TK | DeepSeek V4 Pro (harness) | `chapter_02_THINKING_DS4P.md` |
| FABLE_WEB-TK | Fable 5 Web (web trace) | `MTL_Comparison/FABLE_THINKING_TRACE.md` |

The three harness logs are the model's structured `reasoning_content` as captured by the pipeline; the `FABLE_WEB-TK` web trace is a longer free-form deliberation included for the harness-vs-web contrast (§6.3). No reasoning log exists in the evidence set for the five web contestants' final outputs (ChatGPT, Gemini, web DeepSeek, Qwen, and the Fan TL), so process-tracing claims in §5.9 are scoped to the three harness models plus the Fable web trace, and are never extended to systems whose reasoning was not captured.

---

## 5. Results

Each evidence table is headed by the JP source line and quotes every system's output verbatim with a [CODE:line] citation (§4.5). The rater's per-dimension "best" designation is reported as a neutral observation of measured behavior; aggregate standing is presented as ordinal tiers in §5.8.

### 5.1 Voice Fidelity (20%)

Junna's deadpan register is evidenced in §5.2 (the だめな子 seed). Yamada's gyaru↔kimoota code-switch is the within-scene voice-discrimination test.

**Yamada's entrance code-switch.** JP [JP:359]: 「……こ、こんにちはぁ。あ、あままま、雨森{あまもり}たん！　ふへへっ……」

| System | Rendering |
|--------|-----------|
| FABLE | "…H-Hi theeere. A-Ama-ma-ma—Amamori-tan! Fuhehe…" [FABLE:355] |
| FABLE_WEB | "…H-hello there. A-Ama-ma-ma—Amamori-tan! Fuhehe…" [FABLE_WEB:353] |
| OPUS | "…h-hello. A-a-a-a-Amamori-tan! Fuhehh…" [OPUS:351] |
| DSV4_PRO | "…H-Hello. A-Amama-mama, Amamori-tan! Fuheheh…" [EN:353] |
| GEMINI | "…H-Hello. A-Ama-ma-ma, Amamori-tan! Fuhehe…" [GEMINI:355] |
| CHATGPT | "…H-Hello. A-A-Ama-ma-ma… Amamori-tan! Fuhehe…" [CHATGPT:365] |
| DEEPSEEK | "H-hello. A-Ama-Ama-Amamori-tan! Fuhehe…" [DEEPSEEK:355] |
| QWEN | "…H-hello. A-a-a-amamori-tan! Fuhehe…" [QWEN:357] |
| FAN | "…H-Hello. A-A-A-Amamori-tan! Heh heh heh…" [FTL§2:197] |

*Observation:* All nine reproduce the stammer + honorific collision; differentiation on this passage is negligible. The voice-fidelity dispersion appears not at the entrance but in the deadpan/seed registers (§5.2) and in the humidity binding (§5.5).

### 5.2 Subtext Preservation (15%)

**The だめな子 seed.** JP [JP:71]: 「詩暮{しぐれ}がいなきゃ、私はだめな子」 — a callback seed whose register must survive to the Ch.-end echo [JP:951].

| System | Rendering | Assessment |
|--------|-----------|------------|
| FABLE | "Without Shigure, I'm a hopeless girl." [FABLE:67] | だめ≈"hopeless"; "girl" matches 子 |
| FABLE_WEB | "Without you, Shigure, I'm hopeless." [FABLE_WEB:71] | drops "girl" |
| OPUS | "Without you, Shigure, I'm a broken kid." [OPUS:67] | "broken" implies external damage |
| DSV4_PRO | "Without Shigure, I'm a hopeless girl." [EN:67] | identical to FABLE |
| GEMINI | "Without you, Shigure, I'm useless." [GEMINI:71] | "useless" harsher than だめ |
| CHATGPT | "Without you, I'm no good." [CHATGPT:71] | natural; self-deprecating |
| DEEPSEEK | "Without you, I'm a no-good girl." [DEEPSEEK:71] | colloquial |
| QWEN | "Without you, Shigure, I'm a useless girl." [QWEN:73] | same harshness as GEMINI |
| FAN | "Without you, Shigure, I'm useless." [FTL§2:47] | "useless" — harsher than だめ |

*Observation:* FABLE and DSV4_PRO (both harness) produce the identical, register-matched "hopeless girl"; the harsher "useless/no-good" cluster (GEMINI, QWEN, FAN) overstates だめ.

**The "not yet" architecture.** JP [JP:109]: 「まだ、そうじゃないだろ」 — Shigure's deflection, which Junna echoes and accepts ("少しずつ").

| System | 「まだ、そうじゃないだろ」 rendering |
|--------|----------------------------------|
| FABLE | "We're not that. Not yet." [FABLE:105] |
| FABLE_WEB | "We're not there yet. That's all." [FABLE_WEB:109] |
| OPUS | "We're not yet." [OPUS:105] |
| DSV4_PRO | "We're not there yet." [EN:103] |
| GEMINI | "We're not there yet, right?" [GEMINI:109] |
| CHATGPT | "We're not that yet." [CHATGPT:111] |
| DEEPSEEK | "We're not there yet." [DEEPSEEK:107] |
| QWEN | "But… we're not *there* yet, right?" [QWEN:111] — narrator-attributed to Shigure ("I pushed back… speaking firmly," [QWEN:113]) |
| FAN | "We're not there yet," [FTL§2:67] — Shigure narrating ("I told her, my tone firm") |

*Observation:* All nine preserve the weight-bearing "yet"; variation is minor. GEMINI and QWEN append a confirmatory "right?" (mirroring だろ); the rest render a flat declarative. (Qwen's line is spoken by Shigure as narrator — [QWEN:113]: "I pushed back against her pressure, speaking firmly" — confirming the attribution.)

### 5.3 Prose Rhythm & Naturalness (15%)

**The Bocchi the Rock! outburst.** JP [JP:15]: …アイアム・ボッチ、ぼっち・ざ・ろっく！　視聴覚室より哀{あい}をこめて…… (uses 哀 *sorrow*, not 愛 *love*).

| System | Rendering (close of the outburst) |
|--------|-----------------------------------|
| FABLE | "…I AM BOCCHI, BOCCHI THE ROCK! From the AV Room with SORROW…" [FABLE:13] |
| FABLE_WEB | "…I am bocchi—bocchi the rock! From the A/V room, with sorrow…" [FABLE_WEB:15] |
| OPUS | "…I AM BOCCHI, BOCCHI THE ROCK! From the AV Room with SORROW…" [OPUS:13] |
| DSV4_PRO | "…I AM BOCCHI, BOCCHI THE ROCK! From the AV Room with SORROW…" [EN:13] |
| GEMINI | "…I am a loner, Bocchi the Rock! From the AV room with sorrow…" [GEMINI:15] |
| CHATGPT | "…I am a loner! Bocchi the Rock! With love from the AV room…" [CHATGPT:15] — 哀→love (error) |
| DEEPSEEK | "…I am Bocchi, Bocchi the Rock! With more sorrow than this AV room can hold…" [DEEPSEEK:15] |
| QWEN | "…I am bocchi, bocchi the rock! With love from the AV room…" [QWEN:15] — 哀→love (error) |
| FAN | "…I am Bocchi! Bocchi the Rock! With sorrow, from the AV room…" [FTL§2:19] |

*Observations:* FABLE, OPUS, and DSV4_PRO carry the locked ALL-CAPS "with SORROW" from the harness consistency feed; FABLE_WEB (same model, no lock) renders lowercase, indicating the dramatic register is a harness artifact (§6). CHATGPT and QWEN render 哀 as "love," reversing the valence (the 哀≠愛 distinction); the remaining systems preserve "sorrow." The comedy-beat half of this dimension (the cute/gross volley) is analyzed with the flower metaphor in §5.7.

### 5.4 Fidelity (20%)

**MyGO!!!!! song titles.** JP [JP:223]: 「『壱雫空{ひとしずく}』──いや『輪符雨{リフレイン}』だな」 · JP [JP:227]: …『迷星叫』『影色舞』『詩暮病』… (real band, no official EN titles → keep romaji).

| System | 壱雫空 → 輪符雨 (verbatim) | 迷星叫 | Policy |
|--------|----------------------------|--------|--------|
| FABLE | "'Hitoshizuku'—no, make it 'Refrain.'" [FABLE:219]; narration glosses "lost-star scream… shadow-color dance… Shigure Disease" [FABLE:223] | "Mayoiuta" (spoken) [FABLE:225] | romaji + narration/dialogue ateji split |
| FABLE_WEB | "'Hitoshizuku'—no, make it 'Refrain.'" [FABLE_WEB:219] | "Mayoiuta" [FABLE_WEB:225] | romaji |
| OPUS | "'One Drop Sky'—no, 'Refrain,' actually." [OPUS:217] | "Mayoiuta" [OPUS:221] | invents EN title |
| DSV4_PRO | "'Hitoshizuku'—no, actually, 'Refrain.'" [EN:217] | "Mayoi Uta" [EN:221] | romaji (lock) |
| GEMINI | "'Hitoshizuku'—no, 'Refrain'." [GEMINI:221] | "Mayoiuta" [GEMINI:225] | romaji |
| CHATGPT | "'One-Drop Sky'—no, 'Refrain.'" [CHATGPT:225] | "Stray-Star Song" [CHATGPT:231] | invents 2 EN titles |
| DEEPSEEK | "'Hitoshizuku'—no, 'Refrain.'" [DEEPSEEK:219]; narration "Lost Song… Shigure Sickness" [DEEPSEEK:223] | "Mayoiuta" (spoken) [DEEPSEEK:225] | split attempted, written form translated (inconsistent) |
| QWEN | "'Hitoshizuku'—no, 'Refrain'." [QWEN:221] | "Meiseikyou" [QWEN:225] | romaji (on-reading) |
| FAN | "'Hitoshizuku'─ no, wait, 'Refrain.'" [FTL§2:129] | "Mayoiuta" (footnoted) | romaji + footnote |

*Observation:* OPUS and CHATGPT invent EN titles for 壱雫空; CHATGPT also for 迷星叫. FABLE and DEEPSEEK both attempt a narration-gloss / dialogue-reading split that mirrors ateji structurally — FABLE writes the meaning and speaks the reading; DEEPSEEK writes a translated form ("Lost Song"/"Shigure Sickness") then speaks "Mayoiuta," producing the inconsistency.

**GO!GO!7188 → Chirinuruwowaka lineage.** JP [JP:279]: 「チリヌルヲワカ」 (band led by the former guitar-vocalist of the disbanded GO!GO!7188).

| System | Rendering |
|--------|-----------|
| FABLE | "Chirinuruwowaka." [FABLE:275] |
| FABLE_WEB | "Chirinuruwowaka." [FABLE_WEB:275] |
| OPUS | "Chirinuruwowaka." [OPUS:273] |
| DSV4_PRO | "CHIRINURUOWAKA." [EN:273] — dropped *w* (misspelling) |
| GEMINI | "Chirinuruwowaka." [GEMINI:277] |
| CHATGPT | "CHIRINURUWOWAKA." [CHATGPT:281] (all-caps, complete) |
| DEEPSEEK | "Chirinuruwo." [DEEPSEEK:275] — truncated (missing ワカ) |
| QWEN | "Chirinuruwowaka." [QWEN:277] |
| FAN | "Chirinuruwowaka⁷" [FTL§2:155] (footnoted) |

*Observation:* Two distinct error types — DEEPSEEK (web) truncates the name; DSV4_PRO (same family, harness) misspells it. The remaining systems render it complete. The recurrence across the DeepSeek family supports a training-data gap rather than a single-pass slip (§6).

**The triple-band pun.** JP [JP:195]: 「…ずっとヨルシカ眠れていない」 · JP [JP:197]: 「…ＹＯＡＳＯＢＩが好きなんだよね。ずっと真夜中でいいのに。……」 — three band names as adverbial puns: Yorushika ≈ 夜しか ("only at night"), YOASOBI = 夜遊び ("night play"), Zutomayo (ずっと真夜中でいいのに, stylized as a full sentence).

| System | Yorushika (夜しか) | YOASOBI (夜遊び) | Zutomayo (ずっと真夜中) |
|--------|--------------------|------------------|------------------------|
| FABLE | "can't sleep anywhere but Yorushika. Nights only." [FABLE:191] | "I do love a good YOASOBI—out all night." [FABLE:193] | "wish it could stay midnight forever…" [FABLE:193] |
| FABLE_WEB | "I've been sleeping Yorushika—nights only." [FABLE_WEB:191] | "I do love my YOASOBI—my nights up playing." [FABLE_WEB:193] | "Zutto mayonaka de ii noni…" [FABLE_WEB:193] |
| OPUS | "haven't been sleeping a Yorushika of a wink" [OPUS:189] | "I love YOASOBI." [OPUS:191] | "it'd be fine if it stayed Zutomayo." [OPUS:191] |
| DSV4_PRO | "haven't been able to sleep—yorushika-style" [EN:189] | "I really love my YOASOBI" [EN:191] | dropped — "midnight forever" [EN:191] |
| GEMINI | "haven't been able to sleep at Yorushika" [GEMINI:193] | "I guess I like YOASOBI." [GEMINI:195] | "ZUTOMAYO—I really wish it was midnight all the time" [GEMINI:195] |
| CHATGPT | "I've been sleeping like Yorushika" [CHATGPT:197] | "I like YOASOBI." [CHATGPT:199] | dropped [CHATGPT:199] |
| DEEPSEEK | "haven't been able to sleep—Yorushika style" [DEEPSEEK:189] | "I like YOASOBI." [DEEPSEEK:191] | dropped [DEEPSEEK:191] |
| QWEN | "haven't been able to sleep. Yoasobi." [QWEN:193] — conflates with next band | "I like YOASOBI." [QWEN:195] | "midnight forever" [QWEN:195] |
| FAN | "only at night¹" (meaning + footnote) [FTL§2:115] | "the nightlife²" [FTL§2:116] | "always midnight…³" [FTL§2:116] |

*Observation:* QWEN collapses Yorushika into YOASOBI — the largest single fidelity error; it is not line-editable and would require retranslation of the exchange. CHATGPT, DEEPSEEK, and DSV4_PRO each drop Zutomayo (DSV4_PRO confirms the harness cannot supply band knowledge the model lacks). FABLE, FABLE_WEB, OPUS, GEMINI preserve all three in prose; FAN carries the literal sense of all three *inline* in the dialogue (italic "only at night," "nightlife," "always midnight" [FTL§2:115–116]) and footnotes the band identity — three footnote supplements rather than narrative exits, since the meaning never leaves the running text. Among the preservers the strategies diverge — *isolate* (FABLE), *embed* (OPUS), *lead-in* (GEMINI), *explain* (FAN), versus *drop* (CHATGPT, DEEPSEEK, DSV4_PRO) — mapped to Delabastita's typology in §6.5.

**哀 vs 愛.** JP [JP:15]: 視聴覚室より哀{あい}をこめて (哀 *sorrow*, not 愛 *love* — a parody of "From Russia with Love") — covered in the §5.3 Bocchi table: CHATGPT [CHATGPT:15] and QWEN [QWEN:15] render 哀 as "love"; all others preserve "sorrow."

### 5.5 Humidity / Damp-Gaze Motif (15%)

**The じとぉっと test.** JP [JP:715]: それから、じとぉっと俺を睨{にら}んだ。 (the title's defining onomatopoeia; a neutral "glared" drops the motif).

| System | Rendering | Encodes humidity? |
|--------|-----------|-------------------|
| FABLE | "Then leveled a **damp, accusing stare** at me." [FABLE:707] | Yes — "damp" into the verb phrase |
| FABLE_WEB | "Then she glared at me with that **heavy, lidded stare**." [FABLE_WEB:702] | Partial — canonical lock, no innovation |
| OPUS | "Then she glared at me." [OPUS:707] | No — neutral verb |
| DSV4_PRO | "Then she glared at me—**ji-toooooo**." [EN:707] | Partial — romanizes the giongo |
| GEMINI | "Then, she shot me a **cold, deadpan glare**." [GEMINI:707] | No — "cold, deadpan" misses humidity |
| CHATGPT | "Then she glared at me." [CHATGPT:745] | No |
| DEEPSEEK | "Then she glared at me **with dead eyes**." [DEEPSEEK:709] | No — wrong valence (numb, not damp) |
| QWEN | "Then she shot me a **flat glare**." [QWEN:697] | No — "flat" misses humidity |
| FAN | "Then, she shot me a **reproachful glare**." [FTL§3:101] | No — neutral/affective, no humidity |

*Observation:* The widest single-passage dispersion in the study. Only FABLE encodes the title motif at its trigger point; FABLE_WEB complies with the lock without innovating; DSV4_PRO preserves Japanese sound texture rather than English humidity meaning; the remaining five systems and the Fan TL render it as a neutral or affective glare. The dimension is analyzed as a tracking (not vocabulary) problem in §6.4.

**Secondary humidity passages.** The motif also appears as `雨で湿った大気`, `湿った空気`, and the rain that bookends scene breaks. All systems handle these environmental descriptions adequately; the dispersion is specific to じとぉっと as a character trait, not rain as weather.

### 5.6 Subculture Knowledge (10%)

| Knowledge point | FABLE | FABLE_WEB | OPUS | DSV4_PRO | GEMINI | CHATGPT | DEEPSEEK | QWEN | FAN |
|-----------------|-------|-----------|------|----------|--------|---------|----------|------|-----|
| MyGO!!!!! discography (no official EN) | ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | ⚠ | ✓ | ⚠² |
| GO!GO!7188 → Chirinuruwowaka lineage | ✓ | ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | ✓ | ✓ |
| Yorushika etymology (夜+しか) | ✓ | ⚠ | ⚠⁵ | ✗ | ✓ | ✗ | ✗ | ✗ | ✗³ |
| Bocchi the Rock! multi-layer ref | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ⚠ | ✓ | ✓ |
| YOASOBI pun (夜遊び) | ✓ | ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | ✓ | ✓ |
| Zutomayo as band-name sentence | ✓ | ✓ | ✓ | ✗ | ✓ | ✗ | ✗ | ✗ | ✓⁴ |
| 哀 ≠ 愛 distinction | ✓ | ✓ | ✓ | ✓ | ✓ | ✗ | ⚠ | ✗ | ✓ |

² Romaji approach correct; kanji preserved visually with reading in footnotes — declarative, not operational. ³ Yorushika etymology not recognized — rendered as band name only. ⁴ Zutomayo preserved in footnote; recognized but explained rather than structurally integrated. ⁵ Reasoned about the etymology but reached the wrong parse — "night deer" (シカ read as 鹿) rather than the limiting particle しか ("only at night"); see §5.9c. Fable's log and output both give the correct "nights only," so this cell is corrected from the original ✓ on the basis of the primary reasoning logs.

*Observations:* FABLE and FABLE_WEB show identical operational J-Rock knowledge, indicating the subculture comprehension is model-native and survives the harness-to-web transition. GEMINI matches both Fable variants on subculture knowledge but does not deploy it structurally. OPUS shows deep single-point declarative knowledge elsewhere — its reasoning log alone correctly identifies 四葩 *yohira* as an archaic word for hydrangea (§5.9a) — but misreads the Yorushika etymology as "night deer" (§5.9c) and renders 壱雫空 as a meaning-gloss ("One Drop Sky") despite having retrieved its reading — device knowledge that did not reach the output (§5.6, *Worked micro-case*). DSV4_PRO shares DEEPSEEK's subculture gaps (no Zutomayo, no Yorushika etymology, no YOASOBI pun), confirming these are model-native limitations rather than infrastructure artifacts. QWEN's Yorushika/YOASOBI conflation is the largest subculture failure. CHATGPT and both DeepSeek variants miss Zutomayo, suggesting training-data gaps for newer/niche bands. FAN has declarative knowledge (footnoted identities) with no operational deployment in prose.

**The "Utsu-Rock" term lock.** 鬱ロック (a coined genre label); the canonical term registry enforces "Utsu-Rock."

| System | Genre-label rendering |
|--------|-----------------------|
| FABLE | "Utsu-Rock" Appreciation Society [FABLE:459] (locked) |
| DSV4_PRO | "Utsu-Rock" Appreciation Society [EN:459] (locked) |
| FABLE_WEB | "Depressive Rock" Appreciation Society [FABLE_WEB:456] (lock not enforced) |
| OPUS | "Depressive Rock" Appreciation Society [OPUS:459] (generic) |
| GEMINI | "Depressive Rock" Appreciation Society [GEMINI:461] |
| CHATGPT | "Depressive Rock" Appreciation Society [CHATGPT:477] |
| DEEPSEEK | "Depressive Rock" Lovers' Club [DEEPSEEK:463] |
| QWEN | "Depressive Rock" Appreciation Society [QWEN:455] |

*Observation:* The two systems enforcing the lock (FABLE, DSV4_PRO) are both inside the harness; web systems lack the guardrail. (FABLE_WEB retains the "Utsu-P" score-unit but uses "Depressive Rock" for the genre — the lock is advisory only.)

**MyGO!!!!!'s ateji device.** The knowledge matrix at the head of §5.6 and the term-lock table above both measure the *output* axis — whether a system kept the titles untranslated. A separate and harder question is whether a system grasped *why* the titles resist translation at all. This is the comprehension axis on which the scene was selected (§3.4), and the two axes diverge most sharply here. Because the device is invisible to a reader who does not already hold several layers at once, the background is given in full before the comparison.

*What the titles are.* MyGO!!!!! is a real band — the in-universe musical group of the *BanG Dream!* franchise — whose song titles are written in **gikun ateji**: the kanji are chosen for their *meaning*, while the furigana prints an unrelated *reading*, usually an English word or native *wago*. Each title is therefore two messages at once, one seen and one heard, and the gap between them is the artistic signature. Four titles surface in the scene:

| Song (Kanji) | Literal meaning (seen) | Forced reading (heard) |
|-------------|-----------------|------------------------|
| 迷星叫 | lost-star-scream | まよいうた (Mayoiuta) |
| 壱雫空 | one-drop-sky | ひとしずく (Hitoshizuku) |
| 輪符雨 | ring-symbol-rain | リフレイン (Refrain) |
| 影色舞 | shadow-color-dance | シルエットダンス (Silhouette Dance) |

*The device is stated on the page, not buried.* This is not subtext the reader must infer. When Shigure reads 『輪符雨』 aloud as "Refrain," Junna comments directly on the mechanism: 「雨と書いてレイン。初見じゃ絶対読めないよね」 — "you write the kanji for *rain* and read it 'rein'; no one could read that on first sight" [JP:225]. The scene keeps narrating its own device — "how do you even read that?" [JP:229], "there's no way to read that" [JP:233], and Junna's closing verdict turns on the word 字面 (*jizura*, the *written* appearance of the characters) [JP:257]. A rendering that flattens a title to its meaning does not merely drop a flourish; it contradicts dialogue that is explicitly *about* the flourish.

*The titles are rain-coded, and the chain is the point.* The exchange is a game of *shiritori* (word-chain) in which the pair trade band-and-song references as "our shared language" [JP:201]. The songs named are not arbitrary: 『雨後晴』 (clear skies after rain) [JP:207], 『雨あがり』 (after the rain) [JP:215], then 『壱雫空』 (a single drop from the sky — a raindrop) and 『輪符雨』 (whose final kanji is literally 雨, *rain*) [JP:223]. In a volume titled *Amamori Junna Is High Humid* — 雨森 *Amamori* parses as "rain-forest," 湿度が高い as "high humidity" — the heroine is reciting a chain of rain-titled songs. The MyGO!!!!! ateji are a tributary of the book's controlling weather motif (§5.5), not a detachable trivia set.

*詩暮病 is a counterfeit title built inside the device.* Having set the pattern with two real MyGO songs, Junna writes a third title in the same breath, in the same staff-paper notebook: 『迷星叫』『影色舞』『詩暮病』 [JP:227]. The first two are real; the third is hers. Its written form, 詩暮病, reads as "Shigure Disease" — 詩暮 is the given name of her love interest, Kurimoto Shigure [JP:241], itself a homophone of 時雨 (*shigure*, late-autumn drizzle), so the coinage is *also* rain-coded — while the furigana reading she assigns it is 「あまもりじゅんな」, her own name [JP:231]. The title says, in writing, *sick with Shigure*, and says, in sound, *this is Amamori Junna*: a confession folded into a counterfeit MyGO!!!!! song title, using the band's own meaning-versus-reading device. Shigure deflects by answering with a further ateji, 四葩病 (*Yohira-byō*, after the band YOHILA = 四葩 = an archaic word for hydrangea; §5.9a) [JP:249], and Junna's reply — "not the 字面 I was hoping for" [JP:257] — closes the game on the same written-versus-read axis it opened on.

A second, quieter weather layer sits under the same coinage. The kanji 詩暮 do **not** contain 雨, so this is not a graphic rain clue; the resonance is phonetic. 詩暮 is read しぐれ, homophonous with 時雨, late-autumn rain. Once 詩暮病 is forced to read あまもりじゅんな, the title does more than say "I am sick with Shigure": it lets Amamori Junna name herself as the condition attached to *shigure*-rain. This is why the device belongs to the volume's humidity/weather system rather than to isolated comedy. It ties Shigure's name-sound, Amamori's 雨-bearing surname, and the premise of 湿度 into one counterfeit song title. This layer is not necessary to catch the surface joke, but it is central to the passage's emotional pressure.

*The gap is the payload — which is why this is the scene's hardest comprehension test.* What makes 詩暮病 a confession is neither the written meaning nor the assigned reading but the **distance between them**: "Shigure Disease" (seen) and "Amamori Junna" (heard) are both present and deliberately fail to match. Collapse them to a single value and the confession is gone. This sets the bar above a native reader's default, and the text says so outright: handed the characters and asked how they read, Shigure cannot derive the reading — 「読めるわけないんだよなぁ」, "there's no way you could read that" [JP:233]. A Japanese reader who does not know MyGO!!!!! can parse 詩暮病 perfectly and still miss why it reads as "Amamori Junna," because the band's convention — not the characters — is what licenses the meaning-from-sound divergence. The object under test is the *device*, not the kanji; parsing the kanji is a floor any literate reader already clears. This is also why preserving the glyph is not by itself a solution: it reproduces the Japanese reader's *encounter* (you are confronted with the characters) without reproducing the *comprehension* (the resolved gap) — precisely the content an English reader cannot recover from an opaque grapheme.

Seen this way, the renderings sort by **which coordinate of a two-coordinate object** they carry:

- **Meaning only** — Opus ("One Drop Sky," "Shigure Disease"), ChatGPT: the seen pole survives, the gap collapses.
- **Reading only** — Gemini, Qwen, Fable-web, and DSV4_PRO under its romaji lock: the heard pole survives, which is the correct floor for a *real* song such as 壱雫空 (the recognizable title). But the same single-pole move cannot carry 詩暮病, whose joke-reading ("Amamori Junna") signifies only against its visible written form ("Shigure Disease") — the counterfeit title is the one place in the passage where picking either pole alone fails.
- **Kanji glyph preserved** — Fan TL; DSV4_PRO's "四葩病—Yohira Disease" [EN:243]: the *logographic confrontation* is reproduced — the reader faces the characters — but to an English reader the glyph is opaque, so this transmits the *form* of the Japanese reader's encounter without either pole's *content*; the Fan TL then supplies the content in a footnote (explained, not enacted; §6.5).
- **The gap itself** — Fable 5: meaning in narration, reading in dialogue [FABLE:219, 223, 225], so the English reader receives both poles and perceives the distance.

Only the last conveys the gap itself; the meaning-only and reading-only renderings each transmit a single pole, and the glyph-only renderings reproduce the form while transmitting neither pole's content. The asymmetry is structural, not incidental — English orthography is single-channel (a word is pronounced as written, with no furigana track to hold a second value), so the gap cannot be transposed, only **compensated** by relocating its two poles to separate points in the prose. This is the loss the paper books as irreducible (Appendix C); Fable's narration/dialogue split is a compensation *in place* in the sense of §6.6; and the formal strategy typology is set out in §6.5.

*What a faithful rendering must carry.* To render the passage faithfully a system must hold four facts simultaneously: (1) MyGO!!!!! is a real band with no official English titles — *knowledge*; (2) its titles are gikun ateji whose written form and reading differ on purpose — *device*; (3) the titles named here are rain-coded and feed the volume's humidity motif — *integration*; (4) 詩暮病 is a fake title built on the same device, so it must scan as a song title *and* as a confession — *integration*. A system can satisfy (1) by policy alone and still fail (2)–(4). The four collapse into one floor-and-ceiling test (§3.4): keeping the titles in romaji is the floor; reconstructing the device is the ceiling.

| Model | Kept romaji? (output) | Recognized the ateji as a device? (knowledge) | Integrated 詩暮病 as the same pattern? (comprehension) |
|-------|-------------|----------------------------------|------------------------------|
| FABLE | ✓ | ✓ — narration/dialogue split replicates the ateji signature in English prose | ✓ — treats the fake title identically to the real songs [FABLE-TK:139] |
| FABLE_WEB | ✓ | ⚠ — correct romaji policy; thinking trace shows ateji awareness but no structural replication | ⚠ — correct without structural mimesis |
| OPUS | ✗ | ⚠ — had the ひとしずく reading and flagged the titles as "wordplay" [OPUS-TK:169, 425], but rendered the gloss "One Drop Sky" [OPUS:217]: device-knowledge that did not reach the output | ✗ — analyzed 詩暮病 in a separate pass [OPUS-TK:174] from the band titles [OPUS-TK:169]; the connection is absent from the log |
| GEMINI | ✓ | ✗ — correct policy without recorded device awareness (no log) | ✗ |
| CHATGPT | ✗ | ✗ — two invented titles | ✗ |
| DSV4_PRO | ✓ | ⚠ — log shows form/experience awareness [DSV4-TK:271] but judges the written form "irrelevant" and discards it; romaji also lock-enforced | ✗ |
| DEEPSEEK | ⚠ | ✗ — inconsistent approach | ✗ |
| QWEN | ✓ | ✗ — correct policy; Yorushika/YOASOBI conflation indicates no band-level understanding | ✗ |
| FAN | N/A | ✗ — kanji preserved visually, readings footnoted; meta-textual reference lost | ✗ |

**Worked micro-case — Opus and 壱雫空 ("One Drop Sky").** This single title isolates the comprehension axis from the fluency axis more cleanly than any other data point in the study, and warrants stating in full. Opus did not misread the kanji. Its reasoning log records the correct gikun reading — [OPUS-TK:425] "壱雫空 (ひとしずく) — 'One Drop Sky' (Hitoshizuku)" — that is, it retrieved ひとしずく, the genuine forced reading, not a naive character-by-character on-reading such as "Ichizuku Sora." It also classified the titles correctly as a class — [OPUS-TK:169] "these are wordplay with song titles; the Japanese reader would recognize these" — and even noted the rain kanji buried in the next title — [OPUS-TK:426] "輪符雨 … written as 'Rain' with kanji 'wheel/mark/rain.'" Every component of the device was in hand. Opus nonetheless rendered the title as "One Drop Sky" [OPUS:217] — the literal gloss, as the displayed title. The rendering is fluent, idiomatic English and even keeps the raindrop image; what it discards is the song's identity (no reader can trace "One Drop Sky" to a real MyGO!!!!! release) and the ateji device itself (the deliberate gap between written meaning and printed reading). The failure is therefore not lexical (the reading was known), not linguistic (the English is clean), and not even imagistic (the rain survives); it is a failure to connect the title to its *function* — that it is a recognizable song named in a chain of songs, built on a device that 詩暮病 then reuses as a confession. The logs make the disconnection legible: Opus files the band titles under "music band name jokes" [OPUS-TK:169] and, in a separate pass, treats 詩暮病 as "Junna's core affection-coded joke" [OPUS-TK:174, 251], never linking the two. It held all the pieces of the device and did not assemble them. This is the study's thesis (§1, §8) compressed into one title: *a comprehension failure rendered in fluent prose.* Fable, given the same source and the same policy, kept "Hitoshizuku" [FABLE:219], labelled the set "trick titles" in narration [FABLE:223], and grouped 詩暮病 with the real songs as one continuous series [FABLE-TK:139] — the same components, differently integrated.

*Observation:* The systems separate on three axes that the romaji policy alone conflates — keeping the title (output), recognizing the ateji (knowledge), and integrating it with the motif chain and the 詩暮病 confession (comprehension). Most systems that kept the titles in romaji did so by policy or lock without recorded device-awareness (Gemini, Qwen; DSV4_PRO by lock while judging the form "irrelevant," [DSV4-TK:271]); one system that *had* the device-knowledge nonetheless failed both the output and the integration (Opus); one system (Fable 5) integrated all three, replicating the ateji structurally through a narration-meaning / dialogue-reading split that — per its thinking log — was not explicitly prompted: the harness supplied no rendering for the device (of the five titles, only 輪符雨 appears in the assembled context, with an empty target and an explicit "requires model translation"; context.xml:230, §6.3), so the model's own band knowledge supplied the structural application. The Fable result is a single observed instance and is treated as such in §6. The Opus result is the firmer finding, because it shows the axes are genuinely independent: knowledge of the device did not, on its own, produce preservation of it.

### 5.7 Literary Craft (5%)

**The 詩暮病 / 四葩病 kanji play.** JP [JP:227]: 『詩暮病』 · JP [JP:249]: 『栗本詩暮』の隣に『四葩{よひら}病』… — Junna coins 詩暮病 (a fake MyGO!!!!! title / confession reading "Shigure Disease"); Shigure replies with 四葩病 using the rare kanji 葩.

| System | 四葩病 | Shigure's reaction (diagnosis vs. description) |
|--------|--------|------------------------------------------------|
| FABLE | "Yohila Disease" | "Not the diagnosis I was hoping for" [FABLE:253] |
| FABLE_WEB | "Yohila Syndrome" | "Not the characters I was hoping for" [FABLE_WEB:253] |
| OPUS | "Yohila Disease" | "Not quite the characters I was hoping for" [OPUS:251] |
| DSV4_PRO | "四葩病—Yohira Disease" [EN:243] | "It's not quite the look I was hoping for" [EN:251] |
| GEMINI | "Yohila Disease" [GEMINI:247] | "It wasn't the spelling I was hoping for" [GEMINI:255] |
| CHATGPT | "YOHILA Disease" | (narrative only — no reaction tell) |
| DEEPSEEK | "Yohila Disease" | "It's not the combination I was expecting" [DEEPSEEK:253] |
| QWEN | "Yohila Disease" [QWEN:247] | "It's not quite the visual I was hoping for" [QWEN:255] |
| FAN | keeps 葩 + gloss "the kanji for '葩' (flower)…?" [FTL§2:143] | explained, not enacted |

*Observation:* Only FABLE's "diagnosis" sustains the disease-metaphor through-line, rendering the coinage as a confession *performed* rather than described — the scene's Stage 1→2 emotional hinge (generic lovesickness → self-diagnosis) — while keeping the wording compatible with the quieter 時雨/weather resonance described in §5.6. The others substitute a meta-word for "kanji" (characters/spelling/visual/look/combination), reading 詩暮病 as wordplay rather than confession; OPUS additionally hedges with "one might call" [OPUS:251], and the Fan TL explains the device in a footnote rather than enacting it.

**The "every petal" metaphor — cross-segment integration.** The seed and payoff are ~twenty lines apart. Seed JP [JP:419]: 「山田さんで遊ぶな。花占いみたいに」 · Payoff JP [JP:421]: 『可愛い』と『きもい』を繰り返されるたび、ころころ変わる山田の表情。 (ころころ is a tumbling-onomatopoeia carrying no floral image).

| System | Seed (花占い) | Payoff (ころころ変わる表情) | Chain |
|--------|--------------|----------------------------|-------|
| FABLE | "Quit playing she-loves-me-she-loves-me-not with Yamada-san." [FABLE:411] | "Cute, gross, cute, gross—Yamada's expression flipped with every petal." [FABLE:413] | completed (only system) |
| OPUS | "Stop playing flower-petal prophecy with Yamada-san." [OPUS:411] | "flipped like a rolling coin." [OPUS:413] | seeded, dropped |
| GEMINI | "like she's a game of 'He loves me, he loves me not'." [GEMINI:413] | "flip-flopped with every alternating 'cute' and 'gross.'" [GEMINI:415] | seeded, dropped |
| FABLE_WEB | "She's not a round of he-loves-me, he-loves-me-not." [FABLE_WEB:408] | "flipped like a coin." [FABLE_WEB:410] | seeded, dropped |
| DSV4_PRO | "like she's a fortune-telling flower." [EN:413] | "flipped like a switch." [EN:415] | seeded, dropped |
| DEEPSEEK | "like a flower fortune-telling petal." [DEEPSEEK:415] | "expression kept changing." [DEEPSEEK:417] | seeded, dropped |
| QWEN | "like she's a daisy." [QWEN:413] | "expression shifted wildly." [QWEN:415] | seeded, dropped |
| FAN | "It's like 'he loves me, he loves me not' with a flower." [FTL§2:231] | omitted — jumps to "…Gross-cute" [FTL§2:233] | seed only |
| CHATGPT | omitted — recast as "…Are you a gross-bot?" [CHATGPT:717] | omitted | neither |

*Observation:* Eight of nine systems render the 花占い seed with floral / "loves-me-not" imagery — the image is within reach of nearly every system. Only FABLE carries it into the payoff line; every other floral-seed system substitutes an unrelated image (coin, switch, flip-flop) or omits the payoff (FAN), and CHATGPT drops the device at both points. The discriminator on this dimension is cross-segment integration, not vocabulary — the property §2 argues automatic metrics cannot evaluate. FABLE_WEB (same model, same seed) renders the payoff as "flipped like a coin," so the completion is associated with the harness condition, not the model in isolation (§6.3); the rendering is an instance of **compensation in place**, analysed as the study's clearest cross-segment case in §6.6.

### 5.8 Aggregate standing (ordinal tiers)

The original scoring produced two-decimal composite scores (retained in Appendix B). Because those scores were produced by a single rater without a reproducible rubric or significance testing (§4.3, §7), they are presented here as **ordinal tiers**. Gaps of roughly ≤0.04 on a single-scene, single-rater design are not separable; within-tier ordering is therefore reported as **not statistically distinguishable**. The original document itself conceded this for the adjacent Fan TL / DeepSeek pair (0.01 apart, "within measurement error") — the tier presentation generalizes that concession.

| Tier | Systems (within-tier order not distinguishable) | Characterization |
|------|--------------------------------------------------|------------------|
| **Reference ceiling** | Mizushiro Mizuki (JP source) | Authorial intent; not a translation (Appendix C) |
| **Tier 1** | Fable 5 (harness) | Encoded the humidity motif and completed the petal metaphor; only system observed to do so on this scene |
| **Tier 2** | Fable 5 Web; Gemini 3.1; Opus 4.7 | Strong voice/fidelity/subculture; each drops or only partially encodes the humidity motif |
| **Tier 3** | ChatGPT 5.5; DeepSeek V4 Pro (harness); Fan TL; DeepSeek V4 Web | Competent; one or more of: missed Zutomayo, factual title/name errors, humidity motif absent |
| **Tier 4** | Qwen 3.7 | Yorushika/YOASOBI conflation breaks the triple pun; lowest fidelity and subculture |

Per-dimension head-to-head summary (verbatim evidence; symbols indicate the rater's per-cell judgment, not interval scores):

| Passage | JP_SRC | FABLE | FABLE_WEB | OPUS | DSV4_PRO | GEMINI | CHATGPT | DEEPSEEK | QWEN | FAN |
|---------|--------|-------|-----------|------|----------|--------|---------|----------|------|-----|
| **P1: じとぉっと** | じとぉっと | damp stare | VREC lock | glared | ji-toooooo | cold glare | glared | dead eyes | flat glare | stare |
| **P2: だめな子** | だめな子 | hopeless girl | hopeless | broken kid | hopeless girl | useless | no good | no-good girl | useless girl | no-good girl |
| **P3: MyGO!!!!!** | romaji only | all romaji | all romaji | One Drop Sky | all romaji | all romaji | two EN titles | Lost Song | all romaji | romaji + fn |
| **P4: Triple Pun** | 3 bands | all 3 | all 3 | all 3 | no Zutomayo | all 3 | no Zutomayo | no Zutomayo | Yorushika=YOASOBI | all 3 (footnoted) |
| **P5: Kanji Play** | 詩暮病 / 四葩病 | diagnosis | characters | characters | characters | spelling | adequate | inconsistency | visual | visual + fn |

**Per-tier note on the Fan TL baseline:** the Fan TL falls in Tier 3. This reflects one fan-edited translation (MTL: Freedom; edited by Slimey Translations) on one scene, not human translation as a category (§7.4–§7.5). Its losses are concentrated in addressable categories (humidity motif absent, footnote exits, a register error in "sadist/masochist" for S/M that survived proofreading) rather than in the irreducible kanji architecture.

### 5.9 Process evidence from the reasoning logs (harness systems)

The three harness systems persisted their pre-translation reasoning to a per-chapter thinking log (§4.5). Because these logs were written *before* the rendered output, they let several claims that §5–§6 would otherwise infer from output alone be checked against the model's own decision narrative. The findings below are scoped to the three harness models (Fable 5, Opus 4.7, DSV4_PRO) plus the Fable web trace; no log exists for the five other web outputs, so none of these readings is extended to them.

**(a) Three documented strategies for one device.** The MyGO!!!!! ateji titles (§5.4, §5.6) drew three *different* explicit strategies from the three harness models — under the same `context.xml` and the same "preserve kanji meaning and reading" policy:

| System | Documented strategy | Reasoning-log evidence |
|--------|--------------------|------------------------|
| FABLE | Replicate the ateji split — write the meaning, speak the reading | [FABLE-TK:139] "give written meanings ('lost-star scream'…) + trick readings ('Mayoiuta'…). The 病/disease frame lets Junna's later 期待した字面 line become 'not the diagnosis I was hoping for'" |
| DSV4_PRO | Project the experience, discard the form | [DSV4-TK:271] "The specific kanji form is irrelevant to the experience"; [DSV4-TK:259] "I'll use romanization with explanation woven into the prose" |
| OPUS | Gloss the kanji meaning as the title | [OPUS-TK:425] "壱雫空 (ひとしずく) — 'One Drop Sky' (Hitoshizuku)" — the romaji reading is in the log, parenthetically, but the literal gloss was selected as the rendered title |

This grounds §5.6's observation that only Fable treated the ateji as a signature to replicate: the logs show the other two harness models *consciously choosing not to* — DSV4_PRO judged the written form "irrelevant," and Opus had the romaji reading in hand and selected the gloss. The §5.6 divergence is a set of documented decisions, not an accident of differing knowledge.

**(b) The "Utsu-Rock" difference is hierarchical resolution, not a knowledge gap.** §5.6/§6.2 record that the two harness models rendering "Utsu-Rock" (Fable, DSV4_PRO) enforced a lock the others missed. The logs show the mechanism precisely. All three harness models received the constraint; they resolved its *tier* differently:

- FABLE [FABLE-TK:130]: "鬱ロック → 'Utsu-Rock' … (Vol-1 ENFORCE lock; **this overrides the brief's 'Depressive Rock'** since the exact recurring phrase is continuity-locked from Vol 1 — JP-source + ENFORCE-tier wins)"
- DSV4_PRO [DSV4-TK:148]: "Utsu-Rock (鬱ロック) — yes, appears. COMMIT"
- OPUS [OPUS-TK:165]: "鬱ロック愛好会 → 'Depressive Rock Appreciation Society' — term lock per glossary ('Depressive Rock')"

The harness delivered both a brief-tier entry ("Depressive Rock") and a higher Vol-1 ENFORCE-tier entry ("Utsu-Rock"). Fable and DSV4_PRO surfaced and applied the higher-tier continuity lock; Opus applied the brief-tier term and did not surface the ENFORCE lock. This refines §6.2: the gap is not "Opus ignored a constraint" but "Opus resolved a constraint *hierarchy* to a different (lower) tier than the other two harness models" — consistent with §6.2's general observation that each Opus override is individually defensible (the brief did say "Depressive Rock").

**(c) A correction to the Yorushika-etymology claim.** An earlier statement (§6.2) credited Opus's reasoning with documenting the Yorushika 夜しか ("only at night") etymology "more explicitly than Fable 5's." The primary logs reverse this:

- FABLE [FABLE-TK:142]: renders the pun "can't sleep anywhere but Yorushika — nights only" — the correct 夜しか ("only at night") parse — and localizes 夜好性ガール as "Night-Owl Girl."
- OPUS [OPUS-TK:170]: "pun on band name Yorushika (ヨルシカ = 'night deer')" — an *incorrect* parse, reading シカ as 鹿 ("deer") rather than the limiting particle しか ("only").

Opus reasoned about the etymology but reached the wrong one; Fable reached the right one. §6.2 and the §5.6 observation are corrected accordingly. This does not overturn the compliance-gap finding (which rests on the title, humidity, and lock evidence), but it removes a specific example the primary record contradicts — and it illustrates why process claims must be grounded to the logs rather than to a derivative analysis file (the reversed claim traced to one).

**(d) The humidity motif is an explicit object of deliberation only in Fable's logs.** §6.4 reads the motif as a tracking problem. The Fable web trace shows the tracking happening as conscious self-rationing:

- FABLE_WEB [FABLE_WEB-TK:92]: "that characteristic heavy-lidded stare — I'm being careful not to overuse that description since it's already her signature look"
- FABLE_WEB [FABLE_WEB-TK:122]: "deciding whether to reuse 'that heavy, lidded stare' … or introduce a slight variation to keep the phrasing fresh"

No comparable deliberation about the じとぉっと gaze appears in the Opus or DSV4_PRO logs, and both rendered it as a neutral or sound-coded glare (§5.5). Absence in a log is weaker evidence than presence, so this is suggestive rather than conclusive; but it is consistent with §6.4 — the only logs that show motif-tracking as an explicit decision are Fable's.

**(e) Independent corroboration for Appendix A.** DSV4_PRO's log shows it catching one of the harness's own data-quality issues (Appendix A.6): [DSV4-TK:328] "the name_map says Kuzumi Yojiro, but the translation_brief says Kusumi Yojiro … The name_map is the authority … Going with Kuzumi Yojiro." This is the name-map typo Appendix A documents — direct evidence for A.3's claim that the gate-stripped harness did not silently mislead the model. The nuance the log adds: faced with the same inconsistency, the two models resolved it *oppositely* — the Fable trace defers to the brief ([FABLE_WEB-TK:3] "though the name_map shows a variant reading, the brief's name_lock takes precedence"), landing on the correct "Kusumi," while DSV4_PRO defers to the name_map and propagates the erroneous "Kuzumi" (久住 = "Kusumi" per the JP source). The harness's internal inconsistency thus reached the output of one harness model and not the other — a concrete instance of the §7.6 data-quality caveat.

These logs are the models' self-reports of their own reasoning and may rationalize rather than faithfully record; they are used here to establish that specific renderings were *deliberated choices* rather than accidents, not to certify the quality of those choices.

---

## 6. Discussion

Three structured comparisons in the design support inferences that go beyond per-system scoring. Each is reported with its associated uncertainty; causal language is avoided in favor of "associated with" where the mechanism is not directly measured.

### 6.1 The harness-vs-web difference ("infrastructure dividend")

The constraint-enforcing harness (Appendix A) provides canonical rendering locks, a voice profile system, a cross-pass consistency feed, emotional-temperature calibration, a self-revision loop, and a canonical term registry. Comparing harness-enabled and web systems:

| Condition | Harness? | Model | Tier | Notable |
|-----------|---------|-------|------|---------|
| Harness | Yes | Fable 5 | 1 | Humidity motif encoded; petal metaphor completed |
| Harness | Yes | DeepSeek V4 Pro | 3 | Giongo preservation; term locks enforced |
| Harness | Yes | Opus 4.7 | 2 | Humidity motif dropped despite locks |
| Web | No | Gemini 3.1 | 2 | Strong subculture; humidity partial |
| Web | No | ChatGPT 5.5 | 3 | — |
| Web | No | Qwen 3.7 | 4 | Triple-pun conflation |

A naive reading — Gemini (web, Tier 2) at or above Opus (harness, Tier 2) — might suggest the harness does not matter. The data support a narrower claim: **the harness behaves as a force multiplier on whatever capability the model brings, not a substitute for it.** Two controlled comparisons isolate its effect:

- **Fable 5 vs. Fable 5 Web** (same model, harness present/absent): a small advantage to the harness condition (original estimate +0.04).
- **DeepSeek V4 Pro vs. DeepSeek V4 Web** (same model family, harness present/absent): a slightly larger advantage to the harness condition (original estimate +0.06).

Both differences are within the same order as the ≤0.04 uncertainty band, so the *magnitude* should be read cautiously; the *direction* is consistent across two model families. The original document characterizes this as a consistent ~0.05 dividend "roughly the gap between adjacent rank positions." Restated conservatively: the harness is associated with a one-tier-or-less improvement, consistent across both controlled pairs, and is not large enough to reorder distant tiers.

**What the harness does not do.** The DeepSeek comparison bounds the effect: both DeepSeek conditions miss Zutomayo and truncate "Chirinuruwo." The harness did not supply subculture knowledge the model lacked. Two further negative results: harness systems' subculture scores (Fable 5, Opus) are near-identical and both trail web Gemini, indicating the harness delivers constraints, not facts; and Opus, given the same locks as Fable 5, still produced "depressive rock," "glared," and "One Drop Sky" — the harness delivered the constraint but did not enforce compliance against a model that overrode it.

### 6.2 The compliance gap (within-vendor, identical infrastructure)

Fable 5 and Opus 4.7 are both Anthropic frontier models that received identical infrastructure. Their tier difference is therefore attributable to model behavior, not the harness. The per-dimension judgments (Appendix B) locate the gap:

| Dimension | Direction | Magnitude (per Appendix B) |
|-----------|-----------|---------|
| Voice | Fable 5 higher | Moderate |
| Subtext | Fable 5 higher | Moderate |
| Rhythm | Fable 5 higher | Moderate |
| **Fidelity** | **Fable 5 higher** | **Large** |
| **Humidity** | **Fable 5 higher** | **Largest** |
| Subculture | ~equal | Negligible |
| Craft | Fable 5 higher | Moderate |

The gap is **not** primarily in declarative knowledge — subculture scores are near-equal, and on the one band etymology both models reasoned about explicitly (Yorushika), the primary logs show Opus reaching the *wrong* parse ("night deer") and Fable the correct one ("only at night") (§5.9c). It concentrates in **constraint compliance**:

| Constraint | Delivered by harness | Fable 5 | Opus 4.7 |
|-----------|----------------------|---------|----------|
| じとぉっと → humidity-coded gaze | Yes (`context.xml`) | "damp, accusing stare" | "glared at me" |
| 鬱ロック → "Utsu-Rock" | Yes (term lock) | "utsu-rock" | "depressive rock" |
| 壱雫空 → romaji only | Yes (policy) | "Hitoshizuku" | "One Drop Sky" |
| Voice RAG fingerprints | Yes (per-character) | Applied | Partially applied |

A consistent behavioral pattern is visible: where its internal preference conflicts with a harness constraint, Opus favors its own preference (each override individually defensible — e.g. "One Drop Sky" is arguably more accessible than "Hitoshizuku"), while Fable 5 complies even when the constraint yields slightly less natural isolated output. The "Utsu-Rock" case is a softer variant of the same pattern: the reasoning logs (§5.9b) show Opus resolving a constraint *hierarchy* to the brief tier ("Depressive Rock") where the other two harness models surfaced the higher Vol-1 ENFORCE lock ("Utsu-Rock") — a tier-resolution difference, not a flat refusal. The result is that Opus has higher peak declarative knowledge (its log alone correctly identifies 四葩 *yohira* as an archaic word for hydrangea, [OPUS-TK:174]) but lower integrated compliance. This is the clearest single finding of the study that generalizes beyond translation: under a constraint-delivery architecture, compliance behavior can dominate declarative capability. It is, however, observed on one scene with two models and should be tested at scale before being treated as a model property.

### 6.3 The Fable 5 / Fable 5 Web controlled experiment

The cleanest comparison holds the model and the ~11,700-token `context.xml` fixed and varies only programmatic enforcement:

| Condition | Fable 5 (harness) | Fable 5 Web |
|-----------|----------------------|-----------------|
| `context.xml` | Identical | Identical |
| Canonical rendering enforcement | Programmatic | Advisory only |
| Voice profile / cross-pass / self-revision / register routing | Programmatic | Advisory only |
| Tier | 1 | 2 |

Three specific differences localize the effect:

| Technique | Fable 5 (harness) | Fable 5 Web |
|-----------|----------------------|-------------|
| Humidity encoding | "damp, accusing stare" (creative) | "heavy, lidded stare" (lock-compliant only) |
| Petal metaphor | "flipped with every petal" | "flipped like a coin" |
| MyGO!!!!! ateji device | "Hitoshizuku" kept; meaning-gloss in narration, reading in dialogue; 詩暮病 integrated | "Hitoshizuku" kept; gap not reconstructed |

These support a two-part reading. **(a)** Fable 5's structural literacy — ateji recognition, voice fidelity, subculture knowledge, 花占い comprehension — survives the harness-to-web transition intact, so it is model-native. **(b)** The *operationalization* of that literacy (encoding humidity into a verb phrase, completing a metaphor across twenty lines) appears only in the harness condition.

The MyGO!!!!! ateji row is the one that most constrains the *mechanism*, because for this device the harness can be shown to have supplied no answer. Both conditions recognized the titles as untranslatable band names and kept the romaji — ateji *recognition* is model-native, the (a) trait — but only harness-Fable reconstructed the meaning-versus-reading device in English (glossing the written meanings in narration, speaking the readings in dialogue, and treating 詩暮病 as a member of the set), while web-Fable kept the readings and left the device unbuilt ([FABLE_WEB:219]; §5.6). The reconstruction is the (b) operationalization. What separates this row from the humidity and petal rows is that its (b) gap cannot be attributed to answer-injection. The humidity motif has gaze-related locks and voice fingerprints in the harness, so a skeptic can argue the harness primed the motif and the model merely elaborated it; the ateji device had no such priming. Of the five titles, only 輪符雨 appears in the assembled `context.xml`, flagged as a "Kirakira/Ateji reading for Refrain; likely a song title" with an empty target and an explicit `chosen_reason` of "No stable equivalent found; requires model translation" (context.xml:230; .context/cultural_glossary_en.json:15–21). The other four — 壱雫空, 迷星叫, 影色舞, and the coinage 詩暮病 — are absent from the context entirely. The harness flagged one term and delegated its rendering; it had no solution to hand over. For at least this instance, then, the operationalization dividend cannot be the harness feeding the model an answer.

This result should therefore be classified as **harness-conditioned latent capability**, not as either a pure model variable or a hard constraint effect. The process record shows the distinction. In the harness run, FABLE independently states the strategy: render 迷星叫/影色舞/詩暮病 as written meanings plus trick readings, and preserve the 病 frame so Junna's later 字面 complaint becomes "not the diagnosis I was hoping for" [FABLE-TK:139]. The final output then enacts that plan: the notebook contains titles "spelled *lost-star scream*," "*shadow-color dance*," and "*Shigure Disease*" [FABLE:223], the reading is spoken as "'Amamori Junna'" [FABLE:227], and the payoff lands as "Not the diagnosis I was hoping for" [FABLE:253]. In the web condition, the trace shows the model recognizing the same terrain but choosing a different strategy: it considers keeping the kanji visible because the gag is "fundamentally a visual gag about how things are written" [FABLE_WEB-TK:107], then resolves Shigure's reply as "Yohira Syndrome" [FABLE_WEB-TK:108]. The final output follows that strategy: it keeps 詩暮病 on the page as "Shigure Syndrome" [FABLE_WEB:223], keeps 四葩病 visible as "Yohira Syndrome" [FABLE_WEB:245], and makes Junna's reaction "Not the characters I was hoping for" [FABLE_WEB:253]. The web run did not lack the general ateji concept; it selected a visible-kanji strategy that preserves encounter over reconstructed gap. The harness run did not obey a prewritten solution; it selected and executed the gap-reconstruction strategy under a stricter translation architecture.

Two cautions bound the inference. First, it is one device on one harness-vs-web pair (N = 1 per condition, single rater); the divergence is consistent with run-to-run sampling variance and does not show that harness-Fable would rebuild the device reliably, or that web-Fable could not. Second, excluding answer-injection narrows the candidate mechanisms without identifying one; the alternatives weighed below apply to the ateji case exactly as they do to humidity and the petal metaphor. The case removes the most deflationary explanation of the dividend for one instance; it does not promote the surviving mechanism from hypothesis to finding.

The original explains (b) via a "freed cognitive budget" mechanism: the harness offloads ~600 tokens of constraint management, which are reallocated to craft. **This mechanism is a hypothesis, not a measurement.** The data establish that the operationalization difference is *associated with* the harness condition; they do not establish that token reallocation is the cause. Alternative explanations (e.g. the self-revision loop surfacing the metaphor on a second internal pass, or advisory-vs-enforced framing changing the model's attention allocation) are equally consistent with the observation. The hypothesis is worth testing directly (e.g. by instrumenting token allocation under both conditions) but should not be reported as established.

### 6.4 The humidity motif as the discriminating dimension

Across all comparisons, the humidity motif (じとぉっと / 湿度) produced the widest dispersion. It requires recognition (this is a humidity-coded gaze, not a glare), tracking (across multiple trigger points), voice binding (consistent with Junna's register), and structural placement (culminating in 詩暮病). One harness system (Fable 5) satisfied all four; harness Opus and web Gemini satisfied two or three; the remaining systems and the Fan TL satisfied one or none. The most defensible interpretation is that the motif is a **constraint-tracking problem rather than a vocabulary problem**, and that constraint tracking is precisely what a programmatic harness can support — consistent with the §6.1 force-multiplier reading. This dimension is also the one most exposed to the rater conflict (the humidity score drives Fable 5's Tier 1 placement); it should be re-rated independently before the magnitude is relied upon.

### 6.5 Wordplay-translation strategies (Delabastita's framework)

The renderings of the triple-band pun (§5.4) were described above with ad-hoc strategy labels — *isolate, embed, lead-in, explain, drop*. Translation studies already has an established vocabulary for these choices: Delabastita's (1996) typology of pun-translation strategies, developed for Shakespearean wordplay and since applied across literary and audiovisual translation. Mapping the observed strategies onto that typology converts a local description into a comparable framework and exposes a distinction the binary "preserved / dropped" counting of §5.4 obscures — the systems that "preserved" Zutomayo did so by **three different mechanisms**, not one.

Delabastita's relevant categories are: **PUN→PUN** (render with a target-language pun); **PUN→NON-PUN** (render with a non-punning phrase — *selective* if one sense is kept, *non-selective* if both are carried non-punningly); **PUN→RELATED RHETORICAL DEVICE** (recover the effect through allusion, repetition, etc.); **PUN→ZERO** (omit the punning passage); **PUN ST=TT** (copy the source pun verbatim, e.g. in romaji); and **EDITORIAL TECHNIQUE** (footnote or gloss). Applied to the Zutomayo sentence (ずっと真夜中でいいのに, which simultaneously means "I wish it could stay midnight forever" and names the band):

| Strategy label (§5.4) | System(s) | Delabastita category | What the mapping exposes |
|-----------------------|-----------|----------------------|--------------------------|
| Isolate | Fable 5 | PUN→NON-PUN (non-selective), covert | English meaning carries the band's sense; band identity left recoverable by informed readers, unmarked — an "if you know, you know" rendering |
| Embed | Opus 4.7 | PUN ST=TT (direct copy) | romaji "Zutomayo" inserted into English syntax; reads as foreign, the sentence stumbles |
| Lead-in | Gemini 3.1 | PUN ST=TT (direct copy), fronted | band name as a capitalised appositive plus a non-pun gloss |
| Explain | Fan TL | PUN→NON-PUN (non-selective) + editorial technique | literal sense rendered *inline* in the dialogue (italic "only at night," "nightlife," "always midnight" [FTL§2:115–116]), band identity supplied in a footnote, and the 夜好性ガール epithet localized as "Night-Loving Girl" [FTL§2:117] — both senses carried, a footnote *supplement*, not an exit |
| Drop | ChatGPT, DeepSeek, Qwen | PUN→NON-PUN (selective) / PUN→ZERO | the literal "midnight" sense is kept; the band-pun layer is lost |

The framework's value here is discriminative. Under §5.4's pass/fail counting, Fable 5, Opus, Gemini, and the Fan TL all "preserved" the pun; the typology shows they occupy three distinct categories — covert non-pun, direct copy, and editorial technique — with materially different reader experiences (no exit / foreign intrusion / in-text meaning plus a footnoted identity). The same lens classifies the other two wordplay devices:

- **MyGO!!!!! ateji titles (§5.4):** the correct romaji-retention policy is **PUN ST=TT** — the ateji's kanji-meaning ↔ forced-reading split cannot survive in an alphabet, so the title is copied; the graphemic wordplay itself is necessarily **PUN→ZERO**. The invented "One Drop Sky" / "Stray-Star Song" renderings are **PUN→NON-PUN (selective)** that additionally select the *wrong* sense (the literal kanji gloss) for a band with no official English title — a fidelity error, not merely a strategy choice.
- **哀 ≠ 愛 (§5.4):** the 哀をこめて parody of the idiom 愛をこめて ("with love" → *From Russia with Love*) is best served by **PUN→RELATED RHETORICAL DEVICE** — an allusive substitution ("…with SORROW" echoing the expected "…with love"). The systems that rendered "love" (ChatGPT, Qwen) did not choose a different strategy; they selected the wrong sense, collapsing the device.

Two cautions. First, the strategy a system used does not map cleanly onto its tier: direct copy (Opus) and covert non-pun (Fable 5) sit in adjacent tiers, and the Fan TL's editorial technique places it below several systems that copied or covertly preserved. Strategy choice and execution quality are separate axes; Delabastita's typology classifies the *choice*, not its success. Second, all strategy assignments here are the single rater's reading of each rendering (§7.1–§7.2); the typology is offered to sharpen description, not to certify the underlying judgments.

### 6.6 Compensation as the mechanism of cross-segment quality: the petal metaphor

§5.7 reported that one rendering — Fable 5's "Yamada's expression flipped with **every petal**" — completed a figurative chain the source plants twenty lines earlier (Shigure's 花占い, "he loves me, he loves me not" petal divination, JP ~401) and pays off at a sentence the source leaves *plain* (ころころ変わる山田の表情, JP ~421, where ころころ is a tumbling-onomatopoeia carrying no floral image). That rendering is the study's cleanest single demonstration of why the metrics rejected in §2 cannot evaluate this scene, and it has an established name in translation studies: **compensation in place** (Hervey & Higgins, 1992; Harvey, 1995).

The mechanism is precise. In the Japanese, the seed→payoff link is carried *implicitly*: the 可愛い／きもい alternation at the payoff rhymes with the loves-me/loves-me-not rhythm of the seed, and ころころ faintly evokes the tumbling of petals. English has no equivalent giongo — rendered literally, the payoff sentence ("Yamada's expression changed every time…", as in the Fan TL) is cohesive only locally and **drops the cross-segment figurative tie**. Fable 5 compensates by re-deploying the floral image *lexically and at a displaced location*, making explicit at the payoff what the source carried implicitly across the gap. This is compensation *in place* (the compensating element appears at a different point than the loss it offsets) and *in kind* (a lexical metaphor substitutes for an onomatopoeia-borne image).

The bookend to §2 is exact. Compensation is, by definition, a **cross-segment operation**: the compensating segment offsets a loss located elsewhere. A segment-level metric therefore cannot score it, and worse, would **penalise** it — "every petal" is absent from the JP payoff sentence, so a BLEU or COMET fidelity check evaluating that line in isolation reads "petal" as an unsupported insertion, exactly as Worked Example 1 (§2.1) showed the motif-correct じとぉっと rendering being penalised. The choice becomes legible as correct only when the payoff line is read against a seed twenty lines upstream. This is the same cross-segment property the Introduction (§1) named as the thing literary-MT evaluation must capture and standard metrics miss — here instantiated in a single, checkable pair of lines.

Two limits hold. The controlled comparison (§6.3) associates the compensation with the harness condition, not the model in isolation — Fable 5 Web, the same model with the same 花占い seed rendering, produced "flipped like a coin," an unrelated image — so the *operationalisation* of the compensation, like the humidity encoding, appears only under enforcement, and the mechanism behind that remains the hypothesis of §6.3. And this is one rater's reading of one device; compensation in place is named here to identify the mechanism, not to re-establish the contested score it sits behind.

### 6.7 A literacy taxonomy (proposed, not validated)

The per-system behavior suggests a four-level descriptive taxonomy of translation literacy:

| Level | Definition | Systems observed at this level (this scene) |
|-------|-----------|---------------------------------------------|
| **Structural** | Recognizes an artistic signature as a pattern to replicate, not a policy to follow | Fable 5 |
| **Contextual** | Knows what things are and why they matter; deploys as correct policy | Gemini, Opus |
| **Adequate** | Gets words right, understands the basic situation, misses structural elements | ChatGPT, Fan TL, DeepSeek |
| **Surface** | Translates words correctly, misses identities | Qwen |

This taxonomy is a *description* of the observed range, not a validated instrument. The level assignments are single-rater judgments on a single scene; the same systems could occupy different levels on a scene with different demands (e.g. dialect comedy or historical exposition, neither of which this scene tests).

### 6.8 Practical implications

Subject to all caveats in §7, the observations carry tentative practical implications for the pipeline this scene was drawn from:

- For this series, the harness + Fable 5 combination produced the only Tier 1 rendering on this scene, driven primarily by humidity-motif retention. Gemini 3.1 was the strongest web-only configuration.
- Adding an explicit じとぉっと canonical rendering lock and a MyGO!!!!! romaji instruction ("the band has no official English localizations") would constrain the humidity and title-fidelity dimensions independently of model choice — addressing the two most common failure modes observed.
- For web-interface use, Qwen's triple-pun conflation is a specific failure mode for music-referent scenes; ChatGPT and DeepSeek need subculture fact-checking on band names.
- For fan or human translators, the footnote-exit pattern (three footnotes in one comedy exchange in the Fan TL) is a quality cost worth minimizing; humidity-coded prose is a trainable skill — most LLM systems and the Fan TL missed it equally.

These are implications for one pipeline on one scene, not general recommendations.

---

## 7. Limitations & Threats to Validity

The findings above are bounded by five threats, stated here without mitigation language. Several were noted in passing in the source material; they are consolidated and elevated here because, taken together, they constrain every quantitative claim in the study.

### 7.1 Evaluator independence (primary threat)

The evaluation was produced by a single rater drawn from the same model as one contestant. The rater was an **independent DeepSeek V4 Pro instance**, run in a separate environment (VSCode) with no connection to the translation pipeline, to the `context.xml` harness, or to the `DSV4_PRO` contestant run (#9). It therefore did **not** grade its own generation: the rendering scored as `DSV4_PRO` was produced by a different instance under different infrastructure, and the rater had neither privileged access to nor authorship of that output. This is a narrower conflict than self-grading — but it is not eliminated.

The residual threat is **same-model self-preference bias**. The rater shares model weights and training lineage with one contestant, so it may systematically favor renderings that resemble its own model's stylistic tendencies — over-rewarding choices a sibling model would make, under-rewarding unfamiliar ones — independently of which output is nominally "its own." Under this account the risk is not self-grading of a specific generation but a **model-level aesthetic prior** applied across all nine systems, including the Fan TL baseline. The rater placed `DSV4_PRO` mid-tier (Tier 3), which is consistent with an unbiased rater but does not rule out a diffuse same-model prior that this design cannot detect. **All scores, tiers, and per-dimension judgments should therefore be treated as provisional pending re-rating by independent evaluators built on a different model family with no shared training lineage or a professional human translator/evaluator.** This threat is sufficient to keep the numeric results from being treated as established, and is the reason the body presents tiers rather than scores.

### 7.2 Single rater, no reproducible rubric

Even setting aside the conflict, the scores are single-rater judgments. No operationalized rubric was published that would let an independent evaluator reproduce the two-decimal subscores (e.g. how 0.92 vs. 0.90 on subtext was derived). There is no inter-rater reliability statistic (no Cohen's κ or Krippendorff's α). The dimension-level evidence tables (§5) are reproducible — they quote the renderings directly — but the mapping from those tables to numeric subscores is not. This motivates the ordinal-tier presentation (§5.8) and means within-tier ordering carries no claim. Two partial responses are supplied but do not dissolve the threat: **Appendix E** adds a layer of fully rater-independent measures (verbosity, raw-script retention, factual-anchor retention, footnote apparatus) that any third party can recompute, and **Appendix F** supplies an operationalized, anchored rubric so the subjective dimensions can in principle be re-scored with reported inter-rater reliability. Appendix E notably does *not* recover the ranking (§E.5), which both confirms the §2 thesis and underscores that the reproducible layer cannot substitute for the contested literary judgments — it can only bound and contextualize them.

### 7.3 No significance testing

No confidence intervals, bootstrap estimates, or significance tests accompany the scores. The original itself identified one adjacent pair (Fan TL vs. DeepSeek, 0.01 apart) as "within measurement error"; generalizing that noise floor implies that gaps of roughly ≤0.04 are not separable on this design. Under that band, at least the Tier 2 and Tier 3 groupings contain systems that are not statistically distinguishable from one another. Reported magnitudes (e.g. the +0.04 / +0.06 infrastructure dividends) are within or near this band and should be read as directional, not precise.

### 7.4 N = 1 scene

The study evaluates one ~220-line scene, from one chapter, of one volume, by one author, in one genre (literary romance/comedy light novel). The benchmark's discrimination is validated only within this scope. In particular, the most quotable finding — that four of eight LLM configurations placed above the fan-edited translation (Fan TL) — is scoped to **this scene and this single fan-edited translation**; it is not a categorical result about LLMs versus human translators. Extrapolation to other scene types (dialect comedy, historical exposition, action pacing, large-cast voice differentiation — none tested here) is unsupported. A multi-scene, multi-volume replication would be required to make claims at the level of "systems" rather than "this rendering of this scene."

### 7.5 Single fan-edited baseline

The non-LLM comparison rests on one fan-edited translation (Slimey Translations; machine translation by Freedom, edited by Slimey, proofread by Crash, Jack74593, and Slimey), used because it is the only complete English translation of the volume known to exist as of June 2026. It is a machine-translated, multi-pass edited fan release — not a human-from-scratch translation and not a professional localization produced under publisher editorial standards. Human translation quality varies enormously by individual; a professional translator combining J-Rock literacy with literary prose skill could plausibly place anywhere from Tier 3 to Tier 1. The Fan TL therefore establishes one fan-edited data point — not a human ceiling and not a human floor. All Fan-TL-vs-LLM statements in this document must be read as "this specific fan-edited translation vs. these specific LLM renderings."

### 7.6 Secondary threats

- **Single-pass asymmetry (§4.4):** LLMs were evaluated on first-pass output; the Fan TL was machine-translated then passed through multiple editorial and proofreading cycles. LLM errors are partly first-pass artifacts that a second pass might remove; the asymmetry favors the Fan TL on revisable errors and the LLMs on raw comprehension. The benchmark does not separate "knowledge gap" from "single-pass deployment failure."
- **Mechanism claims are hypotheses (§6.3):** the "freed cognitive budget / ~600 tokens" account of the infrastructure dividend is not measured and is reported as one of several consistent explanations.
- **`context.xml` data-quality issues (Appendix A):** the harness input itself contains a name-map typo and a malformed relationship dyad; neither infrastructure model was misled, but the harness is not a pristine knowledge source, and the measured dividend is net of these internal errors.

### 7.7 Benchmark–conclusion coupling (selection circularity)

A threat specific to this study's provenance must be stated plainly. The benchmark scene was selected for its concentration of motif-tracking and term-lock devices (§3); the constraint-enforcing harness under test was built, by the same pipeline, to enforce exactly such motifs and locks (Appendix A). The aggregate result — that the sole Tier-1 configuration is a harness system (Fable 5, §5.8) and that the harness is associated with a consistent one-tier-or-less lift (§6.1) — is therefore partly *coupled to the scene choice*: a benchmark that rewards motif-lock enforcement, evaluated on systems one of which is purpose-built to enforce motif locks, carries a built-in directional expectation. §3.6 asserts model-agnosticism ("the same scene would have discriminated equally if another system had won"), but that claim is not falsifiable from a single run.

Two qualifications bound how far this threat reaches. First, it attacks the *absolute* standing, not the *controlled comparisons*: the FABLE-vs-FABLE_WEB and DSV4_PRO-vs-DEEPSEEK pairs (§6.1, §6.3) hold the model fixed and vary only the harness, so co-selection cannot manufacture the within-pair difference — it can only inflate how decisive the top tier appears in aggregate. Second, the device carrying the most discriminating weight (the humidity motif, §3.7) is the one most exposed both to this coupling and to the rater conflict (§7.1), which is why §6.4 already flags it for independent re-rating. The defensible reading is that the *mechanisms* (an infrastructure dividend; compliance dominating declarative knowledge) are real and isolated by controlled design, while the *magnitude* of the harness's apparent dominance is partly an artifact of choosing a scene that rewards what the harness does. Separating the two would require a benchmark assembled by a party with no stake in any contestant, across scenes not selected to favor constraint enforcement.

---

## 8. Conclusion

On a single scene chosen as the densest concentration of self-contained meta-linguistic devices in its series, nine contestants — eight LLM configurations and one fan-edited translation — separated into four tiers. Because every contestant produced fluent English, the separation was driven almost entirely by *comprehension*, not *proficiency*: the discriminating errors were not failures of English but failures to recognize what the Japanese was doing — a humidity motif read as a plain glare, a confession read as wordplay, three band-name puns read as one. One harness-enabled configuration (Fable 5) was the only system observed to encode the title's humidity motif at its trigger point and to complete a metaphor chain across twenty lines; it sat closest to the authorial-intent reference, with its residual gap dominated by structurally untranslatable kanji devices (Appendix C) rather than correctable errors. The remaining contestants distributed across the lower tiers according to specific, mostly addressable failures: dropped motifs, missed band references, invented song titles, and one triple-pun conflation. That ordering is partly coupled to a scene chosen to reward constraint enforcement (§7.7); the controlled comparisons below, not the tier ordering, carry the weight.

Three observations are more robust than the per-system ranking, because each rests on a controlled comparison rather than an absolute score:

1. **Standard automatic metrics do not measure what discriminates quality here.** BLEU evaluates none of the seven dimensions and would invert the ranking; COMET evaluates roughly 1.5 and would reorder the top three. The dimensions that matter are cross-segment comprehension properties, not segment-level semantic accuracy (§2).
2. **A constraint-enforcing harness is associated with a small, consistent, one-tier-or-less improvement** across two model families, bounded by the model's native knowledge — it delivers and tracks constraints but does not supply facts the model lacks (§6.1, §6.3).
3. **Under identical infrastructure, constraint-compliance behavior separated two same-vendor frontier models more than declarative knowledge did** (§6.2), now grounded in the models' own reasoning logs (§5.9a–b), which show the separation as a deliberated constraint-*hierarchy* resolution rather than a knowledge difference — a finding that, if it replicates, generalizes beyond translation to constraint-delivery architectures generally.

What remains open is substantial. The scores are single-rater and produced by a same-model rater; the design is N = 1 scene with one fan-edited baseline; no significance testing was performed; and the central infrastructure-dividend mechanism is hypothesized rather than measured. The appropriate next steps are independent re-rating with a published rubric and inter-rater reliability (a starting rubric is supplied in Appendix F), multi-scene replication across distinct literary demand profiles, and direct instrumentation of the proposed token-reallocation mechanism. A first layer of rater-independent measures already accompanies the study (Appendix E), though it deliberately does not substitute for the literary judgments it cannot recover (§E.5). Until then, the contributions that stand most firmly are the benchmark-design framework (§3), the metric-inadequacy analysis (§2), and the reasoning-log process-tracing of the harness systems (§5.9) — all of which are independent of the contested scoring.

In short, what this study delivers is not a ranking of translation systems but a *method* for evaluating them where it is hardest — at the point where comprehension, not fluency, is the bottleneck and where both automatic metrics and segment-level human judgment go blind — together with one fully worked application of that method on nine contestants and a fan-edited baseline. The tier table is the worked example; the method, and the evidence that it measures something real that existing tools miss, is the contribution.

---

## Appendix A: Anatomy of the Harness Input (`context.xml`)

The harness's concrete output is a single XML document (generated 2026-06-10T03:31:58) injected as pre-translation context for every chapter. This appendix documents what it delivers; it grounds the "harness" references in §4–§6 in a specific artifact.

### A.1 Pre-aggregation validation

Before block assembly, a validation gate audits source data against the JP original. This volume's `context.xml` carries a visible audit trail at the top:

```
[1] Stripped fabricated character profile 'Kurimoto_Shigure' — no JP evidence
[2] Stripped fabricated character profile 'Amamori_Junna' — no JP evidence
[3] Stripped fabricated character profile 'Akagi_Eimi' — no JP evidence
[4] Stripped fabricated character profile 'Akagi_Eimei' — no JP evidence
Total corrections: 5
Preserved 0 verified profiles (14 from character_names, 0 from JP evidence)
```

The metadata enrichment stage generated fabricated profiles with empty `full_name` fields and no kanji evidence; the gate stripped them before the model received them. Without this gate the model would have received false character data as authoritative context. The empty `<character_roster>` entries that remain (7 characters with blank `<identity>`, `<personality>`, `<voice>`) are a known gap — the voice profile stage produced no output for this volume.

### A.2 The 13 blocks delivered to the model

| # | Block | Contents | Token est. | Pre-processing stage | Constraint type |
|---|-------|----------|------------|---------------------|-----------------|
| 1 | `<volume_identity>` | Title (JP+EN), author, publisher, volume number, total chapters (14), page progression | ~50 | Document extraction | Identity anchor |
| 2 | `<world_setting>` | Honorifics policy, name order (Family-Given), setting label | ~80 | Metadata enrichment | Cultural policy |
| 3 | `<character_roster>` | 7 characters (canonical names only; identity/personality/voice empty) | ~200 | Voice profile generation | Character existence |
| 4 | `<name_map>` | 7 JP→EN name pairs with kanji | ~100 | Metadata enrichment | Hard name lock |
| 5 | `<relationship_graph>` | 3 dyads (Shigure/Junna: complicated_romance; Shigure/Akagi: musical_rival_friend; Yamada/Shigure: classmate) | ~100 | Metadata enrichment | Relationship awareness |
| 6 | `<verbatim_anchors>` | 29 canonical rendering locks: series title, key lines, character quotes, 16 song-title series anchors, tagged anchors | ~400 | Cross-volume | Hardest constraint — must match exactly |
| 7 | `<voice_fingerprints>` | Empty | 0 | Voice profile generation | (gap) |
| 8 | `<cultural_glossary>` | 11 ateji/term definitions: 湿度が高い, 輪符雨 (ateji for Refrain), 受動的→Maguro, 髭男 (HIGE DANdism abbrev.) | ~250 | Metadata enrichment | Subculture reference |
| 9 | `<eps_arc_tracker>` | Per-character, per-chapter emotional positioning (baseline + band) for 7 characters across 14 chapters | ~800 | Emotional register calibration | Emotional temperature |
| 10 | `<scene_plans>` | Per-scene beat typing, register band, dialogue register, target rhythm, arc, transition, line span, prose tone | ~2,500 | Scene-level pacing plan | Scene-level pacing |
| 11 | `<eps_signals>` | Quantitative per-character speech metrics: register, keigo shift, sentence-length delta, particle signature, pronoun shift, dialogue volume, direct-address frequency | ~1,200 | Quantitative speech analysis | Voice quantification |
| 12 | `<illustration_context>` | 10 illustrations analyzed via vision model: composition, emotional delta, narrative directives, spoiler gates, character-identity resolution with confidence | ~2,000 | Illustration analysis | Visual anchoring |
| 13 | `<translation_brief>` | Volume overview, 7 character profiles, 14-chapter timeline, 6 terminology locks, tone/style guidance, emotion map, 3 motifs, 17 risk flags | ~4,000 | Strategic guidance generation | Strategic guidance |

**Total: ~11,700 tokens** of structured pre-translation context per chapter.

### A.3 Bearing on the evaluation

1. **The harness is a structured knowledge-delivery system, not an abstraction.** Each constraint discussed in §6 maps to a specific block. The compliance gap (§6.2) is visible in how each model treats `<verbatim_anchors>`: Fable 5 accepts the locks; Opus overrides individual entries.
2. **The validation gate (A.1) is the single most consequential feature.** Stripping four fabricated profiles prevented both infrastructure models from translating with false character data; absent the gate, their fidelity would be lower.
3. **The empty `<voice_fingerprints>` block is the most visible gap.** Both infrastructure models scored well on voice despite zero structured fingerprint data, inferring voice from the translation brief and the JP source — suggesting the fingerprint layer may be less load-bearing than assumed, or that block 13 already supplies sufficient voice guidance.
4. **The cultural glossary (block 8) is undersized relative to the scene.** It defines 湿度が高い and 輪符雨 but not MyGO!!!!!, Yorushika, YOASOBI, Zutomayo, Utsu-P, or Chirinuruwowaka — all of which appear in the scene. The subculture knowledge for these terms comes from model training, not the harness; the measured dividend is earned despite this gap.
5. **Scene plans (block 10) and speech metrics (block 11) encode the emotional architecture behind humidity tracking.** The model is pre-calibrated to recognize a trigger point's emotional band before reading the JP text that causes the shift — a plausible mechanism for the §6.4 tracking advantage.
6. **The harness contains its own data-quality issues** (relevant to §7.6): the `<name_map>` encodes `"Kuzumi Yojiro"` while the `<translation_brief>` and JP source use `"Kusumi Yojiro"` (久住陽次郎); and `<relationship_graph>` contains a malformed dyad `character_a="Yamada Youjirou"` concatenating two different characters' names. Neither infrastructure model was misled, but these demonstrate the harness is a living document with a nonzero per-stage error rate.

---

## Appendix B: Raw Single-Rater Scores

The numbers below are the original rater's two-decimal judgments, reproduced unaltered. **They are single-rater judgments produced by a rater built on the same model as one contestant (§4.3, §7.1) and have no published rubric, inter-rater reliability, or significance test.** They are retained for completeness and to ground the ordinal tiers in §5.8; they should not be cited as interval measurements. Per §7.3, gaps of roughly ≤0.04 are within the noise floor of this design.

| Model | Composite | Voice | Subtext | Rhythm | Fidelity | Humidity | Subculture | Craft | Δ vs. source ref |
|-------|-----|-------|---------|--------|----------|----------|------------|-------|----------|
| Mizushiro Mizuki (JP) | 0.96 | 0.96 | 0.97 | 0.95 | 1.00 | 1.00 | 1.00 | 0.96 | — |
| Fable 5 | 0.93 | 0.94 | 0.92 | 0.93 | 0.95 | 0.98 | 0.90 | 0.92 | −0.03 |
| Fable 5 Web | 0.89 | 0.93 | 0.91 | 0.90 | 0.92 | 0.65 | 0.90 | 0.83 | −0.07 |
| Gemini 3.1 | 0.88 | 0.88 | 0.85 | 0.90 | 0.92 | 0.60 | 0.92 | 0.85 | −0.08 |
| Opus 4.7 | 0.86 | 0.90 | 0.88 | 0.88 | 0.80 | 0.55 | 0.88 | 0.85 | −0.10 |
| DeepSeek V4 Pro | 0.84 | — | — | — | 0.80 | 0.45 | — | — | −0.12 |
| ChatGPT 5.5 | 0.82 | 0.82 | 0.85 | 0.85 | 0.75 | 0.55 | 0.70 | 0.80 | −0.14 |
| Fan TL (Slimey) | 0.79 | 0.80 | 0.78 | 0.80 | 0.75 | 0.40 | 0.65 | 0.78 | −0.17 |
| DeepSeek V4 Web | 0.78 | 0.78 | 0.82 | 0.80 | 0.70 | 0.40 | 0.65 | 0.78 | −0.18 |
| Qwen 3.7 | 0.72 | 0.80 | 0.78 | 0.75 | 0.55 | 0.40 | 0.45 | 0.75 | −0.24 |

**Data-consistency note:** the original document's final rankings table listed eight systems and omitted DeepSeek V4 Pro, while its executive summary scored DeepSeek V4 Pro at 0.84 with partial subscores (fidelity 0.80, humidity 0.45). Both figures are reproduced as given; the incomplete subscore row for DeepSeek V4 Pro is an artifact of that inconsistency in the source, not a transcription error here. This discrepancy is itself a minor instance of the reproducibility concerns in §7.2.

**Reading the Δ column:** a negative value was the rater's estimate of cumulative fidelity loss relative to the authorial-intent reference (Appendix C). These deltas inherit every limitation of the composite scores and additionally depend on the conceptual 0.96 reference ceiling, which is not an empirical measurement.

---

## Appendix C: The Authorial-Intent Reference (a Conceptual Device, not a Measurement)

The Japanese source is not a translation and does not compete in the tiers. It is used as a **conceptual reference ceiling** — a way of expressing that every rendering loses something relative to the author's intent. The source was assigned a nominal 0.96 (not 1.00) to represent that even the original cannot be perfectly rendered into English, because parts of the scene are structurally untranslatable. **The 0.96 is a rhetorical device for reasoning about irreducible vs. addressable loss; it is not a measured quantity and should not be treated as one.**

The untranslatable devices that motivate a below-ceiling reference:

| Device | JP mechanism | Why no English equivalent exists |
|--------|-------------|---------------------------------|
| Ateji song titles | Kanji with forced non-standard readings (迷星叫→まよいうた) | English has no dual writing system — meaning and sound cannot diverge in a single grapheme |
| Kanji-play confession | 詩暮病 written "Shigure Disease" / structurally pointing to "Amamori Junna" | Requires a logographic system where one written form carries two simultaneous readings |
| Band-name puns | ヨルシカ ≈ 夜しか (Yorushika ≈ "only at night") | Japanese band naming exploits homophony between loanwords and native words; English bands do not |
| 哀 ≠ 愛 distinction | Two characters both read あい, opposite meanings | English has no character-level semantic disambiguation — "ai" is just a sound |
| 湿度 / じとぉっと | Title motif embedded in a single onomatopoeia | English onomatopoeia does not carry atmospheric/emotional climate the way Japanese giongo does |

The value of this device is analytic: it lets loss be partitioned into **irreducible** (kanji-play architecture, ateji, homophony — unfixable regardless of system) and **addressable** (motif tracking, title policy, the 哀/愛 distinction — fixable with better constraints or model selection). On this scene, the rater attributed the top system's residual gap mostly to irreducible loss and the Fan TL's larger gap mostly to addressable loss. That partition is an interpretive claim resting on the contested scores (§7) and a single rater's judgment of which losses were unavoidable; it is suggestive, not established.

---

## Appendix D: The Subculture-Knowledge Dimension

A cross-cutting observation: subculture knowledge (J-Rock naming conventions, Vocaloid producer lore, internet-slang registers) did not correlate with overall rendering quality in this scene. Gemini matched the Fable variants on subculture knowledge but trailed substantially on humidity. The Fan TL and web DeepSeek were judged equal on subculture knowledge, but the Fan TL's knowledge was **declarative** (footnotes documenting facts) while DeepSeek's was **operational** (attempting deployment in prose, sometimes incorrectly, as with "Chirinuruwo").

| Knowledge type | System judged strongest | 
|----------------|-----------|
| Operational (deploying band knowledge in prose) | Fable 5 |
| Declarative (documenting band facts) | Opus 4.7 / Fan TL |
| Blended (operational + declarative) | Gemini 3.1 |

The two are separable: a system can know a fact (declarative) without deploying it correctly in running prose (operational), and vice versa. No system in this scene combined maximal operational deployment with maximal declarative accuracy. This distinction is offered as a descriptive observation; like the §6.7 taxonomy, it is single-rater and single-scene, and would need independent multi-scene confirmation to be treated as a stable property of any system.

---

## Appendix E: Rater-Independent Measures

The body's scores are single-rater judgments (§7.1–§7.2). The measures below are not: each is computed mechanically from the source files (§4.5) by string- or token-counting, so any third party can reproduce them exactly without a rater. They do **not** rank quality — and that is their analytic point (§E.4). They are included to give the study a layer of reproducible numbers, per the gap named in §7.2.

### E.1 Output length (verbosity)

Word count of each system's rendered chapter (the eight LLM output files contain only the translation — verified free of inline reasoning — so the counts are comparable; all are line-aligned to the ~940-line source structure, so the figure reflects English verbosity at fixed structure). Reproducible with `wc -w`.

| System | Words | | System | Words |
|--------|------:|---|--------|------:|
| Gemini 3.1 | 5,568 | | DSV4_PRO | 5,099 |
| FABLE_WEB | 5,489 | | Qwen 3.7 | 5,015 |
| ChatGPT 5.5 | 5,346 | | Fable 5 | 4,909 |
| — | — | | Opus 4.7 | 4,881 |
| — | — | | DeepSeek Web | 4,869 |

*Observation:* the spread is ~14% (4,869–5,568). Verbosity does not track tier: the most expansive output (Gemini, Tier 2) and one of the tightest (Fable 5, Tier 1) sit at opposite ends. Length is a stylistic signature, not a quality signal on this scene.

### E.2 Raw-script (CJK) retention

Number of output lines containing Japanese characters (kanji or kana) — i.e., where the system left source script *visible* rather than romanizing or translating it. Reproducible with a ripgrep query over the Han/kana Unicode ranges.

| System | Lines with raw CJK | Strategy |
|--------|-------------------:|----------|
| FABLE_WEB | 4 | keep-script-visible |
| DSV4_PRO | 3 | keep-script-visible (e.g. "四葩病—Yohira Disease" [EN:243]) |
| Fable 5, Opus 4.7, Gemini 3.1, ChatGPT 5.5, DeepSeek Web, Qwen 3.7 | 0 | full alphabetization |
| Fan TL | (XHTML; retains 葩 + readings, [FTL§2:143]) | keep-script-visible |

*Observation:* a near-binary strategy split on the ateji gag — three systems (FABLE_WEB, DSV4_PRO, Fan TL) leave some source script on the page; six alphabetize fully. The split crosses tiers and even crosses the same model: harness Fable (0) and web Fable (4) diverge, consistent with the harness's romaji policy pushing toward alphabetization (§6.3). Like E.1, the measure captures *strategy*, not quality.

### E.3 Subculture-anchor retention (four mechanical checks)

Four facts checkable directly against the output strings (ground-truth quotes in §5.4); each is a yes/no string test, not a rater judgment.

| System | Zutomayo present | Chirinuruwowaka spelled correct | Yorushika ≠ YOASOBI (not conflated) | MyGO titles in romaji (not invented EN) | /4 |
|--------|:---:|:---:|:---:|:---:|:--:|
| Fable 5 | ✓ | ✓ | ✓ | ✓ | **4** |
| FABLE_WEB | ✓ | ✓ | ✓ | ✓ | **4** |
| Gemini 3.1 | ✓ | ✓ | ✓ | ✓ | **4** |
| Opus 4.7 | ✓ | ✓ | ✓ | ✗ ("One Drop Sky") | **3** |
| DSV4_PRO | ✗ (dropped) | ✗ ("CHIRINURUOWAKA") | ✓ | ✓ | **2** |
| ChatGPT 5.5 | ✗ (dropped) | ✓ | ✓ | ✗ (2 invented) | **2** |
| Qwen 3.7 | ✗ | ✓ | ✗ (conflated) | ✓ | **2** |
| DeepSeek Web | ✗ (dropped) | ✗ (truncated) | ✓ | ✗ (written forms translated) | **1** |

### E.4 Footnote apparatus

Translator-footnote markers in the band-shiritori scene (Section 0002): the Fan TL carries markers ¹ through ⁷ (band identities, etymologies, the disbanded-GO!GO!7188 lineage, [FTL§2:115–156]); all eight LLM outputs use **zero** footnotes, handling references in running prose. This single structural feature — the editorial apparatus — is what most cleanly separates the Fan TL from every LLM output, independent of any quality judgment. (The footnotes are additions by the human editorial team — Slimey, Crash, Jack74593 — not a model behavior, so the apparatus persists even though the base translation is machine-generated.)

### E.5 Why the rater-free measures do not recover the ranking

None of E.1–E.4 reproduces the §5.8 tiers, and the failure is informative. E.3 — the most quality-adjacent of them — ties **Gemini (Tier 2) with Fable 5 (Tier 1)** at 4/4, because it cannot see the humidity motif or the petal metaphor that separate them (§5.5, §5.7); and it scores **Qwen (Tier 4) at 2/4, level with two Tier-3 systems**, because a string-presence test cannot represent that Qwen's single failure is a non-line-editable conflation (§5.4) while the others' are localized drops. A perfectly reproducible retention count is blind to exactly the cross-segment and severity properties that §2 argues discriminate literary quality — the metric-inadequacy thesis (§2, §6.6), here demonstrated on rater-free data rather than on BLEU/COMET. The reproducible measures are therefore offered as *descriptive* layers (verbosity, script strategy, factual retention, apparatus), not as a quality index.

---

## Appendix F: Operationalized Scoring Rubric (for replication)

§4.3 and §7.1–§7.2 record that no operationalized rubric was published, which is the central barrier to reproducing the scores. This appendix supplies one, derived from the §5 evidence: each dimension is given anchored levels whose exemplars are the renderings already cited in §5, and the outcome levels are those named in §3.7. It is offered so that an independent rater — ideally from a model family with no shared lineage with any contestant (§7.1) — can re-score the nine systems against fixed referents. The anchors are illustrative of *this* scene; the rubric structure (anchored levels + weighted aggregation) is what transfers.

**Procedure.** (1) For each system × dimension, assign the level whose exemplar the rendering most resembles. (2) Weight per §4.2 and sum to a composite. (3) Repeat with ≥2 independent raters and report inter-rater reliability (Krippendorff's α or Cohen's κ) — absent in the present study (§7.2). (4) Map composites to tiers by the §5.8 banding (gaps ≤ ~0.04 not separable).

**Dim 5 — Humidity / Damp-Gaze Motif (15%)** — the highest-discrimination item (§3.7):

| Level | Criterion | Exemplar (this scene) |
|------:|-----------|-----------------------|
| 4 | Humidity bound into the gaze as English *meaning* | "damp, accusing stare" [FABLE:707] |
| 3 | Canonical stare phrase, lock-compliant, no humidity innovation | "heavy, lidded stare" [FABLE_WEB:702] |
| 2 | Source *sound* romanized, meaning not transferred | "ji-toooooo" [EN:707] |
| 1 | Non-humidity affect substituted | "cold, deadpan glare" [GEMINI]; "dead eyes" [DEEPSEEK]; "flat glare" [QWEN] |
| 0 | Plain verb, motif absent | "glared at me" [OPUS:707] |

**Dim 4 — Fidelity (20%):**

| Level | Criterion | Exemplar |
|------:|-----------|----------|
| 4 | All band/title anchors correct; romaji policy held | Fable 5; Gemini 3.1 |
| 3 | One invented title *or* one minor name error | Opus 4.7 ("One Drop Sky") |
| 2 | One band dropped *or* one name corrupted | DSV4_PRO (Zutomayo dropped; "CHIRINURUOWAKA") |
| 1 | Multiple drops/corruptions | DeepSeek Web (Zutomayo dropped; "Chirinuruwo" truncated) |
| 0 | A non-line-editable conflation (retranslation required) | Qwen (Yorushika = YOASOBI, §5.4) |

**Dim 1 — Voice Fidelity (20%)**, anchored on the だめな子 seed (§5.2):

| Level | Criterion | Exemplar |
|------:|-----------|----------|
| 4 | Register-matched deadpan ("hopeless," 子 = "girl") | "hopeless girl" [FABLE:67] / [EN:67] |
| 2 | Register drift (harsher than だめ) | "useless" [GEMINI:71]; "no-good girl" [DEEPSEEK:71] |
| 0 | Register break (implies external damage) | "broken kid" [OPUS:67] |

**Dim 7 — Literary Craft (5%)**, anchored on the 詩暮病 confession (§5.7):

| Level | Criterion | Exemplar |
|------:|-----------|----------|
| 4 | Confession *enacted* through tonal structure | "Not the diagnosis I was hoping for" [FABLE:253] |
| 2 | Confession *described* (meta-word for "kanji") | "spelling" [GEMINI]; "visual" [QWEN]; "look" [EN] |
| 1 | Hedged or footnoted out | "one might call" [OPUS:251]; footnote gloss [FTL§2:143] |

**Dims 2 (Subtext), 3 (Rhythm), 6 (Subculture)** follow the same template; their anchors are, respectively, the "not yet" architecture (§5.2), the Bocchi 哀/愛 outburst and cute/gross volley (§5.3), and the four mechanical checks of Appendix E.3. A full multi-rater application of this rubric, with reported α, is the concrete next step named in §8.

---

## References

### Primary source (the work under analysis)

Mizushiro Mizuki (水城水城) [author]; Shiozaki Shino (潮崎しの) [illustrator]. *Amamori Junna wa Shitsudo ga Takai* (雨森潤奈は湿度が高い). MF Bunko J (KADOKAWA); bunko paperback, 264 pp./vol. No official English edition exists (§3.3); the series title is rendered in this paper as *Amamori Junna Is High Humid*. The analyzed scene is Vol. 2, Chapter 2; cross-volume arc evidence (§3.4) draws on Vol. 1, Chapter 8 and Vol. 3, Chapter 7.

| Vol. | Title | Released | ISBN | Official page |
|------|-------|----------|------|---------------|
| 1 | 雨森潤奈は湿度が高い | 2025-02-25 | 978-4-04-684552-8 | https://www.kadokawa.co.jp/product/322410001699/ |
| 2 | 雨森潤奈は湿度が高い２ | 2025-08-25 | 978-4-04-685183-3 | https://www.kadokawa.co.jp/product/322505001287/ |
| 3 | 雨森潤奈は湿度が高い３ | 2026-04-24 | 978-4-04-685714-9 | https://www.kadokawa.co.jp/product/322510001622/ |

### Compared fan translation (cited as [FTL§2:n])

*Amamori Junna Is High Humid 02* — unofficial fan-edited translation of Vol. 2. Slimey Translations (2025). Per the release colophon: machine translation, "Freedom"; editing, "Slimey"; proofreading, "Crash," "Jack74593," "Slimey."

### Model release documentation (cited as capability-profile sources in §2.3)

- Anthropic. (2026). *Claude Fable 5 and Mythos 5*. Product release post. https://www.anthropic.com/news/claude-fable-5-mythos-5
- OpenAI. (2026). *Introducing GPT-5.5*. Product release post. https://openai.com/index/introducing-gpt-5-5/
- DeepSeek AI. (2026). *DeepSeek V4*. Technical report PDF. Consulted from the project-local archival copy `QC/DeepSeek_V4.pdf`; the PDF is not redistributed in this public package.

### Methods and frameworks

- Papineni, K., Roukos, S., Ward, T., & Zhu, W.-J. (2002). BLEU: a Method for Automatic Evaluation of Machine Translation. In *Proceedings of the 40th Annual Meeting of the Association for Computational Linguistics (ACL)*, 311–318.
- Rei, R., Stewart, C., Farinha, A. C., & Lavie, A. (2020). COMET: A Neural Framework for MT Evaluation. In *Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)*, 2685–2702.
- Delabastita, D. (1996). Introduction. *The Translator*, 2(2) [special issue: *Wordplay and Translation*], 127–139.
- Hervey, S., & Higgins, I. (1992). *Thinking Translation: A Course in Translation Method, French–English*. London: Routledge.
- Harvey, K. (1995). A Descriptive Framework for Compensation. *The Translator*, 1(1), 65–86.

---

## Data Availability

The materials analyzed here — the Japanese source text, the eight systems' English outputs, the three harness reasoning logs, the harness input (`context.xml`) and glossary, and the fan translation — are copyright-restricted third-party works and are **not** redistributed with this paper. The in-text citation labels defined in §4.5 (e.g. `[JP:n]`, `[FABLE:n]`, `[OPUS-TK:n]`, `context.xml:n`) resolve against this private corpus and cannot be retrieved from this document alone. The rater-independent measures (Appendix E) and the operationalized rubric (Appendix F) are recomputable by any party holding licensed copies of the source work and the model outputs; the source novel is commercially available from the publisher (see References).

---

## Copyright, Licensing & Fair Use

The Japanese source novel is © Mizushiro Mizuki and Shiozaki Shino, published by MF Bunko J (KADOKAWA); all rights are reserved by the rights holders. The fan translation is © Slimey Translations. The eight systems' English outputs are derivative works of the copyrighted source, generated for evaluation; their copyright status is unsettled and they are treated here as third-party material.

All third-party text — Japanese source lines, fan-translation lines, and system outputs — is reproduced **only in brief excerpts**, for the purposes of criticism, comment, scholarship, and research (fair use under 17 U.S.C. §107; fair dealing in comparable jurisdictions), with attribution. No chapter is reproduced continuously or in full, and readers are directed to purchase the original (see References).

This paper's own original content — its analysis, argument, tables, figures, scoring, and prose — is released **anonymously** under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License (CC BY-NC-ND 4.0)**. The license applies **only** to the paper's original content and grants no rights in any quoted third-party material, which remains under its respective rights holders.
