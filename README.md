# Portfolio — Applied LLM / VLM Research & Engineering

Applied NLP/ML researcher–engineer. I take large language and vision-language models
from research into production for Korean enterprise: **retrieval-augmented QA, embeddings,
fine-tuning & quantization, vision-language serving, and on-device health sensing** —
trained and served on a shared **H100 SLURM** cluster.

> Affiliations: Korea University · maum.ai  
> Hugging Face: [@hyunseop](https://huggingface.co/hyunseop) · GitHub: [@PFSV](https://github.com/PFSV)

Client engagements below are described by **industry** rather than name — the underlying
code stays in private repos. Public research artifacts (papers, Hugging Face models) are linked directly.

---

## Featured work

| Project | One line | Stack | Status |
|---|---|---|---|
| [Grounded QA for AI contact centers](projects/grounded-qa-contact-center.md) | "Verified-unit" RAG that answers from operator-approved units or abstains — non-fabrication by construction | BM25/SPLADE/dense hybrid, BGE-M3, faithfulness judging | EMNLP-track paper (in revision) |
| [Korean retrieval embeddings](projects/korean-retrieval-embeddings.md) | Fine-tuned BGE-M3-ko & Qwen3-Embedding-4B for Korean retrieval, published to HF | sentence-transformers, MTEB/MIRACL, AutoRAG | **2 public HF models** |
| [On-device rPPG heart-rate coach](projects/on-device-rppg.md) | Front-camera heart rate → bounded workout coaching, fully on-device | PhysNet, Core ML, iOS/Swift, SCAMPS sim-to-real | iOS app + Core ML export |
| [Enterprise RAG agents & chatbots](projects/enterprise-rag-agents.md) | Production RAG/agent chatbots across insurance, rail, appliances | Spring Boot, RAGFlow, Postgres/pgvector, vLLM | Multiple PoCs delivered |
| [LLM fine-tuning & quantization](projects/llm-finetuning-quantization.md) | Domain SFT/ORPO of Gemma-class models + FP8 quant for serving | axolotl, LoRA, FP8, SLURM H100 | Production fine-tunes |
| [Vision-language models](projects/vision-language-models.md) | VLM experiments & serving (LLaVA-NeXT, Qwen-VL, Gemma) on Open WebUI | LLaVA-NeXT, Qwen, Slurm serving | Research + demos |
| [Call-center audio analytics](projects/call-center-audio-analytics.md) | Speaker-diarized call transcripts → LLM summaries & Q&A extraction | WhisperX, gpt-oss-20b, diarization | Delivered pipeline |
| [Real-time functional imaging / neurofeedback](projects/neurofeedback-rtfin.md) | Neurolinguistics + real-time functional imaging research collaboration | embedding tuning, signal ML | Research (rtFIN-NL) |

---

## Skills

**LLM / NLP** — RAG (hybrid retrieval, query expansion, reranking), embeddings & retrieval
eval (MTEB, MIRACL, AutoRAG), faithfulness/grounding, SFT/ORPO fine-tuning, prompt &
agent design, Korean NLP (tokenization, domain adaptation).

**Vision / multimodal** — vision-language models (LLaVA-NeXT, Qwen-VL), remote
photoplethysmography (rPPG/PhysNet), synthetic-data sim-to-real.

**Systems / MLOps** — SLURM H100 clusters, vLLM / Ollama / Open WebUI serving, FP8
quantization, Hugging Face ecosystem, Weights & Biases, Docker Compose, Spring Boot +
Postgres/pgvector backends, on-device Core ML deployment.

**Research** — honest evaluation design (leakage auditing), reproducible benchmarks,
academic writing (EMNLP-style).

---

## A note on rigor

The grounded-QA project includes a worked example of catching an **8×-inflated retrieval
result** caused by question-identity leakage in an indexing scheme, and rebuilding the
headline on a non-leaky held-out evaluation. Honest measurement is a feature here, not an afterthought.

_Last updated: 2026-06-30._
