Factor
Why the split?
How frequently does the data change?
Stable / rarely changes (e.g., core domain rules, company style guide, fixed terminology, reasoning patterns)
Dynamic / frequently updated (e.g., live docs, product specs, internal wikis, code repos, news, user manuals that get revised often)
Fine-tuning locks knowledge in → updating requires retraining (hours–days on 4090). RAG updates by just re-indexing chunks (minutes).
Is it "how to think" or "what to know"?
"How to think" — reasoning patterns, chain-of-thought examples, task formats, tone/style, structured output rules, domain-specific logic/judgment
"What to know" — facts, documents, procedures, examples, reference material, long-form content
Fine-tuning teaches behavior & implicit patterns. RAG provides explicit facts/context without bloating the model.
Data volume & density
Smaller, high-quality, curated sets (1k–100k+ examples, often synthetic or distilled CoT traces)
Larger corpora (thousands to millions of chunks/pages/docs) — the more the better for coverage
Fine-tuning on huge raw data is inefficient/expensive on consumer GPU; RAG scales cheaply via embeddings.
Need for citations / traceability?
Not critical (model internalizes it)
Critical (e.g., compliance, debugging, trust) — RAG naturally provides sources
RAG gives verifiable grounding; fine-tuned knowledge is "in the weights" and harder to cite.
Latency / speed requirements
Very low latency needed (sub-100–200ms ideal)
Can tolerate slight added latency (~50–300ms for retrieval)
Fine-tuning = no extra retrieval step → faster pure inference.
Risk of hallucination on edge cases
High need to reduce hallucinations via internalized patterns
Hallucinations still possible but retrieval reduces them on covered topics
Fine-tuning helps with reasoning style/consistency; RAG helps with factual recall.
