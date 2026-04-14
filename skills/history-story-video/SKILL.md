---
name: history-story-video
license: MIT
description: Use this skill when the user wants to turn a named historical story, event, legend, or人物传记片段 into a storyboard package for short-form video production. Use it for requests such as “帮我制作一个 xxx 的分镜脚本” or “帮我设计 xxx 这个故事”, where the deliverable should include story understanding, protagonist confirmation, a story folder, character design text, protagonist image prompts, and 3-5 scene folders with scene prompts, first/last frame prompts, and narration.
metadata:
  short-description: 将历史故事拆成短视频分镜素材包
---

# History Story Video

## Overview

Use this skill to turn a user-specified historical story into a directory of production-ready storyboard prompt assets.

Default output language is Chinese. Default workspace is the current project directory.

Read [references/output-structure.md](references/output-structure.md) when you need the exact folder tree, naming rules, or a pre-delivery checklist.

## Workflow

### 1. Understand the story first

- Identify the exact story or historical episode the user wants.
- Build a concise understanding of the story's arc, main conflict, beginning, turning point, climax, and ending.
- Determine the most suitable protagonist.
- Show the protagonist choice to the user and wait for confirmation before continuing.
- If the user revises the protagonist, treat the user's version as final and continue with that.

Do not generate the downstream materials before the protagonist is confirmed.

### 2. Create the story workspace

- Create a story folder in the current project directory using the story name.
- Keep the visible folder name close to the user's wording unless it would be unsafe for the filesystem.
- Store all later assets inside this story folder.

### 3. Generate protagonist design assets

- Create a subfolder named after the confirmed protagonist inside the story folder.
- Write a detailed Chinese character design file named `主体设定.md`.
- The design must cover at least:
  - appearance;
  - clothing;
  - temperament;
  - visual style;
  - age or age range if inferable;
  - historical setting cues that keep later images consistent.

Instead of generating image files directly, generate the following four Chinese image-prompt files based on the design:

- `正面图片的提示词.md`
- `侧面图片的提示词.md`
- `背面图片的提示词.md`
- `特写图片的提示词.md`

Each prompt must be detailed enough to be sent directly to an image model. Keep the same face, age, costume, silhouette, and era details across all four prompt files.

### 4. Decide the storyboard count

- Choose the best number of scenes needed to tell the full story cleanly.
- Prefer 3-5 scenes.
- Each scene should cover a key and meaningful stage of the story.
- Avoid repetition, omissions, invented side plots, or material outside the chosen story scope.
- Target each scene to support about 10-15 seconds of narration.

If the story boundary is ambiguous, state your interpretation before generating scene assets.

### 5. Generate scene assets

For each scene, create a folder named `分镜n-故事总结` inside the story folder.

Folder naming rules:

- `n` must follow chronological order starting from 1.
- `故事总结` must summarize that scene's dramatic beat in 10 Chinese characters or fewer.
- The summary should describe the scene's core event, not a vague mood word.

Inside each scene folder, create:

- `分镜的提示词.md`: a Chinese image-generation prompt describing the scene clearly and concretely;
- `首帧图片的提示词.md`: the prompt for the opening keyframe of the scene;
- `尾帧图片的提示词.md`: the prompt for the ending keyframe of the scene;
- `分镜的解说词.md`: narration that can carry the full beat of this scene in Chinese.

Scene rules:

- The prompt must be visually specific and align with the protagonist design.
- The first-frame and last-frame prompts must form a stable transition into adjacent scenes.
- Narration should be complete, concise, and easy to dub.
- Keep costume, lighting logic, character age, props, and geography consistent unless the story itself changes them.

Use static frame prompts that emphasize a decisive story moment rather than vague atmosphere shots.

## Output Rules

- Keep all text outputs in Chinese unless the user asks otherwise.
- Prefer historically grounded visual details over generic fantasy styling.
- If a key detail is uncertain, make the smallest reasonable assumption and state it briefly.
- All output files from this skill should be text files. Do not claim that an image has been generated unless an actual image-generation tool was invoked successfully.
- Do not overwrite existing files silently. If the target story folder already exists, inspect it first and preserve useful work unless the user asks to regenerate.

## Final Response

When the run is complete, report:

- the confirmed protagonist;
- the story folder path;
- the number of scenes generated;
- any assumptions made;
- any prompt files that were skipped or blocked.
