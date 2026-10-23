# 内容生成策略

## 内容完整性要求

### 核心标准
- ✅ 使用 **80% 以上** 的字幕内容，不进行过度删减
- ✅ 保留 **所有主要的对话、观点和信息点**
- ✅ 完整呈现 **视频的各个章节和主题**
- ✅ 确保文章长度与视频时长成比例
- ✅ 对于长对话和讨论，进行合理的分段和整理
- ✅ 保留关键术语、专业名词和引用内容

## Python 代码示例

### 1. 完整阅读策略

```python
def read_and_analyze_full_content(full_text):
    """
    完整阅读和分析所有字幕内容
    """
    paragraphs = []
    current_paragraph = []
    
    for line in full_text.split('\n'):
        if line.strip():
            current_paragraph.append(line.strip())
        else:
            if current_paragraph:
                paragraphs.append(' '.join(current_paragraph))
                current_paragraph = []
    
    if current_paragraph:
        paragraphs.append(' '.join(current_paragraph))
    
    print(f"识别到段落数: {len(paragraphs)}")
    print(f"平均段落长度: {sum(len(p) for p in paragraphs)/len(paragraphs)} 字符")
    
    return paragraphs
```

### 2. 内容完整性验证

```python
def validate_content_completeness(article_content, original_content):
    """
    验证文章内容的完整性
    """
    # 1. 主题一致性检查
    key_topics = identify_key_topics(original_content)
    article_topics = identify_key_topics(article_content)
    
    missing_topics = [t for t in key_topics if t not in article_topics and len(t) > 3]
    
    if missing_topics:
        print("⚠️ 重要主题可能缺失:")
        for topic in missing_topics:
            print(f"  - {topic}")
    
    # 2. 关键词覆盖率检查
    key_words = extract_keywords(original_content)
    article_words = extract_keywords(article_content)
    
    coverage_rate = sum(1 for word in key_words if word in article_words) / len(key_words)
    print(f"关键词覆盖率: {coverage_rate:.1%}")
    
    # 3. 关键信息检查
    critical_info = identify_critical_info(original_content)
    article_critical = identify_critical_info(article_content)
    
    print("\n🎯 关键信息对比:")
    for info in critical_info:
        if info in article_critical:
            print(f"✅ 包含: {info}")
        else:
            print(f"❌ 可能缺失: {info}")
```

### 3. 自动重组策略

```python
def regenerate_with_full_content(original_subtitles, current_article):
    """
    基于完整字幕内容重新调整文章
    """
    # 1. 首先识别当前文章的内容结构
    article_structure = analyze_article_structure(current_article)
    
    # 2. 识别未使用的重要内容
    unused_content = identify_unused_content(original_subtitles, current_article)
    
    # 3. 重组文章，纳入缺失内容
    new_article = integrate_unused_content(current_article, unused_content)
    
    return new_article
```

## Bash 脚本示例

### 内容完整性检查脚本

```bash
# 内容完整性检查
CONTENT_COVERAGE_THRESHOLD=0.8  # 80% 覆盖率要求

# 计算内容使用比例
total_lines=$(cat subtitle_clean.txt | wc -l)
article_lines=$(grep -o "<p>" article.html | wc -l)

# 显示文章和字幕的字符统计
article_chars=$(cat article.html | grep -o "<p>" | wc -l)
subtitle_chars=$(cat subtitle_clean.txt | wc -c)
echo "文章段落数: $article_chars"
echo "字幕字符数: $subtitle_chars"

if [ "$subtitle_chars" -lt 5000 ]; then
  echo "⚠️ 字幕内容过短，可能需要检查下载是否完整"
fi

usage_ratio=$(awk "BEGIN {print $article_lines / $total_lines}")
echo "内容使用比例: $(awk "BEGIN {printf \"%.1f\", $usage_ratio * 100}")%"

if (( $(awk "BEGIN {if ($usage_ratio < $CONTENT_COVERAGE_THRESHOLD) print 1; else print 0}") )); then
  echo "❌ 内容使用比例不足 80%，建议重新生成"
  echo "建议：检查是否有截断或重要内容缺失"
else
  echo "✅ 内容使用比例符合要求"
fi
```

## 最终内容审核清单

**生成文章前必须完成的检查：**

```
✅ 完整读取所有字幕内容
✅ 分析内容结构和主题分布
✅ 确保使用 80% 以上的内容
✅ 检查重要主题是否完整
✅ 验证关键词覆盖率
✅ 确认所有关键信息点
✅ 检查是否有截断或过度删除
✅ 验证文章的逻辑连贯性
✅ 进行可读性测试
✅ 检查引用和来源信息
```
