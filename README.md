# Repolex Knowledge Graph of glue-viz/glue-data-loaders

RDF knowledge graph data for [glue-viz/glue-data-loaders](https://github.com/glue-viz/glue-data-loaders), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download glue-viz/glue-data-loaders
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 33b33f14dba4f3f9b47a9a890fea75cd5d2f12c5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 33b33f14dba4f3f9b47a9a890fea75cd5d2f12c5
│           └── chunk-001.nq.gz
├── blob
│   ├── 082c467b13e76bdd3f857aea81d343c31db92391.nq.gz
│   ├── 0848c698f920d37bf298443f562a7fb4ef190e72.nq.gz
│   ├── 0e1603dcc0de5b25a5f8f2641378cd56f6d4f2c3.nq.gz
│   ├── 2b605d37b364986a3e5a7f270e8d966ca00a2e5e.nq.gz
│   ├── 79f36631d374b4a67646aee73921eb9972fe3d26.nq.gz
│   ├── a7edf35001b9fa72c624c94a5df94fa4b0712ad1.nq.gz
│   ├── c73d091abd98e40df01f64bd824e4e69a0f09401.nq.gz
│   └── e43bdf67780be9e8d777e0a6f4e8a192050148c2.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 33b33f14dba4f3f9b47a9a890fea75cd5d2f12c5.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[glue-viz/glue-data-loaders](https://github.com/glue-viz/glue-data-loaders)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
