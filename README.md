# eBay 2025 University ML Competition — Automotive NER (German Listings)

A domain-specific **Named Entity Recognition (NER)** pipeline for German eBay motor-vehicle parts titles. The goal is to extract structured entities such as **model, brand, part type, kit contents, and size/material** from noisy listing text.

**Result:** Achieved **0.869172 weighted F0.2** using **BIOS tagging** with **FacebookAI/xlm-roberta-large**.

---

## Problem Statement
eBay vehicle-parts titles are short, noisy, and full of abbreviations (e.g., OEM codes, sizes, mixed casing). This project converts raw German titles into structured entities to enable:
- better search relevance  
- normalized product attributes  
- improved cataloging and recommendations  

---

## Dataset
- **Unlabeled:** ~**2M** German motor-vehicle parts titles  
- **Labeled:** **9K** annotated samples (token-level entity tags)

 
---


## Approach
### 1) Preprocessing
- Normalize whitespace and special characters
- Handle common German abbreviations + casing variants
- Optional: rule-based cleanup for units (mm, inch), part numbers, and OEM codes

### 2) Labeling Format
- Converted annotations into **BIOES** scheme:
  - **B**-egin, **I**-nside, **O**-utside, **E**-nd, **S**-ingle-token entity

### 3) Model
- Transformer token classifier:
  - **FacebookAI/xlm-roberta-large**
- Fine-tuning objective:
  - token-level cross-entropy on BIOS tags

### 4) Evaluation
- Primary metric: **weighted F0.2**
  - emphasizes **precision** more than recall (β = 0.2)
- Best score achieved: **0.869172 weighted F0.2**

---
