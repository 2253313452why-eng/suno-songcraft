# Suno 原始提示词与元标签候选库

> 本文件完整保留项目原始资料，供检索流派、乐器、唱腔、音色、情绪、节奏、调式、混音、结构示例和组合范例。它是候选词库，不是当前工作流规范。

> 使用前先读取 `SKILL.md` 及对应的聚焦 reference。若本文件中的固定模板、标签数量、结构解释、可靠性判断、输出格式或创作规则与聚焦 reference 冲突，以聚焦 reference 为准。不要整篇加载；优先使用 `rg` 搜索章节标题或目标术语。不要把视觉词、记谱词、明显误译、重复项或标为低可靠性的条目直接当作 Suno 控制指令。

## 检索目录

- 第 7 节：核心结构与事件标签
- 第 9 节：地域风格、流派、结构、唱腔、声部、声线、音色、情绪、节奏、速度、乐器、技巧、语言、调式、旋律、伴奏、年代、混音与声场
- 第 10 节：普通音乐术语中英文参考
- 第 11 节：来源中的结构示例与补充标签
- 第 12 节：风格组合范例库
- 第 13 节：原始自检清单（仅作历史参考）

## 原始资料正文

# SUNO 提示词与歌词元标签统一规范

> 用途：作为语言模型的外部知识库/外挂提示词。模型应依据本规范，生成可以分别直接粘贴进 SUNO「歌词栏（Lyrics）」和「Style 栏」的内容。

> 最高原则：SUNO 音乐创作需要填写两个栏。歌词栏负责歌词、歌曲段落划分和符合各段音乐特点的局部元标签；Style 栏负责按照固定模板描述全曲风格、编曲、人声与混音。两个栏必须互相配合，不能混写。

## 1. 语言模型角色

你是一名 SUNO 提示词工程助手。你的任务是理解歌词的结构、叙事、情绪、演唱方式和编曲目标，然后分别制作两个可直接使用的输入栏：

1. 保留用户原歌词，不擅自改写歌词内容，除非用户明确要求。
2. 在「歌词栏」中加入 `[Verse]`、`[Chorus]`、`[Bridge]` 等段落划分。
3. 在「歌词栏」各段中加入少量符合该段音乐特点的英文元标签，例如唱腔、乐器、动态、节奏或音效标签。
4. 按照本文件规定的固定编写模板制作「Style 栏」，描述全曲的风格、情绪、调式、乐器、编曲、混音和人声。
5. 确保歌词栏的局部元标签与 Style 栏的全局音乐设计一致。
6. 避免堆砌标签、互相矛盾的标签，以及把普通术语误当成可靠控制指令。
7. 用户信息不足时，采用保守且相互兼容的默认值。

## 2. SUNO 两栏职责

| 输入栏 | 必须填写的内容 | 不应填写的内容 |
| --- | --- | --- |
| 歌词栏（Lyrics） | 原歌词；`[Verse]`、`[Chorus]`、`[Bridge]` 等段落划分；符合各段音乐特点的局部元标签 | 长篇全曲风格说明、混音说明、解释文字 |
| Style 栏 | 按固定模板编写的全曲风格、情绪、调式、乐器、演奏、编曲、人声、混音和声场说明 | 完整歌词、逐句段落标签、与歌词栏矛盾的要求 |

### 2.1 歌词栏内部层级

| 层级 | 作用 | 推荐形式 | 可靠性 |
| --- | --- | --- | --- |
| 歌曲段落标签 | 划分 Intro、Verse、Chorus、Bridge 等段落 | `[Verse 1]` | 高 |
| 局部音乐元标签 | 指示某一段的唱法、乐器、动态、节奏或音效 | `[Whispered Vocal]`、`[Guitar Solo]` | 中，需少量使用 |
| 普通音乐术语 | 辅助模型理解和组合提示词，不保证直接控制 SUNO | `syncopation`、`legato` | 视上下文而定 |

## 3. 强制书写规范

### 3.1 标签语法

- 元标签统一使用英文半角方括号：`[Tag]`。
- 每个结构标签必须单独占一行，放在其控制内容之前。
- 标签使用简洁、自然的英文；优先使用 1 至 4 个词的短语。
- 不在一个方括号中写长句、解释、中文翻译或多个互相独立的命令。
- 同一段落局部标签建议不超过 2 个；全篇非结构局部标签建议不超过 6 个。
- 同一种效果不必在每段重复；只在效果开始或明显变化时标注。
- 不确定某标签是否可靠时，将该要求写入 Style 栏，而不是强行嵌入歌词。

### 3.2 歌词栏开头的全局元标签

歌词栏开头可以放置一行全局元标签，用于快速建立歌曲方向。按照原编写模板，最多使用 5 个，推荐顺序为：

```text
[Style] [Vocal Tone] [Mood] [Vocal Style] [Mode/Key]
```

示例：

```text
[Mandopop Ballad] [Warm Female Vocal] [Melancholic] [Expressive Singing] [Minor Key]
```

注意：歌词开头的全局元标签只是摘要，不能代替 Style 栏。若标签过多或与 Style 栏重复严重，可以省略。

### 3.3 推荐歌曲结构

```text
[Intro]

[Verse 1]
歌词……

[Pre-Chorus]
歌词……

[Chorus]
歌词……

[Instrumental Interlude]

[Verse 2]
歌词……

[Pre-Chorus]
歌词……

[Chorus]
歌词……

[Bridge]
歌词……

[Final Chorus]
歌词……

[Outro]

[End]
```

- 结构应依据歌词实际内容增删，不要为了完整而强行添加空段。
- `Interlude` 可用于给两部分歌词之间留出器乐气口。
- 纯音乐前奏优先写 `[Instrumental Intro]`，纯音乐间奏优先写 `[Instrumental Interlude]`。
- `[End]`、`[Fade Out]` 只能提高结束倾向，不能保证模型精确服从。

### 3.4 局部标签嵌入格式

局部标签放在它要控制的段落标题之后、歌词之前；若只控制一个短语，可紧邻该短语之前单独占行。

```text
[Bridge]
[Whispered Vocal]
[Sparse Piano]
我把最后一句话，留在没有灯的房间

[Final Chorus]
[Powerful Belting]
[Full Band Build]
让所有沉默，在这一刻被听见
```

可组合的局部控制维度：演唱方式、主导乐器、动态变化、节奏变化、空间/效果音。每次只选择真正影响该段的维度。

### 3.5 Style 栏固定编写模板

Style 栏必须按照 `SUNOprompt编写规范.xlsx` 中的模板制作，描述全曲，而不是复述歌词。除非用户明确要求其他格式，否则必须依照以下顺序编写：

```text
This is a [风格] song with [情绪] in a [调式] key.
It opens with [主导乐器及开场方式], blending [辅助乐器、铺底和弦或声音纹理] that remains [演奏技巧或持续状态].
[说明后续需要哪些乐器，以及各乐器使用什么方式演奏和如何推动编曲。]
[说明立体声、声场、空间感和混音需要呈现什么效果。]
The vocal is a [性别/声部] vocal with a [音色] tone, delivered in a [唱腔/演唱技巧] style with [人声情绪].
[按需追加音质约束或纯音乐约束。]
```

Style 栏各句的职责：

| 顺序 | 必须描述的内容 | 示例 |
| --- | --- | --- |
| 1 | 风格 + 情绪 + 调式 | `This is a Mandopop ballad with a melancholic atmosphere in a minor key.` |
| 2 | 开场主导乐器 + 辅助乐器/铺底 + 演奏状态 | `It opens with soft piano, blending warm string pads that remain restrained and sustained.` |
| 3 | 后续乐器、演奏方式与编曲推进 | `Fingerpicked acoustic guitar enters in the verse, while restrained drums gradually build toward the chorus.` |
| 4 | 立体声、声场、空间感与混音 | `The mix is clean and spacious, with a wide stereo field, gentle hall reverb, and distinct instruments.` |
| 5 | 人声性别/声部 + 音色 + 唱腔/技巧 + 情绪 | `The vocal is a warm female vocal with a clear tone, delivered with intimate phrasing and controlled emotional belting.` |
| 6 | 按需追加固定约束 | 清晰乐器或纯音乐约束 |

Style 栏约束：

- 必须优先遵守上述模板顺序，不能只输出若干零散关键词。
- 优先使用连贯英文短句；建议 60 至 140 个英文单词。
- 风格、情绪、调式、乐器、演奏技巧、人声和混音必须相互兼容。
- 乐器不仅要列名称，还必须说明其角色、演奏方式或进入位置，例如 `fingerpicked acoustic guitar enters in the verse`。
- Style 栏描述全曲常态；某一段才出现的特殊变化同时在歌词栏中添加对应局部元标签。
- 需要清晰乐器分离时，可在结尾加入：`All instruments are pure, balanced, and distinct, with no distortion, no harshness, and no ambient noise.`
- 纯音乐必须在结尾加入：`There is no vocal present.`
- 避免在 Style 栏中大量使用方括号；自然英文描述通常更清晰。

## 4. 标签选择决策流程

1. 分析用户歌词和音乐要求，先确定全曲的风格、情绪、调式、编制、人声和混音方向。
2. 制作歌词栏：识别歌词段落并补齐 `[Verse]`、`[Chorus]`、`[Bridge]` 等结构标签。
3. 判断每一段是否存在明确的局部音乐变化，例如耳语、独奏、骤停、渐强。
4. 只给明确变化添加局部元标签；全曲常态要求放入 Style 栏。
5. 按 3.5 节固定模板制作 Style 栏，不能遗漏编曲、混音或人声描述。
6. 检查两个栏是否冲突，例如歌词栏要求 `[Whispered Vocal]` 的段落不应被 Style 栏描述为全程强力喊唱。
7. 检查标签密度；标签数量若接近歌词行数，必须删减。

## 5. 标准输出合同

语言模型默认只输出 SUNO 需要填写的两个栏，并确保两个代码块可分别直接粘贴。不要在代码块中加入解释：

````markdown
## 歌词栏（Lyrics）

```text
[Verse 1]
[符合该段音乐特点的局部元标签]
歌词……

[Chorus]
[符合该段音乐特点的局部元标签]
歌词……
```

## Style 栏

```text
按照 3.5 节固定模板编写的完整英文 Style 描述……
```
````

只有用户要求解释时，才在两个代码块之后追加简短设计说明。

## 6. 禁止事项与低可靠项

- 禁止把整份术语词库中的每个 `[term]` 都当成可靠的 SUNO 歌词元标签。
- 禁止在每句歌词前添加情绪、乐器或唱法标签。
- 禁止同时堆叠近义词，例如 `[Sad] [Melancholic] [Sorrowful] [Mournful]`。
- 禁止用标签要求 SUNO 做无法从音频表达的内容，例如封面构图或纯视觉风格。
- 方言、特色语言和部分中国传统乐器在不同模型版本中的服从度可能较低，应视为实验项。
- 原资料标注“唢呐不生效”和“特色语言大部分不生效”；这类需求应给出备选英文描述，并提醒用户需要试生成。
- `Lip-sync`（假唱）不是有意义的音频生成唱腔控制词，不应使用。
- 普通记谱术语如 `treble clef`、`bar line`、`whole note` 通常不适合作为歌词内标签。

## 7. 核心歌词结构与事件标签

以下标签来自元标签资料，并对明显误译进行了纠正。它们比普通术语更适合直接嵌入歌词。

| 标签 | 中文 | 用途与注意事项 |
| --- | --- | --- |
| [Verse] | 主歌 | 通常节奏性强且克制，相比副歌部分旋律性和能量感较弱。 |
| [Chorus] | 副歌 | 通常是歌曲的副歌，重复出现时会让歌曲感觉更有意图和情感。 |
| [Pre-Chorus] | 预副歌 | 用于主要模式之外的零散歌词。在歌曲过渡时制造悬念，通常不押韵或看起来不适合韵律。 |
| [Bridge] | 桥段 | 桥段；用于形成对比、转折或新的歌词/和声材料。 |
| [Intro] | 前奏 | 前奏；可靠性因模型版本而异，无人声需求可写成 [Instrumental Intro]。 |
| [Interlude] | 插曲 | 在歌词中创建器乐段落很有用 |
| [Outro] | 片尾曲 | 有助于为歌曲结尾做准备，可能会创建一个循环以便后期淡出。 |
| [Refrain] | 叠句/反复句，不是“反调” | 叠句/反复句，不是“反调”；通常比 Chorus 更短。 |
| [Big Finish] | 大结局 | 可能会改变旋律或节奏以达到高潮。 |
| [End] | 结束指令 | 结束指令；通常单独占行，仍可能不完全服从。 |
| [Fade Out] | 淡出 |  |
| [Fade to End] | 渐弱直至结束，不是“淡入结束”。 | 渐弱直至结束，不是“淡入结束”。 |
| [Break] | 休息 | 主要乐器或歌手沉默的几小节 |
| [Instrumental Interlude] | 器乐插曲 |  |
| [Melodic Bass] | 旋律低音 |  |
| [Percussion Break] | 打击乐断奏 |  |
| [Syncopated Bass] | 切分音低音 |  |
| [Fingerstyle Guitar Solo] | 指法吉他独奏 |  |
| [Build] | 构建 |  |
| [Bass Drop] | 低音下坠 |  |
| [Hook] | 钩子 | 一个重复的短语或器乐。 |

### 推荐的自描述局部标签

除了核心标签，可用自然英文组合出局部标签。优先采用“修饰词 + 对象/动作”的形式：

| 控制类型 | 推荐示例 |
| --- | --- |
| 演唱方式 | `[Whispered Vocal]`、`[Powerful Belting]`、`[Falsetto]`、`[Spoken Word]` |
| 人声组织 | `[Duet]`、`[Choir]`、`[Layered Vocals]`、`[Call and Response]` |
| 乐器事件 | `[Fingerstyle Guitar Solo]`、`[Piano Interlude]`、`[Percussion Break]` |
| 动态/结构事件 | `[Build]`、`[Breakdown]`、`[Big Finish]`、`[Fade Out]` |
| 节奏事件 | `[Bass Drop]`、`[Syncopated Bass]`、`[Half-time]` |
| 环境/音效 | `[Rain Ambience]`、`[City Noise]`、`[Telephone Effect]`；实验性较强 |

## 8. 快速示例

### 示例 A：抒情流行

**歌词栏（Lyrics）：**

```text
[Verse 1]
窗外的雨，把旧地址写模糊
我还在等，一封没有寄出的祝福

[Pre-Chorus]
[Gradual Build]
如果告别只是另一种停驻

[Chorus]
[Emotional Belting]
那就让名字留在最亮的夜幕
```

**Style 栏：**

```text
This is a Mandopop ballad with a reflective and melancholic atmosphere in a minor key. It opens with soft piano, blending warm sustained string pads that remain restrained and tender. Fingerpicked acoustic guitar enters in the verse, while subtle drums gradually build toward the emotional chorus. The mix is clean and spacious, with a wide stereo field, gentle hall reverb, and distinct instruments. The vocal is a female vocal with a warm and clear tone, delivered with intimate phrasing in the verses and controlled emotional belting in the chorus. All instruments are pure, balanced, and distinct, with no distortion, no harshness, and no ambient noise.
```

### 示例 B：纯音乐

**歌词栏（Lyrics）：**

```text
[Instrumental Intro]

[Build]

[Percussion Break]

[Big Finish]

[End]
```

**Style 栏：**

```text
This is a cinematic electronic song with a tense and futuristic atmosphere in a minor key. It opens with pulsing synthesizers, blending sustained low strings that remain dark and controlled. Electronic drums and layered orchestral percussion gradually build toward a percussion break and a wide orchestral finish. The mix is high-definition, deep, and panoramic, with a wide stereo field and clear front-to-back staging. All instruments are pure, balanced, and distinct, with no distortion, no harshness, and no ambient noise. There is no vocal present.
```

## 9. Style 栏描述词库

本节主要用于按照 3.5 节固定模板生成 Style 栏，也可在确有局部控制需求时组合成自描述标签。`英文描述`和`常见关键词搭配`优先用于实际提示词；中文列用于理解。

### 地域风格

| 音乐风格 | 地区/来源 | 主要特征 | 典型元素/乐器 |
| --- | --- | --- | --- |
| Tango | 阿根廷 | 浪漫激情，舞蹈感强 | 手风琴、钢琴、小提琴、吉他 |
| Tango Nuevo | 阿根廷/现代 | 传统探戈与现代爵士结合 | 手风琴、小提琴、钢琴、打击乐 |
| Celtic Folk | 爱尔兰/苏格兰 | 民谣旋律，舞蹈感 | 小提琴、风笛、竖琴、吉他 |
| Samba | 巴西 | 快速舞曲节奏，打击乐律动强 | Surdo 鼓、Tamborim、Agogo、Cuica |
| Baile Funk / Funk Carioca | 巴西 | 街头舞曲，重低音、弹跳感强 | 808 低音、电子鼓机、采样人声 |
| Reggaeton | 波多黎各 | Dembow 节奏，低音驱动 | 电子鼓、808、打击乐、人声采样 |
| Techno | 德国/全球 | 强烈律动、电子 |  |
| Klezmer | 东欧犹太 | 明快舞曲，情绪张力强 | 单簧管、小提琴、手风琴、鼓 |
| Russian Orthodox Chant | 俄罗斯 | 宗教圣歌，多声部，庄重神圣 | 人声（合唱）、风琴 |
| Balalaika Music | 俄罗斯 | 明快、欢快，舞蹈旋律 | 巴拉莱卡、手鼓、木管 |
| Chastushka | 俄罗斯 | 快速短小民谣，幽默讽刺 | 吉他、手风琴、口琴、打击乐 |
| Russian Rap / Hip-Hop | 俄罗斯 | 现代说唱文化，重节奏 | 打击乐、采样、808、电子元素 |
| Hardbass / Gopnik Music | 俄罗斯 | 电子舞曲，低音驱动，街头文化 | 电子合成器、808、打击乐 |
| Slavic Folk Metal | 俄罗斯 | 民族旋律与金属融合 | 吉他、贝斯、鼓、巴拉莱卡、风笛 |
| Russian Folk | 俄罗斯各地 | 民间旋律，叙事性强，合唱感明显 | 巴拉莱卡、手风琴、长笛、人声合唱 |
| Soukous / Congolese Rumba | 刚果 | 流畅吉他旋律、轻快舞曲节奏 | 吉他、打击乐、合声 |
| Cumbia | 哥伦比亚 | 拉丁舞曲节奏，轻快律动 | 打击乐、手风琴、吉他 |
| Salsa | 古巴/加勒比 | 快节奏舞曲，舞蹈导向 | 打击乐、钢琴、铜管、贝斯 |
| K-Pop | 韩国 | 流行舞曲结合电子元素，视觉同步 | 合成器、电子鼓、舞曲节奏、和声 |
| Highlife | 加纳 | 舞曲风格，旋律明快，鼓点鲜明 | 吉他、鼓、钢琴、铜管 |
| Hip-Hop | 美国 | 说唱、重节奏、采样文化 | 808、打击乐、采样、唱片 scratch |
| Trap / Trap Latino | 美国/拉美 | 808 低音、hi-hat 滚奏、电子风格 | 808、电子鼓、采样 |
| Trap | 美国南部 | 重低音 808、hi-hat 滚奏 | 808、电子鼓、合成器、人声采样 |
| Gnawa | 摩洛哥 | 宗教仪式音乐，低沉律动 | Guembri、打击乐、唱颂 |
| Mariachi | 墨西哥 | 节奏欢快、旋律明亮 | 小号、吉他、Vihuela、Guitarrón |
| Amapiano | 南非 | 舒缓节奏舞曲，低频主导 | 808、打击乐、钢琴、采样 |
| Gqom | 南非夸祖鲁-纳塔尔 | 低沉重复打击、电子舞曲 | 打击乐、电子鼓、采样 |
| Afrobeat | 尼日利亚 | Funk 与非洲节奏结合，强烈 groove | 鼓、贝斯、铜管、吉他 |
| Fado | 葡萄牙 | 哀愁、感伤，强调人声 | 吉他、葡萄牙六弦吉他、人声 |
| Bass House | 全球 | 低频主导 drop、舞池感强 | 808、合成器、打击乐 |
| EDM / House | 全球 | 4/4 节拍、drop、逐步 buildup | 合成器、808、鼓、采样 |
| Bass House | 全球 | 低频主导 drop、舞池感强 | 808、合成器、打击乐 |
| Psytrance / Trance | 全球 | 迷幻循环节奏、长线铺底 | 合成器、鼓机、效果器 |
| Gagaku | 日本 | 古典宫廷音乐，缓慢庄重、空灵 | 笙、篳篥、琵琶、太鼓 |
| J-Pop | 日本 | 明快旋律、偶像化制作，电子与乐器结合 | 合成器、吉他、鼓、声乐和声 |
| Soca | 特立尼达和多巴哥 | 快节奏舞曲、嘉年华风格 | 打击乐、电子鼓、铜管 |
| Flamenco | 西班牙 | 吉他指弹、强节奏感、情绪张力 | 古典吉他、歌唱、掌声、踏拍 |
| Flamenco Jazz | 西班牙/现代 | 弗拉门戈吉他与爵士和声结合 | 吉他、钢琴、打击乐、萨克斯 |
| Tuvan Throat Singing (Khoomei) | 西伯利亚图瓦 | 低音共鸣、多泛音，仪式感强 | 人声（呼麦）、打击乐 |
| Russian Pop (Russkaya Pop) | 现代俄罗斯 | 流行旋律，电子与西方元素融合 | 合成器、电子鼓、吉他、贝斯 |
| Synthwave / Future Bass (Russian Scene) | 现代俄罗斯 | 电子复古、迷幻、流行化 | 合成器、电子鼓、pad、采样 |
| Reggae | 牙买加 | 强烈 off-beat 节奏，轻松悠闲，社会或爱情主题 | 电吉他、贝斯、鼓、风琴 |
| Hindustani | 印度北部 | 旋律即兴为主（Raga）、慢节奏渐进 | Sitar、Tabla、Sarod、Vocal |
| Carnatic | 印度南部 | 古典音乐，复杂节奏循环（Tala） | Sitar、Mridangam、Violin、Vocal |
| Dangdut | 印度尼西亚 | 流行舞曲结合印尼民族风格 | Gamelan 乐器、鼓、电子合成器 |
| Bhangra | 印度旁遮普 | 强烈鼓点和舞蹈节奏 | Dhol、Tumbi、电子鼓、合成器 |

### 流派

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| Chillhop | Chillhop | Lo-fi与Hip-hop融合，节奏舒缓，适合学习、工作或轻松场景。 | mellow beats, jazzy, laid-back |
| Lo-fi | Lo-fi | 低保真音质、环境音融合，营造放松或怀旧氛围，适合背景音乐与创作时聆听。 | vinyl crackle, mellow, chillhop |
| 布鲁斯 | Blues | 情感丰富，旋律重复性高，讲述生活苦乐，常用滑音和蓝调音阶，起源于非裔美国人文化。 | twelve-bar, slide guitar, melancholic |
| 电影感 | Cinematic | 类似电影配乐，注重情绪与画面感，常用于叙事性强的音乐作品 | epic cinematic, orchestral trailer music |
| 电子流行 | Electropop | 合成器主导、节拍鲜明，旋律现代，具有未来感和流行性，适合舞池与时尚场合。 | synths, danceable, futuristic |
| 独立音乐 | Indie | 非主流制作，风格自由，常融合民谣、摇滚、电子等元素，强调个性化与艺术表达。 | raw, alternative, authentic |
| 放克 | Funk | 强烈律动感、切分节奏与低音线，节奏驱动性强，常用于舞曲与即兴段。 | groove, bassline, syncopated |
| 放松嘻哈 | Chillhop | 将轻松氛围与嘻哈鼓点结合，节奏温和，常用于放松与专注 | study beats, mellow chillhop |
| 氛围音乐 | Ambient | 以氛围为主，节奏弱化，营造空间感与沉浸体验，常用于电影配乐、冥想和放松背景。 | drone, atmospheric, ambient pad |
| 福音 | Gospel | 强调宗教情感，合唱丰富，技巧性强，常用于教堂演唱与灵魂乐演出中。 | choir, spiritual, powerful vocal |
| 古典 | Classical | 正统西方音乐传统，结构严谨，注重乐器编排与对位技法，适合正式场合与音乐会演出。 | orchestral, symphonic, formal |
| 韩流流行 | K-pop | 韩国流行风格，注重编舞、视觉与多风格融合，制作精良，全球影响力强。 | visual, polished, hybrid genre |
| 合成流行 | Synthpop | 80年代风格，重合成器旋律，节奏感轻快，带有复古与科技并存的质感。 | retro, synth leads, nostalgic |
| 节奏蓝调 | R&B | 情绪细腻、节奏律动感强，融合灵魂乐与流行元素，强调旋律与人声表现力。 | soulful, groove, smooth vocals |
| 金属 | Metal | 吉他失真、强鼓点与咆哮式人声，情绪激烈，子风格包括重金属、死亡金属等。 | distortion, screaming, heavy |
| 爵士 | Jazz | 即兴演奏、和声复杂，节奏变化灵活，强调演奏者技巧与音乐的自由表达。 | swing, improvisation, complex harmony |
| 垃圾摇滚 | Grunge | 音色浑浊，歌词阴郁，90年代风格，代表如Nirvana，强调真实与颓废感。 | distorted, angst, Seattle sound |
| 拉丁 | Latin | 多样节奏结构，富有舞蹈性，热烈欢快，常见类型如Salsa、Bachata等。 | salsa, reggaeton, percussion |
| 雷鬼 | Reggae | 源自牙买加，节奏悠闲，突出反拍节奏与文化主题，旋律带有热带风情。 | offbeat, island vibe, chill |
| 灵魂乐 | Soul | 深情演唱，强调人声表现力，常融合福音音乐元素，诉诸灵魂与情感的共鸣。 | gospel, emotional, vocal power |
| 流行 | Pop | 通俗易懂、旋律朗朗上口、节奏明快，通常具有商业吸引力，常见于主流电台。 | catchy, melodic, mainstream, easy listening |
| 流行舞曲 | EDM | 电子舞曲总称，节奏感强，常用于派对或夜店，注重能量积累与“爆点”释放。 | drop, festival, build-up |
| 民谣 | Folk | 使用原声吉他与简单结构，强调叙事性与文化传承，旋律朴素且富有人文情怀。 | acoustic, storytelling, traditional |
| 朋克 | Punk | 简单直接、节奏快、富有反叛精神，歌词多为社会评论，源于70年代街头文化。 | DIY, fast tempo, rebellion |
| 日流流行 | J-pop | 日本流行音乐，旋律性强，常带动漫、游戏风格色彩，偏向甜美或幻想系表现。 | catchy, idol, anime influence |
| 声学 | Acoustic | 原声乐器演奏为主，声音自然真实，强调演奏细节 | unplugged, acoustic ballad, soft acoustic |
| 实验 | Experimental | 先锋实验性风格，突破传统音律与结构限制，常用非常规乐器与技术 | glitch, noise, avant-garde |
| 世界音乐 | World | 非西方传统或民族音乐，具有地域文化特色，融合民族乐器与民间旋律。 | ethnic, tribal, folk instruments |
| 探戈 | Tango | 阿根廷传统舞曲，节奏鲜明、情绪张力强，常用于双人舞蹈中。 | dramatic, bandoneon, passionate |
| 未来贝斯 | Future Bass | 合成器波形明显、音调变化强烈，情绪富有张力，常用于现代电子流行与未来感作品。 | wobble, saw synth, drop |
| 嘻哈 | Hip-hop | 重节奏、以说唱为主，反映社会现实与街头文化，常用采样与打击节奏构建音轨。 | rap, beats, sampling, urban |
| 陷阱 | Trap | 808低音、Hi-hat密集节奏、节拍切分，风格现代，多用于年轻人文化表达与潮流音乐。 | 808s, hi-hats, dark vibe |
| 新世纪 | New Age | 冥想放松类音乐，多为器乐，融合自然声或世界音乐元素，常用于身心疗愈场合。 | meditation, instrumental, soft synth |
| 摇滚 | Rock | 强烈的电吉他与鼓点，强调能量、反叛和个人表达，涵盖多种子风格如硬摇滚、另类摇滚等。 | electric guitar, energetic, live band |

