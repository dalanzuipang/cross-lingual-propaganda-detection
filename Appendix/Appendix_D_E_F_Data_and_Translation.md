# D AUGMENTED TRAINING CORPUS COMPOSITION

**对应论文正文位置：**
- **Section 3.1** "Translation-Based Augmentation Strategy" - 本附录提供语料组成的精确统计
- 正文中提到："(a) PL: 145 original (21%) + 517 translated (76%) + 15 SlavicNLP (2%) = 677 total"，本附录是该数据的来源说明

**内容说明：**
详细说明三个语言的训练语料构成比例（original/translated/SlavicNLP seed）。

---

# E STAGE 2 UNIFIED SPAN LOCALIZATION PROCEDURE

**对应论文正文位置：**
- **Section 3.2** "Detection Granularity: Paragraphs to Spans" - 本附录是该小节的详细流程说明
- 正文中简述三步流程："(1) Prompt construction... (2) Span generation... (3) Post-processing"，本附录提供完整的技术细节和错误传播分析

**内容说明：**
详细说明所有方法共享的LLM-based span定位流程，包括：
- Unified LLM-based Localization（统一的GPT-4o-mini调用流程）
- Error Propagation and Span-Level Difficulty（错误传播机制和span-level难点）

---

# F TRANSLATION ARTIFACTS: RISKS AND THREATS TO VALIDITY

**对应论文正文位置：**
- **Section 3.1末尾** - 正文提到："Translation-based expansion can introduce systematic artifacts... We treat translation as an empirical factor"
- **Section 7** "English vs. Polish: Performance Comparison" - 使用本附录的风险分析解释性能差异

**内容说明：**
系统性讨论机器翻译可能引入的三种风险：
- Literalness and stylistic flattening（字面化和风格平坦化）
- Syntactic interference（句法干扰）
- Cultural localization gap（文化本地化缺失）

**对应正文位置：**
- **Section 3.1 "Translation-Based Augmentation Strategy"** (第2-3页)：正文提到"PL: 145 original (21%) + 517 translated (76%)"，本附录D提供完整语料组成
- **Section 3.2 "Detection Granularity: Paragraphs to Spans"** (第3页)：正文简述了two-stage pipeline，本附录E提供详细的Stage 2 span定位流程
- **Section 7 "English vs. Polish"** (第7页)：正文提到翻译artifacts，本附录F详细讨论三种翻译风险

**说明：** 本文档包含三个附录内容：
- **Appendix D**: 训练语料的详细组成（原始、翻译、SlavicNLP种子数据的比例）
- **Appendix E**: 统一的LLM-based span定位程序（三步流程：prompt构建、span生成、后处理）
- **Appendix F**: 翻译artifacts的三种系统性风险（字面化、句法干扰、文化本地化gap）

We construct the augmented training corpus from SemEval-2023 Task 3 plus the SlavicNLP seed data (in-domain supplement for overlapping languages). For supervised training, the corpus composition is:

• Polish: 145 original (21%) + 517 translated (76%) + 15 SlavicNLP (2%) = 677 total
• Russian: 143 original (21%) + 517 translated (75%) + 27 SlavicNLP (4%) = 687 total
• English: 536 original (100%), no translation augmentation

# E STAGE 2 UNIFIED SPAN LOCALIZATION PROCEDURE

## Unified LLM-based Localization

All methods share the same LLM-based span localization procedure to ensure that span-level differences mainly reflect Stage 1 paragraph-level recall rather than boundary modeling choices. For each propaganda-positive paragraph P with predicted techniques T_P, we run the following steps for each t ∈ T_P:

(1) Prompt construction: We build a structured prompt containing (i) a language-specific expert persona, (ii) the paragraph text, (iii) a concise definition excerpt for technique t, (iv) detection criteria, and (v) keyword references distilled from the annotation guidelines.

(2) Span generation: We call GPT-4o-mini to output JSON-formatted character spans:

{"positions": [{"start": int, "end": int, "confidence": float, "text": str}]}

(3) Post-processing: We filter spans by confidence threshold (≥ 0.7), validate character offsets, and deduplicate overlapping spans with identical technique labels.

## Error Propagation and Span-Level Difficulty

Span F1 is substantially lower than paragraph-level Macro F1 due to (i) cascading errors when Stage 1 misses propaganda paragraphs, (ii) strict character-level overlap matching that penalizes small boundary shifts, and (iii) frequent cross-sentence gold spans that are harder to reproduce from paragraph-based prompting.

# F TRANSLATION ARTIFACTS: RISKS AND THREATS TO VALIDITY

Translation-based augmentation can introduce systematic artifacts that shift surface realizations away from native usage. We summarize three key risks:

• Literalness and stylistic flattening: idioms, metaphors, and emotional intensity may be paraphrased or weakened, potentially diluting cues for techniques such as Loaded_Language.

• Syntactic interference: source-language word order patterns may leak into Slavic targets, creating a mismatch between translated training and native test distributions.

• Cultural localization gap: culture-specific references and allusions may lose salience after translation, weakening technique-specific rhetorical signals.

We therefore treat translation as an empirical factor and quantify its impact through controlled comparisons and technique-level error analysis in later chapters.
