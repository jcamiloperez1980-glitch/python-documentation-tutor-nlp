# Cloud validation log — 20 November 2026

Public endpoint: https://python-documentation-tutor-nlp.streamlit.app/
Repository: https://github.com/jcamiloperez1980-glitch/python-documentation-tutor-nlp

This is a small UI smoke test, not a complete accuracy evaluation or user study.
The deployed configuration is Qwen2.5-1.5B-Instruct GGUF Q4_K_M, llama-cpp-python CPU, MiniLM embeddings and FAISS. The previous 36 BF16/0.5B outputs belong to different configurations and must be reported separately.

## Observed before the final prompt update

| Check | Observation | Assessment |
|---|---|---|
| Public UI | Opened with chat input, temperature, retrieval settings and privacy controls | Passed |
| Dictionary storage | Explained key-value associations; retrieved evidence expandable | Core answer supported; additional restrictions on key types need precise wording |
| Dictionary creation/access | Returned a dictionary literal and bracket key lookup with valid example | Passed this example |
| Follow-up: iterate only keys | Recommended items() and printed both keys and values | Failed: does not answer keys-only request |
| Outside-domain question | Returned the explicit insufficient-evidence refusal | Passed |
| Delete conversation | Cleared displayed prior turns before a new question | Passed UI smoke check |

The failed follow-up motivated stricter evidence-selection instructions. The new prompt does not itself prove correctness. Final-version follow-up validation remains pending until a new answer is observed.

## Local state checks

Five existing unit tests passed: independent sessions, input boundaries, invalid resume token, persistent resume/scoped deletion, rolling history/deletion.
The exact deployment source passed AST syntax validation, and isolated execution of its state components passed RAM-session isolation and deletion assertions.
These checks do not validate hosted SQLite retention, factual accuracy, or inference latency.

## Still required for the academic delivery

- Finish the 12-case evaluation on the exact deployed GGUF configuration and manually review factual correctness and truncation.
- Obtain real independent user feedback with consent; no feedback is invented here.
- Update the article/notebooks to match this deployment packaging, model format, runtime and public URL.
- Complete the IBM learning path in the student's own account and attach the authentic credential.
- Package and submit NLP Fase 4 in campus before its 22 November deadline; no submission is claimed in this log.
