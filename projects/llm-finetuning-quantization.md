# LLM Fine-tuning & Quantization (Gemma-class, FP8)

**Role:** model training & serving optimization · **Output:** domain fine-tunes + quantized serving builds

## Problem
Adapt open-weight LLMs to a Korean enterprise maintenance domain, then make them cheap enough
to serve — on a shared H100 cluster with finite GPU budget.

## Approach
- **Domain SFT / ORPO** of Gemma-class (~4B) models with **LoRA** adapters via **axolotl**,
  iterating across configurations (1/2/4-GPU LoRA runs, focused-SFT and ORPO variants) and
  tracking a full SFT history.
- **FP8 post-training quantization** (`turboquant` flow) to shrink the serving footprint and
  raise throughput while holding quality, with FP8 compose/serve scripts for deployment.
- **SLURM H100** orchestration: batch jobs pinned to the `h100` partition, offline HF cache,
  W&B logging.

## Engineering notes
- Kept large training **checkpoints out of git** (multi-GB LoRA/quant artifacts live on disk,
  gitignored) — repos stay lean and cloneable.
- Reproducible run lineage: each experiment named and logged so results trace back to a config.

## Stack
axolotl · PEFT / LoRA · ORPO · FP8 quantization · Gemma-class models · vLLM · SLURM H100 ·
Hugging Face · Weights & Biases.
