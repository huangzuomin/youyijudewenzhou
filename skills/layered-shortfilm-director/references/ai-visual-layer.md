# AI 视觉概念层制作规范

来源：`layered-shortfilm-director` 原始规范第 5、6、10、14 节。

---

## 1. 先规划镜头，不直接写长视频 Prompt

根据该幕时长和旁白节奏，将 AI 意象层拆成若干镜头。

参考量级：

- 10–15 秒：1–3 镜
- 15–25 秒：2–4 镜
- 25–35 秒：3–5 镜

**不要机械按秒拆。** 每个镜头必须有独立视觉任务。

---

## 2. 每个镜头必须输出

### 镜头编号与名称

示例：

`镜头 A｜从纸面城市回到真实街道`

### 建议时长

示例：

`建议时长：5–6 秒`

必须确保整幕镜头时长总和与该幕总时长大体匹配。

### 镜头作用

用一句话说明：这个镜头为什么存在。

### 文生图提示词

目标：先生成稳定、高质量首帧。

文生图 Prompt 重点描述：

- 构图
- 主体
- 空间
- 景深
- 光线
- 色调
- 材质
- 负空间
- 后期信息层需要的留白
- 人物是否出现
- 是否要避免可读文字
- 是否需要保持与前后镜头一致

不要在首帧 Prompt 中塞过多动作。

文生图首先追求：

> **一张静止下来也成立的画面。**

### 图生视频提示词

目标：基于已经生成的首帧，让视频只发生必要运动。

重点描述：

- 摄像机运动
- 环境运动
- 主体运动
- 节奏
- 稳定性
- 哪些区域尽量不动
- 什么时候镜头应安静
- 是否要给程序信息层稳定锚点

原则：

> **信息密度越高，AI 底图运动越克制。**

### Negative / Hard Constraints

列出这一镜禁止：

- 可读文字
- logo
- AI 假证据
- 随机粒子
- HUD
- 赛博朋克
- 夸张镜头
- 过度人物特写
- 会破坏程序层合成的复杂运动

根据场景补充。

---

## 3. AI 视觉层全局规则

### 3.1 背景不能和信息动画抢戏

当程序信息层是视觉主体时，AI 底图必须：

- 构图清楚
- 主体明确
- 留白充分
- 运动克制
- 不生成复杂文字
- 不自己演完程序层应该表达的逻辑

统一判断标准：

> **background must not compete with information animation**

### 3.2 首帧优先

如果文生视频质量不稳定，默认采用：

`文生图首帧 → 图生视频`

而不是长 Prompt 一次性文生视频。

优先保持：人物稳定、建筑稳定、构图稳定、风格统一、前后镜头一致、后期信息层可跟踪。

### 3.3 AI 意象层只完成 60%–80%

不要让 AI 把这一幕"讲完"。

AI 层只搭建：世界、空间、意象、情绪、物理舞台。

程序层负责完成：概念、关系、状态、判断。

---

## 4. 镜头 Prompt 输出模板

每幕 AI 视觉概念层按以下格式输出：

---

## 镜头 A｜镜头名
**建议时长：X–X 秒**

### 视觉任务
一句话。

### 文生图 Prompt
```text
...
```

### 图生视频 Prompt
```text
...
```

### Hard Constraints
- ...
- ...
- ...

---

重复到该幕全部镜头完成。

最后附：

### 本幕 AI 层统一控制语
```text
same visual world, same color language, background must not compete with information animation, stable composition, generous negative space...
```

---

## 5. 证据规则

凡涉及真实证据：

**AI Prompt 必须加入：**

```text
no readable fabricated documents,
no fake newspaper content,
no invented dates,
no invented source names,
evidence area must remain blank or unreadable for later compositing of verified assets
```

**Astra Brief 必须加入：**

> 程序层不得生成承担事实证明功能的虚假内容。
