# Output Structure

Use this reference when creating or validating the generated asset tree.

## Required tree

```text
<故事名>/
├── <主角名>/
│   ├── 主体设定.md
│   ├── 正面图片的提示词.md
│   ├── 侧面图片的提示词.md
│   ├── 背面图片的提示词.md
│   └── 特写图片的提示词.md
├── 分镜1-故事总结/
│   ├── 分镜的提示词.md
│   ├── 首帧图片的提示词.md
│   ├── 尾帧图片的提示词.md
│   └── 分镜的解说词.md
├── 分镜2-故事总结/
│   ├── 分镜的提示词.md
│   ├── 首帧图片的提示词.md
│   ├── 尾帧图片的提示词.md
│   └── 分镜的解说词.md
└── ...
```

## Naming rules

- Story folder: use the story name the user asked for.
- Protagonist folder: use the confirmed protagonist name.
- Scene folders: use `分镜n-故事总结`, where `故事总结` is 10 Chinese characters or fewer.
- The scene summary should capture the key event of that scene, not a generic emotion or setting.
- Keep filenames exactly as specified in the PRD.

## Consistency checklist

- The protagonist is confirmed by the user before asset generation starts.
- The protagonist design and all prompt files describe the same person.
- The storyboard covers the complete story arc without duplication.
- Each scene maps to roughly 10-15 seconds of spoken content.
- `首帧图片的提示词.md` and `尾帧图片的提示词.md` create a plausible transition between scenes.
- `分镜的提示词.md` is specific enough to regenerate the same scene reliably.
- `分镜的解说词.md` tells the scene clearly without depending on adjacent narration to fill critical gaps.
