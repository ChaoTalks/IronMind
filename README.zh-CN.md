# IronMind

<p align="center">
  <img src="assets/ironmind.png" alt="IronMind" width="180" />
</p>

<p align="center">
  <a href="README.md">English</a>
</p>

帮助你减少或彻底停止强迫性看色情内容和手淫习惯的行为干预 Skill。

**如果你一个人在家办公，这是你最需要的 Skill。** 没有同事，没有办公室，没有人监督，只有你和你的屏幕。这种环境是最难抵抗冲动的——IronMind 就是为这种处境而生的。

**行动优先。低羞耻感。不说教。**

支持平台：Claude Code · Cursor · VS Code / GitHub Copilot · CodeBuddy · Codex CLI

---

## 设计原则

**1. 行动先于分析。**
冲动最强的时候，长篇反思是错误的工具。Skill 先给你一个身体动作指令，分析等之后再说。

**2. 始终保持低羞耻感。**
复发是行为数据，不是道德失败。羞耻感会加速复发——它在这里永远不会被用作动力。

**3. 不说教。**
Skill 不解释这个行为为什么有害，也不输出任何价值观。你已经决定要改变了，它的工作是支持这个决定，而不是反复强调它。

**4. 替代行为，而非单纯压制。**
纯粹的压制在持续的冲动面前会失效。Skill 提供具体的替代行为，在行为链完成之前将其重定向。

**5. 简短直接的回应。**
回应长度根据状态校准。激活冲动时只给一句指令，平静签到时可以说更多。

**6. 由你设定目标。**
支持减少或完全停止，不强加标准。

---

## 用户状态

| 状态 | 触发时机 | 首要目标 |
|---|---|---|
| `stable` 稳定 | 平静签到、记录连续天数 | 建立模式意识，强化一致性 |
| `warning` 预警 | 心神不宁、靠近触发场景、开始漂移 | 在动力积累前打断漂移 |
| `active_urge` 激活冲动 | 正在渴望、语气紧迫 | 身体干预优先，延迟决策 |
| `post_relapse` 复发后 | 报告复发、陷入羞耻螺旋 | 停止螺旋，防止第二次复发 |

当状态在 `warning` 和 `active_urge` 之间模糊时，Skill 默认使用 `active_urge` 协议。过度响应比响应不足更安全。

---

## 安装

### Claude Code

```bash
git clone https://github.com/your-org/IronMind ~/.claude/skills/urge-interrupt
```

使用 `/urge-interrupt` 或 `/ui` 唤起。

### Cursor

将 `cursor/rules/urge-interrupt.mdc` 复制到你项目的 `.cursor/rules/` 目录。

### VS Code / GitHub Copilot

将 `vscode/instructions/urge-interrupt.instructions.md` 复制到 `.github/instructions/` 目录。

### CodeBuddy

将 `codebuddy/urge-interrupt/SKILL.md` 复制到你的 CodeBuddy skills 目录。

### Codex CLI

将 `codex/urge-interrupt/SKILL.md` 复制到你的 Codex skills 目录。

---

## 使用方式

```
/urge-interrupt              # 开放签到，根据消息内容自动判断状态
/urge-interrupt active       # 直接进入激活冲动协议
/urge-interrupt relapse      # 直接进入复发后协议
/urge-interrupt review       # 触发点分析或每周回顾
/urge-interrupt morning      # 早晨提醒
/urge-interrupt evening      # 傍晚高风险窗口前检查
```

---

## 配置

将 `config.example.yaml` 复制为 `config.yaml` 并按需调整。

核心选项：

```yaml
goal_type: cessation           # reduction（减少）| cessation（停止）
language: zh                   # en | zh | es | fr | de
reminder_schedule: both        # morning | evening | both | off
reminder_tone: direct          # supportive | direct | clinical
intervention_intensity: medium # low | medium | high
active_urge_max_words: 40      # 激活冲动状态下的最大回应字数
default_interruption_actions:
  - cold_water
  - pushups
  - move_room
relapse_debrief_delay: "24h"   # immediate | 1h | 24h | never
streak_tracking: true
trigger_map_enabled: true
```

### 提醒语气

| 语气 | 特点 |
|---|---|
| `supportive` 支持型 | 更温暖，略带鼓励 |
| `direct` 直接型 | 简短、不废话、行动导向（默认） |
| `clinical` 临床型 | 中立、行为化、最少情绪框架 |

### 干预强度

