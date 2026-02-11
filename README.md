# Claudius

Personal Claude Code marketplace — a curated collection of skills and plugins.

## Plugins

| Plugin | Description | Language | Version |
|--------|-------------|----------|---------|
| [memory-palace-red-queen](./plugins/memory-palace-red-queen/) | Method of loci + adversarial recall testing | JS | 2.1.0 |
| [qmd](./plugins/qmd/) | Local-first search engine for docs, notes, knowledge bases | TypeScript | 1.0.0 |
| [skillz](./plugins/skillz/) | Self-extending MCP server - dynamic tool creation at runtime | Rust | 1.0.0 |
| [rknowledge](./plugins/rknowledge/) | Knowledge graph extraction from documents via LLMs + Neo4j | Rust | 0.2.0 |
| [clean-docs](./plugins/clean-docs/) | Documentation quality - validate snippets, check links, auto-fix | Python | 1.0.0 |
| [embedeval](./plugins/embedeval/) | Binary pass/fail LLM evaluation CLI | TypeScript | 1.0.0 |
| [rusty-pageindex](./plugins/rusty-pageindex/) | Hierarchical document indexer for vectorless RAG | Rust | 1.0.0 |

## Installation

Register this marketplace in Claude Code:

```
/plugins marketplace add claudius
```

Then install individual plugins:

```
/plugins install qmd@claudius
/plugins install skillz@claudius
/plugins install rknowledge@claudius
```

## Adding a new plugin

1. Create a directory under `plugins/<plugin-name>/`
2. Add `.claude-plugin/plugin.json` with metadata
3. Add skills in `skills/`, agents in `agents/`, or commands in `commands/`
4. Optionally add `.mcp.json` for MCP server configuration
5. Register the plugin in `.claude-plugin/marketplace.json`
