---
name: qmd
description: Local-first search engine for markdown docs, knowledge bases, and meeting notes. Combines BM25 full-text search, vector semantic search, and LLM re-ranking. Use when searching personal notes, documentation, meeting transcripts, or building agentic search workflows.
license: MIT
metadata:
  author: Algiras
  version: "1.0.0"
compatibility: Requires Bun >= 1.0.0 and macOS Homebrew SQLite for extension support.
---

# QMD - Quick Markdown Search

On-device search engine for everything you need to remember. Index markdown notes, meeting transcripts, documentation, and knowledge bases. Search with keywords or natural language.

## Installation

```bash
bun install -g https://github.com/Algiras/qmd
```

## MCP Server

QMD exposes an MCP server for direct AI integration:

```bash
qmd mcp
```

Tools: `qmd_search`, `qmd_vsearch`, `qmd_query`, `qmd_get`, `qmd_multi_get`, `qmd_status`

## Core Commands

### Collection Management
```bash
qmd collection add ~/notes --name notes
qmd collection add ~/Documents/meetings --name meetings
qmd collection list
qmd collection remove <name>
```

### Search Modes

| Command | Mode | Description |
|---------|------|-------------|
| `qmd search` | BM25 | Fast keyword search |
| `qmd vsearch` | Vector | Semantic similarity search |
| `qmd query` | Hybrid | BM25 + Vector + Query Expansion + LLM Re-ranking |

### Indexing
```bash
qmd embed              # Generate vector embeddings
qmd embed -f           # Force re-embed
qmd update             # Re-index all collections
qmd update --pull      # Re-index with git pull first
```

### Retrieval
```bash
qmd get "docs/guide.md"           # Get document by path
qmd get "#abc123"                  # Get by docid
qmd multi-get "journals/2025*.md"  # Get by glob pattern
```

### Output Formats
Use `--json`, `--files`, `--csv`, `--md`, or `--xml` for structured output.

### Agent Workflow
```bash
qmd search "API" --all --files --min-score 0.3
qmd query "error handling" --json -n 10
qmd get "docs/api-reference.md" --full
```

## Score Interpretation

| Score | Meaning |
|-------|---------|
| 0.8 - 1.0 | Highly relevant |
| 0.5 - 0.8 | Moderately relevant |
| 0.2 - 0.5 | Somewhat relevant |
| 0.0 - 0.2 | Low relevance |
