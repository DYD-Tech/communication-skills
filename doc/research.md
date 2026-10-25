# AI / agent 写作调研

调研日期：2026-10-24。范围：面向任务的回复、说明、文档、注释和交接；文学创作只作为对照，不将其审美要求普遍化。

## 方法与证据边界

本轮为定性调研，目的是发现问题和形成可检验的规则，不是统计所有模型的问题发生率。使用中英文检索，组合了 `AI writing complaints verbosity jargon metaphors`、`ChatGPT writing patterns`、`AI 中文 写作 黑话 空话 套话`、`LLM rhetorical styles`、`format bias` 和 `plain language technical terms` 等关键词。

优先采用研究作者发布的摘要与论文页面、官方写作指南；社区帖子用于识别真实读者的不满，中文评论用于补充语言环境。排除了广告型“降 AI 率”工具的效果宣传，不把“看起来像 AI”当成质量判断或作者身份鉴定。研究论文本轮主要核对摘要及官方页面，未复现其数据与实验。

来源分为四类：

- **U：用户需求。** 本项目发起者在 2026-10-24 提出的具体问题与目标，是设计约束，不是总体统计。
- **R：研究证据。** 支持其研究范围内的结论，不能无条件推广到所有模型、语言或任务。
- **G：写作指南。** 提供可借鉴的实践原则，不能单独证明某种缺陷在 AI 中普遍存在。
- **C：社区或评论。** 说明有人遇到、在意这些现象，不据此推断发生率或技术成因。

问题清单中的 **D** 表示本项目据上述材料作出的设计推论，尚待使用和评测检验。来源编号的支持范围如下；它们不是整份清单每个判断的背书。

## 研究证据

### R1：不同模型有不同语言风格

