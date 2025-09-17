# Towards Robustness of Text-to-Visualization Translation Against Lexical and Phrasal Variability

[![ICDE 2025](https://img.shields.io/badge/ICDE-2025-green)](https://ieeexplore.ieee.org/abstract/document/11112835)

This repository contains the dataset and code for the paper "Towards Robustness of Text-to-Visualization Translation Against Lexical and Phrasal Variability" accepted at "2025 IEEE 41st International Conference on Data Engineering (ICDE)".

## 📖 Citation

If you find this work useful, please cite our paper:

```bibtex
@INPROCEEDINGS{11112835,
  author={Lu, Jinwei and Song, Yuanfeng and Zhang, Haodi and Zhang, Chen Jason and Wu, Kaishun and Wong, Raymond Chi-Wing},
  booktitle={2025 IEEE 41st International Conference on Data Engineering (ICDE)},
  title={Towards Robustness of Text-to-Visualization Translation Against Lexical and Phrasal Variability},
  year={2025},
  volume={},
  number={},
  pages={793-806},
  keywords={Translation;Perturbation methods;Large language models;Retrieval augmented generation;Data visualization;Programming;Data engineering;Robustness;Data models;Generators;text-to-visualization;model robustness;large language model;retrieval-augmented generation;input variation},
  doi={10.1109/ICDE65448.2025.00065}
}
```

## 📊 Dataset: nvBench-Rob

nvBench-Rob is a robustness benchmark dataset for text-to-visualization translation, designed to evaluate model performance against lexical and phrasal variability in natural language queries.

### Dataset Statistics

- **Total Samples**: 1,182 visualization queries
- **Database Schemas**: Multiple domains including academic, browser, employee, etc.
- **Query Types**: Bar charts, line charts, pie charts, and other visualization types
- **Robustness Features**:
  - Lexical variations (synonyms, paraphrases)
  - Phrasal variations (different sentence structures)
  - Multiple natural language formulations for each visualization query

### Dataset Files

```
nvBench-Rob/
├── nvBench-Rob_nlq.json          # Main dataset with NLQ variations
├── nvBench-Rob_nlq_schema.json   # Schema-aware NLQ variations
├── nvBench-Rob_schema.json       # Schema information
└── tables.json                   # Database table schemas
```

### Data Format

Each data sample contains:

```json
{
  "vis_query": {
    "vis_part": "Visualize BAR",
    "data_part": {
      "sql_part": "SELECT ...",
      "binning": ""
    },
    "VQL": "Visualize BAR SELECT ..."
  },
  "chart": "Bar",
  "hardness": "Medium",
  "db_id": "database_name",
  "nl_queries": [
    "Present a bar graph representing...",
    "What are the identifiers and names...",
    "Create a bar chart to represent..."
  ],
  "record_name": "identifier"
}
```

### Code

```
├── generate/                    # RAG-based generation pipeline
│   └── generate/
│       ├── run_generate.sh      # Main execution script
│       ├── generate_by_rag_nlq.py    # NLQ-based RAG generation
│       ├── rag_dvqs.py          # DVQ similarity retrieval
│       ├── debug_by_ref_dvqs.py # Reference-based debugging
│       └── debug_by_db_ann.py   # Schema-aware correction
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📧 Contact

For questions or collaborations:

- **Jinwei Lu**: jwlu18@gmail.com
