# Real-Time Functional Imaging / Neurofeedback (rtFIN-NL)

**Role:** ML collaborator · **Output:** research code & models (collaboration with `real-abcd/rtFIN-NL`)

## Context
A research collaboration on **real-time functional imaging + neurofeedback / neurolinguistics**.
My contributions sit on the machine-learning side of the project.

## Contributions
- **Embedding-model tuning** for the project's retrieval/representation needs (a Korean-language
  embedding track parallel to the [enterprise embedding work](korean-retrieval-embeddings.md)).
- **LLM fine-tuning & quantization** for a domain maintenance model (Gemma-class SFT + FP8),
  detailed in [LLM fine-tuning & quantization](llm-finetuning-quantization.md).
- **VLM serving** (Open WebUI + Qwen on Slurm H100) for interactive evaluation.

## Engineering hygiene
This repo is public, so it doubled as a lesson in repo discipline: a committed virtualenv
(~950 files) and multi-GB training archives were **untracked and gitignored** to keep the
public repo lean, and a leaked token was scrubbed from git config.

## Stack
PyTorch · embedding fine-tuning · Gemma-class SFT + FP8 · SLURM H100 · Hugging Face · upstream `real-abcd/rtFIN-NL`.
