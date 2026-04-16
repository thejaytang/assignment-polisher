---
name: assignment-polisher
description: Polish student assignments, essays, reports, and submission text by aligning terminology to user-provided course excerpts, adapting to user-provided writing samples, reducing generic AI phrasing, and applying Polanyi-inspired tacit-knowledge constraints. Use when the user wants style adaptation or critique from text excerpts, not when they need PDF parsing, OCR, or file extraction.
---

# Assignment Polisher

## Overview

这个 skill 只处理学生作业文本的风格调整，不处理 PDF 读取、OCR、文件解析或素材抽取。

它的目标有四个：根据课程材料对齐专业术语，根据过往样本贴近用户文风，降低通用 AI 文本的机械感，并在表达上加入更接近人类实践判断的 **Tacit Knowledge** 气质，同时严格避免虚构经历、来源或事实。

## When To Use

在这些场景触发这个 skill：

- 用户要润色 assignment、essay、report、submission text。
- 用户希望术语更贴近课程、导师或学科语境。
- 用户提供了过往写作样本，希望新文本更像自己写的。
- 用户明确说“减少 AI 感”“更像真人”“更自然”“别太像模板”。
- 用户只想要问题诊断，而不是直接改写。

不要把这个 skill 用在这些场景：

- 用户需要从 PDF、图片、扫描件中抽取文字。
- 用户没有给任何可读文本，只给文件本身。
- 用户要你补事实、补参考文献、补实验结果或伪造个人经验。

如果用户只给 PDF 或图片而没有可读文本，不要假装能处理。直接要求用户提供摘录、转写文本或关键片段后再继续。

## Inputs

必需输入：

- 待润色文本，或明确的改写目标。

可选输入：

- 作业要求摘录。
- 课程材料摘录。
- 过往写作样本。
- 用户本地 profile 路径。

支持中文和英文，也支持中英混合材料。输出语言默认跟随用户要求；若用户没有明确要求，则跟随原稿目标语言。

## Modes

这个 skill 固定支持三个模式：

- **polish**：只输出润色后的正文。
- **polish+notes**：先输出润色后的正文，再给简短说明。
- **critique**：不改写，只指出术语、风格、AI 感和表达问题。

若用户没有明确指定，默认使用 **polish**。

## Core Workflow

### 1. **Build Constraints**

先从用户输入中构造两个临时约束，而不是直接开始改写：

- **term-bank**：列出稳定术语、首选英文写法、可接受中文对译、禁用替代词。
- **voice-profile**：概括用户样本的句长分布、段落推进方式、语气强弱、连接习惯、是否喜欢先举例后判断、是否偏好克制或直接。

优先级固定如下：

- **term-bank**：用户 profile 中已有术语 > 当次课程材料 > 当前草稿中的稳定用法 > 通用学术写法。
- **voice-profile**：用户 profile 中已有风格 > 过往样本 > 当前草稿可保留部分 > 通用学术写法。

如果材料不足，不要声称“已经学会了用户风格”。这时只做保守润色，退回朴素、自然、不过度修饰的通用学术风格。

### 2. **Polish Pass**

先处理术语，再处理风格：

- 先统一关键术语，避免通俗化替换破坏专业准确性。
- 再调句法、段落节奏、语气和连接方式，让文本更接近 **voice-profile**。
- 保留原文中本来就自然、有效、可信的部分，不为了“润色”而全部重写。

如果术语要求与样本文风冲突，词汇层面服从课程术语，句法和段落层面优先贴近用户样本。

### 3. **Humanization Pass**

专门降低机械 AI 痕迹，重点处理这些问题：

- 机械对称句式。
- 空洞过渡词和模板化开场。
- 段落结尾反复总结。
- 每句都写得过满、过圆、过均衡。
- 全文节奏完全一致，像同一个模具压出来。

你要追求的是“像一个认真写作的人”，不是“像一个故意装得不像 AI 的人”。不要用花哨同义词堆砌，也不要靠故作口语化来掩饰。

### 4. **Tacit Knowledge Pass**

这里的目标不是神秘化，而是把 **Tacit Knowledge** 转成可执行写作约束：

- 允许保留少量不完全展开的判断，不把每一步理由都解释到尽。
- 优先把判断嵌入措辞、语气和段落推进，而不是额外补一层“方法论说明”。
- 允许句长和节奏有控制地波动，避免整篇同一模板。
- 适度使用“先给判断，再用一个局部理由或例子支撑”的方式。
- 可以体现熟练者的取舍感，但不能伪造亲身经历、课堂体验、引用来源、实验结果或个人偏好。

## Output Rules

默认只给最终结果，不先输出长篇分析。

当使用 **polish+notes** 时，说明部分应当简短，只覆盖真正重要的修改：

- 术语为什么统一成现在的写法。
- 文风是如何对齐样本的。
- 哪些机械 AI 表达被压掉了。
- 哪些地方为了避免虚构而保守处理。

当使用 **critique** 时，优先指出：

- 术语不一致。
- 语气和样本不一致。
- AI 感明显的模板化表达。
- 说得过满、过空或不自然的地方。

## Guardrails

- 不捏造用户经历、课程经历、研究经历或个人立场。
- 不补不存在的事实、数据、引用或案例。
- 不把不确定的术语硬说成确定标准。
- 不因为追求“真人感”而故意制造语病或低级错误。
- 不把“去 AI 感”理解成“加更多情绪化修辞”。

## References

需要更细的规则时，按需读取这些文件：

- `references/workflow.md`：冲突处理、输出决策、设计依据。
- `references/profile-contract.md`：可选本地 profile 的约定格式。
- `references/eval-cases.md`：人工复核场景与验收标准。
