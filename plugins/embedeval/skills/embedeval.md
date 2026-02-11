---
name: embedeval
description: Binary pass/fail LLM evaluation CLI. Trace-centric, error-analysis-first approach built on Hamel Husain's evaluation principles. Use when evaluating LLM outputs, building failure taxonomies, annotating traces, or setting up eval pipelines.
license: MIT
metadata:
  author: Algiras
  version: "1.0.0"
compatibility: Requires Node.js. Install via npm or curl installer.
---

# EmbedEval - LLM Evaluation CLI

Binary evals. Trace-centric. Error-analysis-first. Evaluate LLM outputs using binary pass/fail judgments.

## Installation

```bash
npm install -g embedeval
# or
curl -fsSL https://raw.githubusercontent.com/Algiras/embedeval/main/install.sh | bash
```

## 3-Command Workflow

```bash
# 1. COLLECT - Import LLM traces
embedeval collect ./production-logs.jsonl --output traces.jsonl

# 2. ANNOTATE - Manual error analysis
embedeval annotate traces.jsonl --user "expert@company.com"

# 3. TAXONOMY - Build failure taxonomy
embedeval taxonomy build --annotations annotations.jsonl
```

## Core Principles

- **Binary only** - PASS or FAIL, no debating scales
- **Error analysis first** - Look at traces before automating
- **Cheap evals first** - Assertions before LLM-as-judge
- **Trace-centric** - Complete session records
- **Single annotator** - "Benevolent dictator" model

## Commands

| Command | Description |
|---------|-------------|
| `embedeval collect` | Import LLM traces from logs |
| `embedeval annotate` | Interactive annotation UI |
| `embedeval taxonomy build` | Build failure taxonomy from annotations |
| `embedeval eval run` | Run automated evaluations |
| `embedeval report` | Generate evaluation reports |

## Output Example

```
Pass Rate: 73%

Top Failure Categories:
1. Hallucination: 12 traces (44%)
2. Incomplete: 8 traces (30%)
3. Wrong Format: 5 traces (19%)
```

## Homepage

https://github.com/Algiras/embedeval