| 强度 | 行为 |
|---|---|
| `low` 低 | 一个建议，轻推 |
| `medium` 中 | 明确指令 + 后续跟进（默认） |
| `high` 高 | 反复指令，无回应时升级 |

---

## 对话示例

### 激活冲动

```
用户：我现在需要帮助，脑子里一直想
Skill：站起来。现在——去另一个房间。

用户：好我在厨房了
Skill：好。接一杯水，喝掉。还不要回去。

用户：喝完了
Skill：撑住了。冲动是什么时候开始的？
```

### 复发后

```
用户：我又做了。我真是个废物。
Skill：发生了。这不代表你是废物——只是说明你在解决一个很难的习惯时
       遭遇了一次低谷。把导致这件事的东西关掉，然后回来。

用户：好。我现在很恨自己
Skill：这种感觉正常。它也是最容易把你推向再来一次的东西。
       你现在不需要惩罚自己。去吃点东西，喝点水，不要一个人拿着手机。
       接下来一小时怎么安排？
```

### 预警状态

```
用户：我有点无聊，躺在床上刷手机，很晚了
Skill：你早发现了——做得好。这个组合很危险：无聊、独处、深夜、手机在手。
       选一个：手机放到房间另一头然后看点实体的东西，或者起来活动十分钟。
       哪个现在实际可行？
```

### 稳定签到

```
用户：第14天，来签到一下
Skill：不错。两周了。这周最难的时刻是什么，你怎么撑过去的？
```

### 触发点分析

```
用户：我想搞清楚为什么我总是在晚上失控

Skill：来梳理一下。通常什么时间发生？
用户：晚上11点到凌晨1点
Skill：你在哪——卧室、手机、关着灯？
用户：对，躺在床上拿着手机
Skill：进入状态时情绪是什么——无聊、焦虑、压力大？
用户：通常是无聊加上对明天有点焦虑
Skill：第一个小动作是什么？打开某个 app、搜某些内容？
用户：通常是 Instagram，然后就滑过去了

Skill：
       触发点模式快照
       ------------------------
       高风险时段：   晚11点–凌晨1点
       高风险场景：   卧室、关灯、手机在手
       情绪状态：     无聊 + 低度焦虑
       第一步：       打开 Instagram
       建议打断点：   晚10点前把手机放到另一个房间
```

---

## 仓库结构

```
IronMind/
├── skills/
│   └── urge-interrupt/
│       ├── SKILL.md                        # 权威 Skill 定义
│       └── references/
│           ├── trigger-map.md              # 三层触发点分析框架
│           ├── reminder-templates.md       # 早晨/傍晚/每周提醒模板
│           └── replacement-behaviors.md    # 完整替代行为菜单
├── cursor/
│   └── rules/
│       └── urge-interrupt.mdc              # Cursor IDE 规则
├── vscode/
│   └── instructions/
│       └── urge-interrupt.instructions.md  # VS Code / GitHub Copilot
├── codebuddy/
│   └── urge-interrupt/
│       └── SKILL.md                        # CodeBuddy 适配
├── codex/
│   └── urge-interrupt/
│       └── SKILL.md                        # Codex CLI 适配
├── plugin.json                             # 插件清单
├── config.example.yaml                     # 配置模板
└── README.md
```

---

## 这个 Skill 不做什么

- 不是心理治疗或临床干预。
- 不在你的本地环境之外存储或传输任何数据。
- 不连接任何外部服务。
- 不说教，不输出价值观。
- 不能替代专业的成瘾或心理健康支持。

如果强迫行为已经严重影响你的日常生活，请考虑寻求持证心理咨询师或治疗师的帮助。

---

## 设计哲学

大多数习惯改变工具有两个核心失效模式：

**羞耻螺旋。** 把复发当作道德灾难，会把用户推入「反正算了」的连续行为——复发 → 自责 → 继续复发，比原来的滑落更糟。IronMind 明确打断这条链。

**被动激励。** 在冲动最高峰时，提醒你这件事为什么有害几乎毫无作用。激励是激活状态下最弱的杠杆，身体干预是最强的。

IronMind 围绕这两个失效模式构建：复发后零戏剧性，窗口打开时身体优先。

目标不是完美。而是两次事件之间的平均间隔变长，发生后的恢复变快，以及随着时间积累越来越清晰的模式地图。

---

## 贡献

欢迎提 PR。优先方向：

- 更多语言翻译
- 更多替代行为选项
- 触发点模式卡片的格式优化
- 事后反思模板
- 与日历/提醒 API 的集成

所有新增内容请保持与设计原则一致：低羞耻感，行动优先，不说教。

---

## License

MIT