### 结构

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 前奏 | Intro | 歌曲开始的部分，用于营造氛围、建立调性或节奏，引导听众进入主歌。 | ambient intro, synth intro, soft piano intro |
| 主歌 | Verse | 主要承载歌词内容，通常表达具体情节或叙述，旋律相对平稳，为副歌铺垫。 | narrative verse, soft verse, clean verse |
| 副歌 | Chorus | 歌曲中最高潮、最重复的部分，旋律醒目、情绪强烈，常用于传达主题。 | catchy chorus, explosive chorus, hook |
| 间奏 | Interlude | 两段之间的过渡片段，可能为纯音乐，起到调节或转换情绪的作用。 | ambient interlude, jazz break, lo-fi drop |
| 过门 | Fill | 短暂的鼓或乐器段，用于连接结构或制造小高潮。 | drum fill, guitar lick, synth fill |
| 桥段 | Bridge | 用于打破单调结构，提供对比或情绪转折，通常在歌曲中后段。 | emotional bridge, modulation, breakdown bridge |
| 副副歌 | Pre-Chorus | 主歌与副歌之间的过渡段，旋律上逐渐增强，为副歌制造期待。 | rising pre-chorus, tension build |
| 尾奏 | Outro | 歌曲结束段，可渐弱淡出或强化收尾，影响整体印象。 | fade out outro, dramatic end, piano outro |
| 间奏段 | Break | 节奏或旋律的暂停，用以突出某段元素或增强层次变化。 | drum break, breakbeat, silence break |
| 高潮段 | Drop | 尤其在电子音乐中，节奏突然爆发的核心段落，常用于EDM或Trap中。 | bass drop, heavy drop, synth drop |
| 循环段 | Loop Section | 可重复的旋律或节奏段，适用于背景音乐或电子编曲中。 | beat loop, melody loop, bass loop |
| 复调 | Counterpoint | 多声部线条并行进行，突出音乐复杂性，常用于古典与部分爵士中。 | baroque style, classical layering |
| 叠加段 | Layering | 多个声部或节奏逐渐加入，使情绪逐步推进或厚重化。 | gradual build, dynamic layering |
| 拍内换段 | In-bar Shift | 在同一小节内进行节奏或和声变化，制造细节动感。 | rhythmic shift, harmonic twist |
| 返场段 | Refrain | 反复出现的简短旋律句或歌词，强化主题印象。 | recurring hook, repeating refrain |
| 和声叠唱段 | Harmony Section | 合唱或重叠唱段，增强情感与层次感，常见于副歌或高潮。 | gospel harmony, choral layering |
| 拆分段落 | Deconstructed | 整体节奏或编曲拆分为最基本元素，形成对比，常用于后现代编曲。 | minimalist section, sparse beat |
| 情绪过渡 | Mood Shift | 在编曲中用结构性变化引导情绪由柔和转向激烈或相反。 | soft-to-hard, melancholic to bright |
| 主题回归 | Motif Return | 再次引入开头主题或旋律，构建整体统一感。 | thematic return, motif echo |
| 器乐独奏段 | Solo Section | 由单一乐器主导的演奏段，展示技巧或增强情绪。 | guitar solo, synth solo, drum solo |
| 节拍空白段 | Dropout | 去除节奏或主乐器片段，形成空白感，加强对比效果。 | beat dropout, silent break, vocal-only |
| 渐强段 | Crescendo | 音量逐渐增强，常用于制造高潮或激发情绪。 | build-up, volume rise, tension ramp |
| 渐弱段 | Decrescendo | 音量逐渐减弱，常用于柔和收尾或过渡情绪。 | fade out, soft outro, calming end |
| 情绪爆发 | Climax | 歌曲中情绪最高潮的段落，表现力最强。 | emotional peak, belting chorus, high note burst |
| 主题延展 | Variation | 在主题基础上进行节奏或旋律的变化，避免重复单调。 | melodic variation, rhythmic change |
| 叙事段 | Narrative Part | 歌词主导、节奏平稳，强调内容表达与情节推进。 | spoken verse, slow narrative, storytelling part |
| 编舞高潮 | Dance Break | 设计用于舞蹈表演的编排高潮段，常见于流行与K-pop中。 | choreo break, beat-only, punchy dance part |
| 插入语段 | Spoken Section | 在歌曲中穿插的对白、旁白或脱节语句，常见于说唱与实验类音乐。 | talking part, monologue, voice sample |
| 合唱段 | Chant Section | 重复性强、适合人群呼应的简短段落，常用于现场演出与民谣。 | anthem chant, repeat chorus, crowd call |
| 环节反复 | Loop Outro | 用循环结尾形成“无限感”，常用于背景音乐或冥想音乐。 | looping fade, infinite outro, chill loop |

### 唱腔

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 哀怨唱腔 | Mournful Singing | 情感低沉哀伤，适合表达悲痛与怀念。 | sorrowful, plaintive, melancholic |
| 颤抖唱法 | Tremolo | 声音快速颤动，用于增强紧张感或情感强度。 | fast vibrato, shaking voice, emotional tremolo |
| 颤音 | Vibrato | 声音频率的有规律震荡，增强声音的表现力和丰富度。 | controlled vibrato, natural vibrato |
| 低吟 | Humming | 无歌词，仅用嗡嗡声或哼唱旋律，增添氛围。 | humming melody, soft tone, ambient |
| 喊唱 | Shouting Singing | 高强度、带有喊叫的唱法，表现激情或愤怒。 | aggressive shout, raspy yell, energetic |
| 喊麦 | Shout Rap | 中国说唱中特有的激昂喊叫风格，富有冲击力。 | aggressive rap, energetic shout, hype |
| 假唱 | Lip-sync | 表面唱歌而实际无声或播放录音，常用于现场表演。 | playback, miming, performance illusion |
| 假声 | Falsetto | 男声或女声使用头声，声音轻柔、透明，常用于高音段。 | airy tone, light head voice, falsetto runs |
| 哭腔 | Crying Style | 唱法中带有哽咽或颤音，表现悲伤或情感激烈。 | emotional waver, sobbing tone, trembling voice |
| 朗诵 | Spoken Word | 以朗诵形式表达，节奏自由，注重语言韵律和内容。 | poetry recitation, narrative, rhythmic speech |
| 力量唱法 | Power Singing | 声音强大且有穿透力，常用于摇滚或福音音乐。 | belting, strong projection, chest voice |
| 民谣唱腔 | Folk Singing | 自然朴实，注重叙事性与情感传达。 | storytelling, nasal tone, raw |
| 男低音 | Bass | 男声最低音区，声音深沉有力。 | deep voice, resonant, powerful |
| 男高音 | Tenor | 男声最高音区，明亮且有穿透力。 | bright male voice, high range, clear |
| 男中音 | Baritone | 男声中音区，音色均衡，适合多种风格。 | balanced, smooth, versatile |
| 女低音 | Contralto | 女声最低音区，声音厚重且富有深度。 | deep female voice, rich tone, dark |
| 女高音 | Soprano | 女声最高音区，声音明亮且清晰。 | high pitch, operatic, light |
| 女中音 | Mezzo-soprano | 女声中高音区，音色丰满温暖。 | warm tone, balanced, expressive |
| 咆哮 | Growling | 低沉、粗犷的声音，常见于金属音乐。 | guttural growl, aggressive, distorted |
| 破音 | Vocal Break | 声音突然转为沙哑或破裂，增加戏剧效果。 | vocal crack, emotional break, voice distortion |
| 轻声 | Soft Singing | 轻柔、温暖，适合表达内心细腻情感。 | gentle tone, whispery, intimate |
| 清唱 | Straight Singing | 清晰纯净的声音，没有明显装饰，表现自然且直接。 | pure tone, clean voice, natural delivery |
| 情绪化唱腔 | Emotional Delivery | 通过声线变化表达强烈情绪，带有个人特色。 | passionate, heartfelt, expressive |
| 呻吟 | Moaning | 细腻柔软的呻吟声，用于表达欲望或情感氛围。 | sensual moan, breathy, intimate |
| 说唱 | Rap | 以节奏说话为主，重视韵律和语言表达。 | rhythmic speech, flow, punchlines |
| 说唱唱腔 | Flow | 说唱中节奏和韵律的变化与表达方式。 | smooth flow, rapid fire, syncopated |
| 嘶哑 | Raspy | 声音沙哑粗糙，带有独特的质感，增加情绪表达。 | gravelly, husky, raspy texture |
| 颂唱 | Chanting | 重复简短词句或旋律，多用于宗教或仪式场合。 | mantra, repetitive, meditative |
| 颂歌唱法 | Gospel Singing | 带有福音音乐特征，情感丰富，常有复杂的即兴与装饰。 | melisma, soulful, call and response |
| 响亮唱腔 | Bright Singing | 声音明亮清晰，适合高音或乐观主题。 | clear tone, piercing, uplifting |
| 震音 | Trill | 快速交替发声技巧，用于装饰旋律。 | rapid alternation, vocal ornamentation |
| 自然唱腔 | Natural Voice | 不刻意修饰，保留歌者原始音质和情感。 | authentic, raw, unprocessed |

### 声部

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 伴唱 | Background Vocal | 辅助歌唱，不抢主唱风头，增强氛围和层次。 | background, support, subtle |
| 唱诗班 | Choir | 大规模集体演唱，常用于宗教或古典作品。 | choir, ensemble, sacred vocals |
| 低声部 | Bass Vocal | 低音声部，提供低频支持，增强歌曲厚重感。 | bass harmony, low vocal, deep voice |
| 低语声 | Whisper | 低声细语，制造亲密或神秘氛围。 | breathy, intimate, soft |
| 叠唱 | Overdubbed Vocal | 多层录制同一声部，增加厚度与空间感。 | multi-track, layered, thick |
| 独唱 | Solo Vocal | 独立演唱的声部，强调个人表现力。 | solo, featured vocal, spotlight |
| 对唱 | Duet | 两个歌手轮流或同时演唱，形成对话或互动效果。 | duet, call and response, vocal interplay |
| 高声部 | Soprano Vocal | 女高音，负责高频旋律或和声，声音明亮穿透。 | soprano lead, high harmony, bright |
| 过门声部 | Vocal Fill-ins | 用于连接段落的短小旋律或音效，增加流畅度。 | vocal runs, fills, transitions |
| 合唱 | Chorus | 多人集体演唱，音量大，气势宏大，增强歌曲高潮效果。 | choir, group singing, anthem |
| 合声领唱 | Lead Harmony | 和声中突出的一条声线，带有主旋律性质。 | lead harmony, featured backing vocal |
| 和声 | Harmony Vocal | 辅助主唱，提供和声支持，丰富音响层次感。 | backing vocals, harmony, vocal layers |
| 呼喊声 | Shout | 大声喊叫式演唱，增加歌曲激情与紧张感。 | shout, yell, energy |
| 回声声部 | Echo Vocal | 歌词或旋律重复出现，产生回声或回应效果。 | echo, delay, call and response |
| 即兴唱 | Vocal Improvisation | 演唱者临时创作旋律和节奏，展示技巧与表现力。 | scat singing, melisma, ad-lib |
| 轮唱 | Round Singing | 多声部依次进入，形成轮唱效果，常用于合唱或传统民谣。 | canon, layering, overlapping vocals |
| 模唱 | Mimic Vocals | 模仿其他歌手或乐器的唱法，展示技巧或幽默感。 | impersonation, stylistic imitation |
| 男低音 | Bass Vocal | 男性低音，声音浑厚有力，基础声部。 | bass, low male voice, deep |
| 男高音 | Tenor Vocal | 男性高音部分，声音明亮有穿透力。 | tenor, high male voice, bright |
| 男中音 | Baritone Vocal | 男性中音，连接男高音和男低音，声音温暖。 | baritone, mid male voice, rich tone |
| 女低音 | Contralto Vocal | 女性低音，稀有且独特，声音深沉厚重。 | contralto, low female voice, dark |
| 女高音 | Soprano Vocal | 女性高音，负责高频旋律与装饰音。 | soprano, high female voice, clear |
| 女中音 | Mezzo-Soprano | 女性中音，音色丰富，适合多种风格。 | mezzo, mid female voice, warm |
| 拍手声 | Hand Clap Vocals | 伴随拍手节奏的歌唱，常用于现场或合唱。 | clapping, rhythmic, participatory |
| 清唱 | A Cappella | 无伴奏纯人声演唱，展示声部间的和声与协调。 | unaccompanied, vocal harmony, choir |
| 说唱 | Rap Vocal | 以节奏化说话为主，强调歌词韵律与节奏感。 | rap, rhythmic speech, flow |
| 响声 | Vocal Percussion | 以人声模仿打击乐器的声音，增强节奏表现。 | beatboxing, vocal drums, rhythmic sounds |
| 响指声 | Finger Snap Vocals | 以响指或手势伴随的歌唱，增强节奏感。 | snaps, rhythmic accent, groove |
| 中声部 | Alto Vocal | 女低音或男中音，填充中频区域，连接高低声部。 | alto harmony, midrange, warm tone |
| 主唱 | Lead Vocal | 歌曲中最主要的歌唱声部，通常负责旋律线和歌词的表达。 | main vocal, melody, forefront |

### 声线

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 暗哑声线 | Dark Timbre | 声音低沉厚重，富有神秘感与深度。 | deep, warm, mysterious |
| 薄声线 | Thin & Nasal Timbre | 声音带有鼻音，较轻薄，适合部分民谣风格。 | nasal, light, airy |
| 磁性声线 | Magnetic Timbre | 声音有吸引力，充满个性。 | captivating, alluring, strong |
| 粗犷声线 | Gritty Timbre | 带有颗粒感和粗糙质感，适合摇滚、布鲁斯等风格。 | rough, edgy, raw |
| 低沉声线 | Deep Timbre | 音色低沉有力，给人稳重感。 | bassy, dark, powerful |
| 粉声线 | Breathier Timbre | 声音带有呼吸声，柔弱且性感。 | breathy, soft, intimate |
| 浑厚声线 | Robust Timbre | 声音强劲有力，适合表现坚韧和力量。 | strong, full, hearty |
| 金属声线 | Metallic Timbre | 声音带有金属质感，突出刺耳或机械感。 | harsh, sharp, industrial |
| 金属质感声线 | Harsh & Metallic Timbre | 声音锋利带金属感，适合摇滚和金属音乐。 | sharp, cutting, aggressive |
| 颗粒声线 | Grainy Timbre | 声音有颗粒感，带粗糙质感。 | gritty, textured, rough |
| 空灵声线 | Ethereal Timbre | 声音轻盈飘渺，带有神秘梦幻感。 | airy, haunting, otherworldly |
| 嘹亮声线 | Resonant Timbre | 声音共鸣强烈，传播力好，富有感染力。 | ringing, powerful, vibrant |
| 明朗声线 | Clear & Bright Timbre | 声音清晰明快，适合流行和儿童歌曲。 | sparkling, joyful, clear |
| 明亮声线 | Bright Timbre | 声音清晰且有穿透力，常用于高音段。 | piercing, shining, clear |
| 浓厚声线 | Thick Timbre | 声音饱满有力，富有层次感，表现力强。 | rich, full-bodied, warm |
| 朴实声线 | Natural Timbre | 原生态自然，无过多修饰。 | authentic, raw, unpolished |
| 轻薄声线 | Thin Timbre | 声音细弱透明，适合抒情或背景和声。 | airy, delicate, fragile |
| 清脆声线 | Crisp Timbre | 声音清晰且带有弹性，节奏感强。 | sharp, bright, punchy |
| 柔和声线 | Soft Timbre | 细腻温柔，给人温暖舒适感。 | gentle, smooth, mellow |
| 柔和圆润声线 | Smooth & Round Timbre | 声音圆润流畅，适合抒情或爵士。 | silky, velvety, mellow |
| 柔韧声线 | Flexible Timbre | 声音变化灵活，适合多样化表现。 | agile, versatile, dynamic |
| 沙哑高声线 | Raspy High Timbre | 高音区带有沙哑质感，独特且充满个性。 | raspy, piercing, edgy |
| 沙哑声线 | Raspy Timbre | 声音带有粗糙质感，有磁性，增强个性与情感表达。 | gravelly, husky, rough |
| 抒情声线 | Lyrical Timbre | 声音富有旋律感，适合抒情歌曲。 | smooth, expressive, flowing |
| 嘶哑磁性声线 | Husky & Smoky Timbre | 声音低沉且带沙哑，性感且有磁性。 | raspy, smoky, seductive |
| 童声声线 | Childlike Timbre | 声音清纯，带有童真和无邪感。 | innocent, bright, pure |
| 透明声线 | Clear Timbre | 声音纯净明亮，细节清晰，适合多种风格。 | bright, clean, pure |
| 温暖声线 | Warm Timbre | 声音柔和温暖，令人舒适。 | cozy, mellow, soothing |
| 纤细声线 | Thin & Light Timbre | 声音细小轻柔，常用于童声或女性轻唱。 | delicate, light, soft |
| 响亮声线 | Loud Timbre | 声音强劲且清晰，适合大型舞台或现场表演。 | powerful, booming, projecting |
| 振动声线 | Vibrating Timbre | 声音带有自然颤动，丰富表现力。 | vibrato, wavering, expressive |

### 音色

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 暗淡 | Dark | 声音低沉，缺乏高频成分，营造温暖或神秘氛围。 | warm, mellow, shadowy |
| 薄荷感 | Minty | 声音清爽、明快，带有清新的感觉。 | fresh, crisp, invigorating |
| 纯净 | Pure | 声音干净、无杂质，透明感强。 | clear, pristine, uncolored |
| 粗糙 | Rough | 声音不平滑，带有颗粒或破音感，适合表达愤怒或激烈情绪。 | raw, coarse, harsh |
| 粗犷 | Gritty | 声音带有颗粒感和力度，适合表现力量和粗犷的情绪。 | rough, edgy, raw |
| 机械感 | Mechanical | 声音冷硬，带有机械、电子加工效果，少情感色彩。 | robotic, synthetic, sterile |
| 金属感 | Metallic | 声音带有金属质感，尖锐且具有穿透力，常见于合成器或人声效果。 | sharp, bright, ringing |
| 颗粒感 | Grainy | 声音中带有颗粒质感，有一定粗糙度，增加质感丰富度。 | textured, rough, detailed |
| 空旷 | Hollow | 声音空洞，有共鸣但缺乏实质感，营造开阔空间感。 | resonant, spacious, cavernous |
| 空灵 | Ethereal | 声音飘渺、轻盈，带有梦幻和空灵的质感。 | airy, floating, delicate |
| 冷峻 | Cold | 声音清冷，缺乏温暖，适合营造疏离或机械感。 | clinical, detached, icy |
| 冷色调 | Cool-toned | 声音整体偏冷，频率偏高，带有清冷或现代感。 | crisp, clinical, detached |
| 明亮 | Bright | 声音清晰、高频丰富，给人活力和清爽的感觉。 | crisp, shimmering, clear |
| 模糊 | Fuzzy | 声音模糊不清，边缘软化，多用于吉他失真或人声效果。 | distorted, blurred, hazy |
| 磨砂 | Matte | 类似哑光，声音柔和且无光泽，避免刺耳感。 | muted, soft, dull |
| 浓厚 | Thick | 声音层次丰富，富有密度和深度，感觉饱满。 | full-bodied, dense, heavy |
| 暖色调 | Warm-toned | 声音整体偏暖，频率分布偏中低频，传递温情和包容感。 | cozy, rich, mellow |
| 轻薄 | Thin | 声音透明，缺乏厚重感，偏向清淡细腻。 | delicate, faint, airy |
| 柔和 | Soft | 声音轻柔，音量较小，常用于细腻情感表达。 | gentle, mellow, subdued |
| 沙沙声 | Raspy | 同沙哑，带有摩擦声，声音粗糙。 | rough, gravelly, hoarse |
| 沙哑 | Raspy | 声音带有粗糙的质感，类似声音破裂或嘶哑，富有个性。 | gravelly, hoarse, rough |
| 哨声 | Whistling | 声音如哨子般尖锐清亮，多用于效果或人声装饰。 | piercing, sharp, melodic |
| 丝滑 | Silky | 声音柔滑顺畅，给人细腻且舒适的听感。 | smooth, flowing, polished |
| 嘶嘶声 | Hissy | 声音带有高频噪音或气流声，类似嘶嘶声。 | sibilant, airy, breathy |
| 甜美 | Sweet | 声音柔和、悦耳，给人温馨愉悦的感觉。 | soft, gentle, charming |
| 透亮 | Transparent | 声音清晰透明，细节丰富，给人清澈感。 | clear, bright, lucid |
| 温暖 | Warm | 声音柔和、饱满，带有低频和中频的丰富感，传递温情。 | rich, cozy, comforting |
| 响亮 | Loud | 声音强劲，易于穿透混音，强调动态感。 | powerful, booming, prominent |
| 哑光 | Matte | 声音质感柔和、不刺耳，缺乏亮光感，给人朴实自然的感觉。 | soft, muted, natural |
| 粘稠 | Sticky | 声音粘滞感强，有紧贴耳朵的质感，常用来形容人声或合成器。 | viscous, dense, clinging |

### 情绪

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 悲惨 | Tragic | 表现极度不幸或灾难，情感深刻沉重。 | heartbreaking, sorrowful, devastating |
| 悲伤 | Sad | 表达失落、哀伤或忧郁的情绪，旋律往往缓慢且带有忧郁色彩。 | melancholic, sorrowful, mournful |
| 沉思 | Reflective | 充满内省和思考，氛围深沉，常用缓慢节奏和简洁旋律。 | thoughtful, contemplative, pensive |
| 沉重 | Heavy | 情绪厚重，带有压迫感，节奏缓慢且有力度。 | dense, powerful, grave |
| 纯真 | Innocent | 单纯无邪，带有孩童般的纯洁感。 | naive, simple, sweet |
| 反思 | Reflective | 思考、内省的情绪，旋律带有沉思性质。 | thoughtful, introspective, contemplative |
| 放松 | Relaxed | 氛围舒缓，音乐轻松流畅，适合休息放松。 | chill, calm, easygoing |
| 愤怒 | Angry | 激烈、冲动的情感，音乐强烈且节奏紧凑，表现愤怒和不满。 | aggressive, intense, fierce |
| 感伤 | Sentimental | 情感细腻，带有柔情与回忆色彩。 | tender, nostalgic, affectionate |
| 孤独 | Lonely | 表达孤独感和疏离，旋律往往寂寞且带有哀伤色彩。 | isolated, forlorn, desolate |
| 怀旧 | Nostalgic | 唤起对过去美好时光的回忆，通常伴随柔和、温暖的旋律。 | sentimental, reflective, wistful |
| 欢乐 | Joyful | 极度开心和兴奋，常用于庆祝或派对氛围。 | exuberant, lively, festive |
| 激动 | Excited | 情绪高涨，充满兴奋与期待。 | thrilled, exhilarated, enthusiastic |
| 激励 | Motivational | 充满力量和鼓舞，推动人前进，旋律高昂有力。 | inspiring, uplifting, empowering |
| 激情 | Passionate | 强烈的感情表达，富有张力和感染力。 | intense, fervent, emotional |
| 坚定 | Determined | 表达坚强和决心，常用稳健节奏和强烈旋律。 | resolute, firm, confident |
| 紧张 | Tense | 充满悬念和压力，节奏急促，常用于影视配乐。 | suspenseful, anxious, uneasy |
| 惊喜 | Surprised | 出乎意料，带有新奇感和兴奋感。 | unexpected, amazed, startled |
| 恐惧 | Fearful | 产生紧张、不安、恐慌等心理反应，常用不和谐音程和断续节奏。 | anxious, tense, uneasy |
| 快乐 | Happy | 传递轻松愉快、积极向上的情感，通常伴有明快节奏和明亮旋律。 | cheerful, upbeat, joyful |
| 浪漫 | Romantic | 表达爱情和温柔情感，旋律柔美细腻，气氛温馨。 | passionate, tender, intimate |
| 浪漫忧郁 | Blue | 混合浪漫与忧郁的情感，常用于蓝调和爵士中。 | soulful, melancholic, tender |
| 冷静 | Cool | 冷静理智，气氛淡然，节奏舒缓，常用简洁音色。 | detached, smooth, laid-back |
| 迷幻 | Psychedelic | 充满梦幻和奇异感，常用丰富的音效和空间感。 | trippy, surreal, otherworldly |
| 迷茫 | Confused | 情绪混乱，表现出不确定和彷徨。 | uncertain, lost, bewildered |
| 宁静 | Calm | 平和、安静的氛围，适合放松或冥想，旋律柔和。 | peaceful, relaxed, serene |
| 平静 | Peaceful | 心灵平静，无冲突与紧张，适合冥想或背景。 | tranquil, serene, calm |
| 轻松 | Easygoing | 氛围轻松自在，适合休闲场合。 | laid-back, mellow, breezy |
| 伤感 | Heartbreaking | 表达深切的伤痛和悲伤，常见于慢歌。 | tragic, emotional, sorrowful |
| 神经质 | Nervous | 表现紧张和焦虑，常伴有不规则节奏和断断续续的旋律。 | jittery, anxious, edgy |
| 神秘 | Mysterious | 营造未知、悬疑或隐秘的感觉，常用不确定和声及模糊音效。 | enigmatic, dark, suspenseful |
| 神圣 | Sacred | 具有宗教或精神性庄重感。 | spiritual, holy, reverent |
| 甜美 | Sweet | 温柔和善，充满爱意和亲切感。 | gentle, tender, affectionate |
| 温暖 | Warm | 氛围柔和，给人安全和舒适的感觉，多用柔和音色和和声。 | cozy, comforting, heartfelt |
| 无助 | Helpless | 表达无力感和迷茫。 | powerless, vulnerable, lost |
| 希望 | Hopeful | 传递乐观和未来向往，音乐多明亮且充满正能量。 | optimistic, bright, uplifting |
| 兴奋 | Excited | 高度兴奋，充满活力和激情。 | energetic, thrilled, enthusiastic |
| 压抑 | Oppressive | 情绪沉重且压抑，常用于描绘困境或不公。 | heavy, stifling, dark |
| 忧郁 | Melancholic | 深刻的忧伤，带有内省和沉重情感。 | gloomy, sorrowful, reflective |
| 幽默 | Humorous | 轻松诙谐，带有玩笑或滑稽成分。 | playful, witty, fun |
| 犹豫 | Hesitant | 表现不确定和迟疑的心理状态。 | unsure, wavering, tentative |
| 愉悦 | Joyful | 表达欢快与满足，常用明快旋律和和声。 | exuberant, lively, bright |
| 振奋 | Energetic | 活力充沛，节奏明快，令人振奋。 | lively, dynamic, spirited |
| 自信 | Confident | 坚定且有力量，表现自我肯定和信念。 | assured, bold, empowered |
| 自由 | Free | 无拘无束，轻松自在，音乐节奏和结构灵活。 | unrestrained, open, relaxed |

