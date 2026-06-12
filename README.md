# Comprehension, Not Fluency: Evaluating Structurally-Embedded Literary Devices in Japanese→English Light-Novel Translation

**A nine-contestant, single-scene case study** · Claude (with Human Supervisor) · June 2026 · CC BY-NC-ND 4.0 (original content only)

---

## What this is

This repository contains an academic case study evaluating how nine translation systems — eight frontier LLM configurations and one fan-edited machine translation — render a single, deliberately chosen scene (~220 lines) from a contemporary Japanese light novel into English.

The scene was chosen for one specific property: it is the densest concentration in its three-volume series of **self-contained meta-linguistic devices** — literary constructions gradeable within a single chapter, without cross-volume memory. Every contestant produces fluent, grammatical English. The study therefore measures *comprehension*, not *proficiency*: its discriminating failures are overwhelmingly cases where a system understood the words but not what the author was doing with them.

**Read the paper:** [`FRONTIER_READING_COMPREHENSION.md`](./FRONTIER_READING_COMPREHENSION.md)

Repository metadata:

- [`CITATION.cff`](./CITATION.cff) — GitHub citation metadata
- [`LICENSE.md`](./LICENSE.md) — CC BY-NC-ND 4.0 license for original paper content only

---

## Systems evaluated

| Code | System | Condition |
|------|--------|-----------|
| `FABLE` | Claude Fable 5 (Anthropic) | API + constraint-enforcing harness |
| `OPUS` | Claude Opus 4.7 (Anthropic) | API + constraint-enforcing harness |
| `DSV4_PRO` | DeepSeek V4 Pro (DeepSeek) | API + constraint-enforcing harness |
| `FABLE_WEB` | Claude Fable 5 (Anthropic) | Web interface |
| `GEMINI` | Gemini 3.1 Pro Extended Thinking (Google) | Web interface |
| `CHATGPT` | ChatGPT 5.5 Extended Thinking (OpenAI) | Web interface |
| `DEEPSEEK` | DeepSeek V4 Thinking (DeepSeek) | Web interface |
| `QWEN` | Qwen 3.7 Max Thinking (Alibaba) | Web interface |
| `FAN` | Slimey Translations (~2025) | Fan-edited MTL (MTL: Freedom; Ed: Slimey; PR: Crash, Jack74593, Slimey) |

The Japanese source serves as an authorial-intent reference ceiling, not a contestant. Three harness systems persisted pre-translation reasoning logs, enabling process-tracing of deliberated choices.

---

## Key findings

### 1. Fluency is cheap; comprehension is the bottleneck
Every contestant produces grammatical, idiomatic English. The scene's discriminating failures are not grammatical errors or mistranslations in the conventional sense — they are failures to recognize what the Japanese author was doing architecturally: a gaze verb that carries a title-motif, a counterfeit song title that doubles as a love confession, three consecutive lines each naming a different J-Rock band. These are comprehension failures expressed in fluent prose, and they are exactly what standard automatic metrics (BLEU, COMET) cannot detect.

### 2. BLEU and COMET evaluate the wrong thing — provably
Worked examples in §2 show that BLEU would actively *penalize* the best rendering of the scene's central motif (because the motif-correct word choice shares no n-grams with a neutral reference) and would *reward* a factual band-name error (because the surrounding prose matches the reference). COMET evaluates roughly 1.5 of the seven quality dimensions and predicts a top-three ordering that inverts the observed ranking. The failure is structural: both metrics are built on segment-level assumptions, and the discriminating properties of this scene are cross-segment by construction.

### 3. The official frontier-model benchmarks cover none of the dimensions we evaluate
The Fable 5 release (Anthropic, 2026) reports leading scores on FrontierCode, Hebbia Finance, Slay the Spire, CursorBench, ViBench, and vision tasks. None of these touch literary translation quality, subculture knowledge integration, cross-segment motif tracking, or constraint compliance in a literary domain. The findings of this study are therefore non-redundant with any existing published evaluation of these models (§2.3).

### 4. A constraint-enforcing harness produces a small, consistent improvement — bounded by native model knowledge
Two controlled pairs — the same model family with harness vs. without (Fable 5 harness vs. Fable 5 web; DeepSeek V4 Pro harness vs. DeepSeek V4 web) — show a one-tier-or-less lift associated with the harness. The lift is real in both pairs, but the harness does not transfer knowledge the model lacks: DeepSeek V4 Pro (harness) still missed the Zutomayo band reference that its non-harness sibling missed, confirming the harness enforces and tracks constraints but cannot supply absent facts.

### 5. Under identical infrastructure, constraint-compliance behavior separated two frontier models more than declarative knowledge
Fable 5 and Opus 4.7 share the same vendor, the same harness, and largely comparable declarative knowledge. Their reasoning logs show the gap is not what they knew but how they resolved a constraint *hierarchy*: Fable surfaced and applied a higher-tier continuity lock; Opus applied a lower-tier brief entry and did not surface the override. The separation is a documented deliberated choice — not an accident of training.

