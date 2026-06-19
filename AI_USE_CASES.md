# AI Use Cases (2026) — Agentic KYC

## Multi-agent crew (MetaGPT / CrewAI)
1. **Doc Extraction** — Gemini multimodal on ID photo → structured fields
2. **Identity Verify** — face-match (open-source: InsightFace / DeepFace) + liveness
3. **Sanctions Check** — RAG over OFAC / UN / EU lists (pgvector)
4. **Risk Score** — Claude Opus 4.7 with rationale citing policy clause
5. **Decision** — guardrailed: auto-approve if score < threshold + sanctions clear, else human-in-the-loop
6. **Critic** — Grok as second-opinion judge (catches Claude false-clears)

## Stack (free/OSS)
- **Crew:** MetaGPT, CrewAI, LangGraph
- **LLMs:** Claude Opus 4.7 (decision), Gemini 2.x (multimodal), Grok (critic), Ollama (private fallback)
- **RAG:** LlamaIndex + pgvector
- **Eval:** Promptfoo with F1 on a golden set of (synthetic) approval cases
- **Observability:** Langfuse + Arize Phoenix
- **MCP:** sanctions provider (e.g. ComplyAdvantage in prod)

## Eval (mandatory gate before launch)
```yaml
tests:
  - vars: { case: file://golden/high_risk_01.json }
    assert:
      - type: equals
        value: "DECLINE"          # known sanction match
      - type: contains
        value: "OFAC"             # cite the list
  - vars: { case: file://golden/low_risk_clean_01.json }
    assert:
      - type: equals
        value: "APPROVE"
      - type: llm-rubric
        value: "Cites policy clause; explains score; no AI slang"
```

Target: **99% F1 across 1000-case golden set before production traffic.** This replicates the production lift from 75% → 99% accuracy on approval workflows.

## Limitations
Real KYC needs licensed sanctions data + sanctions provider integration. Photo ID liveness in browser is mocked. Signature pad captures locally — production needs WORM storage + audit trail.
