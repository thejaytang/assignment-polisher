# Optional Local Profile Contract

这个 skill 支持公开用户自带 profile，但 profile 永远是可选的。

如果用户显式提供一个本地目录路径，可按下面约定读取；如果目录缺失或文件不全，不要报错中断，只读取实际存在的部分。

## Expected Layout

```text
user-profile/
├── style-profile.md
├── term-bank.md
└── samples/
    ├── sample-01.md
    ├── sample-02.md
    └── ...
```

## `style-profile.md`

这个文件用于描述稳定文风偏好，建议包含：

- 目标语言或常用语言组合。
- 语气强弱，例如克制、直接、温和、简洁。
- 常见句长偏好。
- 段落推进习惯，例如先判断后展开，还是先例子后结论。
- 明确禁用表达。
- 明确偏好表达。
- 是否接受较强的 **Tacit Knowledge** 风格，也就是更少“说理铺陈”、更多“判断内嵌在写法里”。

建议写成短段落或简单清单，不需要复杂格式。

## `term-bank.md`

这个文件用于记录课程或专业术语，建议包含：

- 核心术语。
- 首选英文写法。
- 可接受中文对译。
- 禁用替代词。
- 特定课程、导师或学科里的特殊用法。

如果某个术语有多种合法写法，应明确哪一种是首选，避免模型自行摇摆。

## `samples/`

这个目录放用户自己的写作样本，只接受 `.md` 或 `.txt` 一类纯文本样本。

样本建议满足：

- 真实出自用户本人。
- 与当前任务语言一致或接近。
- 质量不低于当前任务要求。
- 不要放太短的片段，最好每份都有完整段落。

## Reading Rules

使用 profile 时遵循这些规则：

- `term-bank.md` 只影响术语与词汇层面，不直接决定段落结构。
- `style-profile.md` 和 `samples/` 共同影响 **voice-profile**。
- `samples/` 的证据强于 `style-profile.md` 的抽象自述；如果两者冲突，优先相信样本文本。
- 如果样本质量明显偏弱，只借用稳定风格信号，不复制明显缺点。

## Privacy and Public Distribution

因为这是公开 skill，仓库本身不应包含任何私人 profile 或私人语料。

这个约定只是告诉用户：如果他们想获得更稳定的个性化效果，可以在本地自备 profile，并在使用时显式提供路径。