### 6. Knowledge of a device did not, on its own, produce preservation of it
The study's sharpest single data point: Opus 4.7 had the correct forced reading of a gikun ateji title in its reasoning log, classified the titles as "wordplay the Japanese reader would recognize," and still rendered a literal gloss as the published title — failing output and comprehension while demonstrating knowledge. The three axes (output, knowledge, comprehension) are genuinely independent.

---

## What this tells us about frontier models and abstract or untranslatable artifacts

This is the question the study was designed to probe. The findings, taken together, support several inferences that extend beyond this single scene.

### The single-channel problem is structural, not incidental

Japanese orthography is two-channel: a character string carries a written meaning (from the kanji) and an assigned reading (from the furigana), and these can be deliberately set in opposition. Gikun ateji — the device at the center of this scene — works by engineering a gap between the two channels. English orthography is single-channel: a word is pronounced as written, with no furigana track. The gap therefore cannot be *transposed* into English; it can only be *compensated* — its two poles relocated to separate points in the prose.

This is not a translation difficulty in the ordinary sense. It is a writing-system constraint. Every contestant faces the same constraint; what separates them is whether they recognize and respond to it as a structural problem or treat it as a vocabulary problem.

### There are four strategies, not two

The naive binary is "kept the title vs. translated it." The evidence supports a four-way taxonomy:

| Strategy | What it preserves | What it loses |
|----------|------------------|---------------|
| **Meaning-only** (Opus, ChatGPT) | The kanji's semantic content | The title's identity and the gap |
| **Reading-only** (Gemini, Qwen, Fable web, DSV4_PRO) | The recognizable title | The written meaning; cannot carry the confession (which lives in the gap) |
| **Glyph-preserved** (Fan TL) | The logographic form — reader faces the characters | The content of either pole; opaque to a reader without Japanese |
| **Gap-compensated** (Fable 5) | Both poles, split across narrative channels | Nothing that could have been preserved — the irreducible loss is booked separately |

Only the fourth strategy conveys the gap itself. For a device where the artistic payload *is* the gap — where the confession in the counterfeit song title depends on the written form and the assigned reading deliberately failing to match — picking either pole alone loses the effect regardless of execution quality.

This taxonomy generalizes beyond ateji: any device where meaning is carried by the *structural contrast* between two channels (surface vs. subtext, script vs. sound, form vs. content) is subject to the same single-channel problem in English, and the same four-way strategy choice.

### Knowledge, comprehension, and output are three independent axes

The ateji case demonstrates this conclusively. A model can have:
- **Knowledge** (knows the correct forced reading, knows the titles are "wordplay") — without
- **Comprehension** (understands that the device is a signature the confession replicates) — and therefore without
- **Output** (preserves or reconstructs the gap)

The reverse also holds: a model can achieve correct output by policy (keep titles in romaji) without recorded device awareness. The conventional measure — did the output preserve the form? — is the output axis alone. It cannot distinguish a model that understands the device from a model that follows a rule that happens to produce the right surface result. Process tracing against reasoning logs (where available) is required to separate them, and this study shows the separation is non-trivial and non-obvious from output alone.

### Constraint enforcement converts latent knowledge into consistent output

Models that knew what a constraint meant, but did not consistently apply it, benefited from the harness. The harness functions not as a knowledge injection (it cannot teach a model what Zutomayo is) but as a *policy system*: it takes model knowledge and converts it into a decision hierarchy that the model then resolves. The finding that constraint-compliance behavior separated two frontier models more than declarative knowledge — with the separation traceable to hierarchical resolution, not knowledge gaps — suggests that *how* constraints are delivered and prioritized may matter as much as *what* the model knows in complex literary domains.

### Standard benchmarks are structurally blind to this capability axis

The comprehension-vs-proficiency axis — fluent output that nevertheless fails to recognize what the source was doing — does not appear in any current frontier model evaluation suite. FrontierCode asks whether code works, not whether the model understood the architectural intent. Hebbia Finance asks whether reasoning is correct, not whether the model recognized the document's argumentative structure. The present study proposes and applies an evaluation framework for this missing axis: select a scene where all contestants produce fluent output, and score on dimensions that require cross-segment comprehension to satisfy. The seven-dimension rubric (§4.2), the item-discrimination profile (§3.7), and the three-axis table (§5.6) are the transferable methodological contributions, independent of the contested single-rater scores.

### The irreducible loss boundary matters for practical deployment

For two of the five evaluated device classes — ateji and kanji-play — no English rendering can fully close the gap; the loss is structural, not correctable by better translation. A system's performance on these devices reflects strategy choice and comprehension, not a deficiency in English that could be fixed. Knowing which losses are irreducible (writing-system constraints) versus addressable (motif tracking failures, missed band references, vocabulary choices) is necessary for any realistic evaluation of literary MT quality, and the paper provides an operationalized method for making that partition (§3.5, Appendix C).

