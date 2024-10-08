## 项目简介

ChatMemOllama 是一个个人微信公众号聊天机器人，结合了本地 AI 模型（由 Ollama 提供）和 mem0 记忆管理功能。该项目旨在提供一个智能、个性化的聊天体验。
注意！使用mem0的版本仅为早期测试版，速度慢且设计不科学(仅依靠mem0不科学)，请先使用旧版
请等待后续更新 欢迎提交pr
目前测试加入tool calling让ai调用函数执行，已经实现让ai使用搜索引擎(未发布)

## 功能特性

- **本地 AI 模型**：使用 Ollama 提供的本地 AI 模型进行对话。
- **记忆管理**：通过 mem0 管理用户的聊天记忆，提供更连贯的对话体验。
- **多用户支持**：支持多个用户同时进行对话（测试版存在逻辑问题）。
- **快速响应**：尽量在 5 秒内回复用户，超时情况下会提示用户等待。

## 安装与使用

### 环境要求

- Python 3.7+
- Flask
- FastAPI
- WeChatPy
- Ollama

### 安装步骤

1. 克隆仓库：
    ```bash
    git clone https://github.com/yourusername/ChatMemOllama.git
    cd ChatMemOllama
    ```

2. 安装依赖：
    ```bash
    pip install -r requirements.txt
    ```

3. 配置环境变量：
    ```bash
    export WECHAT_TOKEN='your_wechat_token'
    export APPID='your_appid'
    export APPSECRET='your_appsecret'
    export EncodingAESKey='your_encoding_aes_key'
    ```

4. 运行应用：
    ```bash
    python justchat.py
    ```

## 贡献指南

欢迎任何形式的贡献！请确保在提交 PR 之前阅读以下指南：

1. Fork 仓库并创建一个新的分支。
2. 提交您的修改并推送到您的分支。
3. 创建一个 Pull Request 并描述您的更改。

## 许可证

本项目基于 Apache 2.0 许可证进行分发。详情请参阅 [LICENSE](./LICENSE) 文件。

## 联系方式

如有任何问题或建议，请通过 email 联系我：lightjunction.me@gmail.com


---

## 作者的话

感谢大家对这个项目的喜欢！😊

作者的想法是将这个 AI 打造为个人的、能持久记忆并轻松访问本地文件的智能体。以下是我的一些心得与展望：

### 项目初衷

> 实现这个完全是可行的。我第一步探索了使用微信官方的接口并连接到我的公众号，并写出了第一版的代码，这个在项目第一天晚上即成功了。

### 遇到的挑战

- **mem0 的速度**：mem0 做向量库检索非常慢，超出了我的预期。
- **微信超时限制**：微信公众号有 5 秒的超时限制，这让我一度怀疑是服务器处理响应有逻辑错误。

### 消息收发流程

1. **程序启动**：代码会在 `@post` 后等待一条 POST 请求。
2. **消息处理**：将请求参数提取为 JSON 格式 `msg_info`，然后依次进行解密、生成回复、加密并最终返回 XML 格式的加密内容。

### 未来计划

- **第三版基本逻辑**：
  - 异步接受响应，AI 生成回复时采用多线程处理。
  - 结合第一版和第二版的优点，实现及时回答及长期记忆。
  - 用 tool calling 方式，让 AI 自主决定是保存记忆还是提取记忆。

### 有趣的功能设想

- **狗语翻译器**：让 AI 决策后调用狗语翻译器加密消息。
- **本地文件访问**：让 AI 调用本地文件，告诉用户文件内容。
- **自动资料收集**：让 AI 自己不停地在网上收集资料并保存。

### 管理员菜单

考虑到个人计算机的算力有限，对于多用户的体验必然很糟糕。因此，可以搞一个管理员菜单：

- **进入管理员模式**：发送 `sudo su`，如果用户的 OpenID 为管理员 ID 即可进入。
- **功能开关**：允许或禁止其他用户调用 AI。

### 感谢

最后，感谢大家对这个项目的喜爱！✨ 这个项目的星星数量出乎我的意料，比我前面几个 repo 的星星多得多。这对我是一种莫大的鼓励，谢谢！

2024.10.9

---

