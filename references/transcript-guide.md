# 逐字稿生成指南

## 核心原则

逐字稿（Transcript）的核心是**完整、准确、原汁原味**地保留视频内容。

### 与其他格式的区别

| 特征 | 逐字稿 | 文章/文案 |
|------|--------|----------|
| 内容 | 完整保留每一句话 | 提炼核心观点 |
| 改写 | ❌ 不允许 | ✅ 允许 |
| 缩写 | ❌ 不允许 | ✅ 允许 |
| 时间戳 | ✅ 必须保留 | ❌ 通常不需要 |
| 口语化 | ✅ 保留口语表达 | ✅ 转为书面语 |
| 重复内容 | ✅ 保留 | ❌ 删除 |

## 逐字稿格式

### 纯文本格式 (.txt)

```
Obsidian Note-Taking System for Academics & Students - Full Tutorial & Demo (Write Papers Faster)
The Effortless Academic
Duration: 53:46

=== TRANSCRIPT ===

[00:00:00]
Five years ago, I decided to start a PhD in biology. I was 36 at this time and my knowledge of biology stopped literally somewhere in high school. But that sent me on a journey to research everything I could find about how to learn faster.

[00:00:27]
I've read the smart notebook, the second brain book, researched the Zettelkasten method, tried all the digital tools I could find and started building this. That's a digital repository of all my knowledge over the last four years.

[00:00:47]
Every paper I've read, every claim I've highlighted, every question and idea instantly searchable. So a little bit like Wikipedia, but for my own research.

...
```

### SRT 字幕格式 (.srt)

```srt
1
00:00:00,000 --> 00:00:05,390
Five years ago, I decided to start a PhD
in biology. I was 36 at this time and my

2
00:00:05,390 --> 00:00:09,710
knowledge of biology stopped literally
somewhere in high school. But that sent

3
00:00:09,710 --> 00:00:12,150
me on a journey to research everything I
could find about how to learn faster.
```

### 双语对照格式 (.txt)

```
=== 中英双语逐字稿 ===
Bilingual Transcript (English & 简体中文)

Video: Obsidian Note-Taking System for Academics & Students
Duration: 53:46

---

[00:00:00 - 00:00:27]
EN: Five years ago, I decided to start a PhD in biology. I was 36 at this time and my knowledge of biology stopped literally somewhere in high school. But that sent me on a journey to research everything I could find about how to learn faster.

ZH: 五年前，我决定开始攻读生物学博士学位。当时我36岁，我的生物学知识实际上止步于高中的某个阶段。但这促使我踏上了研究如何更快学习的一切方法的旅程。

---

[00:00:27 - 00:00:47]
EN: I've read the smart notebook, the second brain book, researched the Zettelkasten method, tried all the digital tools I could find and started building this. That's a digital repository of all my knowledge over the last four years.

ZH: 我阅读了《Smart Notebook》、《第二大脑》等书籍，研究了Zettelkasten方法，尝试了我能找到的所有数字工具，并开始构建这个系统。这是我过去四年所有知识的数字存储库。

---
```

## 处理原则

### 保留的内容

✅ **口语表达**：
- "you know", "I mean", "like" 等填充词保留
- 口语化的句式保留
- 不完整的句子保留（如说话人中断）

✅ **重复内容**：
- 说话人重复的内容完整保留
- 字幕滚动造成的重复也保留（后期可清理）

✅ **停顿和语气**：
- 可以用 "..." 标记明显停顿
- 可以用 "？" 标记疑问语气
- 可以用 "！" 标记强调语气

### 不保留的内容

❌ **背景音乐/音效**：不标注 [music] [sound]
❌ **非语言声音**：咳嗽、笑声等不标注（除非是内容的一部分）
❌ **技术问题**：不标注字幕重复、技术错误等

## 翻译原则

对于双语逐字稿，翻译要求：

### 准确性优先

- ✅ 忠实原文，不添加解释
- ✅ 保持原文语气和情感
- ✅ 术语准确翻译
- ✅ 人名、地名保持原文或标准译名

### 可读性兼顾

- ✅ 符合中文表达习惯
- ✅ 断句清晰自然
- ❌ 不过度美化
- ❌ 不省略原文信息

## 质量检查清单

生成逐字稿后，检查以下项目：

```
□ 时间戳完整且格式正确
□ 没有遗漏段落
□ 没有改写或总结原文
□ 保留了所有口语化表达
□ 标点符号使用恰当
□ 人名、术语拼写正确
□ 双语版本对应关系正确
□ 翻译准确无误
□ 时间轴与音频对齐
```

## 文件命名规范

```
{视频标题}-transcript.txt           # 纯文本逐字稿
{视频标题}-transcript.srt           # SRT字幕文件
{视频标题}-transcript-bilingual.txt # 双语对照版
{视频标题}-transcript-en.txt        # 纯英文版
{视频标题}-transcript-zh.txt        # 纯中文版
```

## 使用场景

### 学术研究
- 精确引用演讲内容
- 分析演讲风格和修辞
- 语言学研究

### 内容创作
- 作为二次创作的素材
- 检索特定片段
- 制作视频字幕

### 语言学习
- 对照学习外语
- 分析句式结构
- 练习听力理解

### 法律用途
- 证据记录
- 证词整理
- 版权保护
