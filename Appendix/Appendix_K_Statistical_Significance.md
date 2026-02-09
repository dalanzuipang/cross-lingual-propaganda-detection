# K SUPPORT-CONTROLLED SIGNIFICANCE CHECKS FOR ENGLISH VS. POLISH

**对应论文正文位置：**
- **Section 5.1** "High-Resource Paradox: Overview" - 本附录是该段落统计检验的详细数据
- 正文中直接引用："paired t-test: t = 0.90, df = 13, p = 0.384; Wilcoxon signed-rank test: p = 0.715"
- 正文中引用："A bootstrap estimate yields a 95% confidence interval of [−6.38%, 20.22%] with p = 0.508. The effect size is small (Cohen's d = 0.24)"

**内容说明：**
本附录提供English vs. Polish性能差异的完整统计显著性检验，通过控制technique support（≥5）来避免split-specific support effects的干扰，包括：
- Paired t-test结果
- Wilcoxon signed-rank test结果
- Bootstrap 95% confidence interval
- Cohen's d effect size

结论：在控制support后，Polish的优势缩小但仍然存在方向性差异，统计显著性较弱，但实践证据明确。

**对应正文位置：**
- **Section 5.1 "High-Resource Paradox: Overview"** (第4-5页)：正文提到"A robustness check controlling for technique support... paired t-test: t=0.90, df=13, p=0.384; Wilcoxon: p=0.715; Bootstrap CI: [-6.38%, 20.22%], p=0.508; Cohen's d=0.24"
- **Section 7 "English vs. Polish: Performance Comparison"** (第7页)：正文分析EN-PL gap的统计显著性

**说明：** 本附录提供了控制support≥5条件下的统计显著性检验完整结果。为了避免split-specific label coverage的影响，仅对14个在两种语言中都有足够样本的技术进行配对检验。结果显示Polish虽然方向性更高，但差异未达到常规统计显著性水平（effect size小，Cohen's d=0.24），说明部分headline gap由样本覆盖差异驱动。

To assess whether the English–Polish Macro F1 gap reflects systematic cross-technique advantages or split-specific support effects, we additionally restrict the comparison to techniques with adequate support in both languages (support ≥ 5 on the evaluated split). Under this restriction, the gap narrows relative to the headline comparison.

Across the 14 well-supported techniques, Polish remains directionally higher, but the difference does not reach conventional statistical significance under paired tests (paired t-test: t = 0.90, df = 13, p = 0.384; Wilcoxon signed-rank test: p = 0.715). A bootstrap estimate yields a 95% confidence interval of −6.38%, 20.22% with p = 0.508. The effect size is small (Cohen's d = 0.24), suggesting practical but weak evidence given limited test support.
