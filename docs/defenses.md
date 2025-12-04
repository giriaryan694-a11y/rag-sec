# AI & RAG System Defenses

This document outlines **defensive strategies** for mitigating vulnerabilities in both RAG systems and standalone AI/LLM systems.

---

## 1. Input & Prompt Validation

* Sanitize user inputs and retrieved documents.
* Block or flag suspicious instructions or commands.
* Implement strict schema checks for document format, metadata, and content.
* Safe PoC: Test inputs containing harmless prompt injection patterns.

---

## 2. Data & KB Security

* Validate and verify all documents before adding to the knowledge base.
* Monitor embeddings for anomalies or spikes in similarity scores.
* Use access control and audit logging for KB modifications.
* Safe PoC: Add dummy documents with safe “poisoning” instructions to test defenses.

---

## 3. Retrieval & Embedding Defenses

* Apply embedding similarity thresholds to detect unusual embeddings.
* Normalize text to prevent homoglyphs and Unicode attacks.
* Limit maximum retrieval results and token length to prevent context flooding.
* Implement monitoring for abnormal retrieval patterns.

---

## 4. Model Hardening & Monitoring

* Fine-tune models with safety-focused datasets.
* Apply red-teaming and safe prompt injection simulations.
* Monitor outputs for unsafe or unexpected content.
* Rate-limit model access to prevent automated extraction attacks.

---

## 5. Metadata & Document Handling

* Validate metadata fields to prevent injection attacks.
* Strip or sanitize harmful tags, titles, or annotations.
* Track metadata changes with audit logs.

---

## 6. Access Control & Sensitive Data Protection

* Implement role-based access to KB and model endpoints.
* Encrypt sensitive documents in KB.
* Avoid storing secrets or PII directly in the KB or training data.
* Safe PoC: Use dummy credentials to test data leakage prevention.

---

## 7. API & Tool Usage Safety

* Limit external tool/API calls to sandboxed environments.
* Validate all API requests and responses.
* Monitor for anomalous patterns indicating abuse.

---

## 8. Summary Table

| Defense Category                | Applicable To | Key Actions                                 |
| ------------------------------- | ------------- | ------------------------------------------- |
| Input & Prompt Validation       | RAG + LLM     | Sanitize inputs, block unsafe instructions  |
| Data & KB Security              | RAG           | Verify documents, monitor embeddings        |
| Retrieval & Embedding Defenses  | RAG           | Normalize text, limit retrieval results     |
| Model Hardening & Monitoring    | RAG + LLM     | Fine-tuning, red-teaming, output monitoring |
| Metadata & Document Handling    | RAG           | Sanitize metadata, track changes            |
| Access Control & Sensitive Data | RAG + LLM     | Encrypt sensitive data, role-based access   |
| API & Tool Usage Safety         | RAG + LLM     | Sandbox APIs, monitor requests and patterns |

---

## ⚡ Notes

* Combine multiple defense layers for robust security.
* Regularly update policies and monitoring for new attack vectors.
* Safe PoCs are critical for testing defenses without risk.

---

## 🛡️ References (Safe & Public)

* [OWASP AI Security & Privacy Guide](https://owaspai.org/)
* [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework)
* [MITRE ATLAS — Adversarial Threat Landscape for AI Systems](https://atlas.mitre.org/)
* [OpenAI Security Guidelines](https://platform.openai.com/docs/guides/security)
