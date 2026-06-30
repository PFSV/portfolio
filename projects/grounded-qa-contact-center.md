# Verified-Unit Grounded QA for AI Contact Centers

**Role:** lead researcher & engineer · **Output:** EMNLP-track paper ("GroundLM") + retrieval/eval pipeline · **Status:** in revision

## Problem
Enterprise AI contact centers can't afford fabricated answers. A customer-facing bot that
paraphrases or hallucinates a policy detail is a liability. The goal: a QA system that is
**non-fabricating by construction** — it returns an *operator-approved unit* (a curated
FAQ question→answer pair) verbatim, or it routes to clarify / abstain / hand off to a human.
Correctness of *retrieval* is still required, but the system can never invent text.

## Approach
- **Retrieval harness** comparing families — `bm25`, `splade`, `dense-{e5,bge-m3,qwen3,gte}`,
  `hybrid-bge-m3`, rerankers — crossed with query methods (`raw`, `persona`, `text2query`,
  `doc2query`, `hyde`, human expansion). 1,100+ line benchmark emitting `summary.csv`,
  `predictions.csv`, and cached dense embeddings.
- **Faithfulness evaluation**: LLM-judge comparison of verified-unit answers vs. free-form RAG
  generation, with recovery/repair steps.
- **Held-out human-query evaluation**: paraphrase-robustness and offline-vs-online query
  expansion bake-offs with latency measurement.
- **Reproducible numbers**: a single `locked_numbers.json` source-of-truth regenerated from
  raw results, so paper figures never drift from the data.

## Result
- Honest, non-leaky headline: **hybrid retrieval + query augmentation ≈ R@1 0.881 / 0.930**
  on held-out human query variants.
- A faithfulness result showing the verified-unit design's non-fabrication advantage over
  free-form RAG.
- Framed as an **industry / application** contribution (EMNLP Industry Track / Findings).

## What makes it interesting: catching our own leakage
An earlier headline reported retrieval R@1 ≈ 0.86–0.90 under a "tuple-index" scheme. On audit,
each unit was indexed as `질문: <representative question> 답변: <answer>`, and the test query
**was that same question string** — so retrieval was matching a query to its own indexed copy:
a **question-identity leakage artifact, ~8× inflated**. We demoted that number to a labeled
"evaluation pitfall" lesson and rebuilt the entire headline on a non-leaky held-out split.
Honest measurement is the contribution as much as the system is.

## Stack
Python · BM25/SPLADE · BAAI/bge-m3 (official) · sentence-transformers · MTEB-style eval ·
LLM-judge (gpt-4o-mini with deterministic fallbacks) · SLURM H100 (offline HF cache) · LaTeX (Tectonic).

## Confidentiality
Built over real enterprise contact-center logs from two domains (automotive & home-appliance).
Raw logs are never published; domains are pseudonymized for double-blind submission. This page
describes method and public results only.
