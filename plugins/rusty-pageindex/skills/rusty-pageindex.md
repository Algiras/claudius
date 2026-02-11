---
name: rusty-pageindex
description: High-performance Rust PageIndex implementation. Transforms documents into hierarchical TOC trees for vectorless, reasoning-based RAG. Use when indexing documentation, building RAG pipelines without vectors, or creating searchable document hierarchies.
license: MIT
metadata:
  author: Algiras
  version: "1.0.0"
compatibility: Requires Rust or install via curl. Supports OpenAI and Ollama for LLM-enriched summaries.
---

# RustyPageIndex

High-performance document indexer that transforms documents into hierarchical Table-of-Contents trees for vectorless, reasoning-based RAG.

## Installation

```bash
# One-liner install
curl -fsSL https://raw.githubusercontent.com/Algiras/rusty-pageindex/main/install.sh | bash

# Or via cargo
cargo install rusty-page-indexer
```

## Authentication

```bash
# OpenAI
rusty-page-indexer auth --api-key "your-key"

# Ollama (local)
rusty-page-indexer auth --api-key "ollama" --api-base "http://localhost:11434/v1" --model "llama3.2"
```

## Core Commands

### Index Documents
```bash
rusty-page-indexer index ./my-project              # Basic index
rusty-page-indexer index ./my-project --enrich      # With LLM summaries
rusty-page-indexer index ./my-project --force        # Force re-index
rusty-page-indexer index ./my-project --dry-run      # Preview
```

### Query
```bash
rusty-page-indexer query "how does authentication work"
```

### Manage Indices
```bash
rusty-page-indexer list     # List all indexed repos
rusty-page-indexer clean    # Clean up indices
```

## Key Features

- **Parallel indexing** - Rayon-based parallel file parsing
- **Multi-repo support** - Index and query across multiple repositories
- **Unified tree** - Folder -> File -> Section hierarchy
- **Incremental updates** - Hash-based caching skips unchanged files
- **LLM enrichment** - Optional summaries via OpenAI or Ollama
- **Vectorless RAG** - Reasoning-based retrieval without embeddings

## Architecture

```
Folder -> File -> Section hierarchy
  project/
    src/
      main.rs [Summary: Entry point...]
        fn main() [...]
        mod config [...]
    docs/
      guide.md [Summary: User guide...]
        ## Installation [...]
        ## Usage [...]
```

## Homepage

https://github.com/Algiras/rusty-pageindex
