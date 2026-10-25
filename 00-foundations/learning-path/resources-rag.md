# RAG resources

Evaluate retrieval and answer generation separately. Use one fixed corpus/query set to compare lexical, dense, hybrid, and reranked retrieval. Status date: 2026-10-25.

| Rank | Resource | Status / evidence | Why and limit |
|---|---|---|---|
| P1 | [Seven Failure Points](https://arxiv.org/html/2401.05856v1), Barnett et al., 2024-01-11 | Foundational original paper | Map corpus, retrieval, packing, extraction, formatting, specificity, and completeness failures; based on three implementations |
| P1 | [RAG survey](https://arxiv.org/abs/2312.10997), Gao et al., revised 2024-03-27 | Foundational original research | Taxonomy of naive/advanced/modular RAG; old model rankings are not current evidence |
| P1 | [Contextual Retrieval](https://www.anthropic.com/news/contextual-retrieval), Anthropic, 2024 | First-party bounded experiment | Contextual embeddings plus BM25/reranking; reported gain is not a promise on this corpus |
| P1 | [Anthropic cookbook](https://github.com/anthropics/anthropic-cookbook) | Active first-party repository | Reproduce a retrieval baseline and source-citation checks |
| P2 | [Evaluating chunking](https://www.trychroma.com/research/evaluating-chunking), Smith/Troynikov, July 2024 | Bounded vendor study | Token-level metrics and chunk ablations; synthetic task limitations apply |
| P2 | [LangChain RAG](https://docs.langchain.com/oss/python/langchain/rag) | Living docs, now Deep Agents | Study retrieve/offload/delegate rather than assume an old two-step tutorial |

Test ACL filters, deletion propagation, stale indexes, missing answers, and documents that contain malicious instructions. Record source revision and authorization scope in retrieval receipts. A good faithfulness score does not establish business correctness.

Ragas was removed from the active table; see [superseded.md](superseded.md).

## Pending: not yet inspected

These links are not admitted recommendations as of 2026-10-25.

- [Building and Evaluating Advanced RAG](https://www.deeplearning.ai/short-courses/building-evaluating-advanced-rag/), Liu/Datta: search-only; substantive syllabus unavailable.
- [LlamaIndex production RAG](https://docs.llamaindex.ai/en/stable/optimizing/production_rag/): search-only; substantive reference not opened. Verify package, version, and URL before admission.
