# Case-30：时尚快剪服装广告 · 真人 · 中/英/韩三语台词版

> 工作流：用户提供一份日语 fashion ad prompt → Agent 分析运镜 + 合规降敏 + 出三语台词版
> **路径归属**：路径 A 概念驱动（真人参考图 + 快剪时尚广告范式）+ 多语言台词变体
> **执行日期**：2026-06-03
> **新范式**：**时尚快剪能量运镜（Fashion Fast-Cut）**——路径 D 三范式（vlog/电影预告/体育解说）之外的第 4 种

---

## 0. 基础信息

- **简称**：时尚快剪服装广告·三语版
- **范式**：Fashion Fast-Cut 时尚快剪（快切+甩镜+频闪+glitch+freeze-frame）
- **时长 / 比例**：10s · 9:16 竖屏（时尚广告竖屏原生）
- **参考图**：@图片1 真人模特（作唯一人脸/身份 + 服装参考）
- **台词**：3 个版本——中文 / 英文 / 韩文
- **字符数**：三版均 ≤1900（精简后实测，见第 5 节）

---

## 1. 原日语 prompt 分析

### 1.1 ✅ 运镜亮点（值得保留并沉淀进 skill）

原 prompt 的**运镜设计确实出色**，这套"时尚快剪能量运镜组"可作为 skill 新增范式：

| 运镜技巧 | 作用 |
|---------|------|
| **fast cuts synced to drums**（鼓点卡切） | 节奏能量，时尚广告核心 |
| **whip pans**（甩镜横扫） | 段间高速转场，凌厉感 |
| **snap zooms**（急推变焦到服装细节） | 强调面料/造型，广告卖点 |
| **white strobe flash frames**（白色频闪过渡帧） | 节拍重音的视觉锤击 |
| **glitch / frame skips**（故障/跳帧） | 潮流前卫感 |
| **low-angle hero shot**（低角度英雄镜） | 气场、剪影张力 |
| **wide-angle lean-in distortion**（广角凑近畸变） | 打破第四面墙的亲密冲击 |
| **slow-mo hair brush**（慢动作甩发） | 节奏对冲，柔化收尾 |
| **freeze-frame ending**（定格收尾） | 封面感、二刷钩子 |

**剪辑公式**：本质是 `editing-rhythm.md` 的**脉冲式（哒哒哒—轰！）**——快切堆叠 + 频闪重音 + 定格收束。

### 1.2 ⚠️ 合规问题（必须降敏，否则即梦 post-TNS 高风险）

原 prompt 有多处擦边，按 `image-to-prompt.md` 合规清单属**中-高风险**：

