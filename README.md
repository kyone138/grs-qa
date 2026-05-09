# GRS-QA: Graph-Structured Question Answering Dataset

[![Paper](https://img.shields.io/badge/Paper-LREC--COLING%202026-blue)](https://lrec.elra.info/lrec2026-main-414)

Official repository for:

**Reasoning Graph-Structured Question Answering: Datasets and Insights from LLM Benchmarking**

---

## Overview

GRS-QA is a graph-structured multi-hop question answering benchmark that augments existing QA datasets with explicit reasoning graphs.

The dataset introduces:

- Directed reasoning graphs for multi-hop QA
- Unified structural annotations across domains
- Positive and negatively perturbed reasoning graphs
- Graph-aware prompting benchmarks for LLM evaluation

GRS-QA combines examples from:

- HotpotQA
- MuSiQue
- 2WikiMultiHopQA
- GSM8K

---

## Paper

📄 Paper Link:

https://lrec.elra.info/lrec2026-main-414

📄 PDF:

```text
paper/GRSQA_LREC2026.pdf
```

---

## Repository Structure

```bash
.
├── data/
├── sample_data/
├── paper/
└── README.md
```

---

## Dataset Features

### Positive Reasoning Graphs

Each question-answer pair is paired with a reasoning graph where:

- Nodes represent evidence sentences or equations
- Directed edges represent logical dependencies
- Graphs encode multi-step reasoning paths

### Negative Reasoning Graphs

We additionally provide structurally perturbed graphs:

- Edge perturbations
- Node perturbations
- Width perturbations (GSM8K)
- Depth perturbations (GSM8K)

These are designed to evaluate robustness and structure sensitivity in LLMs.

---

## Example Data Format

```json
{
  "question": "Who beat the player that won the 2017 Australian men's open tennis single title in the US open?",
  "answer": "Novak Djokovic",
  "graph_type": "Bridge_2_1",
  "nodes": [
    {
      "id": 0,
      "content": "Roger Federer won the 2017 Australian Open."
    },
    {
      "id": 1,
      "content": "Novak Djokovic beat Roger Federer in the US Open."
    }
  ],
  "edges": [
    [0, 1]
  ]
}
```

---

## Supported Graph Types

| Graph Type | Description |
|---|---|
| Bridge | Sequential reasoning |
| Comparison | Entity comparison |
| Compositional | Multi-step compositional reasoning |
| Bridge-Comparison | Hybrid reasoning structures |

---

## Main Findings

Our experiments show:

- Reasoning graph examples outperform graph-as-context prompting
- Smaller LLMs struggle with graph structure understanding
- Mathematical reasoning graphs generalize better across models
- Perturbed graphs significantly degrade performance

---


## Citation

If you use GRS-QA in your research, please cite:

```bibtex
@inproceedings{yone-etal-2026-reasoning,
  title = {Reasoning Graph-Structured Question Answering: Datasets and Insights from LLM Benchmarking},
  author = {Yone, Khin and Trivedi, Devasha and Pahilajani, Anish and Shuai, Jincen and Jain, Samyak Rajesh and Rossi, Ryan and Ahmed, Nesreen K. and Dernoncourt, Franck and Wang, Yu and Park, Namyong},
  booktitle = {Proceedings of the Fifteenth Language Resources and Evaluation Conference (LREC 2026)},
  month = {May},
  year = {2026},
  pages = {5301--5316},
  address = {Palma, Mallorca, Spain},
  publisher = {European Language Resources Association (ELRA)},
  editor = {Piperidis, Stelios and Bel, Núria and van den Heuvel, Henk and Ide, Nancy and Krek, Simon and Toral, Antonio},
  doi = {10.63317/4zjpmtqxxtx4},
  abstract = {Large Language Models (LLMs) have shown remarkable success in multi-hop question-answering (M-QA) due to their advanced reasoning capabilities. However, the influence of reasoning structures on their performance remains underexplored, primarily due to the lack of M-QA datasets that explicitly encode the reasoning pathways underlying each question-answer pair. To address this gap, we introduce the reasoning graph-structured question answering dataset (GRS-QA), which provides both semantic contexts and reasoning structures for the QA pairs. Unlike existing M-QA datasets, GRS-QA explicitly captures intricate reasoning pathways through reasoning graphs, where nodes correspond to textual contexts and edges denote logical flows. Using GRS-QA, we systematically evaluate LLM performance across varying context structures, prompting styles, and data domains. Our empirical analysis reveals that LLMs perform differently based on the reasoning structure, context, and prompting styles, indicating their varying ability to leverage graph-structured knowledge. Notably, providing explicit reasoning guidance proves more effective than supplying contextual information alone.}
}
```

---

## License

Our dataset is released under the Creative Com-
mons Attribution 4.0 International License (CC BY
4.0).
