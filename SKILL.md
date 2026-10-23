---
name: video-to-article
description: 当用户粘贴YouTube/B站等视频链接并要求将视频整理为文章时，立即使用此技能。自动下载字幕、翻译（如需要）、并生成精美的HTML文章或其他平台格式。支持简体中文和英文两种输出语言。
---

# 视频转文章技能

将视频的字幕内容转换为结构清晰、排版精美的文章，支持多种输出格式和平台。

## 核心特性

- 🎬 支持 YouTube、Bilibili、Twitter/X、Vimeo 等主流平台
- 🌐 双语支持：简体中文 / English
- 🎨 5 种 HTML 风格：蓝白商务、Notion深色、Claude风格、暗黑科技、极简现代
- 📱 4 种平台格式：HTML文章、小红书文案、公众号文章、口播稿
- ✅ 内容完整性保证：使用 80% 以上字幕内容
- 🚀 轻量高效：内置 yt-dlp，开箱即用

## 快速开始

### 安装

**Windows 用户**：已内置 yt-dlp.exe，无需额外安装。

**macOS / Linux 用户**：
```bash
# 使用 Homebrew（推荐）
brew install yt-dlp

# 或使用 pip
pip3 install yt-dlp
```

### 使用方法

1. 粘贴视频链接到对话中
2. 按提示选择输出平台（HTML/小红书/公众号/口播稿）
3. 选择文体风格
4. 选择输出语言（中文/English）
5. 等待生成完成

### 支持的平台

| 平台 | 字幕支持 | 备注 |
|------|---------|------|
| YouTube | ✅ 手动+自动 | 最佳支持 |
| Bilibili | ✅ CC字幕 + AI字幕 | 无字幕需提供 SESSDATA（[获取方法](references/cookie-guide.md)） |
| Twitter/X | ✅ 内嵌字幕 | 部分支持 |
| Vimeo | ✅ 手动字幕 | 依赖上传者 |

## 输出格式

### 平台选择

| 平台 | 主格式 | 说明 |
|------|--------|------|
| **HTML文章** | `.html` | 网页阅读，5种精美风格可选 |
| **小红书文案** | `.txt` + `.html`预览 | 纯文本，带emoji和标签 |
| **公众号文章** | `.md` + `.html`预览 | Markdown格式，支持排版工具 |
| **口播稿** | `.txt` + `.html`预览 | 短视频配音稿 |
| **逐字稿** | `.txt` + `.srt` | 完整字幕，原词原意，中英双语 |

### HTML 文章风格

在选择 HTML 文章时，会询问用户选择以下风格之一：

| 风格名称 | 特点 | 设计规范 |
|---------|------|---------|
| 蓝白商务（推荐） | 专业简洁，蓝色渐变 | `templates/blue-white-business.html` |
| Notion深色 | 深色背景，彩色标注 | `templates/notion-dark.html` |
| Claude风格 | 赭石红+米白，噪点纹理 | `references/claude-style.md` |
| 暗黑科技 | 赛博朋克，霓虹光效 | `references/cyber-tech-style.md` |
| 极简现代 | 简约留白，深绿强调 | `references/minimal-modern-style.md` |

> **注意**：由于 AskUserQuestion 最多支持 4 个选项，风格选择分两步进行：
> 1. 先展示 4 种风格（蓝白商务/Notion深色/Claude风格/极简现代）
> 2. 用户选择后，询问是否换成"暗黑科技"风格

### 小红书文体

| 文体类型 | 适用场景 | 模板文件 |
|---------|---------|---------|
| 种草安利文 | 产品推荐、好物分享 | `references/xiaohongshu/zhongcao.md` |
| 干货教程文 | 技能分享、方法教程 | `references/xiaohongshu/ganhuo.md` |
| 情感共鸣文 | 情感故事、人生感悟 | `references/xiaohongshu/qinggan.md` |
| 清单盘点文 | 资源整理、清单合集 | `references/xiaohongshu/qingdan.md` |

### 公众号文体

| 文体类型 | 适用场景 | 模板文件 |
|---------|---------|---------|
| 热点解读文 | 社会热点、行业趋势 | `references/wechat/redian.md` |
| 深度长文 | 知识科普、深度分析 | `references/wechat/shendu.md` |
| 金句提炼文 | 内容精华、语录整理 | `references/wechat/jinju.md` |
| 故事叙述文 | 案例分享、经历讲述 | `references/wechat/gushi.md` |

### 口播稿文体

| 文体类型 | 适用场景 | 模板文件 |
|---------|---------|---------|
| 爆款开场型 | 知识干货、认知颠覆 | `references/koupogao/baokuan.md` |
| 故事叙述型 | 个人经历、经验分享 | `references/koupogao/gushi.md` |
| 清单列表型 | 技巧盘点、方法汇总 | `references/koupogao/qingdan.md` |
| 情绪共鸣型 | 情感话题、人生感悟 | `references/koupogao/qingxu.md` |
| 对话挑战型 | 观点表达、争议话题 | `references/koupogao/duihua.md` |

