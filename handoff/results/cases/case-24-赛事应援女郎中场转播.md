# Case-24：Crimson Rally Muse 红色应援女郎·决赛看台助威（真人版 + 台词）

> 工作流：角色卡驱动 · 无 prompt → Agent 设计场景
> **路径归属**：模板 B 手机竖屏 + 真人化 + 应援口播
> **2026-05-29 主理人反馈**：v1 默片无吸引力 → v2 真人化 + 喊加油台词 + 网红钩子

---

## 0. 基础信息

- **简称**：Crimson Rally Muse 红色应援女郎·决赛看台助威
- **范式**：朋友手机竖屏 vlog · 真人化 · 现场应援口播
- **时长 / 比例**：12s 竖版 9:16（改竖屏更适合抖音应援视频）
- **参考图**：@图片1 Crimson Rally Muse 角色卡（仅作服装/造型参考，渲染成真人）
- **迭代版本**：**v2·真人化 + 喊加油台词 + 网红钩子**

---

## 1. v1 → v2 改动

| 维度 | v1 | **v2** |
|------|-----|------|
| 真人化 | 未强调 | **强力声明 photorealistic real human, NOT anime/cartoon** |
| 视角 | 16:9 转播 | **改 9:16 朋友手机竖屏**（应援视频抖音原生竖屏更带感）|
| 台词 | 无 | **加现场喊加油口播**（最有感染力的应援场景）|
| 钩子 | 平淡找人 | **前 3 秒激动拉镜头 + 带粉丝一起喊 + 高能收尾** |

---

## 2. 完整 Seedance Prompt（v2·真人版 + 台词）

```
Photorealistic live-action 12s vertical 9:16 fan-cam, filmed by a friend in the front row of a packed arena during a fictional 2030 championship final. The subject must be a REAL photorealistic human woman with natural skin texture, visible pores and realistic hair — documentary realism, like real footage indistinguishable from a real video. Use the character card ONLY for outfit, hairstyle and proportions and COMPLETELY re-render in real-life photographic style, IGNORE its art style. Absolutely NOT anime, NOT cartoon, NOT 2D, NOT 2.5D, NOT cel-shaded, NOT manga, NOT illustration, NOT 3D CG, NOT a game character.

Subject: an energetic adult Asian woman, black hair in a high ponytail, wearing a red star-emblem crop top, red shorts, red-gold striped knee-high socks and a red star wristband, holding a glowing red light stick. Arena: red-gold lighting, big LED screens with abstract visuals, waving flags and light sticks, blurred cheering crowd, no real logos. Handheld vertical phone footage, energetic shake, candid friend-shot.

Timeline:
0-2.5s: Phone tilts up from waving light sticks to find her jumping excitedly. She turns to camera, eyes bright, shouts: "决赛打到加时了！太燃了！"
2.5-5.5s: She pumps her light stick twice on the beat, leans in: "宝子们，跟我一起喊——加油！加油！"
5.5-8s: She laughs, a quick finger-heart near her cheek, then a playful blowing kiss. Cute, not erotic.
8-10s: Both hands into a clear heart gesture, LED screen flashing red-gold, ponytail bouncing.
10-12s: She points at the stage: "冠军一定是我们的！记得关注我看后续！" then jumps and cheers as the crowd erupts.

Audio: clear energetic female Mandarin voice shouting cheers, loud arena crowd, rhythmic chanting, exciting music.

Style: photorealistic live-action, consistent realistic face across frames, stable outfit, ponytail flowing. NOT anime/cartoon/illustration/CG. No face morphing, extra fingers, distorted hands, extreme body focus, sexualized pose, minors, nudity or real brand logos.
```

---

## 3. 设计意图

**台词设计**（现场应援网红风，感染力拉满）：
- 开场 hook："决赛打到加时了！太燃了！"（瞬间点燃情绪）
- 中段互动："宝子们，跟我一起喊——加油！加油！"（带粉丝参与）
- 收尾 CTA："冠军一定是我们的！记得关注我看后续！"（涨粉钩子）

**真人化 + 网红钩子**：前 2.5 秒激动跳起来拉镜头（强 hook）→ 喊加油带动参与 → 比心飞吻 → 高能 CTA 收尾。

---

## 4. 五关扫描结果

| 关 | 项 | 结果 |
|---|----|------|
| 1 | 字符数 | **1953**（含超强真人化前缀，<2000）|
| 2 | 品牌词 | ✓ 无 |
| 3 | 涉灰场景词 | ✓ 无 |
| 4 | 夜场 BGM 词 | ✓ 无 |
| 5 | 真人化声明 | ✓ 已加（开头+中段+结尾负面三重）|

---

**报告完成时间**：2026-05-29 21:42
**等待主理人**：跑 v2 验证
