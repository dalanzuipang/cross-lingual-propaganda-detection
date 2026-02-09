# P POLISH: DETAILED TABLES

**对应论文正文位置：**
- **Section 6.1** "Polish: Translation Augmentation Success" - 本附录是该小节的详细数据支持
- 正文中引用多个具体数据：
  - "Baseline degenerates on Task 2 (Macro F1=0.53%)" → Table 12
  - "Name_Calling-Labeling (F1=0.904), exceeding RU (0.649)" → Table 14
  - "Loaded_Language contributes 31.1% of total FP, and the top five techniques contribute 66.8%" → Table 15
  - "Weak techniques... with F1 < 0.3 are dominated by low support" → Table 16
- **Table 4** - Table 17是其Polish部分的详细版

**内容说明：**
本附录提供Polish语言的6个详细表格：
1. **Table 12**: Baseline vs. Augmented方法对比（验证H1）
2. **Table 13**: 三种检测方法的性能对比（paragraph-level + span-level）
3. **Table 14**: Name_Calling的跨语言性能对比（Polish优势明显）
4. **Table 15**: Top 5 False Positives及集中度分析
5. **Table 16**: 弱技术列表（F1<0.3，主要受low support影响）
6. **Table 17**: 三种方法的优缺点和适用场景

**对应正文位置：**
- **Section 6.1 "Polish: Translation Augmentation Success"** (第6页)：正文提到"baseline Macro F1=0.53%... Sup-FT reaches 52.23%... Name_Calling F1=0.904... top five techniques contribute 66.8%"，本附录提供支撑这些结论的6个详细表格
- **Table 1** (第5页)：正文Table 1展示核心指标，本附录Table 12-17提供Polish的完整分析

**说明：** 本附录包含6个Polish语言的详细表格：
- **Table 12**: Baseline vs. 增强方法对比（展示98.6倍的性能提升）
- **Table 13**: 三种方法的全面性能对比
- **Table 14**: Name_Calling跨语言性能（Polish优势明显）
- **Table 15**: Top-5 FP集中度分析（66.8%）
- **Table 16**: 弱技术列表（F1<0.3，主要因样本不足）
- **Table 17**: 三种方法的优缺点和适用场景

## Table 12: Polish Baseline vs. Augmented Methods (Task 2: technique multi-label classification)

| Method | Training Data | Macro F1 |
|--------|---------------|----------|
| Baseline | SlavicNLP seed only (77 seed articles; multilingual mix) | 0.53% |
| Sup-FT | SemEval + translation (+ seed) | 52.23% |
| Prompt-A | Zero-shot (no training) | 49.97% |
| Iter-Ens | Zero-shot (no training) | 50.55% |

## Table 13: Performance Comparison of Three Detection Methods on Polish

| Evaluation Dimension | Sup-FT | Prompt-A | Iter-Ens | Best Method |
|----------------------|--------|----------|----------|-------------|
| **Paragraph-level Classification** | | | | |
| Macro F1 | 52.23% | 49.97% | 50.55% | Sup-FT |
| Micro F1 | 66.75% | 58.88% | 58.65% | Sup-FT |
| Binary F1 | 96.77% | 98.88% | 96.77% | Prompt-A |
| **Character-level Localization** | | | | |
| Span F1 | 8.51% | 5.98% | 7.54% | Sup-FT |
| Precision | 6.22% | 4.75% | 4.76% | Sup-FT |
| Recall | 13.50% | 8.07% | 18.12% | Iter-Ens |

## Table 14: Cross-linguistic Performance of Name_Calling Technique

| Metric | Polish | English | Russian |
|--------|--------|---------|---------|
| F1 | 0.904 | 0.833 | 0.649 |
| Precision | 0.917 | 0.778 | 0.706 |
| Recall | 0.892 | 0.889 | 0.600 |
| Support | 37 | 63 | 20 |
| Gap vs Polish | – | -0.071 | -0.255 |

## Table 15: Top 5 False Positives in Polish (Sup-FT, FP-only)

| Rank | Technique | FP Count | % of Total FP |
|------|-----------|----------|---------------|
| 1 | Loaded_Language | 1,248 | 31.1% |
| 2 | Obfuscation-Vagueness | 464 | 11.6% |
| 3 | Questioning_Reputation | 354 | 8.8% |
| 4 | Doubt | 318 | 7.9% |
| 5 | Appeal_to_Values | 295 | 7.4% |
| **Top 2 Concentration** | | 1,712 | 42.7% |
| **Top 5 Concentration** | | 2,679 | 66.8% |

## Table 16: Polish Weak Techniques (F1<0.3)

| Technique | F1 | Precision | Recall | Support | Main Issue |
|-----------|-----|-----------|--------|---------|------------|
| Straw_Man | 0.000 | 0.000 | 0.000 | 1 | Extremely few samples |
| Appeal_to_Pity | 0.000 | 0.000 | 0.000 | 0 | No test samples |
| Appeal_to_Time | 0.182 | 0.143 | 0.250 | 4 | Insufficient samples |
| Whataboutism | 0.222 | 0.143 | 0.500 | 2 | Extremely low frequency |
| Causal_Oversimplification | 0.267 | 0.154 | 1.000 | 4 | Insufficient samples |

## Table 17: Advantages and Disadvantages of Three Methods on Polish

| Method | Advantages | Disadvantages | Applicable Scenarios |
|--------|------------|---------------|----------------------|
| Sup-FT | Highest Macro F1 (52.23%)<br>Highest Span F1 (8.51%)<br>Balanced technique distribution<br>Lower false positive risk | | Precision priority<br>Comprehensive performance |
| Prompt-A | Highest Binary F1 (98.88%)<br>Zero hallucination<br>Strong interpretability | Lower Macro F1 (49.97%)<br>Lowest Span F1 (5.98%)<br>High API cost | Interpretability priority<br>Zero-shot deployment |
| Iter-Ens | Highest recall (18.12%)<br>Zero hallucination<br>Strong robustness | Increased false positives<br>High inference cost<br>Medium Span F1 (7.54%) | Recall priority<br>Robustness needs |
