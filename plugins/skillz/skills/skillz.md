---
name: skillz
description: Self-extending MCP server that lets AI create and execute custom tools at runtime. Build tools on the fly using Rust WASM or shell scripts without server restarts. Use when you need to create custom tools dynamically, extend AI capabilities at runtime, or build reusable tool libraries.
license: MIT
metadata:
  author: Algiras
  version: "1.0.0"
compatibility: Requires Rust 1.70+ and wasm32-wasip1 target (rustup target add wasm32-wasip1).
---

# Skillz - Self-Extending MCP Server

Dynamic tool creation for AI agents. Traditional MCP servers have a fixed set of tools. Skillz lets AI create new tools on the fly.

## Installation

```bash
rustup target add wasm32-wasip1
cargo install skillz
```

## MCP Configuration

Add to your editor's MCP config:

```json
{
  "mcpServers": {
    "skillz": {
      "command": "skillz",
      "args": ["serve"]
    }
  }
}
```

## How It Works

1. Ask AI to create a tool (e.g., "Build me a tool that fetches weather data")
2. AI writes the code using `create_tool`
3. Code compiles to WASM instantly
4. Tool is available immediately - no restarts

## Built-in MCP Tools

- `create_tool` - Create a new WASM or script tool at runtime
- `list_tools` - List all available dynamic tools
- `delete_tool` - Remove a dynamic tool
- `execute_tool` - Run a dynamic tool with arguments

## Tool Types

| Type | Language | Compilation | Best For |
|------|----------|-------------|----------|
| WASM | Rust | Compiled to WASM | Performance, type safety |
| Script | Shell/Python | Direct execution | Quick utilities, prototyping |

## Example

```
User: "Create a tool that counts words in a file"
AI: [uses create_tool to build and compile a word counter]
AI: "Tool 'word-counter' created. Use it with execute_tool."
```

## Homepage

https://algiras.github.io/skillz
