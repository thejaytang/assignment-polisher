# Workflow Notes

## Purpose

这个文件补充 `SKILL.md` 中没有展开的决策规则。它不是另一份说明书，而是给 skill 使用时的判定依据。

## Resolution Order

处理顺序固定如下：

1. 先确认任务模式：**polish**、**polish+notes** 或 **critique**。
2. 再从用户输入构造 **term-bank** 和 **voice-profile**。
3. 先做术语一致性处理，再做句法和段落层面的文风调整。
4. 最后专门做 **Humanization Pass** 和 **Tacit Knowledge Pass**。

不要把这些步骤打乱。原因很简单：术语准确性是硬约束，风格只是软约束；先把软约束做满，再回头补硬约束，通常会破坏语气和连贯性。

## Conflict Rules

### 课程术语 vs 用户样本

- 词汇层面，课程术语优先。
- 句法和段落层面，用户样本优先。
- 如果用户样本里反复使用了不准确术语，也不要照搬。

### 样本质量偏弱

如果用户样本明显比课程要求弱，不要机械复制其缺点。此时应当：

- 保持术语准确。
- 只借用稳定可取的风格特征，例如简洁程度、句长、段落推进方式。
- 不复制明显问题，例如口水化、逻辑跳步、空泛连接、错误用词。

### 材料不足

如果没有足够样本，不要假装学到了个人文风。应退回：

- 朴素。
- 自然。
- 不过度修饰。
- 不模板化。

换句话说，宁可保守，也不要假装个性化。

## Humanization Heuristics

当文本有明显 AI 感时，优先检查这些信号：

- 每句都“完整且端正”，几乎没有节奏变化。
- 过渡词堆得太密，例如不断重复 “however”, “moreover”, “in conclusion” 一类结构。
- 段落都按同一模板推进，像列表改写成段落。
- 明明一个局部判断就够，却非要补成一整套抽象论证。
- 词汇看似高级，但缺少真实语境中的取舍感。

对应处理方法：

- 合并或打断过于整齐的句群。
- 删除低信息量过渡。
- 让段落推进更像真人写作中的“抓重点”，而不是平均用力。
- 把抽象总结压缩成具体判断或局部例子。

不要通过故意制造口语错误、俚语或拼写波动来“伪装成人”。

## Tacit-Knowledge Rules

这里参考的是 Polanyi 的 **Tacit Knowledge** 方向，即熟练判断常常先体现在写法和取舍里，而不是先被完整说成规则。

在输出里，这意味着：

- 允许出现“我知道这个地方该怎么收，但不需要再写一整段解释”的节制。
- 允许把经验判断放进措辞，而不是单独抽象总结。
- 允许适度保留未完全形式化的判断，但不能牺牲可读性。

这里不意味着：

- 假装自己真的上过这门课。
- 伪造第一手经验。
- 编造导师偏好、课堂共识或引用来源。

## Public-Use Constraint

这是一个公开 skill，不是私人写作替身。

因此默认假设应当是：

- 仓库不存放私人语料。
- 用户语料来自当次输入，或来自用户自己显式提供的本地 profile 路径。
- 如果用户不给样本，就不要伪装成“已经学过他/她的风格”。

## Design Basis

这些文献和官方文档支持了当前工作流设计：

- OpenAI, Model optimization
  - https://developers.openai.com/api/docs/guides/model-optimization
  - 支持“清晰指令、上下文、示例、eval loop”优先。
- Anthropic, Prompting best practices
  - https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
  - 支持结构化上下文、显式角色、few-shot 风格控制。
- Liu and Chang, *Writing Like the Best: Exemplar-Based Expository Text Generation*, ACL 2025
  - https://aclanthology.org/2025.acl-long.1250.pdf
  - 支持先抽取 exemplar 结构与写法，再适配新文本，而不是直接机械模仿。
- Bogoychev and Chen, *Terminology-Aware Translation with Constrained Decoding and Large Language Model Prompting*, WMT 2023
  - https://aclanthology.org/2023.wmt-1.80.pdf
  - 支持显式术语约束和二次 refinement。
- Routledge Encyclopedia of Philosophy, *Knowledge, tacit*
  - https://www.rep.routledge.com/articles/thematic/knowledge-tacit/v-1
  - 支持“知多于能言尽”的写作取向。
- Messingschlager and Appel, *I, ChatGPT*, Nature Humanities and Social Sciences Communications, 2025
  - https://www.nature.com/articles/s41599-025-06341-2
  - 支持通过视角感、自然变异和节奏控制降低 AI 感。
