# Hyeonseop Yoon — Selected Work

I am an Applied NLP / AI researcher building grounded, evidence-driven language systems.
My current work spans retrieval, evaluation, model adaptation, and serving; earlier research on how brains and language models represent meaning informs how I think about grounding and faithful evaluation.

[GitHub profile](https://github.com/PFSV) · [Hugging Face](https://huggingface.co/hyunseop) · [ORCID](https://orcid.org/0009-0000-0905-4337) · [Email](mailto:xianxie31@korea.ac.kr)

Client work is described only at a method-and-outcome level. Proprietary code, data, infrastructure details, and client identities are not published.

## Flagship work

### 1. Grounded QA for enterprise contact centers

- **Problem:** A customer-facing QA system must not invent policy or product details.
- **Contribution:** Designed a verified-unit architecture that returns an operator-approved answer or abstains, and built the retrieval and evaluation harness.
- **Evidence:** An evaluation audit uncovered question-identity leakage that had inflated an early result by roughly 8×. After rebuilding the held-out evaluation, hybrid retrieval with query augmentation reports approximately **R@1 0.881–0.930**.
- **Artifact:** [Method, evaluation design, and limitations](projects/grounded-qa-contact-center.md)

### 2. Korean retrieval embeddings

- **Problem:** Korean enterprise retrieval needs measured domain and language adaptation, not an assumption that fine-tuning always helps.
- **Contribution:** Fine-tuned two public encoders and evaluated them with AutoRAG and MIRACL-style retrieval workflows.
- **Evidence:** On the documented AutoRAG evaluation (720 corpus items, 114 queries), the BGE-M3 variant reports **MRR 0.7773**, **Hit@1 0.6754**, and **Hit@10 0.9474**. The project also records a case where the base model generalized better, and the fine-tuned model was not used.
- **Artifacts:** [BGE-M3 model](https://huggingface.co/hyunseop/rtfin-bge-m3-ko-h100) · [Qwen3 model](https://huggingface.co/hyunseop/rtfin-qwen3-embedding-h100) · [Case study](projects/korean-retrieval-embeddings.md)

### 3. VisionCardio — on-device rPPG

- **Problem:** Estimate heart rate from front-camera video while keeping capture and inference on-device and deferring when signal quality is insufficient.
- **Contribution:** Built the data and training pipeline, Core ML export, and SwiftUI application.
- **Evidence:** With a strict participant split, fine-tuning reduced the documented UBFC heart-rate MAE from **5.63 to 2.80 bpm**. The repository includes code, a tagged release, and an MIT license.
- **Artifacts:** [Code and reproducibility notes](https://github.com/PFSV/vision-cardio) · [Model](https://huggingface.co/hyunseop/vision-cardio-rppg) · [Case study](projects/on-device-rppg.md)

## Research foundation

My earlier work examined metaphor, reasoning, and representational alignment between human neural data and NLP models. This is the origin of the questions that continue through the applied work: what evidence supports a system's output, what does a representation preserve, and when should a system decline to answer?

I have research experience at Seoul National University and Korea University; these were research roles, not degree programs.

| Year | Publication | Venue |
|---|---|---|
| 2024 | [*Metaphor in Mind and Machine*](https://doi.org/10.52294/001c.120592) | OHBM 2024 / *Aperture Neuro* |
| 2023 | *Comparative Analysis of Brain and NLP Models for Reasoning Tasks* | Brain Engineering Society of Korea |
| 2022 | [*Korean Twitter Bot Detection based on Deep Learning*](https://www.dbpia.co.kr/journal/articleDetail?nodeId=NODE11224455) | Korea Software Congress (KIISE) |

[Methods, authorship, and recognition details](projects/brain-and-language-research.md)

## Open-source release

[`pycag`](https://github.com/PFSV/cag) packages a Cache-Augmented Generation workflow for Llama-family models: corpus consolidation, reusable KV-cache prefill, and single or batch query CLIs. It is an alpha research utility available from [PyPI](https://pypi.org/project/pycag/); its README documents the hardware trade-offs, update cost, and lack of automatic citations.

## Additional selected experience

| Area | Scope | Evidence available here |
|---|---|---|
| [Enterprise RAG agents](projects/enterprise-rag-agents.md) | Retrieval, orchestration, and serving for enterprise engagements | Sanitized case study |
| [LLM fine-tuning and quantization](projects/llm-finetuning-quantization.md) | Domain adaptation and serving experiments on shared H100 infrastructure | Sanitized case study |
| [Vision-language models](projects/vision-language-models.md) | Multimodal model evaluation and serving experiments | Sanitized case study |
| [Call-center audio analytics](projects/call-center-audio-analytics.md) | Diarization, transcription, summarization, and structured extraction | Sanitized case study |

These entries are supporting experience rather than public, reproducible releases. Claims are intentionally limited to information that can be shared without exposing client data or internal systems.

## Working principles

- Evaluate on splits that match the intended claim.
- Treat leakage discovery and negative results as useful outcomes.
- Link claims to code, model cards, papers, or explicit evaluation protocols.
- Prefer an abstention path when available evidence is insufficient.
- Keep private client work separate from public demonstrations.

## Technical scope

`Python` · `PyTorch` · `Hugging Face` · `sentence-transformers` · `BM25/SPLADE/dense retrieval` · `RAG evaluation` · `vLLM` · `LoRA/ORPO` · `Docker` · `Postgres/pgvector` · `SLURM/H100` · `Core ML`

Last reviewed: 2026-08-28.
