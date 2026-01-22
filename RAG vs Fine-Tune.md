# RAG vs Fine-Tune: Decision Guide

## How frequently does the data change?

### Fine-tuning
- **Best for:** Stable / rarely changes
- **Examples:** Core domain rules, company style guide, fixed terminology, reasoning patterns
- **Update process:** Requires retraining (hours–days on 4090)

### RAG
- **Best for:** Dynamic / frequently updated
- **Examples:** Live docs, product specs, internal wikis, code repos, news, user manuals that get revised often
- **Update process:** Just re-index chunks (minutes)

**Key insight:** Fine-tuning locks knowledge in → updating requires retraining. RAG updates quickly by re-indexing.

---

## Is it "how to think" or "what to know"?

### Fine-tuning
- **Focus:** "How to think"
- **Use cases:** Reasoning patterns, chain-of-thought examples, task formats, tone/style, structured output rules, domain-specific logic/judgment
- **Effect:** Teaches behavior & implicit patterns

### RAG
- **Focus:** "What to know"
- **Use cases:** Facts, documents, procedures, examples, reference material, long-form content
- **Effect:** Provides explicit facts/context without bloating the model

---

## Data volume & density

### Fine-tuning
- **Scale:** Smaller, high-quality, curated sets (1k–100k+ examples, often synthetic or distilled CoT traces)
- **Note:** Fine-tuning on huge raw data is inefficient/expensive on consumer GPU

### RAG
- **Scale:** Larger corpora (thousands to millions of chunks/pages/docs) — the more the better for coverage
- **Note:** RAG scales cheaply via embeddings

---

## Need for citations / traceability?

### Fine-tuning
- **Traceability:** Not critical (model internalizes it)
- **Limitation:** Fine-tuned knowledge is "in the weights" and harder to cite

### RAG
- **Traceability:** Critical (e.g., compliance, debugging, trust)
- **Benefit:** RAG naturally provides sources and gives verifiable grounding

---

## Latency / speed requirements

### Fine-tuning
- **Performance:** Very low latency (sub-100–200ms ideal)
- **Advantage:** No extra retrieval step → faster pure inference

### RAG
- **Performance:** Can tolerate slight added latency (~50–300ms for retrieval)
- **Note:** Includes retrieval overhead

---

## Risk of hallucination on edge cases

### Fine-tuning
- **Approach:** High need to reduce hallucinations via internalized patterns
- **Effect:** Helps with reasoning style/consistency

### RAG
- **Approach:** Hallucinations still possible but retrieval reduces them on covered topics
- **Effect:** Helps with factual recall