---
title: "Grounded Persona RAG: Lee Kuan Yew Chatbot"
excerpt: "A retrieval-augmented chatbot that simulates Lee Kuan Yew, grounded in 44 real archival transcripts with structural citation validation.<br/><img src='/images/lky_rag_architecture.png' width='300' height='200'>"
collection: portfolio
---

# Grounded Persona RAG: Lee Kuan Yew Chatbot

This project implements a retrieval-augmented chatbot that simulates Lee Kuan Yew, Singapore's first Prime Minister, grounded entirely in real primary-source transcripts rather than the model's general knowledge. The core design insight: persona (how it speaks) and grounding (what it knows) are treated as two separate concerns, so the system can't fabricate facts in a convincing voice.

![Architecture diagram](/images/lky_rag_architecture.png)

## Features:
- **Real Primary-Source Corpus**: 44 speech and press-conference transcripts (1959-1990) fetched directly from the National Archives of Singapore, cleaned and chunked into 536 pieces with full provenance tracking.
- **Hybrid Retrieval**: Dense + sparse embeddings (BGE-M3) fused via Reciprocal Rank Fusion in Qdrant, followed by cross-encoder reranking (BGE-reranker-v2-m3).
- **Query Understanding**: Coreference resolution, temporal filter extraction, and scope classification in a single call, with query-type-gated multi-query expansion, HyDE, and comparative decomposition.
- **Index-Only Citation Binding**: The model only emits citation numbers; the backend resolves them to real sources, making fabricated citations structurally difficult rather than merely discouraged.
- **Two-Stage Generation**: A grounded draft is validated first, then a separate style-transfer pass applies Lee Kuan Yew's voice (mined statistically from the corpus, not hand-written), falling back to the plain draft if the rewrite breaks a citation.
- **Deterministic Grounding Validation**: Every response is checked for citation validity, exact-quote matching, and temporal consistency before it reaches the user.
- **Four Refusal Classes**: No-evidence, out-of-horizon, policy, and chitchat, each answered in character, and the system always breaks character honestly if asked about its own identity.
- **Semantic Cache**: Qdrant-backed cosine-KNN cache cutting repeat-question latency from ~94s to ~2s.
- **Full Evaluation Harness**: A 23-item golden set, retrieval ablation, LLM-as-judge scoring (judge model separate from generator), a RAGAS cross-check, and multi-turn style-drift evaluation.
- **Serving + Observability**: FastAPI backend, Streamlit frontend, and Prometheus metrics.

## Evaluation Highlights:
- Hybrid retrieval improves Recall@50 from 0.92 (dense-only) to 1.00.
- Reranking raises Hit-rate@8 from 0.83 to 0.92.
- Correct-refusal rate of 1.00 across adversarial and out-of-scope test cases.
- Every limitation and real bug encountered during development is documented directly rather than hidden.

## Repository:
- [GitHub Repository](https://github.com/overfero/lky-grounded-rag)

## Demo:
- [Video Walkthrough](https://drive.google.com/file/d/1T2zjmd4lohic5lPdpj2_T7m29juJYXMo/view?usp=sharing)
