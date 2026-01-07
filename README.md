# ML Workshop Series

Machine learning workshops. From fundamentals to production systems.

## Workshops

### 1. The Perceptron (January 2026)

Where machine learning began. Understand how machines learn from examples by implementing the 1957 algorithm that started it all.

| Notebook | Description | Colab |
| --- | --- | --- |
| `04_perceptron.ipynb` | Perceptron from scratch, Iris dataset, XOR problem | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/04_perceptron.ipynb) |

**Resources:**
- [Slides](https://i33ym.cc/slides-perceptron/)
- [Interactive Demo](https://i33ym.cc/demo-perceptron/)
- [Essay](https://i33ym.cc/the-perceptron/)

### 2. Building a Production RAG System (December 2025)

Build a production-ready RAG (Retrieval Augmented Generation) system. Why simple RAG fails and how to fix it.

| Notebook | Description | Colab |
| --- | --- | --- |
| `01_simple_rag.ipynb` | Basic RAG implementation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/01_simple_rag.ipynb) |
| `02_production_rag.ipynb` | Full pipeline with all stages | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/02_production_rag.ipynb) |
| `03_evaluation.ipynb` | Testing and debugging | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/i33ym/workshop/blob/main/notebooks/03_evaluation.ipynb) |

**Resources:**
- [Slides](https://i33ym.cc/slides-rag/)
- [Live Demo](https://i33ym.cc/rag/)
- [Essay](https://i33ym.cc/building-a-rag/)

## Quick Start

```bash
# In Google Colab, run:
!git clone https://github.com/i33ym/workshop.git
%cd workshop
```

## Requirements

- Python 3.8+
- NumPy, pandas, matplotlib (for perceptron)
- OpenAI API key (for RAG notebooks)
- Google account (for Colab)

## All Resources

- [Workshop Index](https://i33ym.cc/workshops/)
- [LangChain Docs](https://docs.langchain.com)
- [LangGraph Docs](https://langchain-ai.github.io/langgraph/)
