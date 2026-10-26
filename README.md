# Sticker Glass Video Skill

**贴纸科普 · 玻璃点缀：把口播里的意思，变成观众看得懂的画面。**

[English](README.en.md) · [下载技能 ZIP](https://github.com/alleinDuck/sticker-glass-video-skill/releases/latest/download/ai-sticker-glass-video.zip) · [完整仓库 ZIP](https://github.com/alleinDuck/sticker-glass-video-skill/archive/refs/heads/main.zip) · [技能入口](skills/ai-sticker-glass-video/SKILL.md) · [MIT License](LICENSE)

![贴纸科普与玻璃点缀静态风格示意](docs/assets/style-preview.png)

> 上图为本仓库原创的静态风格示意，使用虚构产品和模拟文案，展示视觉方法；未使用真实客户素材，不代表产品实测或自动生成视频的效果保证。[查看示例说明](examples/README.md)

录完一段 AI 工具讲解，接下来常常卡在：这一句该放什么画面？哪里用实测截图，哪里用图解？字幕、人物和贴纸怎么摆才清楚？

这个 Skill 将这些判断整理成可复用流程：**读取本次素材 → 生成制作提示词 → 设计静态故事板 → 你确认 → 制作与检查视频。**

它提供创作流程、视觉规范和交付要求。实际读文件、查看媒体、生成图形和渲染视频，由你的 AI 编程助手及已配置的工具执行。

## 能做什么

- **把口播变成画面。** 围绕一句话的含义组织对象、关系和状态，同一产品在镜头间持续出现。
- **保持统一风格。** 浅色画布、白边贴纸、短标签、手绘箭头；产品亮相与窗口层次加入少量玻璃质感。
- **用真实素材支撑讲解。** 优先使用实测截图、录屏与客户资料；缺少证据时明确标注“功能示意”。
- **先看设计，再做动画。** 给出完整静态故事板、详细分镜、素材来源表与关键帧，确认后进入制作。
- **保留原片声音与含义。** 默认保留原声、口播顺序，不补写尾句；提前说明原片字幕与后期字幕的处理方式。

适合 AI 工具介绍、科技科普、产品功能说明，以及口播中的图解插入段。画面可以是全屏图解、人物穿插图解、人物叠加贴纸或产品录屏。

## 效果是什么

| 口播需要表达的内容 | 建议画面 | 观众能理解什么 |
| --- | --- | --- |
| “把素材交给助手” | 文档贴纸进入同一个产品窗口 | 输入是什么、交给谁 |
| “按用途整理” | 原来的对象展开成不同分组，箭头连接结果 | 功能如何组织内容 |
| “先检查，再继续” | 同一窗口切换到预览状态，重点局部放大 | 当前状态与下一步 |

仓库提供[可在浏览器打开的三镜静态故事板](examples/storyboard.html)、[带时间码的分镜说明](examples/STORYBOARD.md)和[素材来源表](examples/素材来源表.md)。示例没有音轨或 MP4，时间码是设计建议；它演示审阅方式和视觉语言，不能用来验证渲染器、配音或音画同步。

## 安装与下载

### 方式一：用 skills CLI 安装

需要 **Node.js 22.20+**。在项目目录执行，按提示选择 AI 助手：

```bash
npx skills add alleinDuck/sticker-glass-video-skill --skill ai-sticker-glass-video
```

直接安装到当前项目的 Codex：

```bash
npx skills add alleinDuck/sticker-glass-video-skill --skill ai-sticker-glass-video -a codex
```

安装为跨项目可用的全局 Skill：

```bash
npx skills add alleinDuck/sticker-glass-video-skill --skill ai-sticker-glass-video -a codex -g
```

Claude Code 或 Cursor 用户可将 `-a codex` 换成 `-a claude-code` 或 `-a cursor`。查看已安装技能：

```bash
npx skills list
# 全局安装时使用
npx skills list -g
```

安装命令与目录规则依据 [Vercel skills CLI 文档](https://github.com/vercel-labs/skills)。其他助手支持加载标准 Skill，不代表它们具备相同的媒体工具或已完成视频制作兼容性测试。

### 方式二：手动下载

1. 点击 [下载技能 ZIP](https://github.com/alleinDuck/sticker-glass-video-skill/releases/latest/download/ai-sticker-glass-video.zip)，解压。
2. 复制解压后的**整个 `ai-sticker-glass-video/` 文件夹**，包含 `SKILL.md`、`references/`、`agents/` 和 `LICENSE`。若下载的是完整仓库，则在 `skills/` 下找到它。
3. 放入对应助手的技能目录，重新开启会话或按助手的刷新方式加载。

| 助手 | 项目内目录 | 全局目录 |
| --- | --- | --- |
| Codex | `.agents/skills/ai-sticker-glass-video/` | `~/.agents/skills/ai-sticker-glass-video/` |
| Claude Code | `.claude/skills/ai-sticker-glass-video/` | `~/.claude/skills/ai-sticker-glass-video/` |
| Cursor | `.agents/skills/ai-sticker-glass-video/` | `~/.cursor/skills/ai-sticker-glass-video/` |

目录以 [skills CLI 的助手目录表](https://github.com/vercel-labs/skills/blob/main/docs/agents.md)为参考。Codex 内置 `skill-installer` 也可安装到 `$CODEX_HOME/skills`（默认 `~/.codex/skills`）；使用一种安装方式即可，避免同名技能的多个副本。

已安装旧版本时先备份自己的修改，再替换完整技能文件夹。

### 方式三：获取仓库源码

```bash
git clone https://github.com/alleinDuck/sticker-glass-video-skill.git
cd sticker-glass-video-skill
```

克隆后仍需按上述方式安装 `skills/ai-sticker-glass-video/`。

## 使用前准备

| 项目 | 用途 |
| --- | --- |
| 支持 Agent Skills 的 AI 助手 | 读取技能、分析素材、生成与编辑工程 |
| 本地文件读写和终端能力 | 访问原视频、SRT、素材与输出目录 |
| 媒体查看与探测工具 | 检查视频、音轨、时间范围和字幕；常用 FFmpeg / ffprobe |
| 可用的浏览器或静态渲染工具 | 预览故事板、导出静态关键帧 |
| 可用的视频渲染工具 | 确认设计后制作 MP4，例如配置好的 HyperFrames 或 Remotion |
| 联网能力（按需） | 核查官方产品资料与补充素材 |

本仓库包含 Skill 与静态示例。模型服务、媒体工具和渲染器需要在你的环境中配置；相关费用和许可按各工具规定执行。`agents/openai.yaml` 是可选的 Codex 界面元数据，其他助手可忽略。

## 如何使用

### 1. 提供本次素材，先获得制作提示词

准备原视频、对应 SRT，以及可选的文档、图片或录屏。说明文档采用哪些部分、图片用在哪里。下面的路径是示例，需换成你自己的文件。

```text
使用 $ai-sticker-glass-video。

原视频：/path/to/project/demo.mp4
字幕：/path/to/project/demo.srt
补充资料：/path/to/project/brief.md，只采用“产品定位”和“功能一”两节。
产品截图：/path/to/project/screenshot.png，用于功能演示。

为这段内容采用贴纸科普、玻璃点缀风格，保留原声。
请先读取这些材料，给出针对本次片段的制作提示词。
```

助手会核对材料、时间范围、画面与字幕，再给可直接采用的制作提示词。这个阶段的产物是提示词。

在其他助手里，用其技能选择方式或直接说“使用 ai-sticker-glass-video”；`$技能名` 是 Codex 的调用写法。

### 2. 采用提示词，生成完整静态审阅包

```text
按这份制作提示词执行，先给完整静态故事板、详细分镜与素材映射、
素材来源表，以及代表性关键帧。等待我确认设计后再制作视频。
```

这一轮应该拿到：

| 文件 | 内容 |
| --- | --- |
| `storyboard.html` | 全段视觉故事板：实际布局、时间、口播、动作说明与素材编号 |
| `STORYBOARD.md` | 输入核对、详细分镜、逐镜素材映射、声音与字幕方案、待核查项 |
| `素材来源表.md` | 本地文件或来源链接、用途、对应镜头、取得状态和事实边界 |
| `关键帧-XX.png`、`关键帧对照.png` | 通常 2–3 张代表性静态帧与对照图 |

先看这些问题：产品是否认得出、每句口播是否有对应画面、字幕是否可见、素材是否真实、尾帧能否接上后文。

需要修改时，可以直接指定镜头：

```text
先修改设计：S02 的功能关系不够清楚，保留产品截图，
用两个白边贴纸和一根箭头说明输入与结果。给我新的审阅版本。
```

### 3. 确认当前设计，开始制作

```text
设计审阅 v1 符合预期，按这个版本制作视频。
保留原声，检查手机可读性、字幕遮挡、音画衔接和结尾，
交付 MP4、含素材的可编辑工程、更新后的素材来源表和检查记录。
```

助手使用实际可用的渲染工具完成预览、修复和导出；无法执行的检查应在交付时说明。

## 工作边界

- 首次只提供文件时，默认先生成针对本次素材的提示词。
- 静态设计阶段不创建动画时间线或输出新视频；制作开始前需确认当前设计。
- 默认保留原声，不新增配音、音乐或音效；有烧录字幕时先说明遮挡与补字幕方案。
- 只有文字或 SRT 时，可以明确要求先做静态设计；缺少音频的时间对齐必须标为建议或待校准。
- 官方宣传、原创图解和用户实测分开标注；不编造成功率、收入、效率提升或产品结论。
- 公开图片不自动具备商用许可；生成内容中的第三方图片、字体和音乐仍需分别核对。

## 常见问题

**只有 SRT，没有视频，可以用吗？**

可以明确要求文字／SRT 的静态设计或无声插入画面。正常的原片包装流程需要视频；没有原声就无法校验逐词同步。

**能直接放进 ChatGPT 普通聊天窗口吗？**

可以作为写作与设计参考。完整制作需要支持技能加载、本地文件、终端和媒体工具的环境，取决于实际提供的能力。

**安装完能自动下载视频渲染器吗？**

Skill 安装只添加说明文件。让助手检查现有环境，并按照所选工具的官方文档配置。

**为什么还要确认两次？**

采用制作提示词确定本次内容与范围；确认静态审阅包确定具体画面。两个节点分别解决“要做什么”和“怎么呈现”。

**能自由换颜色、横屏或不出镜吗？**

可以。固定的是贴纸解释关系、玻璃局部点缀的视觉方法；配色、画幅和人物使用方式根据素材确定。

**实际测试范围是什么？**

发布检查覆盖技能结构、相对引用、安装发现、安装后的文件完整性与静态示例显示。其他助手中的完整制作表现，以及各渲染器的端到端导出，需要在对应环境验证。

## 仓库结构

```text
sticker-glass-video-skill/
├── README.md
├── README.en.md
├── LICENSE
├── CONTRIBUTING.md
├── skills/ai-sticker-glass-video/
│   ├── SKILL.md
│   ├── LICENSE
│   ├── agents/openai.yaml
│   └── references/
│       ├── request-template.md
│       ├── review-package.md
│       └── style-guide.md
├── docs/assets/style-preview.png
└── examples/
    ├── README.md
    ├── storyboard.html
    ├── STORYBOARD.md
    ├── 素材来源表.md
    └── assets/
```

## 参与改进

欢迎通过 [Issues](https://github.com/alleinDuck/sticker-glass-video-skill/issues)反馈问题，或提交 Pull Request。请说明助手环境、输入材料类型、预期与实际结果，并使用已脱敏且可公开的样例。详见 [贡献说明](CONTRIBUTING.md)。

## 许可与参考

本仓库原创技能说明、文档与示例采用 [MIT License](LICENSE)。第三方素材和外部渲染工具遵循各自许可；本仓库许可不替代这些授权。

目录结构遵循 [Agent Skills 规范](https://agentskills.io/specification)；安装说明参考 [skills CLI](https://github.com/vercel-labs/skills)。
