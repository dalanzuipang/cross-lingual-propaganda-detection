# G SEED-ONLY BASELINE CONFIGURATION

**对应论文正文位置：**
- **Section 4** "Baseline" - 本附录是该段落的详细配置说明
- 正文中引用baseline结果："for Polish, Macro F1 = 0.53% (28 predicted labels vs. 348 gold labels), for Russian: Macro F1 = 0.00%"

**内容说明：**
提供seed-only baseline的完整训练配置，证明77篇文章不足以支持稳定的多标签学习。

---

# H ABLATION CONFIGURATIONS FOR SUP-FT

**对应论文正文位置：**
- **Section 4** "Ablation Study Design" - 本附录详细说明三个消融配置
- **Section 7.1** "Ablation Study: Architecture vs. Data" - 使用这三个配置进行实验，结果见Table 5
- 正文中提到："We evaluate three controlled architectures: (1) Config-1... (2) Config-2... (3) Config-3"

**内容说明：**
详细定义三个消融实验配置，用于分离translation、label semantics和dual-encoder架构的效果。

---

# I TECHNIQUE-LEVEL FP/FN METRICS

**对应论文正文位置：**
- **Section 4** "Span-Level Error Analysis" - 本附录提供FP-only share的数学定义
- 正文中使用该公式："Share_t = (FP_t / Σ_k FP_k) × 100%"
- **Table 3** - 使用该公式计算的结果

**内容说明：**
定义technique-level的FP/FN计算方法和FP-only share公式。

**对应正文位置：**
- **Section 4 "Evaluation Protocol" - Baseline部分** (第4页)：正文提到"Baseline yields near-zero performance (Polish: 0.53%, Russian: 0.00%)"，本附录G提供完整的baseline训练配置
- **Section 4 "Evaluation Protocol" - Ablation Study Design部分** (第4页)：正文描述了三个Config的设计，本附录H提供详细说明
- **Section 4 "Evaluation Protocol" - Span-Level Error Analysis部分** (第4页)：正文定义了FP-only share公式，本附录I提供完整的指标定义

**说明：** 本文档包含三个附录内容：
- **Appendix G**: Seed-only baseline的完整配置（77篇文章、XLM-RoBERTa-base、训练参数）
- **Appendix H**: 消融实验的三个配置（Config-1: Base Translation, Config-2: Concat + Expl., Config-3: Dual-Encoder）
- **Appendix I**: Technique-level FP/FN指标的数学定义

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
