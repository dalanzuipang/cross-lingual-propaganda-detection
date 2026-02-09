# D AUGMENTED TRAINING CORPUS COMPOSITION



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
