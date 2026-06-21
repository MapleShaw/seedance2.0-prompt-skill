# Case-26：Neon Heart Streamer 游戏主播·直播间开场（真人版 + 台词）

> 工作流：角色卡驱动 · 无 prompt → Agent 设计场景
> **路径归属**：模板 D 直播间第一人称 + 真人化 + 直播口播
> **2026-05-29 主理人反馈**：v1 默片不知所云 → v2 真人化 + 直播开场口播 + 网红钩子

---

## 0. 基础信息

- **简称**：Neon Heart Streamer 游戏主播·直播间开场
- **范式**：模板 D 直播间第一人称 · 真人化 · 直播开场口播
- **时长 / 比例**：15s 9:16 竖屏（手机直播原生竖屏）
- **参考图**：@图片1 Neon Heart Streamer 角色卡（仅作服装/造型参考，渲染成真人）
- **迭代版本**：**v2·真人化 + 直播口播台词 + 网红钩子**

---

## 1. v1 → v2 改动

| 维度 | v1 | **v2** |
|------|-----|------|
| 真人化 | 未强调 | **强力声明 photorealistic real human, NOT anime/cartoon** |
| 视角 | 16:9 webcam | **改 9:16 竖屏**（手机直播原生）|
| 台词 | 无（默片）| **加完整直播开场口播**（最自然的口播场景）|
| 时长 | 10s | **15s**（直播口播信息量最大，撑满）|

---

## 2. 完整 Seedance Prompt（v2·真人版 + 台词）

```
Photorealistic vertical 9:16 live-stream opening, ~15s, from the viewer's view of a game streamer's phone camera. The subject must be a REAL photorealistic human woman with natural skin texture, visible pores and realistic hair — documentary realism, like real streaming footage. Use the character card ONLY for outfit, hairstyle and proportions; COMPLETELY re-render in real-life photographic style, IGNORE its art style. Absolutely NOT anime, NOT cartoon, NOT 2D, NOT 2.5D, NOT cel-shaded, NOT manga, NOT illustration, NOT 3D CG, NOT a game character.

Subject: an adult Asian woman with long black hair with pink highlights and a heart hair clip, wearing a black leather bomber jacket with a pink LIVE heart emblem and a pink crop top, with a streamer headset. Setting: cute home streaming room, pink-purple RGB lighting, LED keyboard and monitor behind her, plushies, pink LIVE neon sign, ring-light glow. Vertical phone-front-camera framing. A home gaming room, NOT a nightclub.

Timeline:
0-2s: She leans in with a bright excited smile, waves: "家人们晚上好呀！终于等到你们啦～"
2-5s: She adjusts her earpiece, points playfully: "今天直播间有大惊喜哦，记得双击点亮小红心！"
5-8s: A cute finger-heart near her cheek, a wink: "新来的宝子先点个关注，别走丢啦～"
8-11s: She tilts her head, sends a blowing kiss, laughs brightly. Cute youthful energy, not erotic.
11-13.5s: Both hands into a heart gesture, pink LIVE neon brighter: "爱你们哟～"
13.5-15s: She settles back with a cheerful wink, hands on the keyboard: "好啦，我们准备开黑！" Freeze on her smile.

Audio: clear cheerful young female Mandarin voice, lively warm streamer tone, soft upbeat music, a subtle keyboard click.

Style: photorealistic, consistent realistic face, stable outfit, heart hair clip visible, a wholesome young adult streamer at home. No face morphing, extra fingers, distorted hands, extreme body focus, sexualized pose, minors, nudity, real brand logos or real game branding.
```

---

## 3. 设计意图

**台词设计**（直播开场口播，最完整的网红话术）：
- 开场 hook："家人们晚上好呀！终于等到你们啦～"（亲切招呼）
- 互动引导："今天直播间有大惊喜哦，记得双击点亮小红心！"（引导互动）
- 涨粉钩子："新来的宝子先点个关注，别走丢啦～"（明确 CTA）
- 情绪收尾："爱你们哟～" + "好啦，我们准备开黑！"（拉近距离 + 引出正片）

**网红钩子**：直播间开场是抖音/直播平台最经典的高互动场景——完整复刻"招呼 → 引导互动 → 涨粉 CTA → 情绪 → 引出正片"话术结构。15s 撑满信息量。

---

## 4. 五关扫描结果

| 关 | 项 | 结果 |
|---|----|------|
| 1 | 字符数 | **1893**（含超强真人化前缀，<2000）|
| 2 | 品牌词 | ✓ 无 |
| 3 | 涉灰场景词 | ✓ 无 |
| 4 | 夜场 BGM 词 | ✓ 无 |
| 5 | 真人化声明 | ✓ 已加（开头+中段+结尾负面三重）|

---

**报告完成时间**：2026-05-29 21:46
**等待主理人**：跑 v2 验证（预期爆款率最高：直播题材 + 完整口播）
