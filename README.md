# Parallax

**Cross-lingual structural framing analysis of international news coverage**

Most media bias tools compare *sentiment* or *topic selection*. Parallax goes deeper: it analyzes how the same event is structurally framed across languages — differences in grammatical agency, epistemic certainty, and lexical loading that persist even in accurate translations and reveal systematic editorial and ideological assumptions invisible to standard automated analysis.

The core hypothesis: **language encodes ideology in ways that are grammatically detectable.** Not just in what is said, but in who is made the subject of sentences, how certain claims are presented as fact vs. opinion, and which terms are used to label the same referent.

---

## Background

Standard cross-lingual media analysis treats translation as neutral — compare the English version of Al Jazeera to the English version of CNN and you're already comparing framing. But this misses the structural layer. Arabic and Chinese don't just use different words; they use different epistemic conventions, different agency defaults, different ways of signaling whether a statement is the journalist's view or a reported fact. These differences don't survive translation. You have to look at the source language.

A concrete example from our first case study (Trump–Xi Beijing Summit, May 2026):

Xinhua's reporting uses **"指出" (zhǐchū)** as its primary attribution verb for Xi's statements. In English this translates as "pointed out" — but "pointed out" is a **factive verb**: it grammatically presupposes the truth of what follows. Compare:

> *"He said the trade relationship is mutually beneficial"* — neutral attribution, truth open  
> *"He pointed out that the trade relationship is mutually beneficial"* — presupposes it's true

CNN uses "said" and "touted" (with scare quotes). Al Jazeera uses "يرى" (sees/believes). Xinhua uses "指出" (points out). Same summit, same statements — but the epistemic framing is structurally different in ways that only appear in the source language.

This is the kind of signal Parallax is built to detect systematically.

---

## Analytical Framework

Parallax analyzes five dimensions across source-language articles:

| Dimension | What it measures |
|---|---|
| **Outcome framing** | How the event's result is characterized — failure, ambiguity, success |
| **Lexical loading** | How the same referent (person, policy, event) is labeled across sources |
| **Epistemic modality** | How certain the language is — hedging, factive verbs, attribution patterns |
| **Agency attribution** | Who is the grammatical subject; who acts vs. is acted upon |
| **Structural divergence score** | Composite 1–5 rating of how differently the same event is framed |

---

## Case Studies

### Case Study 1: Trump–Xi Beijing Summit (May 14–15, 2026)
**Sources:** CNN (English) · Al Jazeera (Arabic) · Xinhua / People's Daily (Chinese)

Full analysis: [`analysis/trump_xi_summit_may2026.md`](analysis/trump_xi_summit_may2026.md)

**Key findings:**
- All three sources agree Xi had more agency than Trump — but explain it differently. CNN: Trump failed to act. Al Jazeera: Xi strategically exploited the moment. Xinhua: Xi is the natural author of history.
- Xinhua's use of "指出" (factive attribution verb) vs. CNN's "said/touted" is a structurally measurable difference in epistemic commitment detectable only in the source language — not in translation.
- Al Jazeera Arabic mirrors US framing on the bilateral relationship almost exactly while independently asserting China's geopolitical rise as settled fact — an interesting hybrid epistemic stance.
- Taiwan is labeled with the PRC pejorative "台独" in Xinhua, paired with the fixed ideological binomial "水火不容" (fire and water, incompatible) — formula, not editorial judgment.

**Divergence scores:**

| Dimension | Score (1–5) |
|---|---|
| Outcome framing | 5 |
| Taiwan treatment | 5 |
| Epistemic certainty | 4.5 |
| Lexical loading | 4 |
| Agency attribution | 3 |

---

## Why this matters

Existing cross-lingual media tools — GDELT, Media Cloud, and others — operate at the level of topic detection and entity extraction. None systematically analyze structural framing in the source language. The result is that the most ideologically significant differences, the ones baked into grammar rather than vocabulary, are invisible to current automated analysis.

This is a solvable problem. LLMs with strong multilingual capability can analyze source-language text for the specific grammatical and lexical signals that carry framing information. The manual framework developed here is designed to be the specification for that automated system — each analytical dimension is precise enough to be prompted, and the divergence scoring provides a quantifiable output.

---

## Roadmap

**Current:** Manual framework validated on Case Study 1. Analytical dimensions defined with sufficient precision for automated implementation.

**Next:** Automated pipeline using LLM-based structured analysis on source-language text, with article retrieval via news APIs across English, Arabic, and Chinese outlets. The goal is to reduce per-event analysis time from hours to seconds and test whether the patterns identified manually are consistent at scale.

**Longer term:** A tool accessible to researchers, journalists, and general readers — enter any major international news event, get a structured comparison of how it's being framed across language communities, with specific linguistic evidence rather than aggregate sentiment scores.

---

## Status

Active research. Manual analysis complete for Case Study 1. Automated pipeline in development.

**Contact:** hannes31415 on GitHub