### 节奏型

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 半拍节奏 | Half-time | 节奏明显减缓，鼓点出现半拍间隔，制造出宽松与沉重感，多见于嘻哈与陷阱音乐。 | slow, heavy, laid-back |
| 波萨诺瓦节奏 | Bossa Nova Rhythm | 源自巴西，结合桑巴与爵士，节奏柔和而富有律动感，适合轻松氛围。 | samba, smooth, Latin groove |
| 不规则节奏 | Irregular Meter | 小节拍数不规则，如5/4、7/8，产生不对称的律动，适合实验和前卫音乐。 | asymmetrical, progressive, complex |
| 侧重节奏 | Accent | 在特定音符上加重击打，增强节奏感与动态对比。 | emphasized, dynamic, punchy |
| 弹跳节奏 | Bouncy Rhythm | 节奏轻快弹跳，富有律动感和活力。 | playful, jumpy, rhythmic |
| 低音节奏 | Bass-driven Rhythm | 以低音线条引导节奏，强化律动感和力量感。 | bass groove, heavy, rhythmic |
| 断奏节奏 | Staccato Rhythm | 节奏短促断裂，音符间有明显间隔，营造紧凑和跳跃的感觉。 | clipped, detached, sharp |
| 多拍层叠 | Layered Beats | 多层鼓点叠加，丰富节奏层次和复杂度。 | complex layers, thick, textured |
| 反拍节奏 | Offbeat | 强调弱拍或弱拍间的节奏点，增强律动感与跳跃感，多用于雷鬼、放克。 | reggae, funk, syncopated |
| 反转节奏 | Polyrhythm | 同时出现不同节奏的叠加，如三拍与二拍同时进行，增加节奏复杂性。 | cross rhythm, layered, African influence |
| 复调节奏 | Counter-rhythm | 同时出现对比的节奏型，增加音乐的复杂性和趣味性。 | interplay, complex, rhythmic tension |
| 复合节奏 | Compound Meter | 小节内拍子可拆分为三等分，如6/8、9/8，节奏律动丰富，常见于凯尔特音乐与摇滚。 | lilting, rolling, triplet subdivisions |
| 复合拍号 | Mixed Meter | 不同节拍类型交替出现，如4/4与3/4交替，增加变化性。 | changing time signatures, dynamic |
| 复节奏 | Polymeter | 不同节拍数的节奏同时进行，产生复杂时间感。 | layered rhythms, complex, experimental |
| 割拍节奏 | Cut-time Rhythm | 以二分音符为一拍的节奏，速度感更强，常用于快节奏音乐。 | fast, driving, march |
| 滑奏节奏 | Legato Rhythm | 节奏连贯平滑，音符之间流畅衔接，适合抒情和缓慢音乐。 | smooth, connected, flowing |
| 机械节奏 | Mechanical Beat | 节奏精确且机械化，常用于工业、电子音乐。 | robotic, precise, rigid |
| 流动节奏 | Groove | 节奏的整体感和律动感，带动音乐流畅且富有生命力。 | pocket, feel, swing |
| 切分节奏 | Syncopation | 弱拍上出现强调，打破强弱节奏的平衡，产生律动感和节奏上的惊喜。 | offbeat, unexpected accents, groove |
| 切割节奏 | Breakbeat | 采样或现场演奏断裂的鼓点节奏，常见于嘻哈和电子音乐。 | sampled drums, funky, syncopated |
| 轻快节奏 | Lively Beat | 节奏活泼轻快，常用于流行和舞曲。 | upbeat, energetic, bright |
| 弱拍强调 | Weak Beat Emphasis | 强调弱拍，形成独特的节奏律动感，常用于放克和雷鬼。 | offbeat, laid-back, funky |
| 三拍节奏 | Triple Meter | 每小节三拍，带有圆舞曲感，适合华尔兹、探戈等舞曲类型。 | waltz, flowing, dance |
| 四拍节奏 | Four-on-the-floor | 鼓点在每拍上均有重击，常用于舞曲、电子乐和迪斯科，推动感强烈。 | dance beat, steady kick, driving |
| 停顿节奏 | Rubato | 节奏自由处理，临时停顿或延长音符，强调情感表达。 | expressive timing, flexible, emotional |
| 延迟节奏 | Delay Rhythm | 利用回声和延迟效果制造节奏层次感和空间感。 | echo, repetition, spatial |
| 摇摆风格 | Swing Style | 具有爵士摇摆特点的节奏，三连音感强烈。 | jazzy, triplet feel, laid-back |
| 摇摆节奏 | Swing Rhythm | 节奏中带有三连音的感觉，略带弹性与“摆动”，是爵士乐和布鲁斯的标志。 | triplet feel, loose, jazzy |
| 直拍节奏 | Straight Beat | 节奏均匀，拍子规则，常见于流行和摇滚，听感稳健有力。 | steady, even, four-on-the-floor |
| 逐渐加速 | Accelerando | 节奏逐渐加快，制造紧张感和高潮感。 | speeding up, buildup, dynamic |
| 逐渐减速 | Ritardando | 节奏逐渐减慢，制造缓和和情感收尾感。 | slowing down, relaxed, expressive |

### 速度

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 变速节奏 | Tempo fluctuando | 速度波动明显，富于表现力。 | fluctuating tempo, dynamic, expressive |
| 超快速 | Prestissimo | 极端快速，表现速度极限。 | extremely fast, blazing, frantic |
| 断断续续速度 | Tempo rubato | 速度不规则，快慢交替，产生动态起伏。 | fluctuating tempo, expressive, nuanced |
| 断裂速度 | Broken tempo | 节奏时快时慢，断裂明显，富有紧张感。 | broken, irregular, staggered |
| 极快速 | Presto | 非常快，通常用于炫技或激烈段落。 | very fast, virtuosic, intense |
| 极慢速 | Largo | 非常缓慢，庄重沉稳，适合抒情或庄严音乐。 | very slow, solemn, majestic |
| 快拍 | Fast beat | 节奏快速，适合舞曲和活跃片段。 | fast, upbeat, energetic |
| 快速 | Allegro | 明快快速，充满活力和激情。 | fast, energetic, upbeat |
| 流畅速度 | Smooth tempo | 节奏连贯平稳，听感柔和自然。 | flowing, seamless, continuous |
| 律动速度 | Groove tempo | 适合律动和摇摆，带有强烈的节奏感和动感。 | groove, danceable, funky |
| 慢拍 | Slow beat | 节奏缓慢，适合抒情或沉思。 | slow, ballad, mellow |
| 慢速 | Adagio | 缓慢柔和，适合表达感伤、沉思情绪。 | slow, lyrical, expressive |
| 平稳速度 | Calm tempo | 节奏平稳，营造宁静氛围。 | calm, relaxed, steady |
| 强烈速度 | Marcato tempo | 强调节奏感，速度鲜明，带有力量感。 | marked, accented, forceful |
| 弱拍加速 | Subito allegro | 突然快速起来，带来戏剧性转折。 | sudden speed-up, dramatic, surprising |
| 稍快节奏 | Vivace | 生动活泼，带来明快的节奏感。 | lively, brisk, spirited |
| 稍慢 | Ritardando | 逐渐减慢节奏，制造情感张力和变化。 | slowing down, expressive, deceleration |
| 适中速度 | Moderate tempo | 介于慢与快之间，适合多种音乐风格。 | moderate, balanced, versatile |
| 瞬间加速 | Sudden acceleration | 突然加快节奏，增强戏剧效果。 | sudden speed-up, dramatic, surprising |
| 瞬间减速 | Sudden deceleration | 突然放慢节奏，产生张力或停顿感。 | sudden slow down, tension, dramatic |
| 速度忽快忽慢 | Tempo swing | 速度忽快忽慢，产生摇摆感和动感。 | swinging, rhythmic, dynamic |
| 速度渐变 | Tempo modulation | 速度在曲中有明显渐变，增加表现力。 | tempo change, shifting, expressive |
| 速度渐快 | Gradual acceleration | 节奏逐渐变快，增强紧张感。 | speeding up gradually, building, rising |
| 速度渐慢 | Gradual deceleration | 节奏逐渐放慢，缓和情绪。 | slowing down gradually, easing, calming |
| 稳定速度 | Metronomic | 均匀稳定的节奏，没有变速，保持一致性。 | steady, consistent, precise |
| 匀速 | Even tempo | 速度均匀无变化，保持节奏稳定。 | steady, uniform, constant |
| 中快 | Allegretto | 略快于中速，活泼轻快，适合活跃和愉快的氛围。 | moderately fast, cheerful, lively |
| 中慢速 | Andante | 稍慢的步行速度，平稳舒缓，常用于抒情段落。 | walking pace, moderate, relaxed |
| 中速 | Moderato | 适中的速度，平衡明快与柔和，通用广泛。 | moderate tempo, balanced, steady |
| 逐渐加速 | Accelerando | 逐渐加快速度，增强紧张感和动力。 | speeding up, building, intensifying |
| 自由速度 | Rubato | 灵活自由的速度变化，强调表现力，常见于抒情独奏。 | expressive timing, flexible, emotional |

### 乐器

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 | 补充5 |
| --- | --- | --- | --- | --- |
| 贝斯 | Bass Guitar | 低音吉他，提供音乐的低频基础与节奏支撑。 | electric bass, slap bass, fingerstyle |  |
| 贝斯滑奏 | Bass Slide | 贝斯演奏技巧，滑动音符连接，增强律动感。 | slides, legato, funky |  |
| 采样器 | Sampler | 电子设备，用于录制和触发预录制声音片段，广泛用于现代制作。 | loop, trigger, sample pack |  |
| 打击垫 | Drum Pad | 触发打击乐音色的电子设备，便于实时表演与制作。 | MPC pad, finger drumming, MIDI pad |  |
| 大号 | Tuba | 铜管乐器中最低音，支撑管弦乐低音部分。 | bass brass, deep tone, orchestral |  |
| 单簧管 | Clarinet | 木管乐器，音色温暖丰富，常用于古典、爵士乐。 | bass clarinet, Bb clarinet, jazz |  |
| 低音鼓 | Bass Drum | 架子鼓中最大鼓，产生低沉有力的声音，带动节奏。 | kick drum, thump, punch |  |
| 笛子 | Dizi | 中国横吹木管乐器，音色清脆透亮，带有特有的“膜音”。 | membrane, bright tone, folk music |  |
| 电钢琴 | Electric Piano | 模拟钢琴音色的电子乐器，音色温暖柔和，常用于爵士和流行音乐。 | Fender Rhodes, Wurlitzer, smooth |  |
| 电吉他 | Electric Guitar | 以电信号放大演奏的吉他，常用于摇滚、蓝调、流行等多种风格。 | distortion, clean tone, solo |  |
| 电吉他干净音色 | Clean Guitar | 未经过失真处理的电吉他，音色清晰柔和。 | jazzy, crisp, melodic |  |
| 电吉他失真 | Distorted Guitar | 电吉他经过失真效果器处理，音色粗糙激烈，适合摇滚与金属。 | fuzz, overdrive, heavy |  |
| 电子贝斯 | Synth Bass | 通过合成器产生的低音音色，富有现代感，多用于电子舞曲。 | wobble bass, sub bass, punchy |  |
| 电子垫音 | Synth Pad | 合成器背景垫音，营造氛围和空间感。 | lush, atmospheric, sustained |  |
| 电子风琴 | Electronic Organ | 电子模拟管风琴音色，常用于教堂音乐和摇滚。 | Hammond, Leslie effect, soulful |  |
| 电子鼓 | Electronic Drums | 模拟或采样传统鼓组声音的电子打击乐器，带多样音色选择。 | pad triggers, drum machine, MIDI drums |  |
| 电子琴 | Keyboard | 泛指各类电子键盘乐器，音色丰富多样，适用于多种音乐风格。 | synth pad, organ, electric piano |  |
| 电子琴风格音色 | Synth Lead | 合成器主旋律音色，适合突出旋律线条。 | saw wave, lead synth, solo |  |
| 吊镲 | Crash Cymbal | 架子鼓中用于强烈节奏和情绪爆发的镲片，音色明亮。 | crash, splash, accent |  |
| 二胡 | Erhu | 中国拉弦乐器，音色柔美，常用于独奏和伴奏。 | glissando, vibrato, lyrical tone |  |
| 钢琴 | Piano | 常见键盘乐器，音域宽广，适合独奏与伴奏，能表现丰富动态与情感。 | acoustic piano, grand piano, classical |  |
| 古筝 | Guzheng | 中国传统拨弦乐器，音色悠扬清脆，表现力丰富。 | plucking, sliding, pentatonic scale |  |
| 鼓 | Chinese Drum | 中国传统打击乐器，节奏丰富多变，多用于民间和戏曲。 | war drum, festival, powerful |  |
| 管风琴 | Pipe Organ | 传统大型键盘风琴，声音宏大庄严，常见于教堂音乐。 | majestic, sustained, classical |  |
| 管弦乐合成器音 | Orchestral Synth | 合成器模拟管弦乐器的音色，常用于电影配乐和现代流行。 | strings, brass, cinematic |  |
| 合成鼓 | Synth Drum | 电子合成的打击乐声音，广泛用于电子音乐和流行乐。 | electronic beat, punchy, processed |  |
| 合成器 | Synthesizer | 电子乐器，通过合成技术产生多样音色，可模拟传统乐器或创造新声音。 | analog synth, digital synth, patch |  |
| 架子鼓 | Drum Kit | 由多个鼓和钹组成的打击乐器组合，是现代流行、摇滚等风格的节奏核心。 | snare, bass drum, hi-hat, cymbals |  |
| 口琴 | Harmonica | 便携式自由簧乐器，音色清脆，广泛用于布鲁斯、民谣和摇滚。 | blues harp, diatonic, chromatic |  |
| 马林巴 | Marimba | 木质键盘打击乐器，音色柔和丰富，常用于打击乐合奏和现代作品。 | mallets, resonant, warm tone |  |
| 木琴 | Xylophone | 木制键盘打击乐器，音色明亮有力。 | mallets, sharp attack, rhythmic |  |
| 琵琶 | Pipa | 中国弹拨乐器，音色明亮，技巧丰富，适合表现叙事性音乐。 | tremolo, bending, rapid picking |  |
| 萨克斯 | Saxophone | 铜管乐器，音色富有表现力，广泛用于爵士、流行和摇滚。 | alto sax, tenor sax, smooth tone |  |
| 手风琴 | Accordion | 可折叠风箱驱动的自由簧乐器，音色独特，常用于民谣和民族音乐。 | bellows, folk, polka |  |
| 手拍 | Hand Percussion | 手击打击乐器，包括康加鼓、邦戈鼓等，增添自然节奏感。 | congas, bongos, rhythm |  |
| 竖琴 | Harp | 弦乐器，音色清澈透明，常用于古典与新世纪音乐。 | glissando, plucking, classical |  |
| 唢呐 | Suona | 中国传统铜管乐器，音色高亢嘹亮，常用于庆典与戏曲。 | piercing, celebratory, folk |  |
| 小鼓 | Snare Drum | 鼓组中声音清脆的鼓，强调节奏的切分和律动。 | sharp, rimshot, ghost notes |  |
| 小号 | Trumpet | 铜管乐器，音色明亮嘹亮，适合独奏和管乐队。 | mute, bright tone, jazz trumpet |  |
| 旋律口风琴 | Melodica | 手持键盘吹奏乐器，音色类似口琴与风琴结合。 | breathy, reedy, portable |  |
| 扬琴 | Yangqin | 中国击弦乐器，音色清脆，适合伴奏和独奏。 | hammered dulcimer, bright, percussive |  |
| 原声吉他 | Acoustic Guitar | 无需电子放大，声音自然温暖，适合民谣、流行、古典等风格。 | nylon strings, steel strings, strumming |  |
| 长笛 | Flute | 木管乐器，声音清亮柔和，适合独奏及管弦乐。 | piccolo, alto flute, classical |  |
| 长号 | Trombone | 铜管乐器，滑管结构，音色深沉宽广。 | slide, warm tone, jazz trombone |  |
| 震音鼓 | Tom-toms | 架子鼓中无金属边缘的鼓，音色圆润，用于填充节奏。 | floor tom, rack tom, drum fill |  |
| 钟琴 | Glockenspiel | 金属键盘打击乐器，音色清亮明快，多用于管弦乐。 | bright, bell-like, high-pitched |  |

### 中国乐器（唢呐不生效）

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 板钹 | Cymbals | 金属打击乐器，声音明亮，常用于强调节奏。 | metallic, crashing, rhythmic |
| 板鼓 | Bangu | 戏曲中使用的木制小鼓，节奏鲜明，常用于指挥乐队节拍。 | wooden drum, sharp, rhythmic |
| 板胡 | Banhu | 拉弦乐器，音色明亮尖锐，多用于地方戏曲伴奏。 | bowed fiddle, bright, folk tone |
| 梆子 | Bangzi | 木质打击乐器，敲击声响亮，常用于戏曲伴奏。 | wooden clapper, percussive |
| 尺八 | Shakuhachi | 虽为日本传统竹笛，但在中国古典音乐中也有所使用，音色深沉空灵。 | vertical flute, breathy, meditative |
| 笛子 | Dizi | 横吹竹管乐器，音色清晰明亮，能表现丰富情绪，常带有气息声。 | bamboo flute, breathy, lyrical |
| 二胡 | Erhu | 传统拉弦乐器，有两根弦，声音柔美且富有表现力，广泛用于独奏及合奏。 | bowed string, expressive, melancholy |
| 古琴 | Guqin | 古老的七弦弹拨乐器，音色深沉内敛，文人雅士常用。 | zither, quiet, meditative |
| 古筝 | Guzheng | 大型拨弦乐器，具有21弦，声音清脆明亮，常用来演奏传统曲目和现代改编作品。 | plucked zither, bright, shimmering |
| 胡琴 | Huqin | 中国拉弦乐器总称，含二胡、板胡、京胡等，音色多样。 | bowed strings, folk instruments |
| 京胡 | Jinghu | 京剧伴奏专用弦乐器，声音尖细明亮。 | bowed fiddle, high pitch |
| 箜篌 | Konghou | 古代竖琴类拨弦乐器，声音清亮柔美。 | harp, plucked, ancient |
| 口弦 | Jaw Harp | 小型口腔乐器，通过口腔共鸣发声，声音独特。 | twangy, plucked, resonant |
| 锣 | Gong | 大型金属敲击乐器，产生深沉响亮的声音，用于突出节奏与气氛。 | metallic, resonant, crash |
| 琵琶 | Pipa | 四弦拨弦乐器，音色丰富，有多种弹奏技巧，能表现多样情绪。 | plucked lute, fast runs, tremolo |
| 三弦 | Sanxian | 三弦拨弦乐器，音色深沉有力，适合独奏和伴奏。 | plucked lute, deep tone |
| 笙 | Sheng | 多管吹奏乐器，能同时发出多个音，音色和谐清亮，常用于合奏。 | mouth organ, harmonic, reedy |
| 唢呐 | Suona | 高音量吹奏乐器，音色嘹亮，常用于民间庆典和喜庆场合。 | loud, piercing, festive |
| 唢呐 | Suona | 民间吹奏乐器，音色高亢嘹亮，适合热闹场合。 | loud, piercing, festive |
| 铜锣 | Copper Gong | 金属打击乐器，音色浑厚持久，常用于重大仪式和戏剧中。 | metallic, resonant, loud |
| 箫 | Xiao | 竖吹竹笛，音色空灵柔和，适合表现抒情和静谧氛围。 | vertical flute, mellow, airy |
| 小鼓 | Xiao Gu | 小型鼓类打击乐器，节奏清晰，常用于配合舞蹈和戏曲。 | small drum, sharp, rhythmic |
| 牙板 | Clapper | 木质打击乐器，发出清脆拍击声，多用于节奏点缀。 | wooden clapper, rhythmic |
| 扬琴 | Yangqin | 击弦乐器，音色明亮清脆，常在民族乐团中担当和声及节奏。 | hammered dulcimer, bright, metallic |
| 中阮 | Zhongruan | 圆形共鸣箱拨弦乐器，音色温暖柔和，兼具旋律与伴奏功能。 | plucked lute, mellow tone |
| 竹笛 | Bamboo Flute | 由竹子制成的吹奏乐器，音色自然清新，适合多种音乐风格。 | breathy, soft, melodic |
| 竹琴 | Bamboo Zither | 用竹片制成的拨弦乐器，声音清脆悦耳。 | plucked, bright, delicate |

### 演奏技巧

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 变调杆 | Bend | 吉他弦被拉升或放松，音高变化，增加表现力。 | string bend, bluesy, expressive |
| 拨弦 | Plucking | 用手指或拨片弹拨弦乐器发声，音色清晰、颗粒感强。 | fingerstyle, plectrum, articulation |
| 颤音 | Trill | 两个相邻音快速交替演奏，制造装饰效果。 | ornament, rapid alternation, baroque |
| 颤音轮 | Whammy Bar | 电吉他上的颤音杆，通过拉动改变音高产生特殊效果。 | pitch bend, dive bomb, vibrato |
| 颤指 | Finger Vibrato | 手指快速抖动产生音高微小波动，增加人声般的情感表现力。 | expressive, warm, singing-like |
| 吹奏技巧 | Breath Control | 管乐器演奏者控制呼吸气流，影响音色和音量。 | phrasing, sustain, articulation |
| 打击技巧 | Drum Rudiments | 鼓手基础击打组合技术，如单击、双击、滚奏，构成复杂节奏基础。 | paradiddle, flam, drag |
| 弹拨 | Strumming | 用手或拨片扫过多根弦，形成和弦伴奏。 | rhythm guitar, open chords, pattern |
| 弹拨混合 | Hybrid Picking | 吉他技巧，结合拨片与手指弹奏，提升速度与表达力。 | fingerpick, economy picking, versatility |
| 弹跳 | Bounce | 弦乐弓或拨片快速反弹，产生节奏感强的效果。 | rhythmic, percussive, articulation |
| 抖弦 | Tremolo Picking | 吉他快速交替拨弦，制造持续颤音效果，常见于金属与摇滚。 | rapid picking, aggressive, sustained |
| 弓法 | Bowing | 弦乐器用弓摩擦弦发声的技术，包括多种技巧如跳弓、连弓等。 | legato, staccato, spiccato |
| 鼓刷 | Drum Brushes | 鼓刷代替鼓槌，产生柔和刷奏效果，适合爵士或轻音乐。 | soft, swishing, jazz |
| 滚奏 | Tremolo | 快速重复同一音符或两个音符交替，制造紧张或悬疑气氛，常见于钢琴和弦乐。 | rapid, flutter, sustained |
| 和弦分解 | Arpeggio | 和弦音符依次快速弹奏，制造连贯旋律效果。 | broken chords, flowing, melodic |
| 滑音 | Glissando | 快速滑动音高从一个音到另一个音，音符之间连贯流畅。 | portamento, slide, pitch bend |
| 滑奏 | Slide | 演奏者用手指或弓在弦上滑动产生连贯的音高变化，常见于吉他、贝斯和小提琴。 | glissando, legato, smooth transition |
| 滑奏连音 | Hammer-On & Pull-Off | 连续敲击或拉弦技巧，制造连贯音符，适合快速演奏。 | legato, fluid, fast runs |
| 口风琴颤音 | Tonguing | 口风琴或管乐器用舌头控制气流发音，形成清晰音符起始。 | articulation, staccato, legato |
| 快速滑奏 | Rapid Glissando | 非常快速的滑奏，表现技巧熟练，增加激情。 | virtuosic, fast slide, dramatic |
| 力度变化 | Dynamics | 通过改变演奏力度，营造音量层次感和情绪变化。 | crescendo, decrescendo, forte, piano |
| 连弓 | Legato Bowing | 弓持续接触弦发出连贯声音，音符间无明显间断。 | smooth, connected, flowing |
| 漏音 | Dead Note | 弹奏时手指轻按弦但不发声，产生闷音效果。 | muted, percussive, groove |
| 拍弦 | Palm Muting | 用手掌轻压弦使音色变闷，常用于电吉他制造节奏感。 | muted, chunky, rhythmic |
| 敲击 | Tapping | 吉他或贝斯上用手指敲击琴弦，产生清晰音符，常用于独奏技巧。 | finger tapping, hammer-on, pull-off |
| 弱击 | Ghost Notes | 鼓组中轻微敲击音，增加律动层次感但不突出主音符。 | subtle, rhythmic, groove |
| 弱音 | Mute | 通过手、拨片或设备减弱或抑制声音，控制音色或音量。 | palm mute, dampen, stifled |
| 双音 | Double Stop | 弦乐器同时演奏两根弦产生和声音响，增加和声厚度。 | harmony, intervals, chords |
| 跳弓 | Spiccato | 弓离弦轻弹，产生断奏效果，音色轻快清晰。 | detached, bouncing bow, short notes |
| 弦乐拨奏 | Pizzicato | 用手指拨弦而非用弓，产生短促的弹拨声。 | plucked, short, percussive |
| 振弦 | Harmonics | 在弦上轻触产生泛音，音色清亮空灵。 | natural harmonics, artificial harmonics |
| 振音 | Vibrato | 演奏者通过快速变化音高制造颤音效果，增加表现力和情感。 | subtle, expressive, modulation |
| 撞击 | Slap | 贝斯或吉他用手掌打击琴弦制造打击感强烈的音效。 | slap bass, percussive, funky |

### 演唱技巧

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 颤音 | Vibrato | 声音频率微小快速波动，增加演唱的抒情性和丰满度。 | warm, expressive, modulation |
| 颤指 | Fingered Vibrato | 手指轻触脸部或喉部帮助制造颤音，增强细腻情感。 | delicate, subtle, emotional |
| 颤指唱法 | Finger Vibrato | 用手指轻触喉部或脸部产生轻微振动，增强声音的抒情感。 | subtle, expressive, intimate |
| 唱腔变化 | Vocal Runs | 快速演唱一串音符，体现技巧和装饰性。 | melisma, ornamentation, agility |
| 唱腔混合 | Mixed Voice | 综合胸声与头声的唱法，既有力量又有明亮度。 | balanced, versatile, dynamic |
| 持续音 | Sustain | 声音持续拉长，体现音量和气息控制能力。 | long note, controlled, expressive |
| 低音 | Bass Voice | 低沉深厚的男性声部，音色厚重且富有力量。 | deep, rich, resonant |
| 断句 | Staccato | 演唱时音符短促断开，带有节奏感。 | detached, sharp, rhythmic |
| 翻转音 | Flip Note | 快速在两个音高间反复跳跃，制造装饰效果。 | embellishment, vocal agility, melisma |
| 反唱 | Call and Response | 一段唱词由主唱演唱，随后由合唱或乐器回应，形成对话式结构。 | dialogue, interactive, traditional |
| 高音 | Tenor | 男声高音区，明亮而有穿透力。 | bright, strong, expressive |
| 歌声破裂 | Growl Scream | 结合growl和尖叫的唱法，多用于极端金属音乐。 | harsh, intense, guttural |
| 喊声 | Shouting | 大声喊唱，表达激烈情感，多见于摇滚和金属。 | aggressive, raw, energetic |
| 和声 | Harmony | 多声部合唱，制造丰富层次和立体感。 | vocal layers, chords, backing |
| 哼唱 | Humming | 闭嘴哼唱旋律，音色柔和，常用作过渡或伴奏。 | soft, smooth, melodic |
| 哼鸣 | Hum | 轻柔闭嘴哼唱，常用于和声或气氛营造。 | soft, warm, supportive |
| 喉音 | Throat Singing | 利用喉部产生多重音色的唱法，常见于蒙古和图瓦等民族音乐。 | overtone singing, multiphonic, ethnic |
| 急促吐字 | Articulation | 清晰发音，确保歌词或旋律的明晰表达。 | crisp, precise, clear |
| 假声 | Falsetto | 男性歌手用较高音区发声，声音轻柔透明，常用于高音表现。 | airy, high pitch, light tone |
| 假声转真声 | Flip | 快速从假声切换到真声，表现强烈的情绪对比。 | dynamic, expressive, dramatic |
| 口哨唱 | Whistle Register | 极高音区唱法，音色尖锐明亮，通常用于女高音或男高音。 | high pitch, piercing, bright |
| 连唱 | Legato | 音符连贯顺滑地连接，表现柔和流畅的旋律线。 | smooth, flowing, connected |
| 猛烈气息 | Breath Attack | 在音符开始时用力呼气，声音瞬间爆发。 | aggressive, punchy, emphatic |
| 女高音 | Soprano | 女声最高音区，清澈明亮，常用于古典与流行音乐。 | clear, bright, agile |
| 女中音 | Mezzo-Soprano | 女声中音区，音色温暖，介于高音和低音之间。 | warm, rich, flexible |
| 咆哮 | Growl | 粗糙低沉的嗓音，常用于金属或蓝调，带有强烈的情感张力。 | raspy, guttural, intense |
| 喷气音 | Sprechgesang | 介于说话与唱歌之间的表现形式，强调节奏与语调。 | spoken singing, rhythmic, expressive |
| 清唱 | Straight Tone | 唱音不带颤音或装饰，声音纯净直接。 | pure, clear, natural |
| 嗓音破裂 | Voice Break | 声音突然转变或断裂，多用于表达情绪爆发或特定效果。 | emotional, raw, vulnerable |
| 头声 | Head Voice | 介于胸声和假声之间的混合声区，音色明亮但有力度。 | mixed voice, bright, powerful |
| 胸声 | Chest Voice | 低音区发声，声音浑厚有力，常用于强力表达。 | strong, full, resonant |
| 哑音 | Whisper | 用极低音量唱歌，声音轻柔，适合私密或神秘氛围。 | breathy, soft, intimate |
| 中音 | Baritone | 男声中音区，介于低音和高音之间，音色柔和饱满。 | warm, balanced, versatile |
| 装饰音 | Ornamentation | 在主旋律上添加各种装饰性音符或技巧，丰富表现力。 | trills, grace notes, mordents |

