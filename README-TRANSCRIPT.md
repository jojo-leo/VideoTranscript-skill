# 逐字稿功能使用指南

## 功能概述

video-to-article skill 现在支持生成完整的视频逐字稿，包括：

- ✅ **完整保留原文**：不做任何改写、缩写或总结
- ✅ **时间戳标记**：精确定位每段内容的时间
- ✅ **中英双语对照**：高质量翻译，方便学习和引用
- ✅ **多种输出格式**：.txt（纯文本）、.srt（字幕文件）
- ✅ **无字幕视频支持**：使用 Whisper AI 自动转录音频

## 使用场景

### 📚 学术研究
- 精确引用演讲或讲座内容
- 分析演讲者的论述逻辑
- 制作参考文献和引用

### 🎓 语言学习
- 中英对照学习外语
- 分析地道表达方式
- 练习听力和口语

### ✍️ 内容创作
- 作为二次创作的完整素材
- 快速检索特定片段
- 制作视频字幕

### 💼 专业用途
- 会议记录整理
- 访谈内容存档
- 法律证据文档

## 快速开始

### 步骤 1：调用 skill

粘贴视频链接，选择"逐字稿"作为输出格式。

### 步骤 2：选择语言选项

- **仅原文**：保留原始语言（通常是英文）
- **仅译文**：只输出中文翻译
- **双语对照**：中英文对照（推荐）

### 步骤 3：获取文件

生成的文件包括：
```
video-title-transcript.txt           # 纯文本逐字稿
video-title-transcript.srt           # SRT字幕文件
video-title-transcript-bilingual.txt # 双语对照版本
```

## 输出格式

### 纯文本格式

```
=== TRANSCRIPT ===
Video: [视频标题]
Duration: [时长]

[00:00:00]
Five years ago, I decided to start a PhD in biology...

[00:00:27]
That's a digital repository of all my knowledge...
```

### 双语对照格式

```
[00:00:00 - 00:00:27]
EN: Five years ago, I decided to start a PhD in biology...

ZH: 五年前，我决定开始攻读生物学博士学位...

---

[00:00:27 - 00:00:47]
EN: That's a digital repository of all my knowledge...

ZH: 这是我过去四年所有知识的数字存储库...
```

### SRT 字幕格式

```srt
1
00:00:00,000 --> 00:00:05,390
Five years ago, I decided to start a PhD
in biology. I was 36 at this time...

2
00:00:05,390 --> 00:00:09,710
...and my knowledge of biology stopped
literally somewhere in high school.
```

## 处理无字幕视频

如果视频没有字幕，skill 会自动使用 Whisper AI 进行音频转录。

### 前置要求

安装 Whisper：
```bash
pip install openai-whisper
```

安装 ffmpeg：
```bash
# Windows (使用 Chocolatey)
choco install ffmpeg

# macOS
brew install ffmpeg

# Linux
apt install ffmpeg
```

### 自动处理流程

1. skill 检测视频是否有字幕
2. 如果没有，自动下载音频
3. 使用 Whisper 转录音频为文字
4. 生成带时间戳的字幕文件
5. 如需双语版本，使用 Claude 翻译

### 性能建议

| 视频时长 | 推荐模型 | 处理时间 | 准确度 |
|---------|---------|---------|--------|
| < 10分钟 | small | 1-2分钟 | 良好 |
| 10-30分钟 | small/medium | 3-8分钟 | 很好 |
| 30-60分钟 | medium | 10-20分钟 | 很好 |
| > 60分钟 | medium/large | 20-40分钟 | 最佳 |

## 翻译质量

双语版本的翻译遵循以下原则：

### ✅ 做到
- 忠实原文，不添加解释
- 保持原文语气和情感
- 术语准确翻译
- 符合中文表达习惯

### ❌ 避免
- 过度美化或文学化
- 省略原文信息
- 改变原意
- 添加个人理解

## 质量检查

生成的逐字稿会自动检查：

```
✓ 时间戳完整且格式正确
✓ 没有遗漏段落
✓ 保留了所有口语化表达
✓ 标点符号使用恰当
✓ 双语版本对应关系正确
✓ 翻译准确无误
```

## 常见问题

### Q: 逐字稿会改写内容吗？
A: 不会。逐字稿完整保留原文，包括口语化表达、停顿、重复等。

### Q: 双语版本的翻译准确吗？
A: 使用 Claude API 进行高质量翻译，力求准确传达原意，但建议对关键内容进行人工校对。

### Q: 可以生成其他语言的翻译吗？
A: 目前支持英文↔中文，未来可扩展到其他语言。

### Q: Whisper 转录需要多长时间？
A: 取决于视频长度和选择的模型。通常30分钟视频需要5-10分钟处理时间。

### Q: 可以编辑生成的 SRT 文件吗？
A: 可以。SRT 是标准字幕格式，可用任何文本编辑器或字幕编辑软件修改。

## 文件位置

所有生成的逐字稿文件保存在当前工作目录：

```
D:\ClaudeCodeProjects\
├── video-title-transcript.txt
├── video-title-transcript.srt
├── video-title-transcript-bilingual.txt
└── cookies.txt (如使用B站Cookie)
```

## 版权说明

⚠️ **重要提醒**：

逐字稿内容来源于原视频，享有原作者的版权保护。使用时请：

- ✅ 标注原视频来源和作者
- ✅ 仅用于个人学习、研究等合理使用
- ✅ 如需公开发布或商业使用，需获得原作者授权
- ❌ 不得用于侵犯原作者权益的行为

## 技术支持

详细文档请参考：
- [逐字稿生成指南](references/transcript-guide.md)
- [主 SKILL 文档](SKILL.md)
- [音频转文字功能说明](SKILL.md#音频转文字功能)

## 示例文件

查看示例逐字稿：
- `examples/transcript-example.txt` - 纯文本示例
- `examples/transcript-bilingual-example.txt` - 双语对照示例
- `examples/transcript-example.srt` - SRT字幕示例
