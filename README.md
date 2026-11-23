# session-stats（中文版）

一个 Claude Code mod：在输入框上方显示一条彩色的会话统计栏。本仓库是 [Yad-Tazheh/claude-session-stats](https://github.com/Yad-Tazheh/claude-session-stats) 的 fork，界面文字改为中文，并去掉了所有 emoji 图标。

```
轮次 11  步骤 308  速度 215 tok/s   令牌 40.4M  缓存命中 97%   上下文 24%   [详情]
```

## 统计栏说明

| 分组 | 显示内容 |
| --- | --- |
| 时间 | **轮次**：你发起的对话轮数；**步骤**：模型请求次数（含子代理）；**速度**：每秒输出的 token 数 |
| 令牌 | **令牌**：本次会话消耗的全部 token；**缓存命中**：提示词缓存命中率 |
| 上下文 | 上下文窗口已使用的百分比 |

颜色含义（图标已移除，仅用数字颜色区分）：

- **缓存命中**：80% 以上为绿色，50% 以上为黄色，低于 50% 为红色。
- **上下文**：低于 50% 为绿色，低于 80% 为黄色，80% 以上为红色。

## 悬停详情

把鼠标移到某一组统计上，下一行会显示该组的详细数据；点击 **详情** 可固定显示全部三组，再点 **收起** 取消固定。

- **时间**：轮次、步骤、模型耗时、工具耗时、首字延迟、速度
- **令牌**：令牌总计、缓存命中、未缓存输入、缓存写入、缓存读取、输出
- **上下文**：已用 token / 窗口大小，以及占用最大的几类（系统提示词、工具、消息等）

面板较窄时，统计栏会先缩短标签，再把整组统计换到下一行，不会被截断。

## 命令

- `/statsbar show`：显示统计栏
- `/statsbar hide`：隐藏统计栏
- `/statsbar`：切换显示 / 隐藏

## 安装

在终端会话的输入框中：

```
/plugin install session-stats --marketplace mayuri-wylty/claude-session-stats
```

提示添加 marketplace 时回答 `y`，然后选择安装范围（第一项是 user，直接回车即可）。

在 shell 中：

```bash
claude plugin install session-stats --marketplace mayuri-wylty/claude-session-stats
```

在桌面应用中（`/plugin` 不可用）：点击输入框旁的 **+**，选择 **Plugins**，再点 **Add marketplace** 并填入 `mayuri-wylty/claude-session-stats`，最后点 **Add plugin**。

## 说明

- 统计从 mod 加载时开始计数；工具耗时不包含 Agent 工具，因为它的耗时就是子代理自己的模型耗时与工具耗时。
- 函数 hook 是 Claude Code 的早期功能，后续版本可能会有变化。
- 与上游的差异：仅修改了界面文字（中文化、去除图标），统计逻辑未变。

## 许可证

MIT，沿用上游。
