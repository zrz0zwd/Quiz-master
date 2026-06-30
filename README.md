# Quiz Master — 智能出题 Skill

> 学习题库出题风格，基于大纲和参考书，生成高质量练习题。

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## ✨ 功能特点

Quiz Master 是一个智能出题工具，能够：

1. **📚 学习出题风格** — 读取你的题库和参考书，分析出题风格并持久化存储
2. **📝 章节测试** — 根据当前学习进度自动生成章节练习题
3. **🎯 综合模拟** — 出跨章节综合模拟试题，还原真实考试体验

## 📦 安装

### 方式一：安装全部三个命令（推荐）

使用 `install_source` 命令依次安装三个独立 slash command：

```bash
# 安装 /read-respo — 学习出题风格
install_source source="<your-repo>/quiz-master/commands/read-respo" scope="project" kind="skill"

# 安装 /chaptest — 章节测试
install_source source="<your-repo>/quiz-master/commands/chaptest" scope="project" kind="skill"

# 安装 /anology-test — 综合模拟
install_source source="<your-repo>/quiz-master/commands/anology-test" scope="project" kind="skill"
```

安装完成后，输入栏会出现 `/read-respo`、`/chaptest`、`/anology-test` 三个命令。

### 方式二：仅安装主 Skill

如果你只需要一个入口，安装主 SKILL.md 即可：

```bash
install_source source="<your-repo>/quiz-master" scope="project" kind="skill"
```

然后使用 `/quiz-master` 命令，内部选择三种模式。

### 方式三：本地开发使用

直接将 `quiz-master` 文件夹复制到 Reasonix skills 目录：

```bash
# Windows
Copy-Item -Recurse -Force ".\quiz-master" "$env:APPDATA\reasonix\skills\"

# macOS / Linux
cp -r quiz-master ~/.agents/skills/
```

## 🔧 前置依赖

- **docx-editor-cn** — 用于读取 Word 格式（.doc/.docx）的题库和参考书
  - 如果你的题库已经是 Markdown 格式，则不需要此依赖

## 🚀 快速开始

### 第一步：学习出题风格

```
/read-respo 热统 期中试题_热力学.md 汪书热统题.md
```

这将：
1. 读取题库文件（支持 .md、.doc、.docx、.txt）
2. 分析出题风格（题型结构、分值分布、难度梯度、高频考点等）
3. 将风格画像持久化到 agent 记忆中

### 第二步：章节测试

```
/chaptest 热统 第一章到第三章
```

这将：
1. 确认你的学习进度和题目数量
2. 对照大纲筛选考点
3. 生成符合出题风格的章节练习题

### 第三步：综合模拟

```
/anology-test 热统 第一章到第五章 180分钟 150分
```

这将：
1. 确认考试参数（范围、时长、总分）
2. 生成完整综合模拟试卷
3. 可附加答案解析和知识点地图

## 📖 详细文档

每个子功能的详细说明请参考 [SKILL.md](./SKILL.md)。

## 🗂️ 文件结构

```
quiz-master/
├── SKILL.md              # Skill 主文件（agent 使用）
├── README.md             # 用户文档（你正在看的这个）
├── commands/             # 三个独立 slash command
│   ├── read-respo/       # /read-respo — 学习出题风格
│   │   └── SKILL.md
│   ├── chaptest/         # /chaptest — 章节测试
│   │   └── SKILL.md
│   └── anology-test/     # /anology-test — 综合模拟
│       └── SKILL.md
└── examples/
    └── sample_exam.md      # 示例试卷输出
```

## 🎨 输出格式

Quiz Master 生成 **Markdown 格式**的试卷，包含：

- 考试信息头（时间、满分、范围、题型）
- 按题型分类的大题和小问
- 每题的考点标注（对应大纲章节、参考书来源、难度星级）
- 评分标准（教师参考）

Markdown 格式的优势：
- ✅ 可直接导入 Obsidian 等笔记软件
- ✅ 可使用 Pandoc 转为 PDF/Word
- ✅ 版本可控，易于修改和复用

## 🔒 出题原则

1. **风格一致** — 新生成的题目与题库风格高度一致
2. **考点覆盖** — 严格按大纲要求覆盖知识点，不超纲不遗漏
3. **原创性** — 借鉴思路但不直接复制原题
4. **难度合理** — 基础:中等:难题 = 5:3:2
5. **层次递进** — 大题内部小问有逻辑递进
6. **可解性** — 确保所有题目有明确解

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

MIT License
