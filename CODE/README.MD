# Code Release

This repository contains the companion code for the work:


It implements a two-stage pipeline for persuasion/propaganda technique detection:

Stage 1 (Paragraph-level): multi-label classification over a shared 23-technique taxonomy, comparing:
Sup-FT: supervised fine-tuning with an XLM-RoBERTa-based classifier (including an explanation-aware dual-encoder variant)
Prompt-A: zero-shot prompted multi-agent detection (one agent per technique + coordinator)
Iter-Ens: multi-round sampling + voting to improve robustness/recall
Stage 2 (Character-level): LLM-based span localization . It prompts GPT-4o-mini to output JSON spans and applies confidence filtering (≥ 0.7) + post-processing.
