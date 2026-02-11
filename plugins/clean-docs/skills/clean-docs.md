---
name: clean-docs
description: CLI tool for documentation quality - validate code snippets against source, detect broken links, auto-fix issues, and integrate with CI/CD. Use when auditing docs, checking links, validating code examples, or setting up documentation CI pipelines.
license: MIT
metadata:
  author: Algiras
  version: "1.0.0"
compatibility: Requires Python 3.10+. Install via pip or curl installer.
---

# Clean Docs

Documentation quality CLI. Validate code snippets, detect broken links, auto-fix issues, integrate with CI/CD.

## Installation

```bash
pip install clean-docs                       # Core features
pip install 'clean-docs[snippets]'           # + Code snippet validation
pip install 'clean-docs[semantic]'           # + AI-powered analysis
pip install 'clean-docs[snippets,semantic]'  # All features
```

## Core Commands

### Scan for Issues
```bash
clean-docs scan ./docs                          # Basic scan
clean-docs scan ./docs --internal-only          # Internal links only (fast)
clean-docs scan ./docs --verbose --timeout 30   # With options
```

### Validate Code Snippets
```bash
clean-docs validate-snippets ./docs --code-dir ./src
```

### Auto-fix
```bash
clean-docs scan ./docs --fix --dry-run    # Preview fixes
clean-docs scan ./docs --fix              # Interactive
clean-docs scan ./docs --fix --yes        # Auto-fix all
```

### Output Formats
```bash
clean-docs scan ./docs --format json
clean-docs scan ./docs --format markdown --output report.md
clean-docs scan ./docs --github-annotations   # CI annotations
```

### Health Check
```bash
clean-docs doctor    # Check setup and dependencies
```

## Features

- **Code Snippet Validation** - Validate code examples against actual source using tree-sitter
- **Link Checking** - Internal files, external URLs, GitHub repos, anchors
- **Auto-fixing** - Outdated snippets, missing extensions, anchor typos
- **Smart Caching** - SQLite-based with 24h TTL
- **CODEOWNERS Support** - Group issues by team, create PRs per owner
- **CI/CD Ready** - JSON/Markdown output, GitHub annotations, exit codes

## Homepage

https://github.com/Algiras/clean-docs