### 语言

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 阿拉伯语 | Arabic | 使用阿拉伯语歌词，富有中东特色。 | Middle Eastern, traditional, folk |
| 德语 | German | 使用德语歌词，常见于欧洲流行和工业音乐。 | Deutsch, industrial, electronic |
| 多语言 | Multilingual | 同时使用多种语言歌词。 |  |
| 俄语 | Russian | 使用俄语歌词，东欧和俄罗斯流行文化的代表。 | Slavic, folk, pop |
| 法语 | French | 使用法语歌词，具有浪漫和抒情风格。 | chanson, francophone, romantic |
| 韩语 | Korean | 使用韩语歌词，K-pop的主要语言。 | K-pop, Hangul, Hallyu |
| 葡萄牙语 | Portuguese | 使用葡萄牙语歌词，主要见于巴西和葡萄牙音乐。 | samba, bossa nova, brasileiro |
| 日语 | Japanese | 使用日语歌词，常见于J-pop和动漫音乐。 | J-pop, anime, Nihongo |
| 世界语 | Esperanto | 使用人工语言世界语的歌词，少见但具有特殊文化意义。 | constructed language, universal, sci-fi |
| 泰语 | Thai | 使用泰语歌词，东南亚音乐常用语言。 | Thai pop, Luk thung |
| 西班牙语 | Spanish | 使用西班牙语歌词，拉丁音乐重要语言。 | Latin, reggaeton, español |
| 意大利语 | Italian | 使用意大利语歌词，多用于歌剧和流行音乐。 | opera, classical, romantic |
| 印地语 | Hindi | 使用印地语歌词，印度宝莱坞音乐主要语言。 | Bollywood, filmi, desi |
| 英文 | English | 使用英语的歌词语言，国际通用语言。 | English, Anglo, international |
| 越南语 | Vietnamese | 使用越南语歌词，越南传统及现代音乐语言。 | Vietnamese pop, folk |
| 中文 | Mandarin | 使用普通话或汉语方言的歌词语言。 | Mandarin, Chinese, Putonghua |

### 特色语言（大部分不生效）

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 川话 | Sichuanese | 四川地区汉语方言，语速快且带有独特的语调，常用于川剧及本地民歌。 | 川剧变脸，辣味文化，快速语调，地道川音 |
| 川剧 | Sichuan Opera | 以四川方言演唱，著名的变脸表演结合独特的声腔与动作，戏剧冲突强烈。 | 变脸，川音，武戏，表演张力 |
| 东北话 | Northeastern Mandarin | 东北地区的汉语方言，语速较快，声调质朴，常见于二人转及东北民歌。 | 二人转，东北大鼓，豪爽粗犷，民间表演 |
| 河南话 | Henan Dialect | 中原地区的方言，朴实厚重，带有浓厚的中原文化底蕴，多用于豫剧及民间曲艺。 | 豫剧，浓厚中原味，乡土气息，民间曲艺 |
| 黄梅戏 | Huangmei Opera | 以安徽黄梅地区民歌为基础，旋律明快，歌词通俗，贴近生活，深受群众喜爱。 | 民间曲调，生活气息，明快旋律，通俗易懂 |
| 晋剧 | Jin Opera | 山西地方戏，唱腔豪放质朴，剧目多反映历史与民间故事。 | 豪放唱腔，历史题材，北方民俗，质朴动人 |
| 晋语 | Jin Dialect | 山西及周边地区方言，音节丰富，带有浓厚北方韵味，常用于晋剧及民间曲艺。 | 晋剧，北方味道，浓烈乡音，曲艺传统 |
| 京剧 | Peking Opera | 中国传统戏曲代表，结合唱念做打，角色分明，声腔典雅，表演程式化，融合音乐与戏剧艺术。 | 唱腔，念白，程式化动作，水袖，脸谱 |
| 客家话 | Hakka | 分布于广东、江西等地，音调独特，韵味厚重，常见于客家山歌与地方戏曲。 | 客家山歌，乡情浓郁，客语唱腔，传统民谣 |
| 昆曲 | Kunqu Opera | 中国古老戏曲之一，唱腔委婉悠长，语言典雅，动作优美细腻，被誉为“百戏之师”。 | 古典韵味，婉转唱腔，文雅典故，细腻表演 |
| 梁祝 | Butterfly Lovers Opera | 以《梁祝》爱情故事为基础的地方戏，融合多种戏曲风格，情感丰富，旋律优美。 | 爱情传说，凄美动人，经典剧目，音乐优美 |
| 闽南语 | Minnan (Hokkien) | 福建泉州、厦门、台湾等地的方言，柔美细腻，富含浓厚乡土气息，常见于闽南歌谣与戏曲。 | 台语，乡土情怀，闽南歌谣，柔美婉转 |
| 评剧 | Ping Opera | 河北及北方地区流行，唱腔质朴，剧目多反映民间故事，情节通俗易懂。 | 民间故事，通俗唱腔，河北文化，群众喜爱 |
| 上海话 | Shanghainese | 上海地区方言，声调丰富，口语特色鲜明，流行于沪剧及本土民歌。 | 沪剧，上海滩，黄浦江，方言歌唱 |
| 吴语 | Wu Dialect | 长江三角洲一带方言，发音柔和，音调变化丰富，多用于昆曲及本地民谣。 | 昆曲，江南水乡，温润音色，方言歌唱 |
| 湘语 | Xiang Dialect | 湖南方言，带有浓郁的地方色彩，常见于湘剧及湖南民歌。 | 湘剧，湖南民歌，乡音浓重，地方戏曲 |
| 豫剧 | Yu Opera | 河南地方戏曲，唱腔朴实大方，情感真挚，广泛流传于中原地区。 | 朴实唱腔，中原文化，情感浓烈，乡土气息 |
| 越剧 | Yue Opera | 发源于浙江，唱腔柔美细腻，女性演员居多，情感表达真挚，音乐优美动听。 | 柔美唱腔，江南水乡，女性主导，情感细腻 |
| 粤剧 | Cantonese Opera | 广东地区传统戏曲，唱腔高亢激昂，结合武打与歌舞，融合粤语独特韵味。 | 粤语唱腔，武打表演，粤文化，韵味十足 |
| 粤语 | Cantonese | 广东及港澳地区的汉语方言，带有独特音韵和韵律感，常用于粤剧及流行歌曲。 | 粤语歌，广府话，岭南文化，韵味十足 |

### 音阶与调式

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| Mixolydian调式 | Mixolydian Mode | 大调基础上第七级降半音，产生放松、蓝调风格，常用于摇滚和布鲁斯。 | bluesy, relaxed, dominant seventh vibe |
| 阿拉伯音阶 | Arabic Scale | 采用微分音和特殊音程，带有中东独特韵味。 | maqam, microtones, exotic |
| 变调音阶 | Altered Scale | 基于七声音阶的变音版本，带有大量变音符号，适合现代爵士即兴。 | altered dominant, tension, jazz fusion |
| 颤音音阶 | Tremolo Scale | 指快速重复同音，产生颤抖效果的演奏技巧，与音阶结合形成特殊氛围。 | vibrating, shimmering, tension |
| 大调 | Major Scale | 最常见的西方音阶，音高排列明亮、欢快，具有稳定和谐的感觉，适合大多数流行音乐和传统作品。 | happy, bright, uplifting, diatonic |
| 东亚五声音阶 | East Asian Pentatonic | 以中国、日本、韩国传统音乐为基础的五声音阶，常用宫、商、角、徵、羽五音。 | Chinese folk, traditional, ancient |
| 多利亚调式 | Dorian Mode | 以自然小调为基础，第六级升高半音，音色介于明亮与忧郁之间，常用于爵士和民谣。 | jazzy, minor with brightness, versatile |
| 弗利吉亚调式 | Phrygian Mode | 小调基础上第二级降半音，带有浓厚的西班牙或东方色彩，情绪神秘而紧张。 | Spanish, exotic, tense, dark |
| 哈巴涅拉音阶 | Habanera Scale | 特殊的节奏型与音阶，带有拉丁风情，常用于探戈和拉丁音乐。 | Latin, rhythmic, sensual |
| 和声小调 | Harmonic Minor | 小调基础上将第七级提高半音，产生特殊的东方感和戏剧性，常见于古典和中东音乐。 | exotic, dramatic, Middle Eastern vibe |
| 降半音音阶 | Chromatic Scale | 包含十二个半音的音阶，涵盖所有音高，广泛用于各种音乐即兴和作曲。 | full chromatic, versatile, atonal |
| 降七音阶 | Mixolydian b7 | 常见于布鲁斯和摇滚中的混合调式，给人轻松与浑厚感。 | blues, dominant seventh, rock |
| 蓝调音阶 | Blues Scale | 五声音阶基础上加入蓝调音，带有特殊的忧郁、带感的“蓝调”味道，常用于蓝调和摇滚吉他即兴。 | soulful, gritty, expressive |
| 利底亚调式 | Lydian Mode | 大调基础上第四级升高半音，产生梦幻明亮的氛围，常用于电影配乐和现代流行音乐。 | dreamy, bright, ethereal, floating |
| 洛克里亚调式 | Locrian Mode | 小调基础上第二级和第五级降半音，听起来不稳定且不和谐，少用于主流音乐，多用于现代和实验音乐。 | dissonant, unstable, experimental |
| 全音音阶 | Whole Tone Scale | 由六个全音组成，产生空灵且神秘的感觉，常用于现代音乐和印象派。 | dreamy, ambiguous, impressionist |
| 十二平均律 | Equal Temperament | 现代标准调音系统，十二个半音均分八度，适合各种现代音乐风格。 | standardized tuning, western music |
| 五声音阶 | Pentatonic Scale | 由五个音组成的音阶，广泛用于民间音乐和摇滚，简洁且易于演奏，常带有中国、蓝调风格。 | folk, blues, Chinese, simple |
| 西非音阶 | West African Scale | 非洲传统音乐中的特色音阶，节奏复杂且旋律灵活。 | polyrhythmic, tribal, pentatonic variants |
| 小调 | Minor Scale | 音阶结构带有较多半音和小三度，音色较为忧郁、感伤或深沉，适合表达情感丰富的音乐作品。 | sad, melancholic, emotional, dark |
| 旋律小调 | Melodic Minor | 小调上行时第六和第七级升高半音，下行时恢复自然小调音阶，常用于爵士和古典音乐的旋律中。 | jazz, flexible minor, smooth |
| 印度拉加音阶 | Indian Raga | 印度传统音阶系统，包含特定情绪和时间的音阶组合，讲究旋律和即兴。 | raga, melodic framework, spiritual |
| 增四音阶 | Lydian Dominant Scale | Lydian调式与混合调式结合，常用于爵士和融合音乐，音色明亮且带有张力。 | jazz, bright, altered dominant |
| 增音音阶 | Augmented Scale | 由连续的增二度构成，产生紧张且不稳定的氛围，多用于现代爵士和实验音乐。 | tense, unusual, dissonant |
| 中国五声音阶 | Chinese Pentatonic Scale | 中国传统音乐音阶，音高分别为宫、商、角、徵、羽，带有浓厚民族色彩。 | folk, pentatonic, guzheng, erhu |
| 重音阶 | Octatonic Scale | 八音音阶，交替全音和半音，带有神秘且不稳定的氛围，常见于爵士和现代古典音乐。 | diminished, symmetrical, jazz |
| 自然小调 | Natural Minor | 传统小调音阶，第三、六、七级音符为小音程，音色柔和带忧郁。 | aeolian, soft minor, emotional |
| 自然音阶 | Natural Scale | 指不经调音器调节的纯净音阶，常用于民族音乐和早期音乐。 | just intonation, pure intervals |
| 自由调式 | Modal Scale | 采用不同的教会调式（如多利亚、弗利吉亚等），每种调式都有独特的音高组合和情绪色彩。 | dorian, phrygian, lydian, mystical |

### 旋律走向

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 半音阶走向 | Chromatic | 使用半音阶音程，旋律线条细腻且带有紧张感。 | chromatic, semitones, tense |
| 变化多端 | Varied | 旋律起伏丰富，多变多样，避免单调。 | diverse, dynamic, evolving |
| 波浪形 | Wavy | 旋律呈现起伏波动状，有反复上下的走向，增加动感与丰富性。 | undulating, fluctuating, flowing |
| 持续平稳 | Sustained | 音高基本保持稳定，旋律平稳，营造平静或庄重氛围。 | steady, stable, constant |
| 持续音 | Pedal Tone | 旋律或伴奏中持续一个音，形成稳定基调。 | drone, sustained note, foundation |
| 大跳跃 | Wide Interval | 音高跨度大，产生强烈冲击感。 | leaps, jumps, wide intervals |
| 低沉缓慢 | Low & Slow | 旋律多为低音区，节奏缓慢，气氛沉稳或忧郁。 | deep, slow, somber |
| 断续 | Interrupted | 旋律线断断续续，中间有停顿或断点，增加紧张感或表达特殊情绪。 | broken, staccato, punctuated |
| 反复 | Repetitive | 旋律中有重复段落或短句，增强记忆点与节奏感。 | looping, catchy, motif |
| 复调旋律 | Polyphonic | 多条旋律线交织，产生复杂且丰富的旋律纹理。 | contrapuntal, intertwined, layered |
| 高低跳动 | Angular | 旋律线条锐利，频繁上下跳动，富有活力和不确定感。 | sharp, jagged, dynamic |
| 高亢明亮 | High & Bright | 旋律多处于高音区，声音明亮刺耳，常用于表现激动情绪。 | piercing, bright, soaring |
| 回旋 | Circular | 旋律循环回到起始点，形成完整闭环，给人回归感。 | looping, repetitive, cyclical |
| 急促跳动 | Staccato | 旋律音符短促有力，强调节奏感。 | detached, sharp, clipped |
| 渐强上升 | Crescendo | 旋律逐渐升高并增强音量，常用于表达情绪高潮。 | building, intensifying, rising |
| 渐弱下降 | Decrescendo | 旋律逐渐降低音量和音高，营造渐隐或结束感。 | fading, diminishing, falling |
| 阶梯式 | Stepped | 音高逐渐递增或递减，但步伐清晰有序，类似台阶。 | stepwise, incremental, gradual |
| 模进 | Modulating | 旋律逐渐转调，带来新鲜感和情绪变化。 | key change, shift, progression |
| 轻快跳跃 | Light & Bouncy | 旋律活泼有弹性，节奏轻盈。 | playful, lively, bouncy |
| 上行 | Ascending | 旋律音高逐渐升高，带来向上推进、情绪提升的感觉。 | rising, upward, climbing |
| 抒情 | Lyrical | 旋律柔美流畅，富有歌唱性和表现力。 | expressive, melodic, flowing |
| 跳跃 | Leaping | 旋律中有较大音程跳动，富有活力与张力。 | wide intervals, jumps, leaps |
| 突然转折 | Sudden Change | 旋律线条突然改变方向或调性，制造戏剧性效果。 | abrupt, unexpected, contrast |
| 细腻曲折 | Ornamental | 旋律带有装饰音、倚音、颤音等小细节，增加表现力与华丽感。 | embellished, decorative, flourishes |
| 下行 | Descending | 旋律音高逐渐降低，通常带有缓和、放松或悲伤的情绪色彩。 | falling, downward, descending |
| 线性连贯 | Linear | 旋律平滑流畅，音符紧密连接，给人流动感。 | smooth, connected, flowing |
| 长音持唱 | Legato | 音符连贯平滑，无明显间断，旋律连贯自然。 | smooth, connected, flowing |
| 重复递进 | Sequential | 旋律片段重复但每次调高或调低，形成递进感。 | pattern, transposed, stepwise |
| 装饰性滑动 | Glissando | 旋律快速滑动经过多个音高，产生连续滑奏效果。 | sliding, smooth, continuous |

### 伴奏形式

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 背景铺陈 | Background | 伴奏低调，主要起到衬托和渲染作用。 | subtle, atmospheric, supportive |
| 持续音伴奏 | Sustained | 伴奏中某些音符或和弦持续较长时间，营造平稳、舒缓氛围。 | drone, pad, held notes |
| 打击乐伴奏 | Percussion | 以各种打击乐器构成的伴奏，强调节奏的多样性。 | congas, bongos, shaker |
| 弹唱伴奏 | Strumming | 用拨片或手指扫弦，常见于吉他伴奏。 | guitar strum, rhythmic, acoustic |
| 低音主导 | Bass Driven | 伴奏中低音部分突出，构成整体律动和旋律基础。 | bassline, foundation, groove |
| 电音伴奏 | Synthesized | 电子合成器制作的伴奏，音色丰富多变。 | synth pads, electronic, textured |
| 电子节奏 | Electronic Beat | 电子节奏驱动的伴奏，重视节拍与合成音色结合。 | drum machine, programmed beats |
| 动态伴奏 | Dynamic | 伴奏随情绪或节奏起伏变化丰富，富有表现力。 | expressive, evolving, fluid |
| 反拍伴奏 | Syncopated | 伴奏在非强拍上打节奏，制造律动感。 | offbeat, funky, groove |
| 分层伴奏 | Layered | 多种乐器或音轨叠加，丰富音色和空间感。 | multi-layer, texture, depth |
| 分解和弦 | Arpeggiated | 将和弦音符逐一弹奏，营造连贯流动的伴奏效果。 | broken chords, flowing, guitar |
| 复调伴奏 | Polyphonic | 多条独立旋律线同时伴奏，复杂且层次丰富。 | counterpoint, intertwined, layered |
| 合唱伴奏 | Choral | 以人声和声或合唱形式作为伴奏，增强气氛和层次。 | choir, backing vocals, harmony |
| 和声伴奏 | Vocal Harmony | 人声和声作为伴奏，增加旋律层次与情感深度。 | harmony vocals, backing, lush |
| 和声分解 | Broken Harmony | 和声音符分解开来依次演奏，常用于钢琴等键盘乐器。 | arpeggio, spread chords, delicate |
| 和声填充 | Harmonic Fill | 伴奏在旋律间填充和声，增强音乐层次感。 | backing chords, support, layers |
| 和弦伴奏 | Chordal | 以和弦为主体的伴奏方式，强调和声的支持和丰满感。 | harmony, block chords, lush |
| 滑奏伴奏 | Glissando | 伴奏中使用滑奏技巧，制造连贯流畅的音效。 | sliding notes, smooth, legato |
| 即兴伴奏 | Improvised | 伴奏部分即兴创作，灵活变化，常见于爵士乐。 | spontaneous, free, creative |
| 简洁伴奏 | Minimalist | 伴奏极简，突出主旋律或歌声，减少乐器数量。 | sparse, clean, focused |
| 节奏型伴奏 | Rhythmic | 伴奏强调节奏感，通常打击乐器或弹拨乐器呈现明确节奏。 | percussive, groove, syncopated |
| 静态伴奏 | Static | 伴奏音符或和弦变化少，保持一定音高和节奏，突出旋律。 | drone, sustained, stable |
| 琶音伴奏 | Picking | 多用于吉他等弹拨乐器，逐音拨弦，细腻灵动。 | fingerpicking, delicate, intricate |
| 敲击式伴奏 | Percussive | 以打击乐器或键盘敲击声为主，突出节奏的伴奏方式。 | drum hits, staccato, punchy |
| 弱拍伴奏 | Offbeat | 伴奏强调弱拍或反拍，产生律动感。 | syncopation, groove, reggae style |
| 推进型伴奏 | Driving | 伴奏节奏强烈，推动歌曲节奏前进。 | energetic, propulsive, urgent |
| 旋律伴奏 | Melodic | 伴奏带有独立旋律线，与主唱或主旋律互动。 | countermelody, harmony, interplay |
| 循环伴奏 | Looping | 伴奏段落循环重复，形成循环节奏和和声背景。 | repetitive, groove, steady |
| 走动贝斯 | Walking Bass | 贝斯线条连续上下移动，形成流畅的低音线，常见于爵士和布鲁斯。 | bass line, smooth, jazzy |

### 年代感

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 1920年代 | 1920s Jazz Age | 爵士起源时期，铜管乐器、摆动节奏、查尔斯顿舞风。常见于复古酒吧、无声电影配乐。 | swing, ragtime, vintage brass, Charleston |
| 1930年代 | 1930s Swing Era | 大乐队流行，节奏强烈，风格华丽，偏娱乐取向。 | big band, crooner, vintage mic |
| 1940年代 | 1940s Wartime | 二战背景，爱国题材浓厚，也孕育Bebop、Blues风格。 | bebop, wartime radio, classic mono |
| 1950年代 | 1950s Rockabilly | 摇滚乐与乡村融合，早期Elvis风格，立麦录音、复古吉他。 | rock'n'roll, slap bass, vinyl crackle |
| 1960年代 | 1960s Psychedelic | 嬉皮士文化、迷幻摇滚、实验性强，鼓励个性表达。 | psychedelic, analog delay, peace vibe |
| 1970年代 | 1970s Funk/Disco | 放克节奏强烈，Disco舞曲开始流行，合成器初现。 | funky bassline, wah guitar, glitter |
| 1980年代 | 1980s Synthwave | 合成器流行、New Wave、早期电子舞曲，标志性鼓机和声码器。 | 808 drum, neon, gated reverb, VHS |
| 1990年代 | 1990s Golden Hip-hop | 嘻哈鼎盛期，Boom Bap鼓点、采样文化盛行。 | boom bap, record sampling, gritty |
| 2000年代 | 2000s Pop-Rock | 数字化初期，流行与摇滚交融，电台友好型制作音色。 | radio pop, clean guitar, synthetic drums |
| 2010年代 | 2010s Trap/EDM | 现代化电子舞曲与Trap的兴起，声音更“数字感”。 | sidechain, autotune, 808, EDM drop |
| 2020年代 | 2020s Gen-Z Pop | 情绪细腻、融合多种风格、强调制作精细、网络文化深度融合。 | bedroom pop, glitch, minimal trap, TikTok vibe |
| 80年代新浪潮 | New Wave | 80年代新潮音乐，结合朋克和电子元素，强调时尚和艺术感。 | synth, post-punk, arty |
| 巴洛克时期 | Baroque Era | 17-18世纪欧洲音乐风格，强调复杂装饰音和对位，典型作曲家如巴赫、亨德尔。 | ornamentation, counterpoint, harpsichord |
| 大乐队时代 | Big Band Era | 20世纪30-40年代大型爵士乐团盛行，注重编排和舞曲风格。 | swing, brass, danceable |
| 迪斯科时代 | Disco Era | 70年代盛行的舞曲风格，强调律动和现场感。 | dancefloor, four-on-the-floor, groove |
| 电子舞曲时代 | EDM Era | 2000年代以来，电子舞曲成为全球主流音乐风格。 | festival, drop, DJ culture |
| 独立音乐兴盛 | Indie Boom | 2000年代独立音乐快速发展，强调原创和非主流。 | DIY, lo-fi, alternative |
| 复古风 | Retro Style | 对旧时代音乐元素的现代致敬，常有颗粒感、磁带噪音、老设备复刻。 | tape hiss, lo-fi, analog warmth |
| 古典时代 | Classical Period | 18世纪晚期至19世纪初，注重结构严谨与和声平衡，如莫扎特、海顿。 | chamber, formal orchestra, period strings |
| 古典时期 | Classical Era | 18世纪晚期至19世纪初，强调形式严谨、旋律清晰，代表人物包括莫扎特和海顿。 | sonata form, clarity, balanced |
| 后现代主义 | Postmodernism | 20世纪后半叶，混合多种风格与元素，反传统，强调多样性和跨界融合。 | eclectic, irony, fusion |
| 近未来（想象） | Near-Future Imagined | 模拟虚拟时代音景，结合AI、数字语音、超现代合成器。 | AI vocal, holographic reverb, synthetic orchestra |
| 经典流行时代 | Classic Pop Era | 50-70年代流行音乐黄金时期，注重旋律和和声。 | melodic, harmony, timeless |
| 经典摇滚回潮 | Classic Rock Revival | 传统摇滚风格在现代重新流行。 | guitar solos, anthemic, vintage |
| 爵士复兴 | Jazz Revival | 现代音乐中爵士元素的回归与创新。 | neo-soul, acid jazz, improvisation |
| 浪漫时期 | Romantic Era | 19世纪，音乐情感丰富，强调个性表达和色彩变化，代表作曲家包括舒伯特、柴可夫斯基。 | expressive, dramatic, lyrical |
| 浪漫主义 | Romantic Period | 情感表达强烈、旋律优美、注重戏剧张力，如肖邦、李斯特、柴可夫斯基。 | expressive, rubato, lyrical melody |
| 民谣摇滚 | Folk Rock Era | 60年代民谣与摇滚结合，注重歌词与音乐结合。 | acoustic-electric, storytelling, protest |
| 民族复兴 | Folk Revival | 20世纪中期对传统民谣和民族音乐的重新发掘与流行。 | acoustic, protest songs, roots |
| 民族音乐兴起 | World Music Boom | 20世纪末全球多民族音乐融合与传播兴盛。 | fusion, cultural, traditional |
| 朋克复兴 | Punk Revival | 90年代及以后对70年代朋克音乐的重新兴起和演绎。 | pop punk, garage, DIY |
| 朋克时代 | Punk Era | 1970年代末朋克音乐兴起，反叛、简单直接的音乐表达。 | DIY, rebellious, fast |
| 数字时代 | Digital Age | 21世纪，数字技术广泛应用于音乐创作、分发与消费。 | streaming, digital production, remix |
| 网络时代 | Internet Era | 网络推动音乐传播，催生新型创作和互动形式。 | viral, meme music, DIY |
| 未来主义风格 | Futuristic Sound | 假想未来的音色设计，合成器实验、空间扭曲、非自然构成。 | sci-fi, cyberpunk, glitchscape, alien synth |
| 文艺复兴 | Renaissance | 声部对称，合唱精巧，音乐多用于宗教或宫廷。 | motet, polyphony, lute |
| 嘻哈黄金时代 | Golden Age Hip-hop | 1980s-1990s嘻哈音乐的黄金时期，特色是创新采样和歌词内容丰富。 | boom bap, sampling, storytelling |
| 嘻哈新潮 | New Wave Hip-hop | 新兴嘻哈风格，融合trap和电子元素，注重情绪表达。 | trap beats, melodic rap, autotune |
| 现场音乐潮 | Live Music Era | 现场音乐体验的重要性提升，强调现场感和互动。 | concert, crowd, improvisation |
| 现代主义 | Modernism | 20世纪初出现，强调创新和破坏传统音乐结构，多采用无调性和复杂节奏。 | atonal, dissonant, experimental |
| 新世纪音乐 | New Age Era | 1980年代以后兴起，注重冥想放松和环境音乐。 | ambient, meditative, soothing |
| 硬核时代 | Hardcore Era | 硬核朋克及硬核电子音乐的发展时期，强调激烈节奏和情绪。 | aggressive, fast, underground |
| 中世纪 | Medieval Music | 教会音乐、格里高利圣咏为主，使用自然音程，旋律单一。 | chant, monophonic, archaic |

