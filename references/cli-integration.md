# Dreamina CLI 集成指南（可选增值）

> 即梦官方命令行工具 `dreamina` 的集成规范。Skill 的主输出仍是"可复制的中文提示词"，CLI 执行是**可选增值步骤**，用户明确说"跑"才执行。

---

## 0. 设计原则（写在最前，不能违反）

1. **提示词输出是主线，CLI 执行是支线。** 任何情况下都要先给出可复制的提示词文本；CLI 跑不通不影响 Skill 可用性。
2. **消耗积分的命令执行前必须警告。** 跑之前明确告知模型、分辨率、时长、预估消耗；余额不足（<100）拒跑。
3. **默认保守（模式 A）**：生成完提示词后**询问**用户是否执行，绝不默认跑。
4. **不硬编码模型参数。** 以官方 `dreamina <cmd> -h` 的实时输出为准；本文档只描述当前约定的默认值。
5. **以 `submit_id` 和 `gen_status` 判断成败**，不看 exit code。
6. **遇到 `AigcComplianceConfirmationRequired`**：引导用户先去 Web 端完成授权，再 retry。
7. **单次对话内连续失败 3 次后必须停下**，问用户"问题是提示词还是模型，是否换策略"，避免无脑烧积分。

---

## 1. 前置检查

调用 CLI 前按顺序验证：

```bash
# 1. 命令存在
command -v dreamina || echo "CLI 未安装，访问 jimeng.jianying.com/cli 安装"

# 2. 已登录 + 看余额
dreamina user_credit
```

`user_credit` 返回示例：

```json
{
  "total_credit": 5077,
  "user_id": 2107134092516990,
  "user_name": "",
  "vip_level": "maestro"
}
```

**判断规则**：

| 场景 | 动作 |
|--|--|
| 无返回 / 报未登录 | 提示用户 `dreamina login` 后再试，暂停执行 |
| `total_credit < 100` | 拒跑，提示充值 |
| `total_credit < 500` | 警告余额偏低，让用户确认是否继续 |
| `vip_level` 为 `maestro` / `pro` / `vip` | 可以用 `seedance2.0_vip`（1080p 支持） |
| `vip_level` 为空 / 普通 | 降级到 `seedance2.0` 或 `seedance2.0fast`，720p |

---

## 2. 命令选型决策树（路径 C）

```
用户素材只有 1 张图 + 提示词？
├─ 是 → image2video（最轻量，比例自动从图推断）
└─ 否（多图 / 参考视频 / 音频 / @图片1@图片2 多素材 @引用）
    → multimodal2video（全能参考，需手动指定 --ratio）
```

### 2.1 `image2video`（单图场景，路径 C 默认）

**典型调用**：

```bash
dreamina image2video \
  --image='/path/to/scene.jpg' \
  --prompt="$(cat /tmp/dreamina_prompt.txt)" \
  --duration=15 \
  --model_version=seedance2.0_vip \
  --video_resolution=720p \
  --poll=120
```

**关键点**：
- **比例自动从输入图推断**，不要传 `--ratio`（传了会报错）
- `--prompt` 用 `$(cat file)` 读文件的方式传，彻底避开 shell 转义问题（见第 5 节）
- `--duration` 支持 `4-15`，**路径 C v2 默认值由 image-to-prompt.md 的"建议时长"推算决定，不再硬编码 15**（v2 升级）
- `--poll=120` 提交后最多前台等 120 秒，超时自动 fallback 到 `query_result`

### 2.2 `multimodal2video`（全能参考场景）

**典型调用**：

```bash
dreamina multimodal2video \
  --image='/path/to/img1.jpg' \
  --image='/path/to/img2.jpg' \
  --prompt="$(cat /tmp/dreamina_prompt.txt)" \
  --ratio=9:16 \
  --duration=15 \
  --model_version=seedance2.0_vip \
  --video_resolution=720p \
  --poll=120
```

**关键点**：
- 必须指定 `--ratio`，可选 `1:1, 3:4, 16:9, 4:3, 9:16, 21:9`
- `--image` 可重复多次传多张图（上限 9 张）
- 可选 `--video`（上限 3）`--audio`（上限 3，时长 2-15s）
- 至少需要一张 `--image` 或 `--video`

