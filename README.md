# RAG Workshop

Build a production-ready RAG (Retrieval Augmented Generation) system from scratch.

## What You'll Learn

1. **Why simple RAG fails** — and why it only scores 30% accuracy
2. **Hybrid search** — combining vector + keyword search
3. **Reranking** — scoring documents for relevance
4. **Relevance checks** — the CRAG pattern
5. **Grounding verification** — preventing hallucinations

## Notebooks

| Notebook | Description | Colab |
|----------|-------------|-------|
| `01_simple_rag.ipynb` | Basic RAG implementation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/01_simple_rag.ipynb) |
| `02_production_rag.ipynb` | Full pipeline with all stages | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/02_production_rag.ipynb) |
| `03_evaluation.ipynb` | Testing and debugging | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/03_evaluation.ipynb) |

## Quick Start

```python
# In Google Colab, run:
!git clone https://github.com/i33ym/workshop.git
%cd workshop
```

## Requirements

- OpenAI API key (get one at [platform.openai.com](https://platform.openai.com))
- Google account (for Colab)

## Workshop Schedule

- **Session 1:** Simple RAG — understanding the baseline
- **Session 2:** Production RAG — building a real system
- **Session 3:** Evaluation — testing and improving

## Resources

- [Live Demo](https://i33ym.cc/rag/)
- [Full Essay](https://i33ym.cc/building-a-rag/)
- [LangChain Docs](https://docs.langchain.com)
- [LangGraph Docs](https://langchain-ai.github.io/langgraph/)
