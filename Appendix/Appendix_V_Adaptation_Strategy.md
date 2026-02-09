# V EXTENDED NOTES ON TECHNIQUE–LANGUAGE–METHOD ADAPTATION

**对应论文正文位置：**
- **Section 8.3** "Multi-Method Strategy Selection Guide" - 特别是"Method Adaptability Insight"段落
- 正文中提到："Language–technique routing can be used: use a default method per language, but switch methods for a small set of techniques where another paradigm is consistently better (e.g., Doubt in Russian)"

**内容说明：**
本附录详细展开technique-language-method路由策略的实际例子：
- **Polish**: 默认使用Sup-FT，但对Doubt可切换到Prompt-A（0.857 vs 0.831）
- **English**: 默认使用Sup-FT，但需对Loaded_Language进行后处理，保守场景使用Iter-Ens
- **Russian**: 默认使用Sup-FT，但对Doubt切换到Iter-Ens（0.907 vs 0.849）

**验证需求**：正文强调"Further validation is required to evaluate generalization and cost–benefit trade-offs"

**对应正文位置：**
- **Section 8.3 "Multi-Method Strategy Selection Guide" - Method Adaptability Insight** (第8页)：正文提到"Language–technique routing can be used: use a default method per language, but switch methods for a small set of techniques where another paradigm is consistently better (e.g., Doubt in Russian)"
- **Section 9 "Discussion"** (第8-9页)：正文提到"technique-level routing strategies"

**说明：** 本附录提供了technique-language-method路由策略的具体实例，包括：为Polish、English、Russian分别设定默认方法，针对特定技术切换方法（如Russian的Doubt使用Iter-Ens），以及基于置信度的fallback机制。这些策略需要在新领域上验证泛化能力和cost-benefit权衡。

As a practical direction, multilingual personalization can explore a "technique–language–method" adaptation strategy. For example, one may prioritize Sup-FT for Polish as a balanced default, while applying stricter thresholds for Obfuscation-Vagueness-Confusion; for English, retain Sup-FT where it is strong (e.g., Loaded_Language) but suppress over-triggering via post-processing; for Russian, treat Doubt as a candidate for specialized routing (e.g., Iter-Ens) while using Sup-FT as the default for other techniques. Such rules require validation on new domains and explicit evaluation of inference cost, especially for multi-round ensembling.