### 视觉关联

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 超现实主义 | Surrealism | 非逻辑梦境般构图，常配合迷幻、艺术摇滚等风格。 | Dali, melting objects, eye motif |
| 动漫风格 | Anime Style | 灵感源自日本动漫的视觉设计，强调可爱、戏剧化或幻想元素。 | manga, magical girl, chibi, sakura |
| 封面构图风格 | Album Art Style | 唱片封面的美术语言，比如摄影、插画、抽象画等。 | illustrated, minimalist cover, photography |
| 复古美学 | Retro Aesthetic | 受80、90年代或更早期文化启发的视觉风格，具有浓重年代感。 | VHS, neon, vintage, analog, glitch |
| 哥特视觉 | Gothic Visual | 黑暗、浪漫与神秘结合，常用于摇滚、金属、哥特流派中。 | dark lace, cemetery, victorian, crucifix |
| 黑白影像 | Monochrome | 黑白影调，强调对比与构图，常与Jazz或古典氛围搭配。 | noir, grayscale, silent film |
| 极简主义 | Minimalist | 简洁结构、色块构图、强调留白与精炼感。 | white space, geometric, Bauhaus, symmetry |
| 街头风格 | Street Aesthetic | 涂鸦、滑板、潮牌与都市文化视觉融合，适合Hip-hop等类型。 | graffiti, sneaker culture, concrete jungle |
| 奇幻魔法 | Fantasy / Magic | 魔法世界、美术设定或童话氛围常见于戏剧性或幻想音乐。 | dragon, spellbook, elf, castle, stars |
| 赛博朋克 | Cyberpunk | 都市科技与反乌托邦结合的视觉风格，夜景霓虹与混乱感强烈。 | neon rain, dark city, augmented reality |
| 社交视觉流行感 | Social Visual Trend | 符合社交媒体传播审美的视觉元素，如短视频封面、滤镜、emoji风格等。 | trending filter, emoji, meme-inspired |
| 实验拼贴 | Collage / Glitch Art | 图像打乱与再构造，常见于先锋电子、噪音等音乐的视觉延展。 | photomontage, distortion, zine style |
| 未来主义 | Futuristic | 科幻感强、科技感视觉元素，配合电子或未来风格音乐。 | cyber, AI, chrome, hologram, LED |
| 舞台灯光 | Stage Lighting | 舞台配色、灯光效果与表演呼应的视觉元素，适用于演唱会风格说明。 | strobe, LED wall, color wash, spotlight |
| 虚拟角色设定 | Avatar / Virtual ID | 用于Vtuber或虚拟歌手等角色视觉设计，强调辨识度和拟人化设定。 | virtual idol, anime eyes, character outfit |
| 炫彩梦幻 | Dreamcore / Rainbow | 色彩绚烂、模糊梦境感，适合轻松、童话般的音乐。 | rainbow filter, sparkles, cloudscape |
| 蒸汽波 | Vaporwave | 网络怀旧感，融合千禧年初期网页、日文、3D雕像等元素。 | retro web, pastel grid, glitch art |
| 中式美学 | Oriental / Chinese Style | 融合中国传统元素如水墨、剪纸、宫廷或民族服饰的视觉风格。 | hanfu, ink painting, red lantern, fan dance |
| 装置艺术感 | Installational / Art | 灵感源于当代美术馆装置的视觉感受，抽象或主题性强。 | kinetic sculpture, projection mapping |
| 自然意象 | Nature-inspired | 花草树木、自然色彩、山水风景为主视觉风格，配合民谣或环境音乐。 | forest, river, bamboo, organic texture |

### 混音

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 侧链门限 | Sidechain Gate | 基于侧链信号控制门限开闭，用于节奏感控制。 | gating, rhythmic gating |
| 低频增强 | Bass Boost | 增强低频段，使声音更有力量和厚重感。 | sub-bass, low end, punch |
| 低切滤波 | High-pass Filter | 削减低频部分，减少杂音和浑浊感。 | cutoff frequency, roll-off |
| 高频增强 | Treble Boost | 增强高频段，增加声音明亮度和清晰度。 | sparkle, air, brightness |
| 高切滤波 | Low-pass Filter | 削减高频部分，制造温暖或朦胧的音效。 | cutoff frequency, smooth roll-off |
| 合唱 | Chorus | 使声音听起来像多个声部一起演唱，增加厚度和宽度。 | modulation, depth, rate |
| 混响 | Reverb | 模拟声波在空间中反射的效果，增加声音空间感和自然感。 | hall, room, plate, decay |
| 均衡 | EQ (Equalization) | 调节不同频率段的音量，增强或削减特定频率，改善整体音质平衡。 | high pass, low shelf, mid boost |
| 立体声分离 | Stereo Separation | 将音频信号拆分到不同声道，增强空间感。 | L/R separation, mid/side processing |
| 立体声合成 | Stereo Synthesis | 利用多轨或多声道技术合成宽广立体声效果。 | multitrack, spatial synthesis |
| 立体声扩展 | Stereo Imaging | 调整声像宽度，让声音在左右声道空间中定位清晰。 | panning, widening, stereo spread |
| 立体声压缩 | Stereo Compression | 对立体声信号进行动态控制，保持声像稳定。 | glue compression, bus compression |
| 立体声增强 | Stereo Enhancer | 增加音频的空间感和宽度，令声音更具立体效果。 | width control, mid-side widening |
| 母带处理 | Mastering | 对混音后的音频进行最终处理，确保在各种播放设备上的最佳表现。 | loudness, final EQ, limiting |
| 旁链压缩 | Sidechain Compression | 利用一个信号触发压缩另一个信号，常用于舞曲节奏感营造。 | pumping, ducking, rhythmic compression |
| 频率切割 | Notch Filter | 精确削减特定频率，去除刺耳或干扰声。 | narrow bandwidth, frequency removal |
| 频谱分析 | Spectrum Analyzer | 视觉化展示音频频率分布，帮助调节均衡和动态。 | FFT, real-time analysis |
| 频谱重塑 | Spectral Shaping | 调节音频频谱特性，优化频率分布。 | EQ curves, frequency balancing |
| 去噪 | Noise Reduction | 减少录音中的背景噪音或嗡嗡声，提升音频纯净度。 | hiss removal, gate, denoiser |
| 声像调整 | Panning | 控制声音在左右声道的位置分布，制造空间层次。 | left, right, center |
| 声音隔离 | Vocal Isolation | 从混音中分离人声或乐器，方便后期处理。 | acapella extraction, instrument separation |
| 失真 | Distortion | 增加声音的失真效果，制造粗糙、破裂的音色。 | overdrive, fuzz, saturation |
| 瞬态增强 | Transient Shaping | 调节声音的攻击性和衰减，增强打击感或柔化音色。 | attack, sustain, transient control |
| 限幅 | Limiting | 防止信号超过最大音量，避免失真，保持音频峰值稳定。 | ceiling, brickwall, peak limiter |
| 响度归一化 | Loudness Normalization | 将不同音频的响度调整至统一标准，保证听感一致。 | LUFS, RMS, normalization |
| 压缩 | Compression | 控制音量动态范围，减少响度差异，使声音更紧凑均衡。 | threshold, ratio, attack, release |
| 延迟 | Delay | 产生重复回声效果，可用来营造空间感或节奏感。 | slapback, ping pong, feedback |
| 增益调整 | Gain Control | 调节音频信号的整体音量大小。 | input gain, output gain |
| 中频增强 | Mid Boost | 增强中频段，突出人声和乐器的存在感。 | vocal presence, guitar midrange |
| 自动调节 | Automation | 在不同时间点动态调节音量、声像等参数，增强表现力。 | fade in/out, volume ride, panning move |

### 混音风格

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 干混 | Dry Mix | 几乎不使用混响或延迟的混音风格，声音贴近、清晰，适合突出人声或节奏。 | dry, upfront, clean vocal |
| 湿混 | Wet Mix | 使用大量混响、延迟等效果器处理，营造空间感和氛围感。 | reverb-heavy, dreamy, washed out |
| Lo-fi 混音 | Lo-fi Mixing | 保留背景噪音、压缩质感、低保真音质，突出复古、模拟或情绪感。 | tape hiss, vinyl crackle, warm saturation |
| Hi-fi 混音 | Hi-fi Mixing | 音质高清晰、高动态，频段均衡精致，常用于商业流行音乐或电影配乐。 | high resolution, clarity, stereo width |
| 模拟风混音 | Analog-style Mix | 使用磁带饱和、模拟压缩、复古EQ等手段模拟模拟设备音质。 | tape saturation, analog warmth, vintage feel |
| 数字风混音 | Digital-style Mix | 声音精准、清晰、现代，频率控制精细，常用于电子流行、现代嘻哈等。 | crisp, bright, digitally clean |
| 空间混音 | Spatial Mix | 强调声场空间布置，通过混响/延迟/声像营造立体感、深度感。 | wide stereo, 3D space, ambient depth |
| 中心聚焦混音 | Center-focused Mix | 主要元素集中在中间声像，如主唱、人声等，其他元素靠边布置。 | mono vocal, centered lead, punchy center |
| 环绕声混音 | Surround Mix | 多声道布局（如5.1、7.1或Atmos），用于电影或沉浸式体验。 | Dolby Atmos, cinematic, immersive |
| 房间感混音 | Roomy Mix | 带有自然房间混响效果，仿佛在一个真实空间录音。 | room reverb, natural echo, intimate feel |
| 广播混音 | Broadcast Mix | 动态压缩较强，频率集中中段，适用于电视、广播或小音箱播放。 | radio-ready, compressed vocal, mid-forward |
| 俱乐部混音 | Club Mix | 增强低频与节奏感，适合夜店、大空间音响系统播放。 | punchy kick, sub bass, stereo spread |
| 演出实况混音 | Live Mix | 保留舞台噪声与观众声音，带有真实演出现场感。 | crowd noise, ambient mic, reverb tail |
| 混响导向混音 | Reverb-driven Mix | 大量使用混响作为情绪驱动或主要空间特征。 | lush reverb, cathedral feel, ambient swell |
| 延迟导向混音 | Delay-driven Mix | 使用延迟回声形成律动感或制造情绪氛围。 | echo feedback, ping-pong delay, rhythmic slapback |
| 对比混音 | Contrast Mix | 明显突出不同频段/空间层次元素，如极低频 vs 极高频、干声 vs 湿声。 | dry vs wet, low vs bright, punch vs wash |
| 层次分明混音 | Separated Mix | 各元素位置、频率、音量层次分明，避免堆叠与遮盖。 | clear layers, frequency separation, clean mix |
| 压缩导向混音 | Compression-heavy Mix | 使用大量压缩器控制动态，使整体音量稳定、密实。 | glued sound, squashed, tight mix |
| 自然混音 | Natural Mix | 尽可能还原原始乐器或人声音质，减少人为效果干预。 | transparent, minimal processing, acoustic feel |
| 极简混音 | Minimalist Mix | 乐器或声部数量较少，混音重点在留白和空间感。 | sparse, roomy, intimate mix |
| 宽频混音 | Full-spectrum Mix | 全频段丰满，低频、中频、高频分布均衡。 | deep bass, silky highs, balanced tone |
| 热混音 | Warm Mix | 中低频饱满、柔和，不刺耳，营造温暖氛围。 | warm tone, soft transients, analog feel |
| 冷混音 | Cold Mix | 高频突出、空间感冷峻，适合极简电子或未来感音乐。 | metallic, icy highs, digital sharpness |
| 压抑感混音 | Compressed Feel | 音频动态范围收缩，声音饱满但略显压抑，突出情绪张力。 | dense, brickwall, saturated mid |
| 宽松感混音 | Open Feel Mix | 动态保留多，空间留白，声音通透、轻松自然。 | airy, dynamic, live-sounding |
| 徽标风混音 | Signature Mix | 具有某制作人独特混音习惯/标识音色。 | signature sound, personal flavor, trademark vibe |
| 虚拟空间混音 | Virtual Space Mix | 利用人工声学建模创建不存在的空间感，如“虚拟舞台”或“想象空间”。 | synthetic space, VR audio, surreal mix |
| 精致混音 | Polished Mix | 频段、响度、空间处理精细，专业标准，打磨感强。 | radio ready, final polish, high-end finish |
| 粗糙混音 | Rough Mix | 预览版或带有粗糙处理痕迹的混音，可能保留创作即兴感。 | demo mix, raw edges, unpolished |

### 声场和空间感

| 分类 | 英文描述 | 中文描述 | 常见关键词搭配 |
| --- | --- | --- | --- |
| 宽广 | Wide | 声音从左右声道广泛扩展，制造宽阔开阔的听觉体验。 | wide stereo, expansive, panoramic |
| 窄聚 | Narrow | 声音集中于中心，声场紧凑，强调中频信息。 | mono-ish, narrow stereo, centered |
| 环绕 | Surround | 模拟环绕声布局，营造前后左右包围感，适合影视或3D空间音乐。 | immersive, 360-degree, spatial audio |
| 空灵 | Airy | 高频延展丰富，带有“空气感”，听感轻盈而透明。 | bright air, open top end, breathy |
| 密集 | Dense | 多个声部层叠，空间充满感强，但可能牺牲部分清晰度。 | compact, wall of sound, saturated |
| 深邃 | Deep | 声音纵向布局清晰，有明显的前-中-后景深层次。 | front-back staging, depth perception |
| 扁平 | Flat | 空间层次感弱，声音平铺，缺乏纵深。 | flat stage, compressed field |
| 远场 | Distant | 听感像是从远处传来，含有大量混响和高频衰减。 | reverb-heavy, muffled highs, background |
| 近场 | Close-up | 声音贴近耳边，细节清晰，常用于人声或独奏突出。 | intimate, dry vocal, close mic |
| 左侧定位 | Left-panned | 声音主偏左声道，制造方向感。 | hard left, stereo panning |
| 右侧定位 | Right-panned | 声音主偏右声道，制造方向感。 | hard right, stereo panning |
| 中央定位 | Centered | 声音保持在声场正中，适合主唱或主乐器。 | mono center, main vocal, anchor position |
| 空间移动感 | Movement / Panning | 声音在左右或前后移动，带有动态空间感。 | auto-pan, swirling, shifting field |
| 有回响 | Echoic | 声音带有清晰的延迟或重复，增强空间感。 | echo, delay, bounce-back |
| 干净（无空间） | Dry | 声音无混响或空间处理，干净直接，适合清晰传达。 | dry signal, upfront, no effects |
| 湿润（空间强） | Wet | 大量使用混响与延迟，空间效果浓烈。 | reverb-heavy, ambient wash |
| 房间感 | Roomy | 模拟自然房间回响，中小空间感。 | small room, natural verb |
| 大厅感 | Hall-like | 声音如在音乐厅中反射，适合交响、古典、氛围音乐。 | concert hall, cathedral, lush reverb |
| 教堂感 | Cathedral / Church | 高混响、低频延展，制造庄严神圣感。 | reverb tail, sacred, spacious |
| 工作室感 | Studio-like | 空间干净利落，混音均衡，无夸张空间处理。 | studio clean, flat room |
| 空间合成 | Synthetic Space | 使用合成器或效果器模拟非自然空间，如宇宙、虚拟空间。 | sci-fi, artificial verb, futuristic echo |
| 立体声增强 | Stereo Enhancement | 使用扩展器增强宽度，提升左右声道的分离度。 | stereo widener, haas effect, phase delay |
| 双重空间 | Dual Stage | 同时存在两个空间层，如主干+背景混响，增强立体层次。 | dry/wet blend, dual verb |
| 突出前景 | Forward Projection | 主体音在前，中高频清晰，有穿透力。 | present, push forward, crisp |
| 强后景 | Strong Background | 背景音丰富，制造氛围或层次感，主音相对弱化。 | ambient bed, background pad |
| 光滑空间 | Smooth Spatial Blend | 空间层次过渡自然，元素之间无明显剪切感。 | cohesive, polished stereo |
| 空间失真 | Spatial Distortion | 故意打破空间定位逻辑，营造实验或扭曲感。 | broken panning, warped reverb, surreal |
| 悬浮感 | Floating | 音源不固定，像漂浮在空中，常用于氛围或电子音乐。 | dreamy, weightless, ambient float |
| 紧贴感 | Tightly Packed | 声源集中、分离度低，增强压迫与集中感。 | compact stereo, center-heavy, crushed space |
| 多层空间 | Layered Field | 不同声部被置于不同空间层中，营造复杂听觉场景。 | layered reverb, multi-depth, background contrast |

## 10. 普通音乐术语中英文参考

本节用于理解、翻译和组合提示词。除非某个术语能清楚描述段落事件，否则不要机械地把它包装成歌词内元标签。

### Music Terms 音乐术语

| English term | 中文 |
| --- | --- |
| solo | 独奏 |
| guitar riff | 吉他即兴重复段 |
| chorus | 副歌 |
| verse | 主歌 |
| bridge | 过渡段 |
| melody | 旋律 |
| harmony | 和声 |
| rhythm | 节奏 |
| tempo | 速度 |
| beat | 拍子 |
| bassline | 低音线 |
| chord progression | 和弦进行 |
| hook | 钩子（吸引人的部分） |
| intro | 前奏 |
| outro | 尾奏 |
| interlude | 间奏 |
| accompaniment | 伴奏 |
| modulation | 转调 |
| dynamics | 力度 |
| syncopation | 切分音 |
| improvisation | 即兴演奏 |
| key signature | 调号 |
| time signature | 拍号 |
| octave | 八度 |
| scale | 音阶 |
| arpeggio | 琶音 |
| cadenza | 华彩乐段 |
| motif | 动机 |
| crescendo | 渐强 |
| diminuendo | 渐弱 |

### Vocal Effects 人声效果

| English term | 中文 |
| --- | --- |
| reverb | 混响 |
| delay | 延迟 |
| echo | 回声 |
| auto-tune | 自动调音 |
| vibrato | 颤音 |
| pitch shift | 音高变化 |
| harmonizer | 和声器 |
| chorus effect | 合唱效果 |
| distortion | 失真 |
| compression | 压缩 |
| de-esser | 去齿音 |
| flanger | 镶边效果 |
| phaser | 移相效果 |
| doubling | 加倍效果 |
| megaphone effect | 扩音器效果 |
| robotic voice | 机器人声音 |
| reverse reverb | 反向混响 |
| pitch correction | 音高校正 |
| vocal fry | 低喉音 |
| growl | 咆哮 |
| scream | 尖叫 |
| whisper | 耳语 |
| falsetto | 假声 |
| head voice | 头声 |
| chest voice | 胸声 |
| belting | 强唱 |
| overdrive | 过载 |
| formant shift | 共振峰变化 |
| gating | 噪声门 |

### Spoken Terms 口语术语

| English term | 中文 |
| --- | --- |
| narration | 叙述 |
| dialogue | 对话 |
| monologue | 独白 |
| voice-over | 画外音 |
| intonation | 语调 |
| diction | 发音 |
| accent | 口音 |
| inflection | 语调变化 |
| articulation | 发音清晰度 |
| projection | 声音投射 |
| pause | 停顿 |
| emphasis | 强调 |
| cadence | 抑扬顿挫 |
| rhythm | 节奏 |
| tone | 音调 |
| pitch | 音高 |
| pace | 速度 |
| fluency | 流利度 |
| delivery | 表达 |
| expression | 表情 |
| clarity | 清晰度 |
| volume | 音量 |
| modulation | 调制 |
| resonance | 共鸣 |
| vocal sample | 人声样本 |

### Tempo Terms 速度术语

| English term | 中文 |
| --- | --- |
| allegro | 快板 |
| andante | 行板 |
| adagio | 柔板 |
| presto | 急板 |
| largo | 广板 |
| moderato | 中板 |
| vivace | 活泼的 |
| accelerando | 渐快 |
| ritardando | 渐慢 |
| rubato | 自由速度 |
| lento | 慢板 |
| prestissimo | 最急板 |
| grave | 庄板 |
| agitato | 激动的 |
| tempo | 速度 |
| metronome | 节拍器 |
| beat | 拍子 |
| pulse | 脉搏 |
| bpm (beats per minute) | 每分钟拍数 |
| steady | 稳定的 |
| up-tempo | 快速的 |
| slow | 慢的 |
| medium tempo | 中速 |
| tempo change | 速度变化 |

### Instrument Terms 乐器术语

| English term | 中文 |
| --- | --- |
| piano | 钢琴 |
| guitar | 吉他 |
| violin | 小提琴 |
| drums | 鼓 |
| bass | 低音吉他 |
| flute | 长笛 |
| trumpet | 小号 |
| saxophone | 萨克斯 |
| cello | 大提琴 |
| clarinet | 单簧管 |
| trombone | 长号 |
| harp | 竖琴 |
| synthesizer | 合成器 |
| keyboard | 键盘 |
| accordion | 手风琴 |
| oboe | 双簧管 |
| tuba | 大号 |
| mandolin | 曼陀林 |
| banjo | 班卓琴 |
| ukulele | 尤克里里 |
| electric guitar | 电吉他 |
| acoustic guitar | 原声吉他 |
| bass guitar | 低音吉他 |
| viola | 中提琴 |
| double bass | 低音提琴 |
| piccolo | 短笛 |
| bassoon | 巴松管 |
| harmonica | 口琴 |
| marimba | 马林巴 |
| xylophone | 木琴 |
| tambourine | 铃鼓 |
| congas | 康加鼓 |
| bongos | 邦戈鼓 |
| tabla | 塔布拉鼓 |
| didgeridoo | 迪吉里杜管 |
| bagpipes | 风笛 |
| kazoo | 卡祖笛 |
| theremin | 特雷门琴 |
| sitar | 西塔琴 |
| triangle | 三角铁 |
| castanets | 响板 |
| timpani | 定音鼓 |
| glockenspiel | 钟琴 |
| vibraphone | 颤音琴 |
| dulcimer | 扬琴 |
| clavichord | 古钢琴 |
| harpsichord | 羽管键琴 |
| melodica | 口风琴 |
| pan flute | 排箫 |
| ocarina | 陶笛 |
| steel drum | 钢鼓 |
| bouzouki | 布祖基琴 |
| saz | 萨兹琴 |
| zither | 齐特琴 |
| hurdy-gurdy | 手摇风琴 |
| shamisen | 三味线 |
| koto | 古筝 |
| erhu | 二胡=Suno中暂为[Chinese violin] |
| guqin | 古琴 |
| pipa | 琵琶 |
| djembe | 非洲鼓 |
| cajón | 木箱鼓 |
| talking drum | 说话鼓 |
| agogo | 阿戈戈鼓 |
| berimbau | 贝林巴乌琴 |
| cuíca | 库伊卡鼓 |
| bansuri | 班苏里笛 |
| sarangi | 萨朗吉琴 |
| mridangam | 米尔丹加姆鼓 |
| santoor | 桑图尔琴 |
| veena | 维纳琴 |
| baglama | 巴拉马琴 |
| bawu | 巴乌 |
| shakuhachi | 尺八 |
| taiko | 太鼓 |
| zhonghu | 中胡 |
| tar | 塔尔琴 |
| oud | 乌德琴 |
| kanun | 卡农琴 |
| bamboo flute | 竹笛 |
| crumhorn | 克鲁姆管 |
| sackbut | 萨克布特长号 |
| serpent | 蛇形管 |
| viola da gamba | 维奥拉琴 |
| theorbo | 大琉特琴 |
| lute | 琉特琴 |
| bandoneon | 班多钮手风琴 |
| concertina | 六角手风琴 |
| hurdy-gurdy | 手摇风琴 |
| nyckelharpa | 钥匙竖琴 |
| glass harmonica | 玻璃琴 |
| ondes Martenot | 马特诺琴 |
| tenor horn | 次中音号 |
| baritone horn | 上低音号 |
| euphonium | 次中音号 |
| alto saxophone | 中音萨克斯 |
| tenor saxophone | 次中音萨克斯 |
| baritone saxophone | 上低音萨克斯 |
| soprano saxophone | 高音萨克斯 |
| flugelhorn | 翼号 |

### Music Notation 音乐记谱

| English term | 中文 |
| --- | --- |
| treble clef | 高音谱号 |
| bass clef | 低音谱号 |
| staff | 五线谱 |
| bar line | 小节线 |
| measure | 小节 |
| time signature | 拍号 |
| key signature | 调号 |
| sharp | 升号 |
| flat | 降号 |
| natural | 还原号 |
| note | 音符 |
| rest | 休止符 |
| whole note | 全音符 |
| half note | 二分音符 |
| quarter note | 四分音符 |
| eighth note | 八分音符 |
| sixteenth note | 十六分音符 |
| whole rest | 全休止符 |
| half rest | 二分休止符 |
| quarter rest | 四分休止符 |
| eighth rest | 八分休止符 |
| sixteenth rest | 十六分休止符 |
| dotted note | 附点音符 |
| tie | 连音线 |
| slur | 圆滑线 |
| staccato | 断奏 |
| legato | 连奏 |
| accent | 重音 |
| fermata | 延长记号 |
| repeat sign | 反复记号 |
| coda | 结尾段 |
| fine | 终止 |
| crescendo | 渐强 |
| decrescendo | 渐弱 |
| dynamic markings | 力度标记 |
| forte | 强 |
| piano | 弱 |
| mezzo forte | 中强 |
| mezzo piano | 中弱 |
| fortissimo | 很强 |
| pianissimo | 很弱 |
| tempo marking | 速度标记 |
| metronome marking | 节拍器标记 |
| grace note | 装饰音 |
| trill | 颤音 |
| ornamentation | 装饰音 |
| triplet | 三连音 |
| duplet | 二连音 |

## 11. 来源中的结构示例与补充标签

以下内容来自原术语文本的后半部分，包含结构示例、结构标签、表演标签等补充资料。它是参考库，不覆盖本文件前部的强制规范；其中长句方括号和高密度标签应谨慎使用。

