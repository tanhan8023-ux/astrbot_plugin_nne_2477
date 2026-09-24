# astrbot_plugin_nne_2477

AstrBot 活人感人设插件，当前默认人设为 **诺奈 NNE-2477**。

## 功能

- 在 LLM 请求前注入人设、情绪、上下文、记忆和回复策略
- 记录短期聊天上下文，让 bot 能接住前文
- 记录偏好、状态、感谢、道歉、约定等陪伴型记忆
- 根据心情、熟悉度、生活节律和群聊氛围调整回复策略
- 支持“贴人设但不死板”的弹性人设锚点
- 清理重复表达、客服式尾巴和过长回复
- 支持 `/persona`、`/mood`、`/memory`、`/alive`、`/forget`

## 人设文件

这是诺奈 NNE-2477 的专属插件。

插件启动时会固定加载：

```text
data/persona_nne_2477.json
```

因此，直接安装并启用这个插件，就会使用诺奈的人设；不会被旧的
`persona_private.json`、`persona.json` 或环境变量覆盖。

`data/persona.json` 仅作为同内容备份保留。想使用其他人设时，请安装原版活人感插件，不要修改这个诺奈专属副本。
## 常用配置

- `name`: 角色名字
- `identity`: 角色身份
- `personality`: 性格特点
- `speaking_style`: 说话风格
- `rules`: 行为规则
- `example_dialogues`: 示例回复
- `special_users`: 特殊用户关系配置
- `work_knowledge`: 可选知识库
- `max_reply_chars`: 回复软长度限制
- `short_reply_rate`: 低概率短回比例
- `light_reply_rate`: 普通闲聊低存在感轻回比例
- `persona_flexibility`: 人设表达弹性
- `trait_anchor_rate`: 显性体现人设特征的概率
- `catchphrase_cooldown`: 是否避免连续复用口头禅
- `identity_mention_policy`: 身份背景主动提及策略
- `recent_context_limit`: 注入最近聊天上下文条数

## 活人感机制

- 生活节律：根据清晨、白天、晚上、深夜调整回复状态
- 低存在感轻回：非求助、非情绪消息可低概率压成短回
- 人设弹性：核心身份稳定，但不是每句话都展示设定
- 口头禅冷却：避免连续多轮机械复用常用短语
- 陪伴记忆：记录疲惫、身体、心情等最近状态，并在24小时内自然影响回复
- 会话情绪隔离：不同群聊不会互相污染心情
- 记忆去重与清除：重复事实会合并，可用 `/forget` 清除自己的长期记忆
- 技术回复自适应长度：排查问题时不会套用闲聊的短回复限制
