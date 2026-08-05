# Output Contracts

Keep all pasteable content inside clean `text` code blocks. Keep diagnoses, assumptions, and explanations outside. Do not add commentary inside Suno fields.

## Contents

1. Beginner direction confirmation
2. Original song
3. Rewrite and structure-only
4. Style and audit
5. Instrumental and reference analysis
6. Exploration and listening iteration
7. Final delivery

## Beginner direction confirmation

When the beginner confirmation gate applies, do not output Lyrics or Style. Return:

1. One concise sentence translating the supplied material into a creative opportunity.
2. Two to four labeled directions with genuinely different emotional movement, narrative angle, or listening experience.
3. One recommended direction and a simple reason.
4. One compact question asking the user to choose, combine, or replace the directions.
5. An optional reference-song and familiar-versus-innovative-structure question when it would materially affect the work.

Keep the response understandable without music terminology. Do not present a long questionnaire or require the user to answer every dimension.

## Original song

````markdown
## 歌名

《歌名》

## 歌词栏（Lyrics）

```text
完整歌词、结构、气口与元标签
```

## Style 栏

```text
完整英文 Style
```
````

Add a short design note only when useful or requested.

## Rewrite

State `L1`, `L2`, or `L3` when the degree matters, then return the rewritten lyric. Add Suno formatting and Style only when requested or clearly required for direct use. Explain changes only when the user asks for comparison or the scope may surprise them.

## Structure-only L0

````markdown
## 歌词栏（Lyrics）

```text
原词不变，仅加入结构、气口、标点与元标签
```
````

Add Style only when requested. Verify that no lyric word changed.

## Style only

````markdown
## Style 栏

```text
可直接粘贴的英文 Style
```
````

Mention inferred decisions outside the block only when consequential.

## Audit and repair

````markdown
## 主要问题

- 问题、影响与优先级

## 修复后的歌词栏

```text
Lyrics
```

## 修复后的 Style 栏

```text
Style
```
````

List only issues that materially affect the result.

## Instrumental

````markdown
## 音乐结构栏

```text
[Instrumental Intro]
...
[End]
```

## Style 栏

```text
完整纯音乐 Style 与精确人声排除范围
```
````

## Reference analysis

Return reference structure, effective mechanisms, transferable traits, non-copy boundaries, and recommendations for the new work. Do not include unsupported audio claims.

## Multi-direction exploration

Offer two or three directions with genuinely different structure, hook mechanism, narrative strategy, or production. Explain the tradeoff briefly. Fully write only the selected direction unless the user requests complete alternatives.

## Listening iteration

For a narrow change:

````markdown
## 本轮调整

问题、保留项与修改策略。

## 更新段落

```text
明确可替换的 Lyrics 段落
```

## Style 补丁

```text
需要替换或追加的 Style 内容
```

## 预期效果

一句可验证的预期变化。
````

For broad changes, return the complete updated Lyrics and Style to avoid manual assembly errors.

## Final delivery

````markdown
## 最终版本

Vn

## 歌名

《歌名》

## 歌词栏（Lyrics）

```text
最终 Lyrics
```

## Style 栏

```text
最终 Style
```

## 生成注意事项

仅保留必要的概率性或对比生成提醒。
````