---

## 3. 默认参数约定（Skill 路径 C 用）

| 参数 | 默认值 | 何时改 |
|--|--|--|
| `--model_version` | `seedance2.0_vip` | 想快速试片/降本 → `seedance2.0fast_vip`；无 VIP → `seedance2.0` |
| `--video_resolution` | `720p` | 成品满意后用户要 1080p → 改 `1080p`（仅 `seedance2.0_vip` 支持） |
| `--duration` | `15` | 用户要更短就按用户的 |
| `--poll` | `120` | 网络差可调到 `180`；不想等就设 `0` |
| `--ratio`（仅 multimodal） | 跟随路径 C 的比例诊断结果 | - |

**质量 / 速度 / 成本光谱**（从高到低）：

```
seedance2.0_vip (1080p)   ← 最终成片
seedance2.0_vip (720p)    ← 默认
seedance2.0               ← 标准
seedance2.0fast_vip       ← VIP 快速试片
seedance2.0fast           ← 最便宜的试片
```

---

## 4. 交互模板（Skill 路径 C Step 4）

**生成提示词后，Skill 默认输出这段询问**：

```
---

## 是否直接调用 dreamina CLI 生成？

- **图片**：./scene.jpg
- **模型**：seedance2.0_vip
- **分辨率**：720p（效果满意后可升级 1080p）
- **时长**：15s
- **比例**：自动从图推断（image2video）
- **预计前台等待**：最多 120s，超时转后台轮询

**当前余额**：[运行 user_credit 查到的值] 积分

回复：
- `跑` / `yes` → 直接执行 image2video（默认配置）
- `fast` → 换 seedance2.0fast_vip 试片（更便宜更快）
- `1080p` → 升到 1080p 高质量（仅 seedance2.0_vip）
- `no` / 不回 → 只保留提示词，不执行
```

**用户回复后的处理**：

| 回复 | 动作 |
|--|--|
| `跑` / `yes` / `执行` / `go` | 按默认配置调用 image2video |
| `fast` / `试片` | 切换 `--model_version=seedance2.0fast_vip`，其他不变 |
| `1080p` / `高清` | 切换 `--video_resolution=1080p`，警告消耗翻倍 |
| `no` / 不回 / 其他话题 | 不执行，保留提示词 |
| 提出调整提示词 | 回到提示词迭代，调整完再次询问 |

---

## 5. Shell 转义与提示词传递

**问题**：Seedance 提示词经常包含中文引号、英文引号、冒号、逗号、换行，直接塞 `--prompt="..."` 容易翻车。

**稳妥方案：写入临时文件 + `$(cat ...)`**

```bash
# 1. 把提示词写入临时文件（cat heredoc 避开所有转义）
cat > /tmp/dreamina_prompt.txt <<'PROMPT_EOF'
15秒赛博朋克暴雨追逐，8K超高清...（完整提示词多行都可以）
PROMPT_EOF

# 2. 调用时用 $(cat file) 读入
dreamina image2video \
  --image='/path/to/scene.jpg' \
  --prompt="$(cat /tmp/dreamina_prompt.txt)" \
  --duration=15 \
  --model_version=seedance2.0_vip \
  --video_resolution=720p \
  --poll=120
```

**heredoc 用 `<<'PROMPT_EOF'`（带单引号）很关键**，这样里面的 `$` `` ` `` `\` 全部按字面量处理，不会被 shell 二次解释。

**图片路径用单引号包裹**（`'/path/with spaces/img.jpg'`），防空格和特殊字符。

**执行完清理临时文件**：
```bash
rm -f /tmp/dreamina_prompt.txt
```

---

## 6. 异步任务处理

### 6.1 提交成功的识别

提交后 CLI 会返回 JSON（或结构化输出），**关键字段**：

- `submit_id`：任务 ID，必须记下来
- `gen_status`：任务状态（`pending` / `running` / `success` / `fail`）
- `result`：成功时包含视频 URL 或本地保存路径

**判断**：看 `submit_id` 有没有拿到。**不看 exit code**。

### 6.2 Poll 超时的处理

如果 `--poll=120` 到点还没完成，CLI 会返回当前状态（通常是 `running`），此时要告诉用户：

```
任务已提交，submit_id=xxxx
目前仍在生成中，前台等待已超时。可以稍后手动查：

  dreamina query_result --submit_id=xxxx

