# Suno Songcraft

面向 Suno 的歌曲创作与提示词工程 Skill。它可以把一个主题、故事、歌词草稿、参考曲或试听反馈，整理成可直接用于 Suno 的 `Lyrics` 与 `Style`，并在多轮生成中持续修正歌词、结构、演唱、编曲和混音方向。

它既面向音乐小白，也支持已经能描述 BPM、调式、配器和制作要求的创作者。

## 能做什么

- 从零创作中文或其他语言的完整歌曲。
- 改写、润色或重新组织已有歌词。
- 只添加歌曲结构、气口和元标签，不改动原词。
- 分析参考曲的结构、情绪曲线、Hook、叙事和制作机制。
- 生成并协调 Suno 的 `Lyrics` 与 `Style` 字段。
- 控制气口、人声重叠、转调、调外音、转音、和声层与段落能量。
- 根据音频、Suno 链接、视频、时间点或文字反馈进行版本化迭代。
- 优化中文歌词的口语感、具体性、人物声音和“人味”。

## 小白用户会经历什么

如果只给出“按照今天北京的天气写首歌”这类宽泛主题，Skill 不会立刻替用户决定全部音乐方向。它会先把主题转换成两到四个容易理解的方向，例如城市轻快、温柔治愈或夜行情绪，再请用户选择、组合或补充参考曲。

满足下列任意情况后才会进入完整生成：

- 用户已经确认至少两个创作锚点，例如用途、核心表达、情绪、参考曲、风格、结构或演唱方向。
- 用户明确说“直接写”“不用问”或“先出一版”。

这样可以减少看似完整、实际上抓不到用户审美重点的泛化歌曲。

## 安装

### 方式一：让 Codex 安装

在 Codex 中发送：

```text
请安装这个 Skill：
https://github.com/2253313452why-eng/suno-songcraft/tree/main/skills/suno-prompt-engineer
```

安装完成后，在下一轮对话或新任务中使用。

### 方式二：使用 Skill Installer

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo 2253313452why-eng/suno-songcraft \
  --path skills/suno-prompt-engineer
```

默认安装到 `~/.codex/skills/suno-prompt-engineer`。如果目标目录已经存在，安装程序会停止，避免覆盖本地版本。

### 方式三：手动安装

```bash
git clone https://github.com/2253313452why-eng/suno-songcraft.git
mkdir -p ~/.codex/skills
cp -R suno-songcraft/skills/suno-prompt-engineer ~/.codex/skills/
```

仓库也包含完整的 Codex 插件清单，但 `codex plugin add` 需要先配置对应 Marketplace。没有 Marketplace 时，优先按上面的独立 Skill 方式安装。

## 如何调用

可以显式调用：

```text
$suno-prompt-engineer 帮我写一首关于毕业后留在北京的歌。
```

也可以直接用自然语言描述任务。安装成功后，涉及 Suno、歌曲创作、歌词改写、Style、元标签、参考曲分析或试听迭代的需求都可以触发该 Skill。

## 常用方法

### 从零创作

```text
$suno-prompt-engineer 我想写一首送给毕业生的中文歌，情绪从迷茫走向坚定，参考城市流行摇滚，使用容易传播的常规结构。
```

如果想跳过确认：

```text
$suno-prompt-engineer 不用问，先按温柔城市民谣写一版。男声，克制，不要大幅转调。
```

### 优化已有歌词

```text
$suno-prompt-engineer 按 L1 优化下面的歌词，保留故事、视角、核心句和事实，只修复生硬语序、重复和局部押韵。

（粘贴歌词）
```

改写权限分为：

- `L0`：只加结构、标点、气口和元标签，不修改歌词文字与顺序。
- `L1`：保守润色，修复局部语序、节奏、重复和押韵。
- `L2`：允许重排段落、改写部分句子并强化 Hook。
- `L3`：深度重写，只保留用户明确指定的主题、事实或保护句。

用户只说“优化一下”时，默认采用 `L1`。

### 只做结构和元标签

```text
$suno-prompt-engineer 对这份歌词执行 L0：一个字都不要改，只加入适合 Suno 的段落结构、气口、停顿和局部元标签。
```

### 分析参考曲

```text
$suno-prompt-engineer 分析这首参考曲为什么好听。重点拆解歌曲结构、Hook 进入位置、歌词意象、情绪推进和编曲层次，再转化成不构成复制的新歌方案。

（歌曲名称、版本、链接、音频或视频）
```

Skill 只迁移结构、情绪曲线、意象策略、律动、编曲和制作机制，不复制原歌词、旋律、标志性短句或歌手身份特征。

### 根据试听结果迭代

```text
$suno-prompt-engineer 这是 V1 的试听结果：
00:42 副歌进得太平；
01:18 第二段没有气口；
结尾转音太多。

保留主歌配器、歌词主题和主唱音色，只修改相关变量。
```

每轮通常只调整一到三个相关变量，并说明保留项、修改项和预期听感，避免一次堆叠过多限制。

## 默认歌曲结构

面向小白的首版传播型歌曲通常采用：

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Pre-Chorus]
[Chorus]
[Outro]
```

`Bridge` 只用于后段的一次性反转、领悟或能量突破，不会被当作每次副歌前的普通过渡段。如果用户提出可行的创新结构，则优先采用用户结构。

## 中文歌词标准

中文歌词模块会特别检查：

- 是否存在明确的说话者、对象、场景和动作。
- 是否用身体反应、行为和物件代替空泛情绪标签。
- 中文语序是否自然，是否为了押韵强行倒装。
- Verse 2 是否真正增加事实、后果或新的理解。
- Hook 是否口语化、好记、能代表全歌。
- 不规则短句、停顿和省略是否有角色与演唱功能。
- 结尾是否回收或改变前面出现过的细节。
- 歌词是否保留了用户有辨识度的表达，而不是被统一润色成“标准 AI 文风”。

真实经历不会被擅自补写。虚构细节只在歌曲明确属于虚构创作或用户允许创意补全时使用。

## 输出形式

完整创作通常返回：

```text
歌名

Lyrics
完整歌词、结构、气口与局部元标签

Style
英文的曲风、情绪、速度感、和声、配器、人声、动态与混音方向
```

可以直接粘贴的内容会放在干净的代码块中，解释、假设和修改说明放在代码块外。

## 重要说明

- Suno 对提示词的执行具有概率性。Skill 会提高目标结果出现的倾向，但不能保证精确音符、时长、音色身份或每次生成完全一致。
- 参考曲用于抽象机制分析，不应被用于复制受保护的歌词、旋律或标志性表达。
- Style 与元标签应被视为协同控制，而不是绝对控制命令。

## 目录结构

```text
suno-songcraft/
├── .codex-plugin/
│   └── plugin.json
└── skills/
    └── suno-prompt-engineer/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── chinese-human-lyrics.md
            ├── interaction-workflow.md
            ├── lyrics-formatting.md
            ├── lyrics-writing.md
            ├── output-contracts.md
            ├── prompt-library.md
            ├── reference-analysis.md
            └── style-prompting.md
```

## 方法来源

中文“人味”歌词模块参考了 KKKKhazix 的 [`khazix-writer`](https://github.com/KKKKhazix/khazix-skills/tree/main/khazix-writer) 中关于真实素材、身体化情绪、口语节奏、回环和分层自检的方法，并重新适配为歌词创作规范。没有复制作者的个人身份、固定口头禅或公众号文章格式。
