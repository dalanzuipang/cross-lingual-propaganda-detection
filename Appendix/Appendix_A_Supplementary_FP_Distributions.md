# A SUPPLEMENTARY FP DISTRIBUTIONS

**对应论文正文位置：**
- **Section 5.2** "FP Concentration and Hallucination" - 提供了三个语言的详细FP分布数据，扩展了Table 3
- **Section 6.1** "Polish: Translation Augmentation Success" - 支持Polish的FP集中度分析
- **Section 6.2** "Russian: Low-Resource Specialization" - 支持Russian的FP分散度分析
- 正文中简要提到："EN approaches a single-peak regime: total FP is 4,697, with Loaded_Language contributing 2,287 FPs (48.7%)"，本附录提供完整的Top-10列表

**内容说明：**
本附录提供三个语言（English, Polish, Russian）使用Sup-FT方法在span-level检测中的Top-10 False Positive技术详细统计，包括FP数量、占比和对应的F1分数。

**对应正文位置：**
- **Section 5.2 "FP Concentration and Hallucination"** (第5页)：正文Table 3仅展示了Top-10 FP技术的排名和部分数据，本附录提供完整的三语言FP分布表格
- **Section 7 "English vs. Polish: Performance Comparison"** (第7页)：正文提到"EN shows markedly higher FP concentration: Loaded_Language accounts for 48.7%"，本附录提供详细数据支撑

**说明：** 本附录详细列出了三个语言（English、Polish、Russian）在Sup-FT方法下的Top-10 False Positive技术，包括FP数量、占比和F1分数。这些表格支持正文中关于"English FP集中度异常高（48.7%）而Polish和Russian更分散"的结论。

## Table 6: Polish Top-10 False Positive Techniques (Sup-FT, Total FP=4,012)

| Rank | Technique | FP | FP-only Share |
|------|-----------|-----|---------------|
| 1 | Loaded_Language | 1,248 | 31.1% |
| 2 | Obfuscation-Vagueness-Confusion | 464 | 11.6% |
| 3 | Questioning_the_Reputation | 354 | 8.8% |
| 4 | Doubt | 318 | 7.9% |
| 5 | Appeal_to_Values | 295 | 7.4% |
| 6 | Exaggeration-Minimisation | 268 | 6.7% |
| 7 | Name_Calling-Labeling | 249 | 6.2% |
| 8 | Appeal_to_Fear-Prejudice | 233 | 5.8% |
| 9 | Conversation_Killer | 157 | 3.9% |
| 10 | Appeal_to_Hypocrisy | 131 | 3.3% |

## Table 7: English Top-10 False Positive Techniques (Sup-FT, Total FP=4,697)

| Rank | Technique | FP | FP-only Share |
|------|-----------|-----|---------------|
| 1 | Loaded_Language | 2,287 | 48.7% |
| 2 | Doubt | 535 | 11.4% |
| 3 | Name_Calling-Labeling | 367 | 7.8% |
| 4 | Appeal_to_Fear-Prejudice | 272 | 5.8% |
| 5 | Conversation_Killer | 263 | 5.6% |
| 6 | Exaggeration-Minimisation | 239 | 5.1% |
| 7 | Questioning_the_Reputation | 232 | 4.9% |
| 8 | Repetition | 141 | 3.0% |
| 9 | Obfuscation-Vagueness-Confusion | 124 | 2.6% |
| 10 | Flag_Waving | 123 | 2.6% |

## Table 8: Russian Top-10 False Positive Techniques (Sup-FT, Total FP=2,051)

| Rank | Technique | FP | FP-only Share |
|------|-----------|-----|---------------|
| 1 | Loaded_Language | 400 | 19.5% |
| 2 | Doubt | 338 | 16.5% |
| 3 | Questioning_the_Reputation | 212 | 10.3% |
| 4 | Obfuscation-Vagueness-Confusion | 185 | 9.0% |
| 5 | Conversation_Killer | 157 | 7.7% |
| 6 | Appeal_to_Values | 122 | 5.9% |
| 7 | Appeal_to_Fear-Prejudice | 115 | 5.6% |
| 8 | Appeal_to_Hypocrisy | 113 | 5.5% |
| 9 | Exaggeration-Minimisation | 103 | 5.0% |
| 10 | Straw_Man | 92 | 4.5% |

Hallucination on gold=0. We define hallucination as predicting at least one span in an article annotated with no techniques (gold=0). We report hallucination statistics only when they are directly produced by the evaluation script and archived with the experiment outputs.
