# Repolex Knowledge Graph of simonw/commit-rewriter

RDF knowledge graph data for [simonw/commit-rewriter](https://github.com/simonw/commit-rewriter), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/commit-rewriter
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 239658841f4475ed102058c5912f1d0dfe7c43e5
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 239658841f4475ed102058c5912f1d0dfe7c43e5
│           └── chunk-001.nq.gz
├── blob
│   ├── 182b8c743652b6fcc5004d87b0fcafecc75f1209.nq.gz
│   ├── 36037abf83efe95ba0f5a6042a06adf3d0446f15.nq.gz
│   ├── 3a5577205642b4bcf6a074a32767fe7d11e4e2be.nq.gz
│   ├── 4187ae9a5b5257e913d5c9e8587944236a428114.nq.gz
│   ├── 5eadc6c9bd29091d9e22f18859271f5fdd24f4bc.nq.gz
│   ├── 5fb37583f6bec65090a6330ae1b908291d28a1cc.nq.gz
│   ├── 69f945e375ba4bb61b7d8404841b670451b4b3b7.nq.gz
│   ├── 868d99efc3c4a317b869b9bfc30a0ccf857ca73e.nq.gz
│   ├── b6c15090332fe981e8fce86d4d9a6e5eab069239.nq.gz
│   ├── de424daa8dac75c4fe35c99e403f6941df07b2ad.nq.gz
│   └── fc6b399fef6bfb6c92af231f567be8721e483e80.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 239658841f4475ed102058c5912f1d0dfe7c43e5.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
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

[simonw/commit-rewriter](https://github.com/simonw/commit-rewriter)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
