# Q RUSSIAN: DETAILED TABLES

**对应论文正文位置：**
- **Section 6.2** "Russian: Low-Resource Specialization" - 本附录是该小节的详细数据支持
- 正文中引用多个具体数据：
  - "baseline collapses (Macro F1=0.00%)" → Table 18
  - "Sup-FT reaches Macro F1=39.57% and yields comparatively strong span localization (Span F1=11.17%)" → Table 19
  - "Russian shows a distinctive advantage on Doubt: the best result reaches F1=0.907 (Iter-Ens)" → Table 20
  - "Russian's FP distribution is the most dispersed among the three languages (top-2 concentration 36.0%)" → Table 22
- **Table 3** - Table 21和Table 22补充了Russian的详细FP数据

**内容说明：**
本附录提供Russian语言的6个详细表格：
1. **Table 18**: Baseline vs. Augmented方法对比（完全崩溃 → 验证H1的必要性）
2. **Table 19**: 三种检测方法的性能对比（Sup-FT表现最佳）
3. **Table 20**: Doubt技术的跨语言对比（Russian在Doubt上表现最强）
4. **Table 21**: Loaded_Language的跨语言对比（Russian相对保守）
5. **Table 22**: Top 5 False Positives及分散度分析（最分散，36.0%）
6. **Table 23**: Russian在极度稀缺下的弱技术/失败技术列表

**对应正文位置：**
- **Section 6.2 "Russian: Low-Resource Specialization"** (第6页)：正文提到"baseline Macro F1=0.00%... Sup-FT reaches 39.57%... distinctive advantage on Doubt: F1=0.907... conservative on Loaded_Language... FP distribution most dispersed (top-2 concentration 36.0%)"，本附录提供支撑数据
- **Table 1** (第5页)：正文Table 1展示核心指标，本附录Table 18-23提供Russian的完整分析

**说明：** 本附录包含6个Russian语言的详细表格：
- **Table 18**: Baseline完全崩溃（0.00%）vs. 增强方法的恢复
- **Table 19**: 三种方法的全面性能对比
- **Table 20**: Doubt跨语言性能（Russian达到最高0.907）
- **Table 21**: Loaded_Language的保守策略（precision 1.000但recall 0.761）
- **Table 22**: 最分散的FP分布（Top-2仅36.0%，对比English的60.1%）
- **Table 23**: 极端稀缺下的失败技术列表

## Table 18: Russian Baseline vs. Augmented Methods (Task 2: technique multi-label classification)

| Method | Training Data | Macro F1 |
|--------|---------------|----------|
| Baseline | SlavicNLP seed only (77 seed articles; multilingual mix) | 0.00% |
| Sup-FT | SemEval + translation (+ seed) | 39.57% |
| Prompt-A | Zero-shot (no training) | 35.25% |
| Iter-Ens | Zero-shot (no training) | 38.77% |

## Table 19: Performance Comparison of Three Detection Methods on Russian

| Metric | Sup-FT | Prompt-A | Iter-Ens | Best Method |
|--------|--------|----------|----------|-------------|
| **Paragraph-level Classification** | | | | |
| Macro F1 | 39.57% | 35.25% | 38.77% | Sup-FT |
| Micro F1 | 57.19% | 44.48% | 48.05% | Sup-FT |
| Binary F1 | 97.87% | 92.13% | 100.00% | Iter-Ens |
| **Character-level Localization** | | | | |
| Span F1 | 11.17% | 6.13% | 6.16% | Sup-FT |
| Precision | 7.45% | 4.01% | 3.54% | Sup-FT |
| Recall | 22.33% | 12.99% | 23.41% | Iter-Ens |

## Table 20: Cross-linguistic Performance Comparison of Doubt (Best Method per Language)

| Language | Best F1 | Method | Precision | Recall | Support | Gap vs Russian |
|----------|---------|--------|-----------|--------|---------|----------------|
| Russian | 0.907 | Iter-Ens | 0.944 | 0.872 | 39 | – |
| Polish | 0.857 | Prompt-A | – | – | 32 | -0.050 |
| English | 0.750 | Sup-FT/Iter-Ens | 0.714 | 0.789 | 57 | -0.157 |

## Table 21: Cross-linguistic Comparison of Loaded_Language (Paragraph-level)

| Language | F1 | Precision | Recall | Support |
|----------|-----|-----------|--------|---------|
| English | 0.938 | 0.905 | 0.974 | 78 |
| Polish | 0.883 | 0.791 | 1.000 | 34 |
| Russian | 0.864 | 1.000 | 0.761 | 46 |

## Table 22: Top 5 False Positives in Russian (Sup-FT, FP-only)

| Rank | Technique | FP Count | % of Total FP |
|------|-----------|----------|---------------|
| 1 | Loaded_Language | 400 | 19.5% |
| 2 | Doubt | 338 | 16.5% |
| 3 | Questioning_Reputation | 212 | 10.3% |
| 4 | Obfuscation-Vagueness | 185 | 9.0% |
| 5 | Conversation_Killer | 157 | 7.7% |
| **Top 2 Concentration** | | 738 | 36.0% |

## Table 23: Russian weak/failed techniques under extreme scarcity (support and qualitative note)

| Technique | Support | Note |
|-----------|---------|------|
| Appeal_to_Authority | 1 | Complete failure under low support |
| Red_Herring | 1 | Complete failure under low support |
| Appeal_to_Time | 1 | Complete failure under low support |
| Appeal_to_Popularity | 2 | Unstable boundary under low support |
| Whataboutism | 4 | Culture/context dependent; scarce evidence |
