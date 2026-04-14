# History Story Video

把历史故事、历史事件、传奇片段或人物传记片段，拆成适合短视频生产的分镜素材包。

这个仓库打包了 `history-story-video` 这个 Skill，可用于：
- Codex
- Claude Code

一句话概括：

> 给一个历史故事，输出一套可直接进入 AI 绘图、视频生成和配音流程的分镜素材目录。

## 这个 Skill 解决什么问题

很多“历史故事短视频”工作流的问题不在于没有灵感，而在于：
- 故事主线抓不稳
- 主角视角不统一
- 人物形象在多张图里频繁漂移
- 分镜提示词、首尾帧、解说词彼此不匹配
- 输出目录没有规范，后续生产难复用

这个 Skill 的目标，就是把这些问题收敛成一套稳定、可复用、可批量生产的工作流。

它会把故事生产过程整理成这些核心工件：
- `主体设定.md`
- `正面图片的提示词.md`
- `侧面图片的提示词.md`
- `背面图片的提示词.md`
- `特写图片的提示词.md`
- `分镜n-故事总结/分镜的提示词.md`
- `分镜n-故事总结/首帧图片的提示词.md`
- `分镜n-故事总结/尾帧图片的提示词.md`
- `分镜n-故事总结/分镜的解说词.md`

## 工作流概览

Skill 的核心流程如下：

1. 识别用户想讲的历史故事或历史片段
2. 提炼故事主线、冲突、转折和结局
3. 确定最适合承载叙事的主角，并先让用户确认
4. 创建故事目录与主角目录
5. 生成统一的人物设定与 4 组角色提示词
6. 拆成 3 到 5 个关键分镜
7. 为每个分镜生成场景提示词、首帧提示词、尾帧提示词、解说词
8. 最终返回主角、目录路径、分镜数和必要假设

## 仓库结构

```text
.
├── skills/
│   └── history-story-video/
│       ├── SKILL.md
│       ├── agents/openai.yaml
│       └── references/
├── .claude-plugin/
│   └── marketplace.json
├── LICENSE
└── README.md
```

## 安装方式

### 一条命令同时安装到 Codex 和 Claude Code

可以用 `skills` CLI 安装到两个 Agent：

```bash
npx skills add WoodyXu/history-story-video --skill history-story-video -a codex -a claude-code -y
```

如果希望安装到全局目录，而不是当前项目目录：

```bash
npx skills add WoodyXu/history-story-video --skill history-story-video -a codex -a claude-code -g -y
```

### 仅安装到 Codex

Codex 用户也可以直接通过 GitHub 仓库路径安装这个 Skill。目标路径是：

```text
skills/history-story-video
```

安装后建议重启 Codex，使新 Skill 被正确加载。

### 通过 Claude Code Marketplace 安装

本仓库同时提供了 Claude Code 的 marketplace 清单。发布后，用户可以执行：

```text
/plugin marketplace add WoodyXu/history-story-video
/plugin install history-story-video@history-story-video-skills
```

## License

MIT，详见 [LICENSE](LICENSE)。