> **口播稿选择流程**：先展示前 4 种文体，用户选择后询问是否换成"对话挑战型"。

### 逐字稿格式

**逐字稿（Transcript）** 是完整保留视频原始字幕的格式，特点：

- ✅ **原词原意**：不做任何改写、缩写或总结
- ✅ **时间戳**：保留完整的时间轴信息
- ✅ **双语版本**：中英文对照（如需翻译）
- ✅ **可编辑格式**：提供 .txt 和 .srt 两种格式

**适用场景**：
- 需要精确引用原话
- 字幕制作和校对
- 语言学习和研究
- 法律、学术等严谨场景
- 需要查找特定时间点的内容

**输出文件**：
- `{视频标题}-transcript.txt` - 纯文本逐字稿
- `{视频标题}-transcript.srt` - 带时间戳的SRT字幕文件
- `{视频标题}-transcript-bilingual.txt` - 中英双语对照版（如需翻译）

## 音频转文字功能

### 无字幕视频处理

当视频没有字幕时，skill 可以自动提取音频并转换为文字。

**支持的转录方式**：

1. **yt-dlp + Whisper（本地）** - 推荐
   - 下载音频
   - 使用 OpenAI Whisper 模型转录
   - 完全本地处理，隐私安全
   - 支持多种语言识别

2. **在线转录服务（可选）**
   - Google Speech-to-Text
   - Azure Speech Service
   - AssemblyAI
   - 需要 API 密钥

### Whisper 安装

**Python + Whisper**：
```bash
# 安装 Whisper
pip install openai-whisper

# 安装 ffmpeg（必需）
# Windows: choco install ffmpeg
# macOS: brew install ffmpeg
# Linux: apt install ffmpeg

# 验证安装
whisper --help
```

**模型选择**：
| 模型 | 大小 | 速度 | 准确度 | 推荐用途 |
|------|------|------|--------|---------|
| tiny | 39MB | 非常快 | 较低 | 快速预览 |
| base | 74MB | 快 | 一般 | 日常使用 |
| small | 244MB | 中等 | 良好 | 平衡选择（推荐） |
| medium | 769MB | 慢 | 很好 | 高质量转录 |
| large | 1550MB | 很慢 | 最佳 | 专业用途 |

### 使用流程

```bash
# 1. 检测字幕是否存在
yt-dlp --list-subs "视频链接"

# 2. 如果没有字幕，下载音频
yt-dlp -x --audio-format mp3 -o "audio.%(ext)s" "视频链接"

# 3. 使用 Whisper 转录
# 自动检测语言
whisper audio.mp3 --model small --output_format srt,txt

# 指定语言（更快更准确）
whisper audio.mp3 --model small --language English --output_format srt,txt

# 同时翻译成英文
whisper audio.mp3 --model small --task translate --output_format srt,txt
```

### 双语字幕生成

对于逐字稿的双语版本，使用 Claude 进行高质量翻译：

**双语格式示例**：
```
[00:00:00 - 00:00:05]
EN: Five years ago, I decided to start a PhD in biology.
ZH: 五年前，我决定开始攻读生物学博士学位。

[00:00:05 - 00:00:10]
EN: I was 36 at this time and my knowledge of biology stopped literally somewhere in high school.
ZH: 那时我36岁，我的生物学知识实际上止步于高中某个阶段。
```

**处理流程**：
1. 提取原始字幕（带时间戳）
2. 使用 Claude API 逐句翻译（保持原意）
3. 生成双语对照文本
4. 同时生成 .txt 和 .srt 格式

## 版权与来源标注

### 重要说明

本技能基于视频字幕整理内容，生成的文章属于**二次加工**而非原创。为了尊重原创者版权，**必须**在发布时标注来源。

### 各平台标注要求

**小红书文案**：在正文开头或结尾添加
```
📺 内容来源：视频标题
🔗 原视频：https://www.youtube.com/watch?v=xxx
📢 整理自 @频道名称
```

**公众号文章**：在标题下方添加
```markdown
---
📌 来源说明：
本文整理自 YouTube 视频《视频标题》
原视频：https://www.youtube.com/watch?v=xxx
原频道：@频道名称
---
```

**口播稿**：在开头和视频描述中添加
```
【内容来源】
本视频内容整理自：《视频标题》
原视频：https://www.youtube.com/watch?v=xxx
```

### 生成后提示用户

> ⚠️ **重要提示**：生成的内容基于视频字幕整理，发布前请务必添加原始视频来源信息。建议注明「内容整理自@频道名」或附上原视频链接，尊重原创，合理使用。

## 工作流程

## 工作流程

### 交互流程

```
用户粘贴视频链接
        ↓
1️⃣ 询问输出平台（HTML/小红书/公众号/口播稿）
        ↓
2️⃣ 询问文体风格（根据平台显示对应选项）
        ↓
3️⃣ 询问输出语言（中文/English）
        ↓
4️⃣ 下载字幕
        ↓
5️⃣ 生成内容
        ↓
✅ 完成并提示版权说明
```