| 原 prompt 元素 | 风险 | 降敏处理 |
|---------------|------|---------|
| Extreme close-up of lips + ASMR whisper | 性暗示/ASMR 擦边 | 改"看向镜头的自信特写"，去 ASMR/去嘴唇极近 |
| 「バカみたいでしょ？」「でも、好きでしょ。」 | 挑逗台词（"但你喜欢吧"） | 改自信时尚台词，去挑逗 |
| fingers sliding into pocket/seam/**waistband** | 身体部位暗示 | 改"手整理衣领/袖口造型细节" |
| emphasize **silhouette / waist** | 身体凝视 | 改"服装造型/面料/态度"，加护栏 |
| **air kissing** 收尾 | 性暗示 | 改"自信定格 pose" |

**降敏总策略**：保留全部运镜能量，只把"性感挑逗"换成"时尚自信（fashion editorial）"，末尾加 `NOT a body-part closeup, no sexualized framing` 护栏。

---

## 2. 统一英文运镜框架（三版共用）

> **为什么用英文框架**：真人 fashion 广告 + 强运镜术语，英文表达更精准且利于真人化锁定（沿用 case-23 验证过的"真人场景英文框架"例外）。**仅台词三版切换语言**。

三版的台词和 voice 语言不同，其余完全一致。

---

## 3. 三语版本 Prompt（精简版 ≤1900）

### 3.1 中文台词版

```
Hyper-realistic 10s high-fashion commercial, vertical 9:16. Fast cuts synced to drums, handheld camera, high contrast, natural lighting, shallow depth of field, energetic rock beat with heavy drums and electric guitar. Whip pans, snap zooms, white strobe flash transition frames, subtle glitch effects.

REAL photorealistic human woman, natural skin texture and visible pores, NOT anime, NOT cartoon, NOT CG. Use @图片1 as the ONLY face and outfit reference; keep her facial likeness, hairstyle and exact outfit consistent in every shot.

0-2s HOOK: medium-close shot, she looks confidently into the lens, slightly shaky handheld, a small confident smile. She says in Chinese: 「嘿，看这里。」 Cut hard on a guitar drop.
2-4s BURST: rapid cuts on the drums, full-body confident stance, smash cut to a low-angle hero shot, white strobe flash, quick crouch as the camera drops with her, snap zoom to an outfit detail, hair moving, confident smirk.
4-7s PLAYFUL: erratic handheld, she leans toward the lens with slight wide-angle distortion, a quick spin with frame skips and glitch, a playful confident shrug. She says in Chinese: 「跟上我的节奏。」 Cut sharp on the beat.
7-10s ENDING: rhythm slows but stays intense, close-up of her hand adjusting a collar/sleeve detail, side-profile with a soft smile, hair brushing across her face in slow motion, she looks into the camera: 「这，就是我的风格。」 End on a white flash frame and a snap-zoom freeze-frame pose.

Audio: confident female Mandarin voice, energetic rock, punchy drums, electric guitar.
Style: high-fashion editorial, tasteful and confident, focus on outfit styling and attitude, NOT a body-part closeup, no sexualized framing. No text, subtitles, logos or watermark.
```

### 3.2 英文台词版

```
Hyper-realistic 10s high-fashion commercial, vertical 9:16. Fast cuts synced to drums, handheld camera, high contrast, natural lighting, shallow depth of field, energetic rock beat with heavy drums and electric guitar. Whip pans, snap zooms, white strobe flash transition frames, subtle glitch effects.

REAL photorealistic human woman, natural skin texture and visible pores, NOT anime, NOT cartoon, NOT CG. Use @图片1 as the ONLY face and outfit reference; keep her facial likeness, hairstyle and exact outfit consistent in every shot.

0-2s HOOK: medium-close shot, she looks confidently into the lens, slightly shaky handheld, a small confident smile. She says in English: "Hey, look here." Cut hard on a guitar drop.
2-4s BURST: rapid cuts on the drums, full-body confident stance, smash cut to a low-angle hero shot, white strobe flash, quick crouch as the camera drops with her, snap zoom to an outfit detail, hair moving, confident smirk.
4-7s PLAYFUL: erratic handheld, she leans toward the lens with slight wide-angle distortion, a quick spin with frame skips and glitch, a playful confident shrug. She says in English: "Keep up with me." Cut sharp on the beat.
7-10s ENDING: rhythm slows but stays intense, close-up of her hand adjusting a collar/sleeve detail, side-profile with a soft smile, hair brushing across her face in slow motion, she looks into the camera: "This is my vibe." End on a white flash frame and a snap-zoom freeze-frame pose.

Audio: confident female English voice, energetic rock, punchy drums, electric guitar.
Style: high-fashion editorial, tasteful and confident, focus on outfit styling and attitude, NOT a body-part closeup, no sexualized framing. No text, subtitles, logos or watermark.
```

### 3.3 韩文台词版

```
Hyper-realistic 10s high-fashion commercial, vertical 9:16. Fast cuts synced to drums, handheld camera, high contrast, natural lighting, shallow depth of field, energetic rock beat with heavy drums and electric guitar. Whip pans, snap zooms, white strobe flash transition frames, subtle glitch effects.

REAL photorealistic human woman, natural skin texture and visible pores, NOT anime, NOT cartoon, NOT CG. Use @图片1 as the ONLY face and outfit reference; keep her facial likeness, hairstyle and exact outfit consistent in every shot.

0-2s HOOK: medium-close shot, she looks confidently into the lens, slightly shaky handheld, a small confident smile. She says in Korean: "봐, 여기." Cut hard on a guitar drop.
2-4s BURST: rapid cuts on the drums, full-body confident stance, smash cut to a low-angle hero shot, white strobe flash, quick crouch as the camera drops with her, snap zoom to an outfit detail, hair moving, confident smirk.
4-7s PLAYFUL: erratic handheld, she leans toward the lens with slight wide-angle distortion, a quick spin with frame skips and glitch, a playful confident shrug. She says in Korean: "날 따라와." Cut sharp on the beat.
7-10s ENDING: rhythm slows but stays intense, close-up of her hand adjusting a collar/sleeve detail, side-profile with a soft smile, hair brushing across her face in slow motion, she looks into the camera: "이게 내 스타일이야." End on a white flash frame and a snap-zoom freeze-frame pose.

Audio: confident female Korean voice, energetic rock, punchy drums, electric guitar.
Style: high-fashion editorial, tasteful and confident, focus on outfit styling and attitude, NOT a body-part closeup, no sexualized framing. No text, subtitles, logos or watermark.
```

---

## 4. 三语台词对照

| 段落 | 中文 | 英文 | 韩文 |
|------|------|------|------|
| 0-2s Hook | 嘿，看这里。 | Hey, look here. | 봐, 여기. |
| 4-7s Playful | 跟上我的节奏。 | Keep up with me. | 날 따라와. |
| 7-10s Ending | 这，就是我的风格。 | This is my vibe. | 이게 내 스타일이야. |

> 台词已统一降敏：去掉原版「好きでしょ（你喜欢吧）」的挑逗意味，改为**时尚自信**调性，三语保持同一人设。

---

## 5. 设计意图 + 字符数实测

- **运镜全保留**：原日语 prompt 的快切/甩镜/频闪/glitch/低角度/慢动作甩发/freeze-frame 一个不少，时尚能量在线。
- **合规降敏**：ASMR 嘴唇特写→自信镜头特写；挑逗台词→自信宣言；waistband 触摸→整理衣领造型；air kiss→定格 pose；加 fashion editorial 护栏。
- **真人化前缀**：REAL photorealistic + natural skin + NOT anime/CG，防止参考图被带成插画感。
- **精简说明**：v1 三版均超 2000（2149-2177），删去重复修饰（documentary realism / 完整面料括号清单 / cinematic-yet-natural 等冗词）后压到 ≤1900。
- **前 2 秒生死线**：看镜头 + 自信台词 + 吉他重音切入，瞬间抓人。
- **二刷钩子**：freeze-frame 定格收尾 = 封面感。

**字符数实测**（Python `len()`）：见本 case 提交时脚本输出，三版均 ≤1900。

---

## 6. 执行建议

- **CLI 调用**：`image2video`（单图真人参考，比例自动跟随竖图）；若参考图非竖版，改 `multimodal2video --ratio=9:16`。
- **本 case 未实跑**（用户暂未提供真人参考图）——三版为可直接复制模板。
- **合规提醒**：即使已降敏，真人 + fashion + 快剪仍建议先 `seedance2.0fast_vip` 试片，确认 post-TNS 通过再升 1080p。

---

**报告完成时间**：2026-06-03
**报告人**：Claude（执行 Agent）