或者让我稍等 30-60 秒再帮你查一次。
```

**我可以在对话里主动再跑一次 query_result**，但不要无脑轮询烧 token。

### 6.3 失败处理

`gen_status=fail` 时，读 `fail_reason` 字段，常见：

| fail_reason | 含义 | 处理 |
|--|--|--|
| `AigcComplianceConfirmationRequired` | 模型需要先在 Web 端完成授权 | 引导用户去 https://jimeng.jianying.com 对应模型首次使用授权后重试 |
| 内容安全 / 合规相关 | 提示词或图片触发了内容安全 | 分析提示词，去掉敏感元素重写 |
| 配额 / 限流 | 模型当前 capacity 紧张 | 建议换 `seedance2.0fast_vip` 或稍后重试 |
| 超时 / 网络 | 服务端出错 | 直接重试 |

---

## 7. 审计日志建议

每次执行后在对话里简要回显一次执行记录，方便用户回溯：

```
### 执行记录
- 命令：dreamina image2video
- 图片：./scene.jpg
- 模型：seedance2.0_vip / 720p / 15s
- submit_id：xxxxxxxx
- 状态：success
- 结果：[视频路径或 URL]
- 消耗：[如 CLI 返回了扣分数就写]
```

---

## 8. 硬约束（Skill 级 guardrail）

1. **跑之前必须先 `user_credit`**，余额 < 100 拒跑。
2. **prompt 中含品牌名 / 真人名 / 政治人物**时，即使模型没拦也要先警告。
3. **连续失败 3 次强制停下问用户**："问题是提示词还是模型，是否换策略？"
4. **用户没说"跑"就不要跑。** 哪怕提示词改了 N 版，也只输出文本。
5. **不要跑 image2video 时传 `--ratio`**（不支持，会报错）。
6. **不要把 `--prompt` 的内容直接写进命令行字符串**，始终走临时文件方案（第 5 节）。

---

## 9. 常见错误速查

| 现象 | 原因 | 解决 |
|--|--|--|
| `command not found: dreamina` | CLI 没装 / PATH 没刷新 | 重开终端，或 `export PATH="$HOME/.local/bin:$PATH"` |
| 登录状态丢失 | token 过期 | `dreamina relogin` |
| `unsupported ratio` | image2video 传了 `--ratio` | 去掉 `--ratio`，image2video 从图自动推断 |
| `1080p not supported` | 非 `seedance2.0_vip` 模型用了 1080p | 要么换模型，要么改 720p |
| `AigcComplianceConfirmationRequired` | 模型首次使用未授权 | 去 Web 端该模型下走一次生成流程授权，再 retry |
| `duration out of range` | 超出模型支持范围 | seedance2.0 家族支持 4-15s |
| prompt 里的中文冒号变乱码 | shell 转义出错 | 用临时文件方案（第 5 节） |
| 余额充足但秒挂 | 可能是图片格式 / 大小问题 | 换 jpg/png，尺寸控制在 2K 以内 |

---

## 10. 与其他文档的关系

- 路径 C 提示词生成方法论 → [image-to-prompt.md](image-to-prompt.md)
- 平台基础参数（画幅/时长等限制）→ [platform-specs.md](platform-specs.md)
- 实时命令参数以 `dreamina <subcommand> -h` 为准，本文档仅描述 Skill 约定的默认配置

---

## 11. 非路径 C 场景的兼容

虽然默认只在路径 C Step 4 激活 CLI 询问，但如果用户在路径 A / B 中明确说"帮我直接跑"，也可以按同样的决策树调用：

- 路径 A（纯文本）→ `dreamina text2video`（参数类似，`-h` 现查）
- 路径 B 的逐镜头 → 每个镜头单独调 `image2video` 或 `multimodal2video`
- 角色图/首帧图生成 → `dreamina text2image` / `image2image`

这些不是当前集成的主线，用户明确要求时现场查 `-h` 组命令即可。
