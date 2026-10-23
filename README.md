<div align=”center”>

# 🎤 Video Transcript Skill

**AI-powered bilingual video transcription for Claude Code**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://claude.ai/code)
[![yt-dlp](https://img.shields.io/badge/Powered%20by-yt--dlp-green)](https://github.com/yt-dlp/yt-dlp)

[English](#english) · [简体中文](#简体中文)

</div>

---

## 简体中文

### 🎯 核心功能

这个 skill 专注于视频转录的核心能力：

#### 🎤 **双语逐字稿生成**
- **中英文双语对照**：自动生成带时间戳的完整转录文本
- **最大限度保留原意**：不做总结或改写，完整、准确的逐字记录
- **带时间戳**：精确到秒的时间标记，方便定位和引用

#### 🔊 **无字幕视频转录**
- **音频提取**：自动下载视频音频轨道
- **语音识别**：使用 Whisper 等技术将音频转换为文字
- **智能翻译**：支持中英文互译

### 😫 你是否遇到过这些问题？

> **”这个 YouTube 视频没有中文字幕，看不懂...”**
>
> **”想要完整的逐字稿做研究，但手动转录太费时...”**
>
> **”视频没有字幕，但我需要准确的文字记录...”**
>
> **”想生成双语对照的学习材料...”**

如果以上任何一条戳中了你，这个 skill 就是为你准备的。

### ✨ Video Transcript Skill 能帮你做什么？

只需发送一条视频链接，Claude 就能自动：

- 🎤 **生成完整逐字稿**（中英文双语、带时间戳、最大限度保留原意）
- 🔊 **无字幕也能转文字**（自动下载音频并使用语音识别转录）
- 📥 **下载视频字幕**（支持 YouTube、B站、Twitter 等主流平台）
- 🌐 **智能翻译**（英文→中文 或 中文→英文）

### 🎯 使用场景

| 场景 | 示例 |
|------|------|
| 📚 **学术研究** | 生成完整逐字稿用于引用分析、内容研究 |
| 🎓 **语言学习** | 英文视频生成中英双语逐字稿，对照学习 |
| 📝 **会议记录** | 将无字幕的会议录音转成准确的文字记录 |
| 💼 **访谈整理** | 快速将采访视频转成可编辑的文字稿 |
| 🎧 **内容存档** | 为视频内容建立可搜索的文字档案 |

### 🚀 快速开始

#### 1. 安装 Skill

```bash
# 克隆仓库
git clone https://github.com/jojo-leo/video-transcript-skill.git

# 复制到 Claude Code skills 目录
# Windows
cp -r video-transcript-skill "$HOME/.claude/skills/"

# macOS / Linux
cp -r video-transcript-skill ~/.claude/skills/
```

#### 2. 开始使用

在 Claude Code 中发送视频链接：

**生成双语逐字稿：**
```
请生成这个视频的中英文逐字稿：https://www.youtube.com/watch?v=xxxxx
```

**处理无字幕视频：**
```
这个视频没有字幕，请帮我下载音频并转成文字：https://example.com/video
```

Claude 会自动：
1. 检测视频是否有字幕
2. 如果有字幕：直接下载并生成双语逐字稿
3. 如果无字幕：下载音频，使用语音识别转录，然后翻译

### 📺 支持的视频平台

| 平台 | 字幕支持 | 音频转录 | 备注 |
|------|---------|---------|------|
| **YouTube** | ✅ | ✅ | 最佳支持，可生成完整逐字稿 |
| **Bilibili** | ✅ | ✅ | AI字幕需提供 SESSDATA cookie |
| **Twitter/X** | ✅ | ✅ | 部分视频支持 |
| **Vimeo** | ✅ | ✅ | 依赖上传者添加字幕 |
| **本地视频/音频** | ❌ | ✅ | 支持音频转录 |
| **其他平台** | ⚠️ | ✅ | 可尝试音频转录 |

### 🎤 转录输出格式

生成的逐字稿包含：

```
[00:00:15] English text here
[00:00:15] 对应的中文翻译

[00:00:23] Another English segment
[00:00:23] 另一段中文翻译
```

- **时间戳格式**：`[HH:MM:SS]` 精确到秒
- **双语对照**：原文和译文并排显示
- **完整保留**：不做删减或总结
- **易于编辑**：纯文本格式，方便后续处理

### 🌐 语言支持

- **英文→中文**：英文视频生成双语逐字稿（英文原文 + 中文翻译）
- **中文→英文**：中文视频生成双语逐字稿（中文原文 + 英文翻译）
- **音频识别**：支持多语言音频转文字

### 📁 项目结构

```
video-transcript-skill/
├── SKILL.md                      # Skill 主文件
├── README.md                     # 项目说明
├── README-TRANSCRIPT.md          # 转录功能详细文档
├── LICENSE                       # MIT 许可证
├── component/
│   └── yt-dlp.exe               # 内置 yt-dlp（Windows）
└── references/
    ├── transcript-guide.md       # 转录使用指南
    ├── cookie-guide.md           # B站 Cookie 配置指南
    └── content-generation-strategy.md  # 内容生成策略
```

### 🔧 高级配置

<details>
<summary><b>yt-dlp 路径配置</b></summary>

如果 yt-dlp 不在系统 PATH 中，skill 会自动检测以下路径：

| 平台 | 默认检测路径 |
|------|-------------|
| Windows（内置） | `{skill目录}/component/yt-dlp.exe` |
| Windows | `D:/yt-dlp.exe`、`C:/Program Files/yt-dlp/yt-dlp.exe` |
| macOS | `/usr/local/bin/yt-dlp`、`/opt/homebrew/bin/yt-dlp` |
| Linux | `/usr/local/bin/yt-dlp`、`/usr/bin/yt-dlp` |

</details>

<details>
<summary><b>B站视频 AI 字幕获取</b></summary>

B站视频如果没有 CC 字幕，需要提供 SESSDATA cookie 来获取 AI 生成的字幕：

1. 在浏览器登录 B站
2. 按 `F12` → `Application` → `Cookies` → `bilibili.com`
3. 找到 `SESSDATA`，复制它的 Value 值
4. 提供给 Claude

**注意**：SESSDATA 包含账号敏感信息，请勿泄露给他人。

</details>

### 🐛 故障排除

<details>
<summary><b>yt-dlp 命令找不到</b></summary>

```bash
# 检查安装位置
which yt-dlp   # macOS/Linux
where yt-dlp   # Windows

# 更新 yt-dlp
yt-dlp -U
```

</details>

<details>
<summary><b>字幕下载失败</b></summary>

```bash
# 查看可用字幕
yt-dlp --list-subs "视频链接"

# 查看详细错误
yt-dlp --verbose --list-subs "视频链接"
```

</details>

<details>
<summary><b>音频转录不准确</b></summary>

- 确保视频音质清晰
- 尝试使用更高质量的语音识别模型
- 如果视频有多语言，指定正确的源语言

</details>

### 🤝 贡献

欢迎提交 Issue 和 Pull Request！

### 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

### 🙏 致谢

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - 强大的视频下载工具
- [Claude Code](https://claude.ai/code) - AI 编程助手
- [OpenAI Whisper](https://github.com/openai/whisper) - 语音识别技术

---

## English

### 🎯 Core Features

This skill focuses on the essential capabilities of video transcription:

#### 🎤 **Bilingual Transcript Generation**
- **Chinese-English bilingual transcripts**: Automatically generate complete transcripts with timestamps
- **Maximum fidelity**: Complete, accurate word-for-word transcription, not summaries
- **Timestamps**: Precise timing markers down to the second for easy reference

#### 🔊 **Transcription for Videos Without Subtitles**
- **Audio extraction**: Automatically download video audio tracks
- **Speech recognition**: Convert audio to text using Whisper and other technologies
- **Smart translation**: Support for Chinese↔English translation

### 😫 Do These Problems Sound Familiar?

> **"This YouTube video has no English subtitles, I can't understand..."**
>
> **"I need a complete transcript for research, but manual transcription is too time-consuming..."**
>
> **"The video has no subtitles, but I need an accurate text record..."**
>
> **"I want bilingual learning materials..."**

If any of these resonate with you, this skill is for you.

### ✨ What Can Video Transcript Skill Do?

Just send a video link, and Claude will automatically:

- 🎤 **Generate complete transcripts** (Bilingual Chinese-English, with timestamps, maximum fidelity)
- 🔊 **Transcribe videos without subtitles** (Auto-download audio and use speech recognition)
- 📥 **Download video subtitles** (YouTube, Bilibili, Twitter, and more)
- 🌐 **Smart translation** (English→Chinese or Chinese→English)

### 🎯 Use Cases

| Scenario | Example |
|----------|---------|
| 📚 **Academic Research** | Generate complete transcripts for citation analysis and content research |
| 🎓 **Language Learning** | Create bilingual transcripts from English videos for comparative study |
| 📝 **Meeting Records** | Convert unsubbed meeting recordings to accurate text |
| 💼 **Interview Processing** | Quickly convert interview videos to editable transcripts |
| 🎧 **Content Archiving** | Build searchable text archives for video content |

### 🚀 Quick Start

#### 1. Install Skill

```bash
# Clone the repository
git clone https://github.com/jojo-leo/video-transcript-skill.git

# Copy to Claude Code skills directory
# Windows
cp -r video-transcript-skill "$HOME/.claude/skills/"

# macOS / Linux
cp -r video-transcript-skill ~/.claude/skills/
```

#### 2. Start Using

Send a video link in Claude Code:

**Generate bilingual transcript:**
```
Please generate a bilingual transcript for this video: https://www.youtube.com/watch?v=xxxxx
```

**Process videos without subtitles:**
```
This video has no subtitles, please download the audio and transcribe it: https://example.com/video
```

Claude will automatically:
1. Check if the video has subtitles
2. If yes: Download and generate bilingual transcript
3. If no: Download audio, transcribe using speech recognition, then translate

### 📺 Supported Platforms

| Platform | Subtitle Support | Audio Transcription | Notes |
|----------|-----------------|---------------------|-------|
| **YouTube** | ✅ | ✅ | Best support, complete transcripts |
| **Bilibili** | ✅ | ✅ | AI subtitles require SESSDATA cookie |
| **Twitter/X** | ✅ | ✅ | Partial video support |
| **Vimeo** | ✅ | ✅ | Depends on uploader subtitles |
| **Local video/audio** | ❌ | ✅ | Audio transcription supported |
| **Other platforms** | ⚠️ | ✅ | Try audio transcription |

### 🎤 Transcript Output Format

Generated transcripts include:

```
[00:00:15] English text here
[00:00:15] 对应的中文翻译

[00:00:23] Another English segment
[00:00:23] 另一段中文翻译
```

- **Timestamp format**: `[HH:MM:SS]` precise to the second
- **Bilingual alignment**: Original and translation side by side
- **Complete preservation**: No deletions or summaries
- **Easy to edit**: Plain text format for easy processing

### 🌐 Language Support

- **English→Chinese**: Generate bilingual transcripts (English original + Chinese translation)
- **Chinese→English**: Generate bilingual transcripts (Chinese original + English translation)
- **Audio recognition**: Multi-language audio-to-text support

### 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### 🙏 Acknowledgments

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - Powerful video download tool
- [Claude Code](https://claude.ai/code) - AI coding assistant
- [OpenAI Whisper](https://github.com/openai/whisper) - Speech recognition technology

---

<div align="center">

**⭐ If this project helps you, please give it a star! ⭐**

Made with ❤️ by [jojo-leo](https://github.com/jojo-leo)

</div>
