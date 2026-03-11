# LLM_Eval_Tools
Evaluation Tools for LLM Responses

This repository contains implementations of the evaluation tools used in the study “AI and Patient Safety: A Comparative Evaluation of Generative AI Agents in EU Healthcare Law Consultations.” The code provides a reproducible framework for evaluating large language model (LLM) responses against expert-validated reference answers using both full-text semantic similarity metrics and keyword-based conceptual evaluation. 
This repository include scripts that are designed to operate directly on each of the two datasets used in the paper:

•	DS1: Question–answer pairs derived from EU cross-border healthcare information materials. (Datasets/QA.xlsx)

•	DS2: Structured legal case scenarios related to EU healthcare law. (Datasets/KC.xlsx)

The provided code pipelines load these datasets, preprocess the texts, generate evaluation scores for LLM responses, and output comparable metrics across models.

This repository is structured as follows:

LLM_Eval_Tools/
│

├── FullTextEvaluation/

│   │

│   ├── BertScore/

│   │   ├── bertscore_ds1.py

│   │   └── bertscore_ds2.py

│   │

│   ├── SemanticScore/

│   │   ├── semantic_comparison_of_texts_ds1.py

│   │   └── semantic_comparison_of_texts_ds2.py

│   │

│   └── WordMoverDistance/

│       └── word_mover's_distance_(for_texts).py

│

└── KeywordsEvaluation/

    │
    
    ├── Embedding_Based/
    
    │   ├── keywords_extraction.py
    
    │   └── compare_cases_keywords.py
    
    │
    
    └── YAKE/
    
        └── yake_kw_extraction.py
        
        └── yake_keywords_comparison.py
        

Full-Text Evaluation Tools (applied on DS1 and DS2)

BERTScore

Measures semantic similarity between generated responses and reference answers by aligning contextual token embeddings from a pretrained BERT model. It computes precision, recall, and F1 scores based on semantic token matching.

Semanatic Score [Sentence-BERT (SBERT)]

Generates fixed-length sentence embeddings that allow efficient semantic similarity comparison using cosine similarity. This enables evaluation of overall semantic alignment between responses and ground-truth answers.

     all-MiniLM-L6-v2

         A lightweight general-purpose sentence transformer model used for computing baseline semantic similarity between texts.

     LegalBERT

         A domain-specific transformer model trained on legal corpora. It captures legal terminology and concepts, making it particularly
         useful for evaluating responses in EU healthcare law contexts.

     BioBERT

         A biomedical language model trained on medical literature. It helps capture healthcare-related terminology within responses.

Word Mover’s Distance (WMD)

Computes the semantic distance between documents by measuring the minimum cost required to transform one document’s word embeddings into another.


Keyword-Based Evaluation Tools (Applied on DS2 only)

Keywords are extracted from texts using two methods; embedding-based (Keybert, LegalBert, and BioBert) in addition to the statistical method (YAKE).

Embedding-Based

Extracts representative keywords from texts using embedding similarity between document representations and candidate phrases.

YAKE (Yet Another Keyword Extractor)

A statistical keyword extraction algorithm that identifies important terms based on word frequency, position, casing, and contextual distribution.

Keyword Matching Metrics: The repository includes scripts that compute:

•	Exact keyword matching

•	Partial keyword matching

•	Semantic keyword similarity

•	Set-level embedding similarity

•	Keyword-level Word Mover’s Distance

Together, these tools provide a multi-level evaluation pipeline for assessing how well LLM-generated responses reproduce the semantic meaning and key legal concepts present in expert reference answers. The repository enables researchers to reproduce the experiments from the paper and extend the evaluation to additional LLM systems or datasets.

The scripts were designed to run on Google Colab.