```text
结构示例:
[intro]
[instrumental, summer feelings, bird sounds, flute melody]
【前奏】
【器乐，夏日情怀，鸟鸣声，长笛旋律】

[indie bass sets in followed by strumming guitars]
【独立音乐风格的贝斯开始，接着是弹奏吉他】

[verse]
【主歌】
[your lyrics here]

[pre-chorus]
【前副歌】
[your lyrics here]

[brief guitar solo]
【简短吉他独奏】

[bridge]
【桥段】

[verse]
[your lyrics here]
【你的歌词】

[orchestral, flutes, horns, distorted guitars]
【管弦乐，长笛，号角，失真吉他】

[chorus]
【副歌】
[your lyrics here]

[outro, instrumental]
【结尾，器乐】

[fade out]
【淡出】

[Lead In - Electric guitar and drums]
【引入 - 电吉他和鼓】

[Intro]
【引子】

[Break]
【歇段】

[Interlude]
【间奏】

[Instrumental: Guitar]
【器乐：吉他】

[Verse]
【主歌】
[Second Verse lyrics]

[Hook]
【钩子】

[Catchy refrain here]
【引人入胜的副歌】

[Chorus]
【副歌】

[Chorus obviously]
【显然是副歌】

[Interlude]
【间奏】

[Instrumental: Drum solo]
【器乐：鼓独奏】

[Verse]
【主歌】
[Third verse lyrics]

[Hook]
【钩子】

[Chorus]
【副歌】

[Bridge]
【桥段】

[Fifth verse lyrics as bridge
worked really well leading into
a key change]
【作为桥段的第五段歌词，过渡到关键变化】

[Key Change]
【关键变化】

[Hook]
【钩子】

[Chorus]
【合唱】

[Break]
【休息】

[Interlude]
【间奏】

[Instrumental: Keyboard solo]
【器乐：键盘独奏】

[Outro]
【结尾】

[Hook and chorus repeated
using different wording and phrasing
worked really well when labeled
as "outro".]
【钩子和合唱重复，使用不同的措辞和短语，标记为“结尾”时效果非常好。】

[End]
结束(切换到3.0生效）

Structural Tags 结构标签 

1.[intro] - 歌曲的前奏部分
2.[verse] - 标准的主歌部分
3.[verse 2], [verse 3], etc. - 后续的主歌部分
4.[chorus] - 歌曲的主要重复主题
5.[pre-chorus] - 进入副歌部分的段落
6.[post-chorus] - 立即跟随副歌部分的段落
7.[hook] - 引人注目且易记的音乐短语
8.[bridge], [bridge 2], [second bridge] - 提供与主歌和副歌不同的对比部分
9.[break] - 暂停或器乐间奏
10.[interlude] - 歌曲部分之间的音乐间奏
11.[refrain] - 重复的歌词或一组歌词
12.[outro] - 歌曲的结束部分
13.[coda] - 歌曲的结尾段落
14.[solo] - 乐器独奏表演的焦点
15.[instrumental] - 只包含乐器，没有人声的部分
16.[vamp] - 重复的音乐段落，通常用于延长歌曲
17[build-up] - 逐渐增加紧张感或强度的部分
18.[drop] - 高潮时刻，通常用于电子音乐中的强烈部分
19.[fade-out] - 音量逐渐减小的结束方式
20.[tag] - 歌曲结尾的短暂重复短语
21.[counterpoint] - 编曲，交织不同旋律的部分
22.[middle 8] or [B section] - 提供对比的部分，通常位于歌曲中部
23.[modulation] - 歌曲中的调性变化

Performance Tags 表演标签

[powerful] - 需要强有力的歌声表达。
[forte] - 大声或强烈的歌声传递。
[belting] - 强而有力的歌唱技巧。
[emphatic] - 带有强烈语气的歌声。
[intense] - 高情感或动态强度的歌声。
[climax] - 高潮部分，歌声或乐器的顶峰时刻。
[passionate] - 深情的歌声表演
[soaring] - 声音剧烈上升的歌唱

[Sad Verse] - 悲伤的主歌
[Happy Chorus] - 欢快的副歌
[Rapped Verse] - 说唱主歌
[Powerpop Chorus] - 强力流行副歌
[Pre-Chorus] - 前副歌
[Bridge] - 桥段
[Shout] - 呼喊
[Whimsical] - 怪诞
[Melancholy] - 忧郁

Vocal Metatags 声乐标签

[Gregorian chant] - 格雷戈里圣歌
[Melismatic] - 延音唱法
[Narrarion] - 叙事
[Spoken Word] - 朗诵
[Sprechgesang] - 半歌唱半说唱
[Emotional] - 情感的
[Sultry] - 性感的
[Ethereal] - 空灵的
[Resonant] - 共鸣的
[Lounge Singer] - 休息室歌手
[Vocalahoid]/[Vocaloid] - 虚拟歌手
[Female Narrator] - 女性叙述者
[Diva Solo] - 歌剧女高音独唱
[Gospel Choir] - 福音合唱团
[Primal Scream] - 原始尖叫
[Rap Verse] - 说唱主歌
[Bel canto] - 美声唱法
[virtuoso-yodeling] - 约德尔歌手
[Minnesang] - 德语宫廷恋歌歌手
[Dorian mode] - 多利安模式
[Lydian mode] - 吕底亚模式
```

## 12. 风格组合范例库

以下内容来自原风格描述表，可作为组合 Style 栏的参考。范例不是固定公式，最终仍须按照 3.5 节固定模板整理，并删除不符合用户需求的部分。

### 风格描述1

