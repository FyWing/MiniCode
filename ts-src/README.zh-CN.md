# MiniCode TypeScript

[English](./README.md) | [Python 运行时](../README.md)

本目录包含 TypeScript 终端编程助手，提供模型与工具执行循环、终端界面、文件编辑审批、本地技能及 MCP 集成。

## 主要功能

- 浏览、搜索、读取和编辑文件，执行终端命令。
- 交互式会话记录、输入历史与斜杠命令。
- 文件改动预览与命令权限检查。
- 本地技能发现与管理。
- 接入 MCP 工具、资源和提示词。

## 安装

安装 Node.js 和 npm 后执行：

```bash
git clone https://github.com/FyWing/MiniCode.git
cd MiniCode/ts-src
npm install
npm run install-local
```

安装器会配置模型连接并创建本地启动命令。设置保存在 `~/.mini-code/settings.json` 和 `~/.mini-code/mcp.json`。

## 使用方式

启动已安装的命令：

```bash
minicode
```

也可以在本目录直接运行：

```bash
npm run dev
```

## 配置

`~/.mini-code/settings.json` 示例：

```json
{
  "model": "your-model-name",
  "env": {
    "ANTHROPIC_API_KEY": "your-api-key"
  }
}
```

使用兼容的自定义接口时，可设置 `ANTHROPIC_BASE_URL`。项目级 MCP 服务可在 `.mcp.json` 的 `mcpServers` 中配置。不要将凭据写入需要提交的文件。

## 常用命令

| 命令 | 作用 |
| --- | --- |
| `/help` | 查看交互命令。 |
| `/tools` | 查看可用工具。 |
| `/skills` | 查看发现的技能。 |
| `/mcp` | 查看 MCP 连接。 |
| `/status` | 查看运行状态。 |
| `/model` | 查看或切换模型。 |
| `/config-paths` | 查看配置文件路径。 |

本地扩展管理：

```bash
minicode skills list
minicode skills add /path/to/skill --name my-skill
minicode mcp list
```

## 目录结构

| 路径 | 内容 |
| --- | --- |
| `src/index.ts` | 命令入口。 |
| `src/agent-loop.ts` | 模型和工具执行循环。 |
| `src/tools/` | 内置工具。 |
| `src/tui/` | 终端界面。 |
| `src/config.ts` | 配置加载。 |
| `docs/` | 项目静态展示页面。 |
| `py-src/` | 内嵌 Python 实现。 |

## 开发验证

```bash
npm run check
npm run dev
```

## 相关文档

- [English README](./README.md)
- [架构说明](./ARCHITECTURE.md)
- [项目展示页面](./docs/index.html)
- [内嵌 Python 运行时](./py-src/README.md)
