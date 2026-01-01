# Disentangled Question Answering (DisentangledQA)

This repository contains an end-to-end implementation of the paper
**“Disentangled Retrieval and Reasoning for Implicit Question Answering.”**

The project focuses on solving **implicit QA** tasks by explicitly separating **retrieval** and **reasoning** instead of learning them as a single entangled process.


## What this implements

The pipeline closely follows the original paper and is structured into clear, independent stages:

1. **Query generation**
   Implicit questions are decomposed into focused sub-queries to reduce the lexical gap between the question and supporting evidence.

2. **Disentangled retrieval**

   * BM25 is used for high-recall candidate retrieval
   * A dense dual-encoder retriever reranks passages semantically
     Retrieval is evaluated using **Recall@K**, matching the paper’s protocol.

3. **Reasoning module**
   A T5-based sequence-to-sequence model performs reasoning over retrieved passages to produce binary (Yes/No) answers.

Each component is trained and evaluated separately to maintain interpretability and alignment with the paper.

---

## Dataset and evaluation

* Dataset: **StrategyQA**
* Metrics:

  * Retrieval: Recall@3 / Recall@5 / Recall@7
  * Reasoning: Answer accuracy
* Evaluation follows the setup described in the original paper.

---

## Tech stack

* Python
* PyTorch
* Hugging Face Transformers
* Sentence-Transformers
* BM25 (rank-bm25)

The implementation is compatible with **Kaggle and Colab** environments.

---

## Structure

The repository is organized as step-wise notebooks covering:

* Query generation
* BM25 retrieval
* Dense retriever training
* Reasoner training
* Final evaluation

Each stage can be run independently.

---

## Notes

* Hyperparameters are aligned with those reported in the paper where applicable
* Data loaders support StrategyQA’s JSONL format
* The design makes it easy to extend or ablate individual components

---

## Reference

Qian Liu et al.,
**Disentangled Retrieval and Reasoning for Implicit Question Answering**
