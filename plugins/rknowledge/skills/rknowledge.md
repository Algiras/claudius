---
name: rknowledge
description: Build knowledge graphs from documents using LLMs. Extract concepts and relationships from PDF, Markdown, HTML, and text files, store in Neo4j, and export to various formats. Use when analyzing documents, building knowledge bases, or creating graph-based RAG systems.
license: MIT
metadata:
  author: Algiras
  version: "0.2.0"
compatibility: Requires Docker for Neo4j backend. Supports Anthropic, OpenAI, Google, and Ollama (local) LLM providers.
---

# RKnowledge - Knowledge Graph Builder

Production-grade knowledge graph extraction CLI. Extract concepts and relationships from any document using LLMs, store in Neo4j, analyze with graph algorithms, and explore with interactive visualization.

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/Algiras/RKnowledge/main/install.sh | bash
```

Or via cargo:
```bash
cargo install rknowledge
```

## Prerequisites

Neo4j (via Docker):
```bash
docker run -d --name neo4j -p 7474:7474 -p 7687:7687 \
  -e NEO4J_AUTH=neo4j/password neo4j:latest
```

## Core Commands

| Command | Description |
|---------|-------------|
| `rknowledge extract` | Extract knowledge graph from documents |
| `rknowledge query` | Query the knowledge graph |
| `rknowledge path` | Find shortest path between concepts |
| `rknowledge stats` | Graph statistics (PageRank, density) |
| `rknowledge communities` | Detect concept communities (LPA) |
| `rknowledge viz` | Launch interactive visualization |
| `rknowledge export` | Export to JSON, CSV, GraphML, Cypher |

## Features

- **Multi-format**: PDF, Markdown, HTML, plain text
- **Multi-provider LLM**: Anthropic, OpenAI, Google, Ollama (local/free)
- **Concurrent extraction**: Parallel LLM calls with `-j` flag
- **Smart entity typing**: Free-form LLM classification
- **Tenant isolation**: Multiple projects in one Neo4j instance
- **Domain-aware prompting**: Specialized extraction for medical, legal, technical docs
- **Incremental**: `--append` merges into existing graph
- **Graph analytics**: PageRank, community detection, shortest path, density

## Example Workflow

```bash
# Extract from a document
rknowledge extract ./paper.pdf --provider anthropic -j 4

# Query concepts
rknowledge query "machine learning"

# Find connections
rknowledge path "neural networks" "backpropagation"

# Visualize
rknowledge viz --open

# Export
rknowledge export --format graphml -o graph.graphml
```

## Homepage

https://github.com/Algiras/RKnowledge
