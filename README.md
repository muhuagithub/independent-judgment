# Independent Judgment · 独立判断

让 AI 的认同、修正或反对来自事实和推理，而不是用户的措辞与期待。

一个轻量、零运行依赖的中文 Skill + 精简提示词。

[完整 Skill](skills/independent-judgment/SKILL.md) · [精简提示词](prompts/精简版提示词.txt)

## 这是什么

当用户问“是不是……”“也就是说……”“所以……”时，问题里往往已经包含一个结论。这份 Skill 引导 AI 把这个结论作为需要判断的信息，根据知识、证据和上下文决定是否认同、修正、限定或质疑。

核心原则：**用户的观点是需要判断的信息，而不是默认事实。**

它也要求回答保持校准：理解正确时直接确认，部分成立时只修正必要部分，证据不足时表达不确定性。不要为了表现独立而刻意反驳；简单且明确的问题可以直接回答。

## 快速开始

### 方式一：复制提示词

复制 [精简版提示词](prompts/精简版提示词.txt)，粘贴到你与 AI 的对话开头，再提出需要判断的问题。此方式不需要安装 Skill。

### 方式二：安装 Skill

以 Claude Code 的个人 Skill 目录为例，在终端执行：

```bash
git clone https://github.com/muhuagithub/independent-judgment.git
cd independent-judgment
mkdir -p ~/.claude/skills
cp -r skills/independent-judgment ~/.claude/skills/
```

安装后，在 Claude Code 中显式调用：

```text
/independent-judgment 准确率从 80% 到 84%，是不是提升了 4%？
```

Claude Code 也支持根据描述选择相关 Skill。安装位置与调用方式见 [Claude Code 官方文档](https://code.claude.com/docs/en/skills)。其他支持 Skill 的工具，请按其文档将整个 `skills/independent-judgment` 目录放入对应位置。

## 回答示例

以下为预期行为示意，不是实际模型评测结果。

| 情况 | 用户观点 | 预期判断 |
| --- | --- | --- |
| 正确 | “准确率从 80% 到 84%，提升了 4 个百分点，对吗？” | 直接确认，无须刻意补充反对意见。 |
| 错误 | “只要两个变量相关，就能证明其中一个导致另一个，对吗？” | 不能。相关性本身不能确立因果关系。 |
| 部分成立 | “准确率从 80% 到 84%，模型有提升，提升了 4%，对吗？” | 准确率有提升；绝对提升为 4 个百分点，相对提升为 5%。 |
| 证据不足 | “新版上线后投诉减少了，所以一定是新版让用户更满意了？” | 目前证据不足以确认因果关系，还需考虑使用量、用户构成和统计时间等因素。 |

## 原则速览

- 不因带有结论的措辞而默认认同。
- 对事实、逻辑、因果关系和概念解释独立判断。
- 只指出真正影响结论的不确定性、假设和边界条件。
- 正确时直接确认，不刻意寻找分歧。
- 部分成立时保留正确部分，只修正必要部分。
- 证据不足时不把可能性表达成事实。
- 回答深度与问题复杂度匹配，必要时才展开额外检查。

完整说明见 [SKILL.md](skills/independent-judgment/SKILL.md)。

## 仓库结构

```text
independent-judgment/
├── README.md
├── LICENSE
├── .gitignore
├── skills/
│   └── independent-judgment/
│       └── SKILL.md
└── prompts/
    └── 精简版提示词.txt
```

## 参考

仓库组织方式参考 [anti-defensive-writing-Skill](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill)：Skill、可直接复制的精简提示词与使用说明配套提供。

## 许可证

[MIT License](LICENSE)。
