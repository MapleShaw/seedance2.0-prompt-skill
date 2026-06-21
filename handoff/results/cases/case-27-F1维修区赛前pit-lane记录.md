# Case-27：Azure Pitlane Siren F1 维修区女郎·赛前 pit lane（真人版 + 台词）

> 工作流：角色卡驱动 · 无 prompt → Agent 设计场景
> **路径归属**：模板 B 手机竖屏 + 真人化 + 赛车应援口播
> **2026-05-29 主理人反馈**：v1 默片不知所云 → v2 真人化 + 赛车应援台词 + 网红钩子

---

## 0. 基础信息

- **简称**：Azure Pitlane Siren F1 维修区女郎·赛前 pit lane
- **范式**：朋友手机竖屏 vlog · 真人化 · 赛车现场口播
- **时长 / 比例**：12s 9:16 竖版
- **参考图**：@图片1 Azure Pitlane Siren 角色卡（仅作服装/造型参考，渲染成真人）
- **迭代版本**：**v2·真人化 + 赛车应援台词 + 网红钩子**

---

## 1. v1 → v2 改动

| 维度 | v1 | **v2** |
|------|-----|------|
| 真人化 | 未强调 | **强力声明 photorealistic real human, NOT anime/cartoon** |
| 台词 | 无（默片）| **加赛车现场应援口播**（带粉丝看比赛）|
| 钩子 | 平淡 pan | **赛车轰鸣开场 hook + 带看比赛 + 夺冠 flag 收尾** |

---

## 2. 完整 Seedance Prompt（v2·真人版 + 台词）

```
Photorealistic raw smartphone vlog, vertical 9:16, ~12s, filmed by a friend in the racing pit lane before a fictional 2030 grand prix. The subject must be a REAL photorealistic human woman with natural skin texture, visible pores and realistic hair — documentary realism, like real footage. Use the character card ONLY for outfit, hairstyle and proportions; COMPLETELY re-render in real-life photographic style, IGNORE its art style. Absolutely NOT anime, NOT cartoon, NOT 2D, NOT 2.5D, NOT cel-shaded, NOT manga, NOT illustration, NOT 3D CG, NOT a game character.

Subject: an adult Asian woman with black hair with blue highlights, in a blue-white bomber crop jacket with a lightning emblem, sport top, black shorts, fingerless gloves and a pit comms headset. Setting: pit garage, a modern racing car silhouette in background (no real logos), engineers in blue-white uniforms passing, tools and tire racks, blue team lighting, faint revving engines and radio chatter. A professional pit lane, NOT a nightclub. Handheld phone footage, candid friend-shot.

Timeline:
0-2.5s: Camera pans from the racing car to find her adjusting her headset, focused. She turns to camera, eyes bright: "比赛马上就要开始啦！"
2.5-5.5s: She steps toward the camera through the pit lane: "今天我们车队冲冠军，跟我一起加油好不好？"
5.5-8s: An engineer crosses the foreground; she reappears, laughs, a finger-heart near her cheek, then a playful blowing kiss. Cute, not erotic.
8-10s: She turns toward the car, then back, both hands into a heart gesture, blue team light on her.
10-12s: She points at the car: "发车啦！记得关注我看比赛直播！" then a confident wink as camera pulls back.

Audio: clear energetic female Mandarin voice, excited racing-fan tone, revving engines, team radio chatter, dynamic music.

Style: photorealistic, consistent realistic face, stable outfit, headset visible. No face morphing, extra fingers, distorted hands, extreme body focus, sexualized pose, minors, nudity, real brand logos or real racing/sponsor branding.
```

---

## 3. 设计意图

**台词设计**（赛车现场应援网红风）：
- 开场 hook："比赛马上就要开始啦！"（现场紧张感）
- 互动："今天我们车队冲冠军，跟我一起加油好不好？"（带粉丝参与）
- 收尾 CTA："发车啦！记得关注我看比赛直播！"（涨粉钩子）

**网红钩子**：赛车轰鸣开场 + 带粉丝看比赛 + 工程师擦镜（模板 B 经典技巧）+ 夺冠 flag 收尾。

---

## 4. 五关扫描结果

| 关 | 项 | 结果 |
|---|----|------|
| 1 | 字符数 | **1980**（含超强真人化前缀，<2000）|
| 2 | 品牌词 | ✓ 无 |
| 3 | 涉灰场景词 | ✓ 无 |
| 4 | 夜场 BGM 词 | ✓ 无 |
| 5 | 真人化声明 | ✓ 已加（开头+中段+结尾负面三重）|

---

**报告完成时间**：2026-05-29 21:48
**等待主理人**：跑 v2 验证
