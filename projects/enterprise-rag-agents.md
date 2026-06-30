# Enterprise RAG Agents & Chatbots

**Role:** applied LLM engineer across multiple client PoCs · **Output:** delivered retrieval/agent chatbots

Production-oriented retrieval-augmented chatbots and tool-using agents, delivered across several
Korean enterprise domains (described by industry; client code is private):

- **Insurance (life / P&C / claims):** FAQ and claims-consultation assistants — RAG over policy
  and product corpora, served behind a Spring Boot backend with Postgres/pgvector, RAGFlow for
  document indexing, and embedding/rerank pipelines.
- **National rail operator:** a RAG agent over operations/maintenance documentation
  (docker-compose deployment, Redis, axolotl-fine-tuned backbone).
- **Home-appliance rental:** a customer-facing FAQ chatbot (Kakao messenger channel) and an
  AICC (AI contact-center) proof of concept.
- **SAP / consulting:** an assistant agent for SAP-process experts.
- **Premium automotive:** FAQ, maintenance, and spec-lookup LLM assistants.

## What this work involved
- **Retrieval design:** hybrid dense+sparse retrieval, query rewriting/expansion, rerankers,
  and chunking strategies tuned per corpus.
- **Serving:** vLLM / Ollama model backends, embedding services, and Spring Boot APIs with
  pgvector; Docker Compose deployments.
- **Grounding & safety:** routing to clarify/abstain/handoff rather than fabricate — the
  pattern formalized in the [grounded-QA paper](grounded-qa-contact-center.md).
- **Hardening:** these PoCs are also where I learned to keep secrets out of source — see the
  repo-hygiene work in the [next-steps plan](https://github.com/PFSV).

## Stack
Spring Boot · Postgres + pgvector · RAGFlow · Redis · vLLM / Ollama · BGE-M3 embeddings ·
Docker Compose · OpenAI / open-weight LLMs.

## Confidentiality
Client names withheld; this is a sanitized capability summary, not a code disclosure.