---

## Methodology in brief

- **Scene selection**: Five explicit criteria (§3.1), with a documented elimination table of candidate scenes (§3.2) and a post-hoc item-discrimination profile (§3.7)
- **Evaluation**: Seven weighted dimensions (Voice Fidelity 20%, Fidelity 20%, Subtext Preservation 15%, Prose Rhythm 15%, Humidity Motif 15%, Subculture Knowledge 10%, Literary Craft 5%)
- **Scoring**: Single rater (an independent DeepSeek V4 Pro instance, disclosed as a threat to validity in §7.1); results presented as **ordinal tiers** rather than interval scores (§5.8)
- **Process tracing**: Pre-translation reasoning logs for three harness systems (Fable 5, Opus 4.7, DeepSeek V4 Pro) ground output claims to deliberated choices (§5.9)
- **Controlled comparisons**: Two model-constant / harness-varying pairs (§6.1, §6.3), isolating the infrastructure dividend from model capability
- **Rater-independent measures**: Appendix E (verbosity, script retention, factual anchor retention, footnote apparatus) — recomputable without access to the private corpus
- **Replication rubric**: Appendix F — anchored rubric for independent re-scoring with inter-rater reliability

**Primary threat to validity**: the rater shares model weights with one contestant (§7.1). All scores and tiers are provisional pending re-rating by independent evaluators built on a different model family.

---

## Data availability

The analyzed materials — the Japanese source text, the eight LLM outputs, the three harness reasoning logs, the harness input, and the fan translation — are copyright-restricted works and are **not** distributed with this repository. The in-text citations (`[JP:n]`, `[FABLE:n]`, `[OPUS-TK:n]`, etc.) resolve against a private corpus.

The rater-independent measures (Appendix E) and operationalized rubric (Appendix F) are recomputable by any party holding licensed copies of the source work. The primary source novel is commercially available from the publisher:

| Vol. | Released | ISBN | Official page |
|------|----------|------|---------------|
| 1 | 2025-02-25 | 978-4-04-684552-8 | https://www.kadokawa.co.jp/product/322410001699/ |
| 2 | 2025-08-25 | 978-4-04-685183-3 | https://www.kadokawa.co.jp/product/322505001287/ |
| 3 | 2026-04-24 | 978-4-04-685714-9 | https://www.kadokawa.co.jp/product/322510001622/ |

Source novel: *雨森潤奈は湿度が高い* by Mizushiro Mizuki (水城水城), illus. Shiozaki Shino (潮崎しの). MF Bunko J, KADOKAWA. No official English edition.

---

## Citation

If you use the methodology, benchmark-design framework, or findings of this paper, please cite:

```
Anonymous. (2026). Comprehension, Not Fluency: Evaluating Structurally-Embedded Literary
Devices in Japanese→English Light-Novel Translation — A Nine-Contestant, Single-Scene
Case Study. [Preprint / repository]. CC BY-NC-ND 4.0.
```

---

## License

The paper's original content — analysis, argument, tables, rubrics, and prose — is released anonymously under **CC BY-NC-ND 4.0**. This license applies only to the paper's original content. All quoted third-party material (Japanese source lines, system outputs, fan-translation excerpts) remains under its respective rights holders. Brief excerpts are reproduced solely for criticism, comment, and scholarship (fair use, 17 U.S.C. §107).

---

## Open questions this study raises

1. **Does the comprehension-vs-proficiency gap replicate across scene types?** The benchmark was designed for a scene with high J-Rock subculture density and ateji devices. The same axis — fluent output masking a comprehension failure — may manifest differently (or not at all) in dialect comedy, historical exposition, or action pacing.

2. **What is the mechanism behind the infrastructure dividend?** The harness is associated with a one-tier-or-less lift, but the "freed cognitive budget" account is a hypothesis, not a measured mechanism. Instrumenting token allocation before and after constraint injection would test it directly.

3. **Do the three axes (output / knowledge / comprehension) separate in other device classes?** The ateji case is the clearest demonstration, grounded in reasoning logs. The pattern may extend to other culturally-embedded literary devices — dialect, register code-switching, structural irony — where fluency and comprehension diverge.

4. **How does constraint-hierarchy resolution behave at scale?** The paper documents one instance across two models. Whether the hierarchy-resolution pattern holds across more models, more constraint types, and more literary domains is an open empirical question.

5. **Can the rubric (Appendix F) achieve acceptable inter-rater reliability?** The paper supplies an anchored rubric for independent re-scoring. Whether independent raters achieve agreement sufficient to validate the tier distinctions is the study's immediate next step, and the answer determines whether the ordinal tiers can be treated as established.
