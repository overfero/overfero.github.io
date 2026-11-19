---
title: "Refi Voice AI"
excerpt: "An outbound AI voice agent that calls homeowners about mortgage refinancing, extracts loan details in a real conversation, and computes actual savings deterministically.<br/><img src='/images/refi-voice-ai-dashboard.png' width='300' height='200'>"
collection: portfolio
---

# Refi Voice AI — AI Outbound Voice Agent for Mortgage Refinancing

This project is an outbound voice agent that calls Indonesian homeowners about KPR (mortgage) refinancing, holds a real conversation to extract their loan details, computes actual refinancing economics deterministically, and routes the result into a lead score, a CRM, and follow-up messaging.

Demo video: [link video di sini]

## Features:
- **Real Telephony**: Telnyx + Pipecat + OpenAI's Realtime API, tested end to end on a live outbound phone call with full duplex speech-to-speech audio, no separate STT/TTS step.
- **Deterministic Economics Engine**: A pure-function annuity and break-even calculator computes refinancing savings, never left to the LLM to guess.
- **Evidence-Grounded Extraction**: Every extracted field carries a confidence level and a verbatim transcript span, so a hallucinated value is caught mechanically instead of trusted on faith.
- **State-Machine Conversation Logic**: Slot-filling, retry limits, and opt-out/hostility handling run on an explicit state machine rather than an LLM improvising control flow.
- **Optional LLM Upgrade**: Post-call intent, sentiment, and summary analysis upgrade automatically to an LLM (OpenAI or Anthropic, combined into a cross-vendor fallback chain) when an API key is configured, falling back to rule-based logic otherwise.
- **Compliance Built In**: A do-not-call list, a calling-window gate checked before every dial, and a consent ledger built from call outcomes.
- **CRM Sync & Follow-Up Messaging**: Idempotent CRM upsert with a circuit breaker, plus deterministic email/WhatsApp generation with every figure read straight from the economics engine.
- **Dashboard**: A Next.js campaign dashboard reading call replay data directly, with a human-review console for low-confidence extractions.
- **Infrastructure as Code**: A full Terraform stack (RDS, ElastiCache, ECS Fargate, ALB) actually provisioned and torn down against a local AWS emulator, since no live AWS account was available.

## Repository:
- [Refi Voice AI Repository](https://github.com/overfero/refi-voice-ai)
