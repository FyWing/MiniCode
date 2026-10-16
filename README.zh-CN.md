# MiniCode Python

[English](./README.en.md)

MiniCode Python 是面向本地开发的终端编程助手，将模型工具调用、持久化会话、项目记忆、编辑检查点和运行状态诊断组织在同一条工作流中。

![MiniCode 界面](./Docs/Documentation/assets/readme/minicode-frontend-hero.png)

## 主要功能

- 读取、搜索和编辑项目文件，执行终端命令与测试。
- 查看、保存、恢复和回放会话。
- 检索项目记忆，在长会话中保留相关上下文。
- 通过检查点、回退预览和回退命令恢复文件编辑。
- 检查模型配置、服务可用性和运行状态。
- 通过本地技能与 MCP 工具扩展工作流。

## 环境要求

- Python 3.11 或更高版本。
- Windows、macOS 或 Linux 终端。
- 使用真实模型时需要配置相应服务的凭据。

## 安装

```bash
git clone https://github.com/FyWing/MiniCode.git
cd MiniCode
python -m pip install -e ".[dev]"
```

建议使用独立的虚拟环境。

## 配置

在 `~/.mini-code/settings.json` 中配置模型与凭据。以下为兼容 Anthropic 接口的配置示例：

```json
{
  "model": "your-model-name",
  "env": {
    "ANTHROPIC_API_KEY": "your-api-key"
  }
}
```

使用前将示例值替换为实际配置。使用兼容的自定义接口时，可设置 `ANTHROPIC_BASE_URL`。其他环境变量参见 [.env.example](./.env.example)。

凭据应保存在本地设置或环境变量中，不要提交到仓库。

## 使用方式

启动交互式会话：

```bash
minicode-py
```

执行单次任务：

```bash
minicode-headless "说明当前仓库的目录结构。"
```

检查模型服务与运行环境是否就绪：

```bash
minicode-readiness --json --fail-on blocked
```

### 会话命令

| 命令 | 作用 |
| --- | --- |
| `/help` | 查看可用命令。 |
| `/session` | 查看当前会话。 |
| `/sessions` | 浏览已保存的会话。 |
| `/session-replay` | 回放会话活动。 |
| `/memory` | 查看项目记忆。 |
| `/checkpoints` | 查看编辑检查点。 |
| `/rewind-preview` | 预览文件恢复操作。 |
| `/rewind` | 从检查点恢复编辑。 |
| `/readiness` | 检查模型与运行环境状态。 |

## 运行流程

```text
用户任务 -> Agent 循环 -> 模型 -> 工具 -> 验证 -> 回复
                |                 |
           会话与项目记忆      检查点与编辑恢复
```

Agent 读取工作区、选择工具、处理工具结果并生成回复。会话、记忆与检查点数据用于支持执行过程中的检查和恢复。

## 目录结构

| 路径 | 内容 |
| --- | --- |
| `minicode/` | 主要 Python 运行时和命令入口。 |
| `Main/` | 应用入口契约与模块结构。 |
| `Package/` | 共用工程模块。 |
| `tests/` | Python 测试。 |
| `benchmarks/` | 评测脚本与报告。 |
| `Docs/Documentation/` | 架构和实现文档。 |
| `ts-src/` | TypeScript 实现及内嵌 Python 副本。 |
| `openspec/` | 规格说明和变更计划。 |

## 开发验证

在仓库根目录运行 Python 测试：

```bash
python -m pytest
```

内嵌的 `ts-src/py-src/` 与根目录 Python 包使用相同的发行包名，开发时应使用不同的虚拟环境。

## 相关文档

- [English README](./README.en.md)
- [实现说明](./Docs/Documentation/OPTIMIZATION_SUMMARY.md)
- [记忆架构](./Docs/Documentation/memory_theory.md)
- [TypeScript 运行时](./ts-src/README.zh-CN.md)
- [内嵌 Python 运行时](./ts-src/py-src/README.md)
