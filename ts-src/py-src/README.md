# MiniCode Python Runtime

[仓库主说明 / Main README](../../README.md)

本目录是内嵌的 Python 终端助手实现。默认安装和使用仓库根目录的 Python 包时，请参考主 README；只有需要单独开发本目录实现时，才安装这里的包。

This directory contains an embedded Python terminal assistant. Use the repository root package by default. Install this copy only when developing the embedded implementation separately.

## 功能 / Features

- 文件浏览、搜索与编辑 / File browsing, search, and editing.
- 终端命令与工具调用 / Shell commands and tool execution.
- 权限审批 / Permission approvals.
- 会话持久化与项目记忆 / Session persistence and project memory.
- 本地技能与 MCP 集成 / Local skills and MCP integration.

## 安装 / Installation

需要 Python 3.11 或更高版本。请使用独立虚拟环境，避免与根目录中同名的发行包冲突。

Requires Python 3.11 or newer. Use a separate virtual environment to avoid conflicts with the identically named root package.

```bash
git clone https://github.com/FyWing/MiniCode.git
cd MiniCode/ts-src/py-src
python -m pip install -e ".[dev]"
```

## 配置 / Configuration

在 `~/.mini-code/settings.json` 中设置模型和凭据。Configure the model and credentials in this file:

```json
{
  "model": "your-model-name",
  "env": {
    "ANTHROPIC_API_KEY": "your-api-key"
  }
}
```

使用前替换示例值，不要提交真实凭据。Replace the placeholders before use and do not commit real credentials.

## 使用 / Usage

```bash
minicode-py
```

也可以直接运行 / Or run the module directly:

```bash
python -m minicode.main
```

常用命令 / Common commands:

```text
/help
/tools
/config
/context
/memory
/exit
```

## 开发验证 / Development

在本目录运行 / Run from this directory:

```bash
python -m pytest
```

## 目录结构 / Directory Structure

| 路径 / Path | 内容 / Contents |
| --- | --- |
| `minicode/` | Python 运行时 / Python runtime. |
| `minicode/tools/` | 内置工具 / Built-in tools. |
| `minicode/tui/` | 终端界面 / Terminal UI. |
| `tests/` | 测试 / Test suite. |
| `pyproject.toml` | 包配置与命令入口 / Packaging and command entry point. |
