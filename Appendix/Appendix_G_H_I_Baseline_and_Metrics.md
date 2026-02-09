# G SEED-ONLY BASELINE CONFIGURATION



We fine-tune XLM-RoBERTa-base on the SlavicNLP seed data (77 articles) for paragraph-level multi-label classification using sigmoid outputs. Input paragraphs are tokenized with padding/truncation to a maximum length of 256 tokens. We use a fixed decision threshold of 0.3 to predict all techniques whose probabilities exceed the threshold.

Training uses a 75%/25% train/validation split on the seed set, batch size 8, learning rate 5 × 10^-5, 8 epochs, and mixed precision (FP16). Due to the absence of Croatian training data, we report baseline results only for Polish and Russian.

# H ABLATION CONFIGURATIONS FOR SUP-FT

We evaluate three controlled architectures:

• Config-1 (Base Translation): XLM-RoBERTa trained on translated text only, without label semantics or dual-encoder structure.

• Config-2 (Concat w/ Explanations): Single-encoder model concatenating paragraph text with technique definitions/explanations.

• Config-3 (Dual-Encoder): Full dual-encoder with cross-attention fusion (reported as Sup-FT in main experiments).

These ablations isolate (i) label semantics (Config-2 vs. Config-1), (ii) dual-encoder fusion (Config-3 vs. Config-2), and (iii) the combined effect (Config-3 vs. Config-1).

# I TECHNIQUE-LEVEL FP/FN METRICS

For span-level error analysis, we compute per-technique false positives (FP) and false negatives (FN). To quantify error concentration, we define the FP-only share for technique t as:

Share_t = (FP_t / Σ_k FP_k) × 100%,

where the denominator is the total FP count for a given language/method setting.
