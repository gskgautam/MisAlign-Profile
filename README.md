# MisAlign-Profile

MisAlign-Profile is a unified benchmark designed to analyze **cross-dimensional misalignment** in Large Language Models (LLMs) across **safety, value, and cultural** dimensions.

---

## Repository Structure

The repository contains the following files:

- `dataset_with_responses.csv`  
  The final MISALIGNTRADE dataset containing prompts paired with aligned and misaligned responses, along with their inferred safety, value, and cultural domains.

- `before_generation_count.csv`  
  Domain-wise statistics showing the number of prompts after classification, expansion, and deduplication, prior to response generation.

- `after_generation_count.csv`  
  Domain-wise statistics showing the number of retained aligned–misaligned response pairs after candidate filtering and feedback-guided resampling.


## 🔍 Overview

Existing benchmarks evaluate alignment dimensions in isolation. However, real-world scenarios require models to **simultaneously satisfy multiple dimensions**, leading to trade-offs.

MisAlign-Profile introduces:
- A **unified evaluation framework**
- A large-scale dataset: **MISALIGNTRADE**
- Systematic analysis of **cross-dimensional trade-offs**

> Empirical findings show **12%–34% trade-offs** across alignment dimensions. :contentReference[oaicite:0]{index=0}

---

## 📦 Dataset: MISALIGNTRADE

- **19,664 samples**
- **112 normative domains**:
  - 14 Safety
  - 56 Value
  - 42 Cultural
- Each sample includes:
  - Prompt
  - Aligned response ✅
  - Misaligned response ❌
  - Domain labels
  - Semantic types:
    - Object
    - Attribute
    - Relation

---

## ⚙️ Pipeline

### Stage I: Dataset Construction
- Prompt classification (domain + semantic type)
- Expansion via LLMs (Gemma, Qwen)
- Deduplication using SimHash
- Response generation (aligned & misaligned)
- Two-stage filtering + feedback-guided resampling

### Stage II: Benchmarking
- Zero-shot evaluation of LLMs
- Tested on:
  - General-purpose aligned models
  - Dimension-specific fine-tuned models
  - Open-weight LLMs

---

## 📊 Metrics

- **Coverage (↑)**: Detects misalignment
- **False Failure Rate (↓)**: Avoids penalizing correct outputs
- **Alignment Score (↑)**: Harmonic mean of performance

---

## 📈 Key Findings

- General-purpose aligned models achieve the best balance (AS ≈ 79–86%)
- Dimension-specific models:
  - High coverage ⚠️
  - Very high false failure rates (over-conservative)
- Relation-level misalignment is hardest (lowest performance)
- Misalignment arises from **systematic trade-offs**, not isolated failures

---
