# Brain × Language Models — Cognitive-Neuroscience Research

**Role:** researcher (first / co-author) · **Output:** 3 peer-reviewed papers, 3 best-paper awards
**Where:** Hankuk Univ. of Foreign Studies (English Linguistics & Language Technology) · Korea University (Brain & Cognitive Engineering / [BSPL](https://bspl-ku.github.io/)) · Seoul National University (Brain & Cognitive Science)

The research foundation behind the applied LLM work: studying how **human brains** and
**artificial language models** represent and process meaning. The trajectory runs
*linguistics → brain-vs-NLP comparison → applied LLM* — which is exactly why the production
work cares so much about grounding, faithfulness, and honest evaluation.

---

## Comparative Analysis of Brain and NLP Models for Reasoning Tasks
*Juhyeon Lee, **Hyeonseop Yoon**, Jong-Hwan Lee.* Brain Engineering Society of Korea (BESK), 2023.
🏆 **Best Paper award (poster) — NeuroImage & AI.** [[abstract PDF]](https://besk.kr/Upload/Board/2023%20%ED%95%9C%EA%B5%AD%EB%87%8C%EA%B3%B5%ED%95%99%ED%9A%8C%20%ED%95%98%EA%B3%84%20%EC%9B%8C%ED%81%AC%EC%83%B5%20%EC%B4%88%EB%A1%9D%EC%A7%91_%EC%B5%9C%EC%A2%85.pdf)

**Question:** do NLP models resemble the human brain when *reasoning*?

**Method:**
- **Task set:** bAbI — 20 reasoning tasks, 10k instances each (clues / question / answer).
- **Models:** BERT, GPT-3, T5, LSTM, and QRN, fine-tuned on the bAbI training set.
- **Neural data:** fMRI on 103 native-Korean + 26 native-English speakers (mean age 22.9),
  one instance per task under three conditions (text / image / text+image).
- **Alignment:** per-layer model **RDMs** (pairwise embedding correlation-distance) vs. a
  searchlight (r=4) **neural RDM** from the text condition, compared by **Representational
  Similarity Analysis** (Spearman); a layer-assignment map kept the highest-t-score layer (p < 10⁻⁴).

**Findings:**
- Task accuracy — **QRN 99.7%**, T5 95.1%, GPT-3 (CoT) 86.2%, LSTM 86.1%, BERT 81.0%, GPT-3 (few-shot) 80.3%.
- BERT's **13th/12th/4th layers** aligned most often with neural representations; the
  **left supramarginal gyrus** was the most frequently implicated region (7/20 tasks).

*Keywords: fMRI, reasoning, RSA, bAbI, NLP, Transformer, BERT.*

---

## Metaphor in Mind and Machine — *Unraveling Conceptual Metaphors for NLP Applications*
***Hyeonseop Yoon**, Shin-ae Yoon* (Organization for Human Brain Mapping).
**OHBM 2024 Annual Meeting** (Seoul), published in **Aperture Neuro**. [doi:10.52294/001c.120592](https://doi.org/10.52294/001c.120592)
🏆 **Best Paper award (poster) — Max Planck Institute for Human Cognitive & Brain Sciences.**

Work on **conceptual metaphor** — how figurative, non-literal meaning is processed in the
mind and machine — framed toward **NLP applications**. Presented at the 30th OHBM Annual
Meeting and recognized with a Max Planck best-paper award.

> *(Full abstract is in the OHBM 2024 abstract book and not separately web-extractable; this
> summary reflects the verified title, subtitle, venue, and award. Paste the abstract to deepen it.)*

---

## Korean Twitter Bot Detection based on Deep Learning
*딥 러닝 기반 트위터 한국어 악성 봇 판별 모델 구축* — ***Hyeonseop Yoon**, Jeong-Sik Park.*
Korea Software Congress (**KSC 2022**, KIISE). [[DBpia]](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE11224455)
🏆 **Best Paper (Language Technology) — KIISE**, 2022.

A deep-learning system to **detect malicious automated (bot) accounts in Korean-language
Twitter text** — an early applied-NLP project on Korean text modeling and classification
(the same problem space as the `osome-iu/Botometer101` practicum).

---

## Through-line to the applied work
- **Grounding & faithfulness** in the [contact-center QA paper](grounded-qa-contact-center.md) is the engineering form of the cognitive-science question these papers ask: what does it mean for a system to *understand*?
- **Brain–NLP representational alignment** → the [retrieval-embedding](korean-retrieval-embeddings.md) work.
- **Neural signal processing** → the [rtFIN-NL neurofeedback](neurofeedback-rtfin.md) collaboration and the [rPPG](on-device-rppg.md) sensing project.

## Stack
fMRI analysis · searchlight RSA / representational dissimilarity · bAbI · BERT / GPT-3 / T5 / LSTM / QRN · PyTorch · Korean-language NLP · deep learning.
