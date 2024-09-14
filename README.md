## serv00自动化批量保号，每15天自动登录一次面板，并发送消息到Telegram

### 操作步骤

#### 1. Fork 仓库

1. **访问原始仓库页面**：
    - 打开你想要 fork 的 GitHub 仓库页面。
    - 点击页面右上角的 "Fork" 按钮，将仓库 fork 到你的 GitHub 账户下。

#### 2. 设置 GitHub Secrets

1. **创建 Telegram Bot**
    - 在 Telegram 中找到 `@BotFather`，创建一个新 Bot，并获取 API Token。
    - 获取 Chat ID：发送消息给 Bot，然后访问 `https://api.telegram.org/bot<your_bot_token>/getUpdates` 找到 Chat ID。

2. **配置 GitHub Secrets**
    - 转到你 fork 的仓库页面。
    - 点击 `Settings` -> `Secrets`，添加以下 Secrets：
        - `ACCOUNTS_JSON`: 账号信息的 JSON 数据。例如：
          ```json
          [
            {"username": "serv00的账号", "password": "serv00的密码", "panel": "panel6.serv00.com"},
            {"username": "ct8的账号", "password": "ct8的密码", "panel": "panel.ct8.pl"}
          ]
          ```
        - `TELEGRAM_BOT_TOKEN`: 你的 Telegram Bot 的 API Token。
        - `TELEGRAM_CHAT_ID`: 你的 Telegram Chat ID。

#### 3. 启动 GitHub Actions

1. **配置 GitHub Actions**
    - 进入 `Actions` 页面，启用 GitHub Actions。

2. **运行工作流**
    - 根据你设置的定时任务，GitHub Actions 将自动运行脚本。需要手动触发时，可以在 Actions 页面手动运行工作流。

### 注意事项

- **保密性**: Secrets 是敏感信息，请确保不要将它们泄露到公共代码库或未授权的人员。
- **更新和删除**: 在仓库的 Secrets 页面进行管理。
