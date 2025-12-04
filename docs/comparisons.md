# RAG vs AI/LLM Vulnerabilities Comparison

This document compares vulnerabilities in **RAG systems** and **standalone AI/LLM systems**, highlighting differences, overlaps, and unique considerations.

---

## 1. Overview

* **RAG (Retrieval-Augmented Generation)**: Combines an LLM with an external knowledge base. Vulnerabilities arise from both the model and the retrieval mechanism.
* **Standalone AI/LLM**: Model operates without retrieval augmentation. Vulnerabilities are mostly limited to input/output handling, model extraction, and data poisoning.

---

## 2. Vulnerability Categories and Differences

| Category                           | RAG Systems                                  | Standalone AI/LLM                            | Notes / Differences                                                                |
| ---------------------------------- | -------------------------------------------- | -------------------------------------------- | ---------------------------------------------------------------------------------- |
| Prompt Injection                   | Document-level instructions in KB or input   | Input text instructions                      | In RAG, malicious instructions can be hidden in retrieved docs.                    |
| Data Poisoning                     | KB documents or embeddings poisoned          | Training/fine-tuning data poisoned           | RAG can be poisoned post-training; LLM poisoning usually during training.          |
| Retrieval Manipulation             | Retriever is tricked to return wrong docs    | Not applicable                               | Only RAG has retrieval layer vulnerabilities.                                      |
| Context Flooding                   | Overloading retrieved context                | Token overflow in input prompt               | Both can fail due to context limit, but RAG combines retrieved content + prompt.   |
| Embedding Attacks                  | Embedding vectors can be manipulated         | Not applicable                               | Embedding attacks are specific to RAG embeddings.                                  |
| Sensitive Data Leakage             | KB data retrieved unintentionally            | Model output can leak training/internal data | Both can leak sensitive info; RAG leaks KB, AI/LLM leaks internal model knowledge. |
| Metadata Injection                 | Malicious metadata manipulates retrieval     | Not applicable                               | Unique to RAG metadata handling.                                                   |
| Model Evasion / Adversarial        | Rare, mostly at retrieval level              | Crafted inputs to mislead LLM                | Standalone LLMs more prone to classic adversarial attacks.                         |
| Output Manipulation / Jailbreaking | Can be triggered via retrieved documents     | Triggered via crafted prompts                | RAG adds an extra attack vector through KB content.                                |
| API/Tool Exploitation              | LLM in RAG pipeline may trigger unsafe tools | Standalone LLM with tool access only         | Both can be exploited if tools/APIs are connected.                                 |

---

## 3. Key Insights

1. **RAG-specific vulnerabilities**: Retrieval manipulation, embedding attacks, metadata injection, context flooding combining KB + prompt.
2. **LLM-specific vulnerabilities**: Model extraction, adversarial input, prompt injection, output/jailbreaking.
3. **Overlap**: Data poisoning, sensitive data leakage, prompt injection.
4. **Safe Testing**: Always use dummy KBs, safe PoCs, and sandboxed environments.

---

## ⚡ Notes

* Understanding both RAG and LLM vulnerabilities helps design secure AI systems.
* Security strategies must cover both retrieval and generation layers in RAG.
* Ethical red-team exercises should simulate these attacks safely.

---

## 🛡️ References (Safe & Public)

* [OWASP AI Security & Privacy Guide](https://owaspai.org/)
* [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework)
* [MITRE ATLAS — Adversarial Threat Landscape for AI Systems](https://atlas.mitre.org/)
