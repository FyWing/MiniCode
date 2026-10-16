# MiniCode TypeScript

[简体中文](./README.zh-CN.md) | [Python Runtime](../README.en.md)

This directory contains the TypeScript terminal coding assistant. It provides a model/tool loop, terminal UI, file editing approvals, local skills, and MCP integration.

## Features

- File browsing, search, reading, editing, and shell execution.
- Interactive transcript, command history, and slash commands.
- File-change review and command permission checks.
- Local skill discovery and management.
- MCP tools, resources, and prompts.

## Installation

Install Node.js and npm, then run:

```bash
git clone https://github.com/FyWing/MiniCode.git
cd MiniCode/ts-src
npm install
npm run install-local
```

The installer configures the model connection and creates the local launcher. Settings are stored in `~/.mini-code/settings.json` and `~/.mini-code/mcp.json`.

## Usage

Launch the installed command:

```bash
minicode
```

Or run directly from this directory:

```bash
npm run dev
```

## Configuration

Example `~/.mini-code/settings.json`:

```json
{
  "model": "your-model-name",
  "env": {
    "ANTHROPIC_API_KEY": "your-api-key"
  }
}
```

For a compatible custom endpoint, configure `ANTHROPIC_BASE_URL`. Project-scoped MCP servers can be defined in `.mcp.json` under `mcpServers`. Keep credentials out of committed files.

## Commands

| Command | Purpose |
| --- | --- |
| `/help` | List interactive commands. |
| `/tools` | Inspect available tools. |
| `/skills` | Inspect discovered skills. |
| `/mcp` | Inspect MCP connections. |
| `/status` | Inspect runtime status. |
| `/model` | Inspect or change the model. |
| `/config-paths` | Show configuration paths. |

Local extension management:

```bash
minicode skills list
minicode skills add /path/to/skill --name my-skill
minicode mcp list
```

## Directory Structure

| Path | Contents |
| --- | --- |
| `src/index.ts` | Command entry point. |
| `src/agent-loop.ts` | Model and tool execution loop. |
| `src/tools/` | Built-in tools. |
| `src/tui/` | Terminal UI. |
| `src/config.ts` | Configuration loading. |
| `docs/` | Static project showcase. |
| `py-src/` | Embedded Python implementation. |

## Development

```bash
npm run check
npm run dev
```

## Documentation

- [Chinese README](./README.zh-CN.md)
- [Architecture](./ARCHITECTURE.md)
- [Project Showcase](./docs/index.html)
- [Embedded Python Runtime](./py-src/README.md)
