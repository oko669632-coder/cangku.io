# 塔罗牌 AI 解牌配置指南

## 功能概述

本应用集成了 AI 解牌功能，在完成三张牌的抽取后，会自动进入 AI 解牌环节，为每张牌提供神秘而富有启发性的解读。

## 支持的 AI 接口

应用支持 **OpenAI 兼容格式** 的 API，包括但不限于：

- **OpenAI** (GPT-4, GPT-3.5, etc.)
- **DeepSeek** (深度求索)
- **Azure OpenAI**
- **Other OpenAI-compatible providers** (任何兼容 OpenAI API 的服务)

## 配置步骤

### 1. 获取 API 密钥

#### 使用 OpenAI
1. 访问 https://platform.openai.com/account/api-keys
2. 创建新的 API 密钥
3. 保存密钥（不要泄露）

#### 使用 DeepSeek
1. 访问 https://platform.deepseek.com/
2. 注册并创建 API 密钥
3. API 基础 URL: `https://api.deepseek.com/v1`

#### 使用其他提供商
确保提供商支持 OpenAI 兼容的 `/v1/chat/completions` 接口。

### 2. 启用 AI 解牌

1. 启动应用并点击"进入仪式"
2. 右上角会出现 **⚙️ AI 解牌配置** 面板
3. 点击"启用 AI 解牌"旁的开关，使其变为金色激活状态

### 3. 填写配置信息

在配置面板中填写以下信息：

| 配置项 | 说明 | 示例 |
|--------|------|------|
| **API 基础 URL** | API 服务的基础地址 | `https://api.openai.com/v1` |
| **API 密钥** | 你的 API 认证密钥 | `sk-...` 或 `sk-proj-...` |
| **模型** | 使用的 AI 模型名称 | `gpt-4`, `gpt-3.5-turbo`, `deepseek-chat` |
| **解牌语言** | 解读语言选项 | `中文` / `英文` / `中英双语` |
| **解牌风格** | 解读风格偏好 | `神秘学派` / `心理学派` / `实用主义` / `诗意派` |

### 4. 测试连接

1. 填写完配置后，点击 **测试连接** 按钮
2. 如果显示 "✓ 连接成功"，说明配置正确
3. 如果显示 "✗ 连接失败"，请检查：
   - API 密钥是否正确
   - API 基础 URL 是否正确
   - 网络连接是否正常

### 5. 保存设置

点击 **保存设置** 按钮，设置会被保存到浏览器本地存储，下次使用无需重新配置。

## 使用流程

### 完整仪式流程

1. **启动应用** → "进入仪式"
2. **握拳洗牌** → 对着镜头握紧拳头
3. **张开手掌** → 铺开牌阵
4. **抽取三张牌** → 依次伸出食指抽取"过去、现在、未来"三张牌
5. **牌面翻转** → 牌自动翻转显示
6. **进入解牌** ✨ → 自动弹出 AI 解牌面板

### 解牌面板操作

- **查看解读**：每张牌的解读会在面板中显示
- **下一张**：跳转到下一张牌的解读
- **完成仪式**：结束解牌，回到初始状态准备新的仪式

## 配置示例

### OpenAI 配置
```
API 基础 URL: https://api.openai.com/v1
API 密钥: sk-proj-xxxxxxxxxxxxxxxx
模型: gpt-4
```

### DeepSeek 配置
```
API 基础 URL: https://api.deepseek.com/v1
API 密钥: sk-xxxxxxxxxxxxxxxx
模型: deepseek-chat
```

## 常见问题

### Q: 如果不配置 AI 会怎样？
A: 应用仍可正常使用，只是解牌时会显示默认的静态解读，而不是 AI 生成的动态解读。

### Q: API 调用会产生费用吗？
A: 这取决于你使用的 API 服务提供商。请查看相关服务的定价页面。

### Q: 我的 API 密钥安全吗？
A: 密钥存储在你的浏览器本地存储中，不会上传到任何服务器。请仍然妥善保管密钥，避免在他人面前输入。

### Q: 支持哪些塔罗牌？
A: 目前支持标准的 22 张大牌（大阿卡那）。解读会基于牌的象征意义和在 "过去-现在-未来" 占卜中的含义。

### Q: 如何修改解牌风格？
A: 在配置面板中修改"解牌风格"选项并点击保存即可。支持的风格有：
- **神秘学派**：强调象征和玄学意义
- **心理学派**：从心理分析角度解读
- **实用主义**：给出实际建议和启示
- **诗意派**：用诗意优美的语言表达

## 技术细节

### API 调用格式

应用使用标准的 OpenAI 兼容 API 格式：

```bash
POST {API_BASE_URL}/chat/completions

Header:
- Content-Type: application/json
- Authorization: Bearer {API_KEY}

Body:
{
  "model": "gpt-4",
  "messages": [
    {
      "role": "system",
      "content": "你是一位神秘而富有智慧的塔罗牌解读师..."
    },
    {
      "role": "user",
      "content": "解读牌义提示..."
    }
  ],
  "temperature": 0.7,
  "max_tokens": 500
}
```

### 本地存储键名

所有配置通过 localStorage 存储，键名如下：
- `ai_enabled` - AI 是否启用
- `ai_api_url` - API 基础 URL
- `ai_api_key` - API 密钥
- `ai_model` - 模型名称
- `reading_language` - 解牌语言
- `reading_style` - 解牌风格

## 支持和反馈

如遇到问题或有改进建议，欢迎反馈。

---

享受神秘的塔罗牌体验！✨🔮✨