[Do LLMs write like humans? Variation in grammatical and rhetorical styles](https://arxiv.org/abs/2410.16107)，Reinhart 等，2024 年首版，2025 年修订并发表于 PNAS。

作者比较 Llama 3 与 GPT-4o 的多个变体及人类文本，观察到语法与修辞特征存在系统差异。这支持“不能假定所有模型的表达习惯相同”。它不证明本技能能够统一这些差异，也不能替代中文任务的实测。用途：设置跨模型、跨文体评测。

### R2：评判可能偏爱篇幅与格式

[From Lists to Emojis: How Format Bias Affects Model Alignment](https://aclanthology.org/2025.acl-long.1308/)，Zhang 等，ACL 2025。

研究报告了对列表、链接、加粗、表情等格式的偏好，以及对长回答的偏好；这些偏好可能与内容质量分离。用途：评测中把正确性、理解效果与排版分开，不能把更长、更工整直接判为更好。不据此声称列表或长回答本身有害。

### R3：迎合可能损害真实性

[Towards understanding sycophancy in language models](https://www.anthropic.com/research/towards-understanding-sycophancy-in-language-models)，Sharma 等，2023-10-23。

研究在五个助手、四类生成任务中观察到迎合行为，并分析偏好反馈与迎合的关联。用途：把“尊重读者”与“同意读者”分开；错误前提需要纠正。研究的模型和任务范围有限，不用于评价当前所有模型。

### R4：中间推理表达与任务表现的关系

[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://doi.org/10.48550/arXiv.2201.11903)，Wei 等，2022 年首版，2023 年修订。

研究在特定模型和算术、常识、符号推理任务中发现，中间推理示例有助于任务表现。这只能说明某类提示方法可能有效，不能推出“文风更好就一定推理更强”。本项目仅将清晰工作记录对后续任务的帮助作为待验证假设，不要求公开内部思维过程。

## 写作指南

### G1：术语、读者需求与名称一致性

[ONS：Writing and editing — Plain language](https://service-manual.ons.gov.uk/content/writing-for-users/plain-language)。页面未显示稳定发布日期，2026-10-24 检索。

指南强调按读者需要选取内容、解释必要技术词汇、保持概念名称一致。本项目据此采用按上下文解释术语的规则；不机械照搬英文缩写的形式要求。

### G2：通俗表达可以保留复杂内容

[Australian Government Style Manual：Plain language and word choice](https://www.stylemanual.gov.au/writing-and-designing-content/clear-language-and-writing-style/plain-language-and-word-choice)。2026-10-24 检索。

指南指出通俗语言可以表达复杂思想，专业词与缩写应结合受众使用。用途：避免把“外行能懂”误解成删除所有术语，也不把展开英文全称当作充分解释。

### G3：结构与阅读目的

[Australian Government Style Manual：Quick guide — plain language](https://www.stylemanual.gov.au/style-manual-resources/quick-guides/quick-guide-plain-language)。2026-10-24 检索。

指南建议优先呈现重要信息、一段处理一个主题，并按内容选择列表。用途：确定阅读顺序。其英文句长建议不直接转换为中文硬性字数限制。

## 社区与中文讨论

### C1：技术回答中的不必要比喻

[Why is ChatGPT suddenly using so many metaphors in replies?](https://www.reddit.com/r/ChatGPT/comments/1op5z3b/why_is_chatgpt_suddenly_using_so_many_metaphors/)，Reddit，检索结果标注 2025-11-05，2026-10-24 访问。

发帖者希望技术问题得到直接回答，讨论中也有人反映比喻冗长、语气变化及纠正后反复出现。用途：设计“直接解释优先”和多轮保持测试。帖子中的更新归因未经核实，不采纳为事实。

### C2：碎片化格式和列表泛滥

[I hope someone from OpenAI sees this post to fix the writing style of chatGPT](https://www.reddit.com/r/OpenAI/comments/1up6crk/i_hope_someone_from_openai_sees_this_post_to_fix/)，Reddit，2026-07-06；本轮依据检索返回的帖子与评论片段。

讨论提到单词单独成行、列表套列表及长对话中的风格回退。用途：补充可读性和多轮稳定性测试。它没有证明所有版本均存在该问题。

### C3：明确要求简短后仍然冗长

[Why does chatgpt write so g*ddamn much?](https://www.reddit.com/r/ChatGPT/comments/1x5lpjj/why_does_chatgpt_write_so_gddamn_much/)，Reddit，2026-10-14；本轮依据检索片段。

记录读者对篇幅不服从要求的抱怨。用途：测试明确字数限制下是否仍能保留关键含义。单条反馈不能比较不同模型的优劣。

### C4：套路句式与装饰过多

[What GPT writing patterns annoy the hell out of you?](https://www.reddit.com/r/ChatGPT/comments/1qyou8d/what_gpt_writing_patterns_annoy_the_hell_out_of/)，Reddit，2026-02-07；本轮依据检索片段。

讨论指出反复的对照句、自问自答和密集强调格式。用途：检查无信息增量的修辞，不建立禁词表。

### C5：中文表达中的空泛和模板化

[智能写作的“AI味”问题](https://www.cssn.cn/skgz/bwyc/202607/t20260703_6057355.shtml)，简圣宇，中国社会科学报，2026-07-03。

文章描述空泛内容、固定衔接词、模板结构和重复收尾。本项目只采纳这些可观察的评论线索；文章把模型生成概括为必经外部检索流程等技术断言，不作为本项目的技术依据。“减少比喻”也不与其文学表达诉求混为一谈。

## 综合判断

调研支持把注意力放在读者能否理解内容，而非消除几个所谓“AI 特征”。R1 提供跨模型差异的证据，R2 提醒评测不能被格式或篇幅影响，R3 提醒流畅、友好可能掩盖不真实；G1–G3 为清晰表达提供实践参考，C1–C5 补充读者具体反感的现象。

以下仍是待验证的项目假设：

1. 按上下文解释术语，能同时改善理解和术语学习，而不过度增加篇幅。
2. 稳定的沟通原则能减少不同模型的质量差异，同时保留任务所需文体。
3. 清晰的可见工作记录能改善交接和后续任务表现。

本轮不足：社区样本偏向英文 ChatGPT 用户；中文直接用户反馈较少；研究多基于较早模型；未做用户理解实验。后续优先收集真实中文失败案例和不同模型的同题输出，而不是继续堆叠风格禁令。

## 2026-10-25 补充：已有材料对表达和维护的影响

新增查阅上下文风格学习、作者风格模仿研究，以及小规模变更的工程指南。来源、支持范围和不支持的推论统一记录在 [已有材料设计](existing-material.md) 的“研究依据及边界”中。它们支持把上下文风格影响视作需要测试的风险，不支持“旧文档必然抵消技能”或“必须先清理全库”的结论。