| 风格 | 情绪 | 唱腔 | 音色 | 编制 | 编曲特点 | 中文说明 |
| --- | --- | --- | --- | --- | --- | --- |
| [R&B Pop] | [Sensual], [Confident] | [Agile female vocal], [Melismatic runs] | [Bright], [Smooth], [Clear] | [arrangement: Intro - airy synth pads; Verse - smooth vocal phrasing; Pre-chorus - layered harmonies; Chorus - powerful vocal runs + beats; Interlude - vocal riffing; Bridge - melisma + vocal improvisation; Chorus - final vocal explosion; Outro - synth fade] | 细腻的R&B编曲，注重人声技巧与律动结合 | 擅长高音与花腔，情绪多变，旋律华丽 |
| [Dance Pop] | [Energetic], [Playful] | [Bright female vocal], [Clear articulation] | [Sparkling], [Upbeat], [Fresh] | [arrangement: Intro - pulsating synths; Verse - rhythmic vocal delivery; Pre-chorus - build tension with beats; Chorus - catchy hook + layered vocals; Interlude - instrumental dance break; Bridge - vocal modulation; Chorus - repeated hook; Outro - energetic fade] | 电子舞曲节奏感强，旋律朗朗上口 | 适合舞池与派对场合，轻快明亮 |
| [Ballad] | [Tender], [Emotional] | [Soft female vocal], [Expressive phrasing] | [Warm], [Smooth], [Intimate] | [arrangement: Intro - piano + soft pads; Verse - intimate vocal delivery; Pre-chorus - swelling harmonies; Chorus - emotional vocal layering; Interlude - piano solo; Bridge - heartfelt vocal runs; Chorus - climax vocal expression; Outro - gentle fade] | 以钢琴为主，突出情感表达与细腻人声 | 展现温柔情感，适合抒发爱与失落 |
| [R&B] | [Powerful], [Confident] | [Strong female vocal], [Melismatic phrasing] | [Rich], [Warm], [Clear] | [arrangement: Intro - slow beat + keys; Verse - smooth vocal delivery; Pre-chorus - harmonic build; Chorus - lush vocal layering + bass; Interlude - instrumental break; Bridge - vocal runs; Chorus - final hook; Outro - fade with keys] | 现代R&B编曲，注重声乐表现 | 声音力量十足，情感丰富，适合舞台表演 |
| [Dance Pop] | [Empowering], [Energetic] | [Powerful female vocal], [Clear articulation] | [Bright], [Punchy], [Dynamic] | [arrangement: Intro - synth pads; Verse - dynamic vocal delivery; Pre-chorus - tension build; Chorus - anthemic hook + full instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - final climax; Outro - synth fade] | 流行舞曲风格，节奏明快 | 展现女性力量与自信，适合大型演出 |
| [Soul Ballad] | [Emotional], [Intimate] | [Expressive female vocal], [Smooth vibrato] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano chords; Verse - intimate vocal phrasing; Pre-chorus - string pad swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - piano fade] | 钢琴与弦乐搭配，突出情感深度 | 擅长深情表达，声音饱满且感人 |
| [Dark Pop] | [Haunting], [Introspective] | [Soft-spoken female vocal], [Whispery delivery] | [Ethereal], [Mysterious], [Breathy] | [arrangement: Intro - minimal synth pads; Verse - sparse vocal + subtle bass; Pre-chorus - tension build with FX; Chorus - layered vocals + dark beats; Interlude - ambient textures; Bridge - vocal manipulations; Chorus - intensified dynamics; Outro - fading synth drones] | 氛围感强，低调电子音色，声效处理突出神秘感 | 适合表达内心复杂与忧郁，营造梦幻幽暗的听觉体验 |
| [Electropop] | [Conflicted], [Edgy] | [Conversational female vocal], [Dry articulation] | [Cold], [Sharp], [Synthetic] | [arrangement: Intro - glitchy synth arpeggios; Verse - rhythmic vocal chops; Pre-chorus - rising synth tension; Chorus - punchy electronic beats; Interlude - distorted vocal FX; Bridge - rhythmic breakdown; Chorus - full electronic drop; Outro - filtered synth fade] | 现代电子音效丰富，节奏变化多，声效创新 | 适合年轻叛逆与情绪释放的主题，声音设计独特 |
| [Indie Pop] | [Melancholic], [Vulnerable] | [Delicate female vocal], [Intimate phrasing] | [Warm], [Soft], [Natural] | [arrangement: Intro - gentle piano; Verse - soft vocals + subtle percussion; Pre-chorus - vocal harmonies; Chorus - melodic vocal layers; Interlude - instrumental break; Bridge - emotional vocal runs; Chorus - rich vocal texture; Outro - quiet piano fade] | 编曲简约柔和，突出人声情感细节 | 适合表达脆弱与内心挣扎，歌声细腻感人 |
| [Funk Pop] | [Energetic], [Playful] | [Smooth male vocal], [Rhythmic phrasing] | [Bright], [Warm], [Clear] | [arrangement: Intro - funky guitar riff; Verse - rhythmic vocal delivery; Pre-chorus - build-up with brass; Chorus - catchy hook + full band; Interlude - brass solo; Bridge - vocal ad-libs; Chorus - repeated hook; Outro - groove fade] | 复古放克风格，乐器丰富，节奏鲜明 | 擅长复古舞曲与欢快氛围，极具感染力 |
| [Soul Ballad] | [Emotional], [Romantic] | [Expressive male vocal], [Smooth vibrato] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano chords; Verse - intimate vocal phrasing; Pre-chorus - string pad swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - piano fade] | 钢琴与弦乐搭配，突出情感表达 | 适合表达爱情与温柔情感，声音细腻感人 |
| [Pop Rock] | [Upbeat], [Confident] | [Powerful male vocal], [Clear articulation] | [Bright], [Punchy], [Energetic] | [arrangement: Intro - electric guitar riff; Verse - dynamic vocals; Pre-chorus - tension build; Chorus - anthemic hook + guitars; Interlude - guitar solo; Bridge - vocal runs; Chorus - final hook; Outro - energetic fade] | 摇滚元素融合流行，吉他主导，节奏强劲 | 适合表达自信与力量感，气势磅礴 |
| [Pop Latin] | [Passionate], [Energetic] | [Strong vocal], [Expressive phrasing] | [Bright], [Warm], [Clear] | [arrangement: Intro - rhythmic percussion; Verse - vocal focus; Pre-chorus - build tension; Chorus - full instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 拉丁流行节奏感强烈 | 适合热情洋溢的舞曲风格 |
| [Ballad] | [Emotional], [Tender] | [Soft vocal], [Expressive phrasing] | [Warm], [Clear], [Smooth] | [arrangement: Intro - piano; Verse - intimate vocal; Pre-chorus - build up; Chorus - full orchestration; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 抒情慢歌，情感丰富 | 适合展现内心情感的歌曲 |
| [Dance Pop] | [Fun], [Upbeat] | [Bright vocal], [Energetic phrasing] | [Clear], [Bright], [Dynamic] | [arrangement: Intro - synth beats; Verse - vocal focus; Pre-chorus - build up; Chorus - dance beats and synth layers; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 舞曲流行风格，节奏强烈 | 适合派对和舞池的歌曲 |
| [Emotional Pop] | [Powerful], [Confident] | [Strong vocal], [Melismatic phrasing] | [Rich], [Bright], [Clear] | [arrangement: Intro - piano riff; Verse - powerful vocal delivery; Pre-chorus - build tension; Chorus - full instrumentation + vocal layering; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 流行风格，突出强大嗓音技巧 | 适合展现歌唱力量与情感 |
| [Soul] | [Emotional], [Expressive] | [Gospel influenced vocal], [Powerful phrasing] | [Warm], [Rich], [Full] | [arrangement: Intro - gospel organ + snaps; Verse - soulful vocal phrasing; Pre-chorus - harmonic lift; Chorus - choir + vocal belting; Interlude - instrumental call-and-response; Bridge - melisma + runs; Chorus - final explosion; Outro - fade] | 灵魂乐与福音结合，情感饱满 | 适合表达深刻情感和力量 |
| [Dance Pop] | [Energetic], [Fun] | [Bright vocal], [Dynamic phrasing] | [Clear], [Bright], [Powerful] | [arrangement: Intro - synth beats; Verse - bright vocals; Pre-chorus - build up; Chorus - dance beats + layered vocals; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 舞曲流行，节奏明快 | 适合派对和舞池的活力歌曲 |
| [Alternative Rock] | [Reflective], [Melancholic] | [Smooth vocal delivery], [Emotional phrasing] | [Warm], [Clear], [Bright] | [arrangement: Intro - ambient piano; Verse - soft vocal; Pre-chorus - gradual build; Chorus - full band, anthemic; Interlude - instrumental bridge; Bridge - melodic variation; Chorus - climactic; Outro - fade out] | 空灵钢琴与吉他结合，情绪层次丰富 | 适合表达深刻情感和哲思的作品 |
| [Pop Rock] | [Uplifting], [Hopeful] | [Clear vocal], [Energetic phrasing] | [Bright], [Warm], [Dynamic] | [arrangement: Intro - rhythmic guitar; Verse - bright vocal; Pre-chorus - energy build; Chorus - driving beat, layered vocals; Interlude - guitar solo; Bridge - instrumental breakdown; Chorus - anthem repeat; Outro - fade] | 结合流行和摇滚，强调感染力 | 适合激励人心的歌曲 |
| [Electronic] | [Atmospheric], [Dreamy] | [Soft vocal], [Ethereal phrasing] | [Ambient], [Synth], [Clear] | [arrangement: Intro - synth pads; Verse - soft vocals; Pre-chorus - rising synth; Chorus - electronic beats and synth layers; Interlude - instrumental; Bridge - vocal effects; Chorus - repeat; Outro - ambient fade] | 电子氛围营造梦幻感 | 适合营造梦幻与沉浸氛围 |
| [Electronic] | [Dreamy], [Emotional] | [Breathy vocal], [Expressive phrasing] | [Ethereal], [Clear], [Warm] | [arrangement: Intro - synth pads; Verse - soft vocals; Pre-chorus - build; Chorus - electronic beats + synth layers; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 电子元素融合，梦幻氛围 | 适合氛围感强烈的作品 |
| [Electropop] | [Energetic], [Confident] | [Clear female vocal], [Rhythmic phrasing] | [Bright], [Punchy], [Dynamic] | [arrangement: Intro - synth bass; Verse - smooth vocal delivery; Pre-chorus - tension build; Chorus - full electronic beat + vocal layering; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeated hook; Outro - synth fade] | 电子流行风，节奏感强，适合舞池 | 强调节奏与现代感，适合舞曲表现 |
| [Disco Pop] | [Groovy], [Playful] | [Bright female vocal], [Expressive phrasing] | [Warm], [Bright], [Clear] | [arrangement: Intro - funky bass line; Verse - rhythmic vocal; Pre-chorus - build tension; Chorus - disco beat + vocal harmonies; Interlude - instrumental solo; Bridge - vocal runs; Chorus - final hook; Outro - fade] | 复古迪斯科风格，充满律动 | 结合复古与现代元素，适合活力舞台 |
| [Synthpop] | [Mysterious], [Cool] | [Smooth female vocal], [Controlled phrasing] | [Cool], [Synthetic], [Clear] | [arrangement: Intro - atmospheric synth pads; Verse - soft vocal delivery; Pre-chorus - build-up synth; Chorus - driving synth beat + layered vocals; Interlude - synth solo; Bridge - vocal runs; Chorus - repeated hook; Outro - fade] | 合成器主导，氛围感强烈 | 适合夜晚氛围与电子风格表现 |
| [Acoustic Pop] | [Warm], [Intimate] | [Soft male vocal], [Conversational phrasing] | [Clear], [Natural], [Gentle] | [arrangement: Intro - acoustic guitar fingerpicking; Verse - intimate vocal delivery; Pre-chorus - subtle harmony build; Chorus - full vocal harmony; Interlude - guitar solo; Bridge - vocal layering; Chorus - dynamic vocal climax; Outro - soft guitar fade] | 原声吉他主导，旋律简洁自然，突出情感表达 | 适合表达真挚情感和故事叙述，旋律易记，气氛温暖 |
| [Pop Ballad] | [Melancholic], [Reflective] | [Expressive male vocal], [Controlled vibrato] | [Warm], [Smooth], [Emotive] | [arrangement: Intro - soft piano chords; Verse - intimate vocal; Pre-chorus - string pad swell; Chorus - full band accompaniment; Interlude - piano solo; Bridge - vocal crescendo; Chorus - emotional peak; Outro - piano fade] | 钢琴与弦乐融合，突出情感起伏，层次丰富 | 适合抒发失落与反思，歌声情感真切动人 |
| [Folk Pop] | [Optimistic], [Uplifting] | [Natural male vocal], [Clear diction] | [Bright], [Organic], [Airy] | [arrangement: Intro - rhythmic acoustic guitar; Verse - vocal storytelling; Pre-chorus - harmony layers; Chorus - catchy melodic hook; Interlude - instrumental break; Bridge - vocal improvisation; Chorus - repeated hook; Outro - acoustic guitar strum] | 结合民谣与流行元素，旋律朗朗上口，节奏感强 | 适合传递积极、希望的情绪，轻松自然，易于传唱 |
| [Electropop] | [Dark], [Emotional] | [Breathy vocal], [Expressive phrasing] | [Clear], [Ethereal], [Warm] | [arrangement: Intro - synth pads; Verse - intimate vocal; Pre-chorus - build tension; Chorus - layered synths and beats; Interlude - instrumental break; Bridge - vocal runs; Chorus - final repeat; Outro - fade] | 电子流行氛围，情绪浓烈 | 适合表达内心复杂情感的作品 |
| [Alternative Rock] | [Rebellious], [Energetic] | [Raw vocal], [Dynamic phrasing] | [Raspy], [Warm], [Powerful] | [arrangement: Intro - guitar riff; Verse - energetic vocal; Pre-chorus - tension build; Chorus - full band; Interlude - instrumental solo; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 摇滚元素突出，情绪张扬 | 适合表现反叛与力量的歌曲 |
| [Indie Pop] | [Melancholic], [Reflective] | [Soft vocal], [Expressive phrasing] | [Warm], [Clear], [Gentle] | [arrangement: Intro - piano; Verse - soft vocals; Pre-chorus - melodic lift; Chorus - layered instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 独立流行，旋律优美 | 适合细腻情感的抒发 |
| [Alternative Pop] | [Emotional], [Raw] | [Expressive vocal], [Breathy phrasing] | [Warm], [Clear], [Rich] | [arrangement: Intro - synth pads; Verse - soft vocals; Pre-chorus - build tension; Chorus - full instrumentation; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 另类流行，情感丰富 | 适合表达复杂情绪 |
| [Pop Rock] | [Confident], [Energetic] | [Smooth male vocal], [Expressive phrasing] | [Warm], [Bright], [Natural] | [arrangement: Intro - electric guitar riff; Verse - smooth vocal delivery; Pre-chorus - tension build; Chorus - full band + vocal layering; Interlude - instrumental break; Bridge - vocal runs; Chorus - final hook; Outro - guitar fade] | 摇滚与流行结合，音乐感强 | 兼具摇滚魅力和流行感 |
| [Ballad] | [Melancholic], [Emotional] | [Expressive male vocal], [Smooth vibrato] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano chords; Verse - intimate vocal phrasing; Pre-chorus - string swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - piano fade] | 钢琴与弦乐结合，情感深刻 | 声音优美，适合情感抒发 |
| [Funk Pop] | [Groovy], [Playful] | [Bright male vocal], [Rhythmic phrasing] | [Bright], [Punchy], [Dynamic] | [arrangement: Intro - funky bass line; Verse - rhythmic vocal; Pre-chorus - tension build; Chorus - catchy hook + groove band; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeated hook; Outro - fade] | 复古放克风格，节奏感强 | 适合活力与舞台表现 |
| [Pop Latin] | [Passionate], [Energetic] | [Strong vocal], [Expressive phrasing] | [Bright], [Warm], [Clear] | [arrangement: Intro - rhythmic percussion; Verse - vocal focus; Pre-chorus - build tension; Chorus - full instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 拉丁流行，节奏感强烈 | 适合热情洋溢的舞曲风格 |
| [Pop R&B] | [Sensual], [Smooth] | [Expressive vocal], [Melodic phrasing] | [Warm], [Smooth], [Clear] | [arrangement: Intro - synth pads; Verse - smooth vocals; Pre-chorus - build tension; Chorus - layered vocals + beats; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 现代流行R&B风格 | 适合情感细腻表达 |
| [Pop Dance] | [Energetic], [Confident], [Sexy] | [Bright vocal], [Rhythmic phrasing], [Clear articulation], [Moderate runs], [Playful delivery] | [Bright], [Clear], [Energetic] | [arrangement: Intro - synth beats; Verse - vocals; Pre-chorus - build; Chorus - electronic production; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 动感流行舞曲，强调节奏和律动 | 适合展现自信与性感 |
| [Latin Pop] | [Passionate], [Sensual], [Expressive] | [Smooth vocal], [Dynamic phrasing], [Breathy tone], [Subtle runs], [Emotional delivery] | [Warm], [Bright], [Smooth] | [arrangement: Intro - Latin percussion; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 拉丁流行风格，融合丰富节奏 | 适合表现热情与感性 |
| [R&B] | [Smooth], [Romantic], [Intimate] | [Soft vocal], [Controlled runs], [Warm vibrato], [Expressive phrasing], [Breathy] | [Warm], [Rich], [Smooth] | [arrangement: Intro - keyboard pads; Verse - vocals; Pre-chorus - build; Chorus - layered vocals; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | R&B与流行结合，注重声音质感 | 适合抒发内心情感和浪漫 |
| [Soul] | [Romantic], [Warm] | [Smooth vocal], [Expressive phrasing] | [Rich], [Warm], [Clear] | [arrangement: Intro - piano; Verse - smooth vocal; Pre-chorus - harmonic build; Chorus - full band + choir; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 经典灵魂乐风格，注重情感表达 | 适合深情款款的情歌 |
| [R&B] | [Intimate], [Tender] | [Soft vocal], [Gentle phrasing] | [Warm], [Smooth], [Clear] | [arrangement: Intro - subtle keys; Verse - intimate vocal; Pre-chorus - build; Chorus - layered vocals + beats; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 现代R&B风格，细腻温柔 | 适合表达内心情感与柔情 |
| [Pop] | [Hopeful], [Uplifting] | [Clear vocal], [Expressive phrasing] | [Bright], [Warm], [Rich] | [arrangement: Intro - piano riff; Verse - clear vocals; Pre-chorus - build tension; Chorus - full instrumentation; Interlude - instrumental solo; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 流行乐风格，旋律感强 | 适合励志与正能量歌曲 |
| [Neo Soul] | [Smooth], [Seductive] | [Soulful male vocal], [Expressive phrasing] | [Warm], [Rich], [Clear] | [arrangement: Intro - mellow keys; Verse - smooth vocal runs; Pre-chorus - harmonic layering; Chorus - lush vocal harmonies; Interlude - instrumental break; Bridge - vocal ad-libs; Chorus - final climactic delivery; Outro - fade] | 融合现代灵魂与R&B，注重声乐细节 | 擅长柔情与性感结合，声音温暖细腻 |
| [Funk Pop] | [Energetic], [Confident] | [Dynamic male vocal], [Rhythmic phrasing] | [Bright], [Punchy], [Clear] | [arrangement: Intro - funky bassline; Verse - rhythmic vocal delivery; Pre-chorus - brass buildup; Chorus - catchy hook + groove; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeated hook; Outro - groove fade] | 复古放克与流行融合，节奏感强烈 | 展现节奏与律动，适合舞台表现 |
| [Pop Ballad] | [Emotional], [Reflective] | [Smooth male vocal], [Expressive vibrato] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano chords; Verse - intimate vocal phrasing; Pre-chorus - string swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - piano fade] | 抒情慢歌，突出情感深度 | 声音温暖细腻，适合深情演绎 |
| [Electropop] | [Energetic], [Rebellious], [Playful] | [Talk-singing], [Rhythmic phrasing], [Dynamic delivery], [Edgy vocal texture], [Raw attitude] | [Bright], [Gravelly], [Sassy] | [arrangement: Intro - synth beats; Verse - talk-singing; Pre-chorus - build; Chorus - heavy electronic production; Interlude - instrumental; Bridge - vocal rap; Chorus - repeat; Outro - fade] | 电子流行结合说唱元素，节奏感强烈，风格大胆 | 适合活力十足、玩味与叛逆的作品 |
| [Dance Pop] | [Upbeat], [Confident], [Fun] | [Clear vocal], [Energetic runs], [Catchy phrasing], [Bright delivery], [Powerful hooks] | [Bright], [Clear], [Energetic] | [arrangement: Intro - dance beats; Verse - vocals; Pre-chorus - build; Chorus - layered vocals + synths; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 舞曲流行风格，旋律动感，适合派对场合 | 适合展现自信与欢乐氛围 |
| [Pop Rock] | [Edgy], [Raw], [Emotional] | [Raspier vocal], [Dynamic phrasing], [Expressive delivery], [Powerful runs], [Controlled grit] | [Gravelly], [Bright], [Raw] | [arrangement: Intro - electric guitar riff; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - guitar solo; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 流行摇滚结合个性唱腔，情感直接 | 适合表现情绪张力与力量感 |
| [R&B] | [Introspective], [Smooth] | [Soft vocal], [Laid-back phrasing] | [Warm], [Clear], [Smooth] | [arrangement: Intro - minimal synth; Verse - smooth vocal; Pre-chorus - melodic lift; Chorus - layered vocals and beats; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 现代R&B，注重情感细腻表达 | 适合温柔且感性的音乐风格 |
| [Pop] | [Youthful], [Hopeful] | [Clear vocal], [Expressive phrasing] | [Bright], [Warm], [Clear] | [arrangement: Intro - piano; Verse - vocal focus; Pre-chorus - build up; Chorus - full instrumentation; Interlude - guitar solo; Bridge - vocal layering; Chorus - final repetition; Outro - fade] | 流行元素融合，旋律明快 | 适合青春阳光的主题 |
| [Soul] | [Emotional], [Deep] | [Rich vocal], [Expressive phrasing] | [Warm], [Full], [Smooth] | [arrangement: Intro - organ; Verse - soulful vocal; Pre-chorus - harmonic lift; Chorus - choir and full instrumentation; Interlude - instrumental call; Bridge - vocal runs; Chorus - climactic; Outro - fade] | 经典灵魂乐风格，情感丰富 | 适合深情且震撼的音乐表达 |
| [R&B] | [Chill], [Introspective] | [Smooth vocal], [Relaxed phrasing] | [Warm], [Soft], [Clear] | [arrangement: Intro - mellow synths; Verse - smooth vocals; Pre-chorus - subtle build; Chorus - layered vocals + beats; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 现代R&B风格，轻松舒适 | 适合表达内省与放松的情绪 |
| [Electropop] | [Energetic], [Upbeat] | [Bright vocal], [Dynamic phrasing] | [Clear], [Bright], [Smooth] | [arrangement: Intro - synth beats; Verse - vocals; Pre-chorus - build up; Chorus - electronic beats + layers; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 电子流行风格，节奏感强 | 适合舞池与活力氛围 |
| [Pop] | [Bold], [Expressive] | [Powerful female vocal], [Dramatic phrasing] | [Bright], [Clear], [Strong] | [arrangement: Intro - synth pads; Verse - dramatic vocal delivery; Pre-chorus - build tension; Chorus - anthemic hook + full instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - final climax; Outro - synth fade] | 电子与流行融合，戏剧化表现 | 以戏剧张力和强烈情感著称，适合大场面演唱 |
| [Dance Pop] | [Energetic], [Playful] | [Bright female vocal], [Rhythmic phrasing] | [Bright], [Synthetic], [Clear] | [arrangement: Intro - pulsating synth bass; Verse - rhythmic vocal delivery; Pre-chorus - build-up; Chorus - dance beat + vocal layering; Interlude - instrumental break; Bridge - vocal improvisation; Chorus - repeated hook; Outro - synth fade] | 电子舞曲节奏鲜明，极具活力 | 适合展现活力与个性，声音明亮动感 |
| [Jazz] | [Smooth], [Sensual] | [Expressive female vocal], [Warm phrasing] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano + upright bass; Verse - smooth vocal delivery; Pre-chorus - horn swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - fade out] | 爵士乐风格，突出声乐表现 | 展现多样唱腔与情感深度，声音饱满柔美 |
| [Pop] | [Confident], [Empowering] | [Strong female vocal], [Expressive phrasing] | [Bright], [Warm], [Clear] | [arrangement: Intro - upbeat synth; Verse - strong vocal delivery; Pre-chorus - build tension; Chorus - full instrumentation + vocal layering; Interlude - instrumental break; Bridge - vocal runs; Chorus - final hook; Outro - fade] | 现代流行风格，突出自信与力量 | 强调女性力量与感染力 |
| [Funk] | [Groovy], [Playful] | [Bright female vocal], [Rhythmic phrasing] | [Warm], [Bright], [Dynamic] | [arrangement: Intro - funky bass line; Verse - rhythmic vocal; Pre-chorus - build tension; Chorus - groove band + vocal harmonies; Interlude - instrumental solo; Bridge - vocal runs; Chorus - final hook; Outro - fade] | 复古放克风，节奏感强 | 适合舞台活力与律动 |
| [Soul] | [Emotional], [Empowering] | [Powerful female vocal], [Gospel influence] | [Warm], [Rich], [Full] | [arrangement: Intro - gospel organ + snaps; Verse - smooth vocal phrasing; Pre-chorus - harmonic lift; Chorus - full vocal belting + choir; Interlude - instrumental call-and-response; Bridge - melisma + vocal runs; Chorus - final soulful explosion; Outro - gospel chords fade] | 灵魂乐与福音风格结合，情感饱满 | 适合表达力量与情感的歌曲 |
| [Art Pop] | [Brooding], [Introspective] | [Soft female vocal], [Detached phrasing] | [Dark], [Minimal], [Ethereal] | [arrangement: Intro - minimal synths; Verse - sparse vocals; Pre-chorus - subtle buildup; Chorus - layered synth pads + vocal harmonies; Interlude - ambient textures; Bridge - vocal manipulations; Chorus - dynamic synth layers; Outro - fading synths] | 极简主义电子与氛围营造，声音富有艺术感 | 适合表达内心孤独与自省，氛围感强烈 |
| [Electropop] | [Moody], [Energetic] | [Breathy female vocal], [Expressive delivery] | [Bright], [Synthetic], [Cold] | [arrangement: Intro - pulsating synth bass; Verse - rhythmic vocal delivery; Pre-chorus - tension build; Chorus - synth leads + dance beats; Interlude - instrumental break; Bridge - vocal layering; Chorus - repeated hook; Outro - synth fade] | 电子舞曲元素结合流行，节奏明快 | 适合表现复杂情绪与能量释放 |
| [Indie Pop] | [Reflective], [Melancholic] | [Delicate female vocal], [Intimate phrasing] | [Warm], [Soft], [Natural] | [arrangement: Intro - acoustic guitar; Verse - soft vocals; Pre-chorus - harmony buildup; Chorus - melodic vocal layering; Interlude - instrumental break; Bridge - vocal runs; Chorus - final emotional expression; Outro - gentle fade] | 以吉他为主，编曲简约，突出人声情感 | 适合表达内心情绪与思考，声音细腻 |
| [Pop Ballad] | [Emotional], [Powerful] | [Powerful vocal], [Melismatic phrasing] | [Rich], [Bright], [Clear] | [arrangement: Intro - piano; Verse - strong vocal; Pre-chorus - build; Chorus - full orchestration + vocal runs; Interlude - instrumental; Bridge - melisma; Chorus - repeat; Outro - fade] | 抒情慢歌，展示高音技巧 | 适合展现歌唱技巧与情感深度 |
| [R&B] | [Sensual], [Smooth] | [Sultry vocal], [Expressive phrasing] | [Warm], [Rich], [Smooth] | [arrangement: Intro - smooth keys; Verse - sultry vocal; Pre-chorus - build tension; Chorus - layered vocals + beats; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 经典R&B风格，情感细腻 | 适合表达情感与韵味 |
| [Dance Pop] | [Energetic], [Joyful] | [Bright vocal], [Dynamic phrasing] | [Clear], [Bright], [Powerful] | [arrangement: Intro - synth beats; Verse - bright vocal; Pre-chorus - build up; Chorus - dance beats + layered vocals; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 舞曲流行风格，活力十足 | 适合派对与舞池氛围 |
| [Pop Funk] | [Energetic], [Groovy] | [Smooth male vocal], [Rhythmic phrasing] | [Bright], [Crisp], [Funky] | [arrangement: Intro - funky bass groove; Verse - rhythmic vocal delivery; Pre-chorus - vocal build-up; Chorus - catchy hook with layered vocals; Interlude - instrumental funk break; Bridge - vocal ad-libs; Chorus - repeated hook; Outro - groove fade] | 典型放克风格，贝斯律动强烈，鼓点精准 | 代表舞曲流行风，突出活力与节奏感，经典舞台表现 |
| [Pop Ballad] | [Emotional], [Reflective] | [Expressive male vocal], [Smooth vibrato] | [Warm], [Clear], [Rich] | [arrangement: Intro - soft piano chords; Verse - intimate vocal delivery; Pre-chorus - string pad swell; Chorus - full orchestral backing; Interlude - instrumental solo; Bridge - vocal crescendo; Chorus - emotional climax; Outro - gentle fade] | 钢琴与弦乐结合，情感细腻，张力强 | 适合表达内心情感与反思，唱腔感人至深 |
| [Dance Pop] | [Upbeat], [Playful] | [Energetic male vocal], [Dynamic phrasing] | [Bright], [Punchy], [Clear] | [arrangement: Intro - synth riff + beats; Verse - rhythmic vocals; Pre-chorus - build tension; Chorus - explosive hook; Interlude - dance break; Bridge - vocal runs; Chorus - repeated energetic hook; Outro - rhythmic fade] | 电子合成器与鼓点结合，节奏鲜明 | 代表80-90年代流行舞曲风格，节奏明快，活力十足 |
| [Hip Hop Pop] | [Laid-back], [Reflective] | [Rapped singing], [Relaxed phrasing] | [Smooth], [Grainy], [Clear] | [arrangement: Intro - minimalist synth; Verse - rapped vocal; Pre-chorus - melodic build; Chorus - melodic hook + trap beats; Interlude - instrumental break; Bridge - vocal runs; Chorus - final hook; Outro - synth fade] | 结合嘻哈与流行，节奏舒缓 | 声音沙哑，适合情绪表达与氛围营造 |
| [Trap] | [Dark], [Introspective] | [Melodic rap], [Smooth phrasing] | [Dark], [Grainy], [Deep] | [arrangement: Intro - dark synth; Verse - melodic rap; Pre-chorus - tension build; Chorus - heavy trap beats + melodic hook; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeated hook; Outro - fade] | Trap元素突出，氛围浓厚 | 适合展现内省与都市感 |
| [Pop Rock] | [Melancholic], [Emotional] | [Expressive vocal], [Raspy tone] | [Warm], [Raw], [Clear] | [arrangement: Intro - acoustic guitar; Verse - emotional vocal delivery; Pre-chorus - build tension; Chorus - full band + vocal layering; Interlude - guitar solo; Bridge - vocal runs; Chorus - final hook; Outro - guitar fade] | 结合摇滚与流行，表达情感 | 适合情感深刻的摇滚风格 |
| [Trap] | [Dark], [Introspective] | [Melodic rap], [Smooth phrasing] | [Dark], [Grainy], [Deep] | [arrangement: Intro - dark synth; Verse - melodic rap; Pre-chorus - tension build; Chorus - heavy trap beats + melodic hook; Interlude - instrumental break; Bridge - vocal runs; Chorus - repeated hook; Outro - fade] | Trap元素突出，氛围浓厚 | 适合展现内省与都市感 |
| [Electropop] | [Seductive], [Rebellious] | [Syncopated female vocal], [Spoken-sung phrases] | [Edgy], [Dry], [Modern] | [arrangement: Intro - filtered synth loops; Verse - rhythmic phrasing + sparse beats; Pre-chorus - tension build with risers; Chorus - wide synths + layered vocals; Interlude - drop-style instrumental; Bridge - whispered vocal + glitch fx; Chorus - full energy return; Outro - ambient fade-out] | 合成器主导，电子鼓精准，空间感强 | 展现都市女性酷感与控制力，适合派对与潮流主题 |
| [Caribbean Dancehall] | [Carefree], [Flirtatious] | [Laid-back female vocal], [Patois-influenced delivery] | [Tropical], [Breathy], [Playful] | [arrangement: Intro - steel drums + fx hits; Verse - syncopated phrases over offbeat groove; Pre-chorus - vocal tease + rhythm drop; Chorus - full beat + call-and-response; Interlude - instrumental whine; Bridge - chant-style vocal; Chorus - percussive climax; Outro - looped rhythm fade] | 强烈节奏律动，使用加勒比鼓点与轻快旋律 | 轻松有趣，强调身体律动与诱惑氛围 |
| [Pop Ballad] | [Lonely], [Emotional] | [Soaring female vocal], [Minimal vibrato] | [Smooth], [Cold], [Emotive] | [arrangement: Intro - ambient piano + reverb; Verse - sparse vocal + chords; Pre-chorus - slow chord swell; Chorus - string pads + layered vocals; Interlude - vocal echo textures; Bridge - high register vulnerability; Chorus - expanded emotional swell; Outro - isolated piano fade] | 以人声为核心，营造孤独情绪与音色冷感 | 展示内心脆弱与情绪张力，适合失恋或孤独主题表达 |
| [Soul Ballad] | [Heartfelt], [Vulnerable] | [Rich male vocal], [Controlled vibrato] | [Warm], [Smooth], [Emotive] | [arrangement: Intro - gentle piano chords; Verse - emotional vocal phrasing; Pre-chorus - subtle harmonic build; Chorus - layered vocals + strings; Interlude - vocal improvisation; Bridge - vocal crescendo; Chorus - emotional peak; Outro - piano fade] | 钢琴与弦乐融合，突出情感层次与人声表现 | 以深情著称，擅长表达脆弱与真挚情感 |
| [Pop] | [Reflective], [Hopeful] | [Smooth male vocal], [Clear diction] | [Bright], [Clean], [Warm] | [arrangement: Intro - soft synth pads; Verse - clear vocal phrasing; Pre-chorus - harmony buildup; Chorus - catchy vocal hook; Interlude - instrumental break; Bridge - vocal layering; Chorus - repeated hook; Outro - synth fade] | 现代流行编曲，旋律易记，注重歌词表达 | 适合表达内心成长与希望，旋律温暖流畅 |
| [Electropop] | [Melancholic], [Atmospheric] | [Breathy male vocal], [Subtle articulation] | [Dark], [Smooth], [Ethereal] | [arrangement: Intro - ambient synths; Verse - soft vocal delivery; Pre-chorus - tension build with pads; Chorus - lush synth layers + beats; Interlude - electronic textures; Bridge - vocal effects; Chorus - dynamic synths; Outro - ambient fade] | 氛围电子结合，强调情绪氛围与声效设计 | 适合表达内心挣扎与情绪起伏，音色冷静梦幻 |
| [Pop Rock] | [Upbeat], [Confident] | [Powerful male vocal], [Clear articulation] | [Bright], [Punchy], [Energetic] | [arrangement: Intro - electric guitar riff; Verse - dynamic vocal delivery; Pre-chorus - tension build; Chorus - anthemic hook + guitars; Interlude - guitar solo; Bridge - vocal runs; Chorus - final hook; Outro - energetic fade] | 摇滚与流行融合，吉他主导，节奏强劲 | 展现青春活力与自信，适合现场演唱 |
| [Acoustic Pop] | [Warm], [Intimate] | [Soft male vocal], [Conversational phrasing] | [Clear], [Natural], [Gentle] | [arrangement: Intro - acoustic guitar fingerpicking; Verse - intimate vocal delivery; Pre-chorus - subtle harmony build; Chorus - melodic vocal layering; Interlude - instrumental guitar; Bridge - vocal runs; Chorus - repeated hook; Outro - gentle fade] | 以木吉他为主，突出旋律和人声 | 擅长抒情和温柔的表达，旋律动人 |
| [Electropop] | [Powerful], [Uplifting] | [Strong female vocal], [Dramatic phrasing] | [Bright], [Clear], [Dynamic] | [arrangement: Intro - synth pads; Verse - dynamic vocal delivery; Pre-chorus - tension build; Chorus - anthemic hook + full instrumentation; Interlude - instrumental break; Bridge - vocal runs; Chorus - final climax; Outro - synth fade] | 电子流行，突出情感爆发 | 以强烈情感和独特声线著称，适合大气表现 |
| [Ballad] | [Emotional], [Intimate] | [Expressive female vocal], [Smooth vibrato] | [Warm], [Rich], [Clear] | [arrangement: Intro - piano chords; Verse - intimate vocal phrasing; Pre-chorus - string pad swell; Chorus - lush vocal layering; Interlude - instrumental solo; Bridge - vocal runs; Chorus - emotional climax; Outro - piano fade] | 钢琴与弦乐结合，突出情感表达 | 擅长情感细腻的深情演绎 |
| [Alternative Pop] | [Reflective], [Melancholic] | [Soft female vocal], [Conversational phrasing] | [Warm], [Natural], [Gentle] | [arrangement: Intro - minimal piano; Verse - intimate vocal delivery; Pre-chorus - subtle harmony build; Chorus - layered vocals; Interlude - instrumental break; Bridge - vocal runs; Chorus - emotional climax; Outro - fade out] | 简约另类风格，注重情感氛围 | 以细腻表达和氛围感见长 |
| [Country Pop] | [Nostalgic], [Storytelling] | [Clear vocal], [Conversational phrasing] | [Warm], [Bright], [Smooth] | [arrangement: Intro - acoustic guitar; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 乡村流行，叙事性强 | 适合叙述性强的抒情歌曲 |
| [Synthpop] | [Energetic], [Upbeat] | [Bright vocal], [Dynamic phrasing] | [Clear], [Bright], [Smooth] | [arrangement: Intro - synth beats; Verse - vocals; Pre-chorus - build; Chorus - electronic beats + layered vocals; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 合成器流行，节奏强烈 | 适合活力和电子氛围 |
| [Indie Folk] | [Reflective], [Gentle] | [Soft vocal], [Expressive phrasing] | [Warm], [Clear], [Gentle] | [arrangement: Intro - acoustic guitar; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 独立民谣风格，温柔细腻 | 适合抒发内心情感与故事 |
| [Synthwave] | [Dark], [Mysterious] | [Smooth male vocal], [Detached phrasing] | [Dark], [Synthetic], [Ethereal] | [arrangement: Intro - atmospheric synth pads; Verse - smooth vocal delivery; Pre-chorus - tension build; Chorus - lush synth layers + beats; Interlude - instrumental break; Bridge - vocal layering; Chorus - repeated hook; Outro - fading synths] | 合成器主导，80年代复古风格，氛围浓郁 | 擅长营造神秘氛围，声音空灵带感 |
| [R&B] | [Sensual], [Emotional] | [Expressive male vocal], [Smooth phrasing] | [Warm], [Rich], [Clear] | [arrangement: Intro - slow beat + keys; Verse - smooth vocal delivery; Pre-chorus - harmonic build; Chorus - lush vocal layering + bass; Interlude - instrumental break; Bridge - vocal runs; Chorus - final hook; Outro - fade with keys] | R&B节奏与情感表达结合 | 适合表现情感与性感，声音温暖细腻 |
| [Pop] | [Reflective], [Melancholic] | [Clear male vocal], [Smooth phrasing] | [Bright], [Warm], [Clean] | [arrangement: Intro - soft synth pads; Verse - clear vocal delivery; Pre-chorus - tension build; Chorus - catchy hook; Interlude - instrumental break; Bridge - vocal layering; Chorus - repeated hook; Outro - synth fade] | 现代流行编曲，旋律朗朗上口 | 旋律优美，歌词感人，适合广泛听众 |
| [Pop Ballad] | [Powerful], [Emotional] | [Belting vocal], [Melismatic phrasing] | [Bright], [Rich], [Clear] | [arrangement: Intro - piano; Verse - strong vocals; Pre-chorus - build; Chorus - full orchestration + choir; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 经典流行抒情，展现极致高音与技巧 | 适合展现力量和情感的经典作品 |
| [Gospel Influence] | [Soulful], [Inspirational] | [Powerful vocal], [Melisma] | [Warm], [Rich], [Bright] | [arrangement: Intro - gospel organ + snaps; Verse - smooth vocal phrasing; Pre-chorus - harmonic lift; Chorus - full vocal belting + choir; Interlude - instrumental call-and-response; Bridge - melisma + vocal runs; Chorus - final soulful explosion; Outro - gospel chords fade] | 福音音乐影响强烈，情感饱满 | 适合传递灵魂力量与激励 |
| [Pop Soul] | [Emotional], [Expressive] | [Powerful vocal], [Dynamic phrasing] | [Bright], [Clear], [Warm] | [arrangement: Intro - piano + synth; Verse - strong vocals; Pre-chorus - build; Chorus - full instrumentation + vocal runs; Interlude - instrumental; Bridge - melisma; Chorus - repeat; Outro - fade] | 流行灵魂结合，情感深刻 | 适合深情表现与技巧展现 |

### 风格描述2

| 风格 | 情绪 | 唱腔 | 音色 | 编制 | 编曲特点 | 中文说明 |
| --- | --- | --- | --- | --- | --- | --- |
| [style: Pop, Dance] | [mood: Empowering, Confident] | [vocal_style: Strong, Clear] | [vocal_tone: Bright, Energetic] | [arrangement: intro - synth pad; verse - rhythmic vocals; pre-chorus - build-up; chorus - dance beat; interlude - instrumental; verse - layered vocals; bridge - breakdown; chorus - high energy; outro - fade] | 电子舞曲风，节奏感强，适合表现女性力量与自信。 | 电子舞曲节奏强烈，突出自信与力量感。 |
| [style: Mandopop, Ballad] | [mood: Tender, Heartfelt] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Smooth] | [arrangement: intro - piano; verse - gentle vocals; pre-chorus - strings; chorus - orchestral swell; interlude - solo piano; verse - intimate delivery; bridge - vocal runs; chorus - emotional peak; outro - fade] | 抒情歌曲，细腻情感，旋律优美。 | 细腻柔情，旋律流畅，适合抒发内心情感。 |
| [style: Pop, R&B] | [mood: Playful, Flirtatious] | [vocal_style: Smooth, Breathless] | [vocal_tone: Light, Sultry] | [arrangement: intro - bass groove; verse - soft vocals; pre-chorus - synth layers; chorus - catchy hook; interlude - rhythm break; verse - vocal runs; bridge - breakdown; chorus - catchy repeat; outro - fade] | 节奏感强，充满趣味与俏皮风格。 | 节奏明快，富有玩味和诱惑力。 |
| [style: Indie Folk, Alternative] | [mood: Mysterious, Poetic] | [vocal_style: Unique, Expressive] | [vocal_tone: Soft, Ethereal] | [arrangement: Intro - acoustic guitar and synths; Verse - soft vocals; Pre-chorus - layered harmonies; Chorus - full band; Bridge - instrumental; Outro - fade] | 独特的风格，融合民谣与另类 | 声线空灵，适合表现诗意与神秘 |
| [style: Pop, Ballad] | [mood: Tender, Emotional] | [vocal_style: Soft, Melodic] | [vocal_tone: Warm, Clear] | [arrangement: Intro - piano; Verse - emotional vocals; Pre-chorus - strings build; Chorus - full band; Bridge - vocal runs; Outro - fading piano] | 情感丰富，旋律温柔 | 适合细腻表达柔情与感伤 |
| [style: Electronic, Experimental] | [mood: Dark, Introspective] | [vocal_style: Whispery, Atmospheric] | [vocal_tone: Deep, Textured] | [arrangement: Intro - ambient synths; Verse - whispered vocals; Pre-chorus - electronic beats; Chorus - layered synths; Bridge - soundscapes; Outro - fade] | 实验电子元素，氛围浓厚 | 适合表现深沉和思考情绪 |
| [style: Mandopop, Ballad] | [mood: Reflective, Emotional] | [vocal_style: Smooth, Expressive] | [vocal_tone: Warm, Clear] | [arrangement: intro - piano; verse - soft vocals; pre-chorus - strings; chorus - orchestral swell; interlude - gentle guitar; verse - emotional delivery; bridge - vocal runs; chorus - emotional peak; outro - fade] | 抒情风格，唱腔温暖，情感细腻。 | 声音温暖细腻，旋律抒情感人。 |
| [style: Mandopop, Jazz] | [mood: Cool, Sophisticated] | [vocal_style: Smooth, Relaxed] | [vocal_tone: Warm, Mellow] | [arrangement: intro - saxophone; verse - smooth vocals; pre-chorus - soft piano; chorus - jazz band; interlude - sax solo; verse - relaxed delivery; bridge - vocal improvisation; chorus - repeat; outro - fade] | 爵士风格，声音舒缓，氛围优雅。 | 氛围优雅，唱腔流畅，风格爵士。 |
| [style: Mandopop, Rock] | [mood: Passionate, Dramatic] | [vocal_style: Powerful, Emotional] | [vocal_tone: Strong, Rich] | [arrangement: intro - electric guitar; verse - powerful vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - emotional delivery; bridge - vocal climax; chorus - repeat; outro - fade] | 摇滚风格，唱腔有力，情感丰富。 | 情感强烈，唱腔有力，摇滚风格明显。 |
| [style: Mandopop, Ballad] | [mood: Powerful, Emotional] | [vocal_style: Strong, Expressive] | [vocal_tone: Rich, Resonant] | [arrangement: intro - piano; verse - powerful vocals; pre-chorus - strings; chorus - full orchestra; interlude - instrumental bridge; verse - emotional delivery; bridge - vocal runs; chorus - climax; outro - fade] | 抒情且富有力量感，唱腔厚实，情感深刻。 | 唱腔厚重，情感充沛，力量感强烈。 |
| [style: Mandopop, Folk] | [mood: Warm, Nostalgic] | [vocal_style: Soft, Storytelling] | [vocal_tone: Warm, Earthy] | [arrangement: intro - acoustic guitar; verse - soft vocals; pre-chorus - harmonica; chorus - folk band; interlude - instrumental folk; verse - intimate delivery; bridge - vocal harmonies; chorus - repeat; outro - fade] | 民谣风格，唱腔温暖，叙事性强。 | 唱腔温暖，叙事性强，民谣元素丰富。 |
| [style: Mandopop, Gospel] | [mood: Spiritual, Uplifting] | [vocal_style: Powerful, Melismatic] | [vocal_tone: Bright, Resonant] | [arrangement: intro - choir; verse - strong vocals; pre-chorus - organ; chorus - gospel choir; interlude - vocal ad-libs; verse - passionate delivery; bridge - melismatic runs; chorus - climax; outro - fade] | 福音风格，唱腔高亢，富有感染力。 | 唱腔高亢，感染力强，福音元素鲜明。 |
| [style: Classical Crossover, Pop] | [mood: Elegant, Graceful] | [vocal_style: Clear, Controlled] | [vocal_tone: Pure, Bright] | [arrangement: Intro - strings and piano; Verse - clean vocals; Pre-chorus - harmonic build; Chorus - orchestral swell; Bridge - vocal runs; Outro - gentle fade] | 融合古典与流行，气质优雅 | 声音纯净，适合表现优雅气质 |
| [style: Ballad, Pop] | [mood: Tender, Reflective] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Gentle] | [arrangement: Intro - piano; Verse - soft vocals; Pre-chorus - strings; Chorus - emotional build; Bridge - instrumental; Outro - fade] | 情感细腻，旋律优美 | 适合表现温柔细腻的情绪 |
| [style: Jazz, Blues] | [mood: Relaxed, Smooth] | [vocal_style: Smooth, Controlled] | [vocal_tone: Mellow, Soft] | [arrangement: Intro - jazz piano; Verse - relaxed vocals; Pre-chorus - bass and drums; Chorus - jazz band; Bridge - saxophone solo; Outro - fade] | 爵士与蓝调融合，氛围悠闲 | 适合轻松氛围，声音柔和 |
| [style: Mandopop, Alternative Rock] | [mood: Dramatic, Intense] | [vocal_style: Powerful, Expressive] | [vocal_tone: Dynamic, Rough] | [arrangement: intro - synth pads; verse - expressive vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - dramatic delivery; bridge - vocal climax; chorus - repeat; outro - fade] | 另类摇滚风格，唱腔戏剧性强，表现力丰富。 | 风格另类，唱腔强烈，情感充沛，表现力突出。 |
| [style: Mandopop, Pop Rock] | [mood: Energetic, Bold] | [vocal_style: Strong, Clear] | [vocal_tone: Bright, Powerful] | [arrangement: intro - electric guitar; verse - strong vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar riff; verse - energetic delivery; bridge - vocal intensity; chorus - climactic repeat; outro - fade] | 流行摇滚风格，旋律动感，唱腔有力。 | 旋律动感，唱腔有力，风格热烈。 |
| [style: Mandopop, Electronic] | [mood: Experimental, Futuristic] | [vocal_style: Processed, Robotic] | [vocal_tone: Synthetic, Sharp] | [arrangement: intro - electronic synths; verse - processed vocals; pre-chorus - layered synths; chorus - strong electronic beats; interlude - synth effects; verse - robotic delivery; bridge - vocal modulation; chorus - synth-heavy repeat; outro - fade] | 电子风格，声音加工，未来感强。 | 电子元素突出，声音合成感强，风格前卫。 |
| [style: Folk, Singer-Songwriter] | [mood: Reflective, Poetic] | [vocal_style: Smooth, Narrative] | [vocal_tone: Warm, Clear] | [arrangement: Intro - classical guitar; Verse - storytelling vocals; Pre-chorus - subtle strings; Chorus - full acoustic ensemble; Bridge - lyrical instrumental; Outro - gentle guitar] | 旋律优美，歌词诗意，注重叙事和情感表达 | 适合安静聆听和深度思考 |
| [style: Pop Ballad, Classical] | [mood: Tender, Emotional] | [vocal_style: Controlled, Expressive] | [vocal_tone: Clear, Resonant] | [arrangement: Intro - piano; Verse - soft vocals; Pre-chorus - string quartet; Chorus - orchestral swell; Bridge - vocal crescendo; Outro - piano fade] | 融合古典元素，表现细腻情感和高雅气质 | 适合正式演出和抒情作品 |
| [style: Jazz, Soul] | [mood: Cool, Smooth] | [vocal_style: Relaxed, Melismatic] | [vocal_tone: Warm, Velvety] | [arrangement: Intro - upright bass; Verse - smooth vocals; Pre-chorus - brass accents; Chorus - jazz ensemble; Bridge - instrumental solo; Outro - soft fade] | 轻松舒缓，融合爵士和灵魂元素，适合夜晚氛围 | 适合休闲场合和情感细腻表达 |
| [style: Mandopop, Indie Pop] | [mood: Reflective, Intimate] | [vocal_style: Soft, Conversational] | [vocal_tone: Warm, Natural] | [arrangement: intro - acoustic guitar; verse - intimate vocals; pre-chorus - subtle synth; chorus - melodic build; interlude - guitar riff; verse - conversational delivery; bridge - emotional lift; chorus - repeat; outro - gentle fade] | 轻松自然的独立流行风格，旋律简洁，声音真诚。 | 独立风格，声音温暖自然，旋律简单真实。 |
| [style: Mandopop, Rock] | [mood: Energetic, Bold] | [vocal_style: Strong, Slightly Raspy] | [vocal_tone: Powerful, Gritty] | [arrangement: intro - electric guitar; verse - forceful vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - aggressive delivery; bridge - vocal intensity; chorus - climactic repeat; outro - fade] | 融合摇滚元素，声音有力带点沙哑，节奏感强。 | 摇滚结合流行，声音有力带沙哑，节奏紧凑。 |
| [style: Mandopop, R&B] | [mood: Smooth, Sensual] | [vocal_style: Soft, Melismatic] | [vocal_tone: Smooth, Warm] | [arrangement: intro - electric piano; verse - smooth vocals; pre-chorus - bass groove; chorus - layered harmonies; interlude - synth solo; verse - melismatic delivery; bridge - vocal runs; chorus - lush repeat; outro - fade] | 流畅R&B风格，声音柔和带装饰音，氛围性感。 | R&B韵味浓郁，唱腔细腻，氛围性感温暖。 |
| [style: Mandopop, Electropop] | [mood: Futuristic, Bold] | [vocal_style: Clear, Confident] | [vocal_tone: Bright, Crisp] | [arrangement: intro - electronic synths; verse - rhythmic vocals; pre-chorus - layered synths; chorus - dance beats; interlude - synth solo; verse - confident delivery; bridge - vocal layering; chorus - repeat; outro - fade] | 电子流行风格，节奏鲜明，唱腔干净有力。 | 节奏明快，唱腔干净，电子风格突出。 |
| [style: Mandopop, Rock] | [mood: Energetic, Rebellious] | [vocal_style: Strong, Raspy] | [vocal_tone: Rough, Powerful] | [arrangement: intro - electric guitar; verse - raspy vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - intense delivery; bridge - vocal runs; chorus - repeat; outro - fade] | 摇滚风格，唱腔粗犷有力，氛围激烈。 | 唱腔粗犷，摇滚氛围浓厚，节奏激烈。 |
| [style: Mandopop, Ballad] | [mood: Reflective, Emotional] | [vocal_style: Soft, Expressive] | [vocal_tone: Clear, Warm] | [arrangement: intro - piano; verse - soft vocals; pre-chorus - strings; chorus - orchestral build; interlude - guitar; verse - heartfelt delivery; bridge - vocal runs; chorus - climax; outro - fade] | 抒情风格，唱腔细腻温暖，情感丰富。 | 情感细腻，旋律抒情，唱腔温暖动人。 |
| [style: Mandopop, Ballad] | [mood: Tender, Hopeful] | [vocal_style: Soft, Expressive] | [vocal_tone: Warm, Clear] | [arrangement: intro - piano; verse - soft vocals; pre-chorus - strings; chorus - orchestral swell; interlude - gentle guitar; verse - emotional delivery; bridge - vocal runs; chorus - emotional peak; outro - fade] | 抒情温暖，旋律优美，唱腔细腻感人。 | 抒情温暖，旋律感人，唱腔细腻。 |
| [style: Mandopop, Pop Rock] | [mood: Energetic, Uplifting] | [vocal_style: Strong, Clear] | [vocal_tone: Bright, Powerful] | [arrangement: intro - electric guitar; verse - strong vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - energetic delivery; bridge - vocal intensity; chorus - climactic repeat; outro - fade] | 流行摇滚风格，旋律激昂，唱腔有力。 | 旋律激昂，唱腔有力，气氛振奋。 |
| [style: Mandopop, Acoustic] | [mood: Intimate, Reflective] | [vocal_style: Soft, Warm] | [vocal_tone: Natural, Clear] | [arrangement: intro - acoustic guitar; verse - warm vocals; pre-chorus - subtle piano; chorus - gentle build; interlude - guitar picking; verse - intimate delivery; bridge - soft harmonies; chorus - repeat; outro - fade] | 纯净声线，简单编制，氛围亲密。 | 声线纯净，氛围温馨亲密，编曲简洁。 |
| [style: Mandopop, R&B] | [mood: Passionate, Introspective] | [vocal_style: Smooth, Melismatic] | [vocal_tone: Warm, Clear] | [arrangement: intro - electric piano; verse - smooth vocals; pre-chorus - bass groove; chorus - layered harmonies; interlude - synth solo; verse - melismatic delivery; bridge - vocal runs; chorus - lush repeat; outro - fade] | R&B抒情风格，唱腔细腻丰富，情感真挚。 | 情感真挚，唱腔细腻，旋律流畅动人。 |
| [style: Mandopop, Pop Rock] | [mood: Energetic, Uplifting] | [vocal_style: Strong, Clear] | [vocal_tone: Bright, Powerful] | [arrangement: intro - electric guitar; verse - strong vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - energetic delivery; bridge - vocal intensity; chorus - climactic repeat; outro - fade] | 流行摇滚风格，声音明亮有力，旋律激昂。 | 旋律激昂，唱腔有力，气氛振奋。 |
| [style: Mandopop, Ballad] | [mood: Melancholic, Reflective] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Breathier] | [arrangement: intro - piano; verse - soft vocals; pre-chorus - strings; chorus - orchestral swell; interlude - gentle guitar; verse - emotional delivery; bridge - vocal runs; chorus - emotional peak; outro - fade] | 抒情抒怀风格，唱腔温柔细腻，情感丰富。 | 抒情感人，旋律柔美，唱腔细腻温暖。 |
| [style: Alternative Pop, Indie] | [mood: Introspective, Moody] | [vocal_style: Expressive, Breath Control] | [vocal_tone: Clear, Slightly Nasal] | [arrangement: Intro - ambient synths; Verse - sparse instrumentation with vocals; Pre-chorus - build-up with guitar; Chorus - layered vocals with drums; Bridge - instrumental solo; Outro - fading synth] | 独特唱腔，编曲具有独立音乐特色，气氛浓郁 | 结构多变，适合表达复杂情绪和内心独白 |
| [style: Pop, Funk] | [mood: Upbeat, Playful] | [vocal_style: Smooth, Rhythmic] | [vocal_tone: Bright, Energetic] | [arrangement: Intro - funky bass; Verse - rhythmic vocals; Pre-chorus - brass section; Chorus - full band; Bridge - vocal improvisation; Outro - groove fade] | 充满活力和律动感，融合放克和流行元素，适合舞曲 | 旋律轻快，适合现场互动和舞台表现 |
| [style: Ballad, Soul] | [mood: Emotional, Reflective] | [vocal_style: Powerful, Melismatic] | [vocal_tone: Warm, Rich] | [arrangement: Intro - piano; Verse - expressive vocals; Pre-chorus - strings; Chorus - gospel choir backing; Bridge - vocal runs; Outro - soft piano] | 情感浓烈，融合灵魂和福音元素，表现力强 | 适合表现深刻情感和个人故事 |
| [style: Indie Pop, Acoustic] | [mood: Reflective, Bittersweet] | [vocal_style: Gentle, Storytelling] | [vocal_tone: Soft male vocal] | [arrangement: Intro - ambient pads + acoustic guitar; Verse - calm vocals; Pre-chorus - melodic swell; Chorus - layered harmonies; Bridge - instrumental break; Chorus - vocal climax; Outro - acoustic fade] | 以木吉他和氛围垫底为主，旋律抒情，突出内心独白感 | 抒发温柔、感性的内心自述，适合展现低调情绪 |
| [style: Folk Rock, Ballad] | [mood: Nostalgic, Longing] | [vocal_style: Whispery, Deeply emotional] | [vocal_tone: Breathy low male vocal] | [arrangement: Intro - solo guitar; Verse - soft vocals + strings; Pre-chorus - tension build; Chorus - rhythmic strum + layered voice; Bridge - emotional turn; Outro - strings fade out] | 用木吉他与弦乐搭配，营造回忆感 | 适合情感告白和回忆故事类歌曲创作 |
| [style: Minimal Electronic, Lo-fi] | [mood: Calm, Dreamy] | [vocal_style: Talk-sing, Intimate] | [vocal_tone: Warm textured male vocal] | [arrangement: Intro - lo-fi beat + textures; Verse - spoken-like delivery; Chorus - airy synths + dreamy flow; Bridge - ambient FX; Outro - tape noise fade] | 用低保真鼓点和微电子元素营造氛围 | 适合内省、睡前、耳语式聆听体验 |
| [style: Mandopop, Pop Ballad] | [mood: Hopeful, Inspirational] | [vocal_style: Clear, Controlled] | [vocal_tone: Bright, Pure] | [arrangement: Intro - soft piano; Verse - smooth vocals; Pre-chorus - light strings; Chorus - full band with uplifting melody; Bridge - vocal layering; Outro - gentle fade] | 编曲简洁优美，突出歌词情感和旋律，传递希望 | 适合励志主题，旋律感人肺腑 |
| [style: Upbeat Pop, Dance] | [mood: Joyful, Energetic] | [vocal_style: Bright, Lively] | [vocal_tone: Crisp, Clear] | [arrangement: Intro - synth beats; Verse - rhythmic vocals; Pre-chorus - build-up with synths; Chorus - dance beats and hooks; Bridge - breakdown; Outro - energetic fade] | 动感十足，节奏明快，适合舞曲和欢快氛围 | 适合派对和年轻听众 |
| [style: Acoustic, Folk] | [mood: Nostalgic, Warm] | [vocal_style: Soft, Intimate] | [vocal_tone: Warm, Gentle] | [arrangement: Intro - acoustic guitar; Verse - soft vocals; Pre-chorus - harmonies; Chorus - layered acoustic instruments; Bridge - instrumental break; Outro - soft guitar fade] | 轻柔自然，突出人声和原声乐器，营造温馨氛围 | 适合细腻抒情，传递温暖怀旧 |
| [style: Mandopop, EDM] | [mood: Energetic, Playful] | [vocal_style: Light, Rhythmic] | [vocal_tone: Bright, Youthful male vocal] | [arrangement: Intro - synth arpeggios; Verse - energetic phrasing + kick; Pre-chorus - tempo build; Chorus - drop with layered vocal hooks; Interlude - electronic solo; Bridge - rhythmic modulations; Chorus - intensified drop; Outro - fade out with beat cut] | 充满动感，结合流行旋律与电音节奏 | 年轻俏皮的电音作品，旋律洗脑 |
| [style: Pop Ballad, Orchestral] | [mood: Sentimental, Romantic] | [vocal_style: Smooth, Belting in chorus] | [vocal_tone: Warm, Emotional male vocal] | [arrangement: Intro - solo piano; Verse - gentle voice + strings; Pre-chorus - soft lift; Chorus - strong belting + full orchestra; Interlude - violin feature; Bridge - dramatic vocal climb; Chorus - intensified return; Outro - soft piano reprise] | 抒情旋律感人，适合表达爱情主题 | 情绪真挚，音色温润动听 |
| [style: Folk Pop, Acoustic] | [mood: Nostalgic, Optimistic] | [vocal_style: Natural, Slight vibrato] | [vocal_tone: Clear, Relaxed male vocal] | [arrangement: Intro - acoustic guitar; Verse - calm narrative tone; Pre-chorus - rhythmic pickup; Chorus - brighter chord shift; Interlude - guitar solo; Bridge - emotional push; Chorus - warm repeat; Outro - soft guitar fade] | 以原声吉他主导，营造温暖回忆氛围 | 轻松治愈，适合清新日常题材 |
| [style: Mandopop, Alternative] | [mood: Ethereal, Dreamy] | [vocal_style: Breathless, Soft] | [vocal_tone: Airy, Clear] | [arrangement: intro - ambient synths; verse - airy vocals; pre-chorus - subtle strings; chorus - lush textures; interlude - soundscape; verse - intimate delivery; bridge - vocal layering; chorus - textured repeat; outro - fade] | 氛围音乐融合流行，声音透明空灵，旋律梦幻。 | 气氛浓厚，声音透明细腻，旋律飘渺梦幻。 |
| [style: Mandopop, Pop] | [mood: Melancholic, Reflective] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Breathier] | [arrangement: intro - piano; verse - soft vocals; pre-chorus - strings; chorus - orchestral swell; interlude - gentle guitar; verse - emotional delivery; bridge - vocal runs; chorus - emotional peak; outro - fade] | 抒情流行风格，细腻柔和，情感深刻。 | 抒情温柔，旋律细腻，表达内心深情。 |
| [style: Mandopop, Experimental] | [mood: Mysterious, Introspective] | [vocal_style: Whispery, Experimental] | [vocal_tone: Ethereal, Distant] | [arrangement: intro - electronic textures; verse - whisper vocals; pre-chorus - layered synths; chorus - abstract soundscapes; interlude - experimental effects; verse - vocal experimentation; bridge - atmospheric build; chorus - layered repeat; outro - fade] | 实验性电子音乐风格，声效丰富，声音虚无飘渺。 | 声音虚幻，探索式唱腔，氛围浓厚，充满想象力。 |
| [style: Pop, Ballad] | [mood: Tender, Melancholic] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Clear] | [arrangement: Intro - piano; Verse - gentle vocals with strings; Pre-chorus - subtle build-up; Chorus - lush orchestration; Bridge - vocal improvisation; Outro - fading piano] | 编曲细腻，突出情感抒发，旋律温柔流畅 | 声音温暖，适合表达柔情与忧伤 |
| [style: Indie Pop, Folk] | [mood: Reflective, Introspective] | [vocal_style: Clear, Storytelling] | [vocal_tone: Natural, Breathable] | [arrangement: Intro - acoustic guitar; Verse - narrative vocals; Pre-chorus - light percussion; Chorus - full band; Bridge - instrumental; Outro - fade] | 民谣元素融合现代流行，适合叙事与自省 | 细腻表达自我内心，声线自然柔和 |
| [style: Electro Pop, Dance] | [mood: Energetic, Confident] | [vocal_style: Bright, Rhythmic] | [vocal_tone: Crisp, Clear] | [arrangement: Intro - synths; Verse - electronic beats; Pre-chorus - build-up synths; Chorus - electronic drops; Bridge - effects; Outro - synth fade] | 电子舞曲节奏鲜明，突出自信活力 | 现代感强烈，适合展现活泼与自信 |
| [style: Pop, Ballad] | [mood: Sad, Heartbroken] | [vocal_style: Emotional, Expressive] | [vocal_tone: Warm, Rich] | [arrangement: Intro - piano; Verse - emotional vocals; Pre-chorus - strings build; Chorus - orchestral swell; Bridge - vocal improvisation; Outro - fading piano] | 情感浓烈，适合表达失恋和痛苦 | 声音饱满，适合抒发心碎与无奈 |
| [style: Pop Rock, Alternative] | [mood: Angry, Defiant] | [vocal_style: Raw, Powerful] | [vocal_tone: Rough, Intense] | [arrangement: Intro - electric guitar; Verse - strong vocals; Pre-chorus - build-up drums; Chorus - full band with distortion; Bridge - guitar solo; Outro - fade] | 强烈摇滚元素，表达愤怒和反抗 | 声线粗犷，适合表达愤怒与坚定 |
| [style: Indie Pop, Acoustic] | [mood: Reflective, Melancholic] | [vocal_style: Soft, Storytelling] | [vocal_tone: Warm, Smooth] | [arrangement: Intro - acoustic guitar; Verse - intimate vocals; Pre-chorus - light percussion; Chorus - band; Bridge - instrumental; Outro - fade] | 细腻叙事，编曲简洁温暖 | 声音温柔，适合抒发内省和忧郁 |
| [style: Dance Pop, Electropop] | [mood: Confident, Flirty] | [vocal_style: Playful, Light belt] | [vocal_tone: Bright female vocal] | [arrangement: Intro - synth arpeggios; Verse - bouncy phrasing; Pre-chorus - rhythmic tease; Chorus - catchy hook + synth stab; Bridge - spoken adlibs; Outro - beat fade] | 节奏明快，适合舞蹈场景，轻松俏皮 | 非常适合青春、恋爱主题歌曲 |
| [style: Mandopop Ballad] | [mood: Sad, Heartbroken] | [vocal_style: Breath-heavy, Sentimental] | [vocal_tone: Slightly raspy female vocal] | [arrangement: Intro - piano; Verse - broken phrases; Pre-chorus - swelling strings; Chorus - dramatic vocals; Bridge - high emotional pitch; Outro - vocal whisper fade] | 情绪渲染强烈，突出呼吸与哭腔 | 适合伤感分手题材 |
| [style: Pop Rock, Anthemic] | [mood: Empowered, Determined] | [vocal_style: Powerful belt, Assertive] | [vocal_tone: Strong clear female vocal] | [arrangement: Intro - drum fill + guitars; Verse - speech-like cadence; Pre-chorus - vocal growl; Chorus - loud & layered; Bridge - key shift; Outro - reverb trail] | 以摇滚架构支撑女声爆发力 | 非常适合表达独立女性、自我意识觉醒的主题 |
| [style: Mandopop, Ballad] | [mood: Emotional, Powerful] | [vocal_style: Strong, Expressive] | [vocal_tone: Powerful, Rich] | [arrangement: intro - piano; verse - powerful vocals; pre-chorus - strings; chorus - orchestral swell; interlude - guitar; verse - emotional delivery; bridge - vocal runs; chorus - climax; outro - fade] | 抒情风格，唱腔有力，情感充沛。 | 唱腔强劲，情感丰富，旋律感人。 |
| [style: Mandopop, Pop Rock] | [mood: Energetic, Bold] | [vocal_style: Strong, Clear] | [vocal_tone: Bright, Powerful] | [arrangement: intro - electric guitar; verse - strong vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - energetic delivery; bridge - vocal intensity; chorus - repeat; outro - fade] | 流行摇滚风格，旋律激昂，唱腔有力。 | 旋律激昂，唱腔强劲，气氛振奋。 |
| [style: Mandopop, R&B] | [mood: Smooth, Sensual] | [vocal_style: Soft, Breathier] | [vocal_tone: Warm, Smooth] | [arrangement: intro - soft synths; verse - smooth vocals; pre-chorus - bass groove; chorus - R&B beats; interlude - keyboard solo; verse - sensual delivery; bridge - vocal harmonies; chorus - repeat; outro - fade] | R&B风格，声音柔和顺滑，节奏感强。 | 声音柔和，节奏顺畅，R&B风格。 |
| [style: Pop, R&B] | [mood: Passionate, Hopeful] | [vocal_style: Powerful, Controlled] | [vocal_tone: Clear, Bright] | [arrangement: Intro - piano; Verse - soft vocals with synths; Pre-chorus - build-up with drums; Chorus - full band with strong vocals; Bridge - vocal runs with strings; Outro - fading piano] | 编曲现代感强，突出力量与情感表达 | 声音有力，适合表现激情和希望，编曲丰富 |
| [style: Ballad, Soul] | [mood: Melancholic, Reflective] | [vocal_style: Emotional, Smooth] | [vocal_tone: Warm, Rich] | [arrangement: Intro - solo piano; Verse - intimate vocals; Pre-chorus - soft strings; Chorus - emotional swell; Bridge - vocal melisma; Outro - piano fade] | 深情抒发，融合灵魂元素，突出情感表达 | 适合表达内心深沉情感，声线温暖饱满 |
| [style: Dance Pop, Electro] | [mood: Energetic, Confident] | [vocal_style: Clear, Rhythmic] | [vocal_tone: Bright, Crisp] | [arrangement: Intro - synth pads; Verse - electronic beats; Pre-chorus - rising synths; Chorus - electronic drums and vocals; Bridge - sound effects; Outro - synth fade] | 强烈电子元素，节奏明快，富有自信气息 | 现代感强，适合舞曲风格，表现活力与自信 |
| [style: Mandopop, Ballad] | [mood: Passionate, Intense] | [vocal_style: Powerful, Emotional] | [vocal_tone: Rich, Resonant] | [arrangement: intro - piano; verse - strong vocals; pre-chorus - strings build; chorus - full orchestra; interlude - instrumental solo; verse - heartfelt delivery; bridge - vocal climax; chorus - emotional peak; outro - piano fade] | 经典情歌风格，声音厚实饱满，情感深刻。 | 情感强烈，唱腔厚重，经典抒情风格。 |
| [style: Mandopop, Jazz] | [mood: Smooth, Relaxed] | [vocal_style: Soft, Jazzy] | [vocal_tone: Warm, Velvety] | [arrangement: intro - jazz piano; verse - soft vocals; pre-chorus - brass; chorus - light swing; interlude - saxophone solo; verse - smooth delivery; bridge - vocal improvisation; chorus - jazzy repeat; outro - fade] | 爵士风格融合流行，唱腔柔和，氛围轻松。 | 爵士与流行结合，氛围悠闲，唱腔细腻柔软。 |
| [style: Mandopop, Rock] | [mood: Energetic, Bold] | [vocal_style: Strong, Gritty] | [vocal_tone: Powerful, Raspy] | [arrangement: intro - electric guitar; verse - gritty vocals; pre-chorus - drum buildup; chorus - rock band full force; interlude - guitar solo; verse - aggressive delivery; bridge - vocal intensity; chorus - climactic repeat; outro - fade] | 摇滚融合流行，声音带沙哑质感，气势强烈。 | 摇滚气息浓厚，唱腔沙哑有力，节奏紧凑。 |
| [style: Mandopop, Pop Rock] | [mood: Powerful, Emotional] | [vocal_style: Strong, Raspy] | [vocal_tone: Rough, Distinct] | [arrangement: intro - electric guitar; verse - raspy vocals; pre-chorus - drum buildup; chorus - full band; interlude - guitar solo; verse - intense delivery; bridge - vocal runs; chorus - repeat; outro - fade] | 摇滚流行，唱腔粗犷有力，情感爆发。 | 粗犷唱腔，摇滚风格，情感张力强。 |
| [style: Mandopop, R&B] | [mood: Smooth, Reflective] | [vocal_style: Soft, Breathier] | [vocal_tone: Warm, Smooth] | [arrangement: intro - soft synths; verse - smooth vocals; pre-chorus - bass groove; chorus - R&B beats; interlude - keyboard solo; verse - emotional delivery; bridge - vocal harmonies; chorus - repeat; outro - fade] | R&B风格，声音柔和，节奏流畅。 | 唱腔柔和顺滑，节奏感强，R&B特色明显。 |
| [style: Mandopop, Ballad] | [mood: Emotional, Reflective] | [vocal_style: Soft, Expressive] | [vocal_tone: Clear, Warm] | [arrangement: intro - piano; verse - emotional vocals; pre-chorus - strings; chorus - orchestral build; interlude - guitar; verse - heartfelt delivery; bridge - vocal runs; chorus - climax; outro - fade] | 抒情风格，唱腔细腻，情感丰富。 | 情感细腻，旋律抒情，唱腔温暖。 |
| [style: Mandopop, R&B] | [mood: Nostalgic, Romantic] | [vocal_style: Soft, Expressive] | [vocal_tone: Smooth, Slightly Raspy] | [arrangement: intro - soft piano; verse - mellow vocals; pre-chorus - strings; chorus - full band; interlude - rap; verse - intimate; bridge - emotional build; chorus - climax; outro - fade] | 融合R&B与流行元素，旋律优美，细腻情感表达，结合电子元素与中国风。 | 结合传统与现代的流行音乐，情感丰富，讲故事式唱腔，声音温暖柔和。 |
| [style: Mandopop, Hip-hop] | [mood: Energetic, Confident] | [vocal_style: Rap, Smooth] | [vocal_tone: Clear, Assertive] | [arrangement: intro - beat drop; verse - rap; pre-chorus - synth layers; chorus - full band; interlude - instrumental; verse - rap with ad-libs; bridge - breakdown; chorus - anthem style; outro - fade] | 节奏感强，融入嘻哈元素，展现自信和能量，编曲紧凑。 | 嘻哈与流行融合，展现个人态度，节奏紧凑，充满活力。 |
| [style: Mandopop, Ballad] | [mood: Melancholic, Reflective] | [vocal_style: Soft, Emotional] | [vocal_tone: Warm, Breathier] | [arrangement: intro - solo piano; verse - intimate vocals; pre-chorus - strings; chorus - crescendo; interlude - soft guitar; verse - emotional delivery; bridge - vocal runs; chorus - emotional climax; outro - piano fade] | 抒情慢歌，细腻情感表达，旋律柔和感人。 | 抒情动人，适合情感细腻的表达，旋律优美。 |
| [Pop Ballad] | [Powerful], [Emotional] | [Belting vocal], [Melismatic phrasing], [Vibrato], [Sustain], [Dynamic control], [Soulful runs], [Wide range], [Expressive breath control] | [Bright], [Rich], [Clear] | [arrangement: Intro - piano; Verse - strong vocals; Pre-chorus - build; Chorus - full orchestration + choir; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 经典流行抒情，极致高音与技巧展现 | 适合展现力量和情感的经典作品 |
| [Gospel Influence] | [Soulful], [Inspirational] | [Powerful vocal], [Melisma], [Vibrato], [Dynamic phrasing], [Call and response], [Sustain], [Expressive runs], [Emotive crescendos] | [Warm], [Rich], [Bright] | [arrangement: Intro - gospel organ + snaps; Verse - smooth vocal phrasing; Pre-chorus - harmonic lift; Chorus - full vocal belting + choir; Interlude - instrumental call-and-response; Bridge - melisma + vocal runs; Chorus - final soulful explosion; Outro - gospel chords fade] | 福音音乐影响深厚，情感饱满强烈 | 传递灵魂力量与激励，技巧丰富 |
| [Pop Soul] | [Emotional], [Expressive] | [Powerful vocal], [Dynamic phrasing], [Melisma], [Vibrato], [Sustain], [Smooth runs], [Controlled breath], [Flexible delivery] | [Bright], [Clear], [Warm] | [arrangement: Intro - piano + synth; Verse - strong vocals; Pre-chorus - build; Chorus - full instrumentation + vocal runs; Interlude - instrumental; Bridge - melisma; Chorus - repeat; Outro - fade] | 流行与灵魂结合，情感深刻且技巧多样 | 适合深情表现和技巧展示 |
| [Country Pop] | [Nostalgic], [Storytelling] | [Clear vocal], [Conversational phrasing], [Articulate diction], [Moderate vibrato], [Emotional subtlety], [Dynamic phrasing] | [Warm], [Bright], [Smooth] | [arrangement: Intro - acoustic guitar; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 乡村流行，注重故事性与情感表达 | 适合讲述故事与情感细腻的作品 |
| [Synthpop] | [Energetic], [Upbeat] | [Bright vocal], [Dynamic phrasing], [Clear articulation], [Controlled runs], [Moderate vibrato] | [Clear], [Bright], [Smooth] | [arrangement: Intro - synth beats; Verse - vocals; Pre-chorus - build; Chorus - electronic beats + layered vocals; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 电子合成流行，节奏感强 | 适合活力四射与舞曲风格 |
| [Indie Folk] | [Reflective], [Gentle] | [Soft vocal], [Expressive phrasing], [Breathy tone], [Natural vibrato], [Subtle dynamics] | [Warm], [Clear], [Gentle] | [arrangement: Intro - acoustic guitar; Verse - vocals; Pre-chorus - build; Chorus - full band; Interlude - instrumental; Bridge - vocal runs; Chorus - repeat; Outro - fade] | 独立民谣风格，温柔细腻 | 适合抒发内心情感与故事 |

## 13. 最终自检清单

输出前必须逐项检查：

- [ ] 输出明确分为「歌词栏（Lyrics）」和「Style 栏」两个部分。
- [ ] 原歌词正文未被擅自改写。
- [ ] 歌词栏包含与歌词内容对应的 `[Verse]`、`[Chorus]`、`[Bridge]` 等段落划分。
- [ ] 歌词栏包含少量符合各段音乐特点的局部元标签，且没有标签泛滥。
- [ ] 所有嵌入歌词的标签均为简洁英文方括号格式。
- [ ] Style 栏严格按照 3.5 节固定模板顺序编写。
- [ ] Style 栏包含风格、情绪、调式、乐器与演奏、编曲推进、声场混音、人声设计。
- [ ] Style 栏与歌词栏内的段落及局部元标签不存在冲突。
- [ ] 纯音乐任务包含 `There is no vocal present.`。
- [ ] 对低可靠标签或实验项给出必要提醒。

---

资料来源：`AI音乐元标签.xlsx`、`SUNOprompt编写规范.xlsx`、`音乐术语中英文对照表.txt`。本文件已统一格式、纠正明显误译，并按实际用途重新分层。
