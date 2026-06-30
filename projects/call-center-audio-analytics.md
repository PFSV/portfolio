# Call-Center Audio Analytics (Diarization → LLM Insight)

**Role:** pipeline design & implementation · **Output:** delivered audio→insight pipeline

## Problem
Turn raw recorded customer-consultation calls (insurance domain) into structured analytics:
**conversation summaries** and extracted **customer-question / answer** pairs.

## Pipeline
1. **Ingest** raw `.wav` recordings + existing STT `.result` files.
2. **Speaker diarization & transcription** — **WhisperX v3** (Korean-pinned) to produce
   speaker-attributed transcripts.
3. **Distillation** — an LLM (**gpt-oss-20b**) post-processes and concatenates STT + diarized
   text into a cleaned "essence" representation.
4. **Analysis** — a second LLM task emits structured JSON: `상담내용요약` (consultation summary)
   and `고객질문답변` (customer Q&A).

## Why it's useful
- Converts unstructured call audio into queryable, auditable structured data for QA and
  knowledge-base seeding (feeds the FAQ/RAG systems elsewhere in this portfolio).
- Korean-language ASR + diarization tuned for real, noisy call recordings.

## Stack
WhisperX v3 (diarization, Korean) · gpt-oss-20b · Python batch pipeline · JSON output schema.

## Confidentiality
Built on sample consultation data; client name withheld, raw audio never published.
