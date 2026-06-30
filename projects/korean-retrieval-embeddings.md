# Korean Retrieval Embeddings (BGE-M3-ko & Qwen3) — H100 fine-tunes

**Role:** model fine-tuning & evaluation · **Output:** 2 public Hugging Face models + benchmark artifacts

## Problem
Korean enterprise retrieval (RAG over FAQ / policy / manuals) needs embedding models tuned
for the domain and language, with **measured** retrieval quality — not vibes.

## What I built
Fine-tuned two strong base encoders on an H100 SLURM flow and published both, with full
benchmark artifacts on the model cards:

- 🤗 **[`hyunseop/rtfin-bge-m3-ko-h100`](https://huggingface.co/hyunseop)** — based on `dragonkue/BGE-m3-ko`
- 🤗 **[`hyunseop/rtfin-qwen3-embedding-h100`](https://huggingface.co/hyunseop)** — based on `Qwen/Qwen3-Embedding-4B`

## Results

**AutoRAG** (corpus 720, 114 queries):

| model | MRR | Hit@1 | Hit@5 | Hit@10 |
|---|---:|---:|---:|---:|
| rtfin-bge-m3-ko | **0.7773** | 0.6754 | 0.9123 | **0.9474** |
| rtfin-qwen3-embedding | 0.7677 | 0.6579 | 0.9035 | 0.9298 |

**MIRACL** (`MIRACLRetrieval`, multilingual retrieval benchmark): BGE fine-tune reaches
**mRR 0.5773 / mAP 0.4328**, Recall@100 ≈ 0.90.

## Why it matters
- The whole flow is **reproducible** via the H100 SLURM pipeline and documented on HF.
- It feeds directly into the [grounded-QA](grounded-qa-contact-center.md) retrieval stack —
  with the important caveat learned there: for *that* benchmark the win came from **query
  expansion, not the domain checkpoint**, so the official `BAAI/bge-m3` is used where the
  domain fine-tune didn't generalize. Knowing *when not* to use your own model is part of the job.

## Stack
sentence-transformers · BGE-M3 / Qwen3-Embedding · MTEB / MIRACL · AutoRAG · SLURM H100 ·
Hugging Face Hub · Weights & Biases.