### 步骤详解

#### 1. 获取视频信息

```bash
# 使用 yt-dlp 获取视频信息
yt-dlp --print "%(title)s" \
       --print "%(uploader)s" \
       --print "%(upload_date)s" \
       --print "%(duration)s" \
       --print "%(thumbnail)s" \
       --print "%(webpage_url)s" \
       --skip-download "视频链接"
```

**平台识别图标：**
- YouTube: 📺
- Bilibili: 📱  
- Twitter/X: 🐦
- Vimeo: 🎬

#### 2. 下载字幕

**标准字幕下载：**
```bash
yt-dlp --write-subs --write-auto-subs \
       --sub-lang "zh-Hans,zh,en" \
       --skip-download "视频链接"
```

**B站 AI 字幕（需要 Cookie）：**
```bash
# 自动生成 cookies.txt
cat > cookies.txt << EOF
# Netscape HTTP Cookie File
.bilibili.com	TRUE	/	TRUE	过期时间	SESSDATA	${USER_SESSDATA}
EOF

# 下载字幕
yt-dlp --write-auto-subs --sub-lang zh-Hans \
       --skip-download --cookies cookies.txt "视频链接"
```

> B站 Cookie 获取方法详见：[references/cookie-guide.md](references/cookie-guide.md)

#### 3. 处理字幕内容

```bash
# 读取字幕到内存
SUBTITLE_CONTENT=$(cat subtitle.srt)

# 清洗字幕（去除时间戳和标签）
CLEAN_CONTENT=$(echo "$SUBTITLE_CONTENT" | \
  sed '/^[0-9]\+$/d' | \
  sed '/-->.*$/d' | \
  sed '/^$/d' | \
  sed 's/<[^>]*>//g')
```

**内容完整性要求：**
- ✅ 使用 80% 以上的字幕内容
- ✅ 保留所有主要对话和观点
- ✅ 完整呈现各个章节
- ✅ 文章长度与视频时长成比例

详细策略见：[references/content-generation-strategy.md](references/content-generation-strategy.md)

#### 4. 生成最终文件

使用对应的模板文件生成内容：
- **HTML文章**：`templates/blue-white-business.html` 或 `templates/notion-dark.html`
- **小红书/公众号/口播稿**：使用对应的 `references/` 模板

#### 5. 清理临时文件

```bash
# 只保留必要文件
rm -f *.srt *.vtt
# 保留 cookies.txt 供后续使用
```

## 文件命名规范

```
{平台}-{文体}-{视频标题}.{扩展名}

示例：
├── HTML-蓝白商务-6个吸引力法则.html
├── 小红书-种草文-6个吸引力法则.txt
├── 小红书-种草文-6个吸引力法则-预览.html
├── 公众号-热点解读-6个吸引力法则.md
├── 口播稿-爆款开场-起床后工作1分钟.txt
└── cookies.txt  # B站 Cookie（如使用）
```

## 故障排除

### 常见问题

**1. yt-dlp 找不到**
```bash
# 检查安装
yt-dlp --version
which yt-dlp  # macOS/Linux
where yt-dlp  # Windows

# 更新到最新版
yt-dlp -U
```

**2. 字幕下载失败**
```bash
# 查看可用字幕
yt-dlp --list-subs "视频链接"

# 详细调试
yt-dlp --verbose --list-subs "视频链接" 2>&1 | tee debug.log
```

**3. B站 AI 字幕问题**

详见完整指南：[references/cookie-guide.md](references/cookie-guide.md)

常见原因：
- Cookie 已过期 → 重新登录获取
- SESSDATA 格式错误 → 确保复制完整值
- cookies.txt 格式错误 → 检查是否为 Netscape 格式

**4. 网络连接问题**
```bash
# 测试网络
curl -I "https://www.youtube.com"

# 使用代理（如需要）
yt-dlp --proxy "http://proxy:port" "视频链接"
```

## 注意事项

- **语言处理**：根据用户选择的语言进行翻译和整理
- **内容完整性**：严格遵循 80% 以上字幕使用率
- **文件管理**：只保留 cookies.txt 和最终输出文件
- **版权标注**：生成后必须提示用户添加来源信息
- **模板使用**：HTML 使用 `templates/` 中的模板，其他平台使用 `references/` 中的模板

## 参考资源

- [Cookie 获取指南](references/cookie-guide.md) - B站 SESSDATA 详细获取方法
- [内容生成策略](references/content-generation-strategy.md) - 内容完整性验证和代码示例
- [蓝白商务模板](templates/blue-white-business.html) - HTML 蓝白商务风格模板
- [Notion深色模板](templates/notion-dark.html) - HTML Notion深色风格模板
- [风格设计规范](references/) - 各种风格的详细设计规范
