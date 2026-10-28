# Repolex Knowledge Graph of napari/shared-workflows

RDF knowledge graph data for [napari/shared-workflows](https://github.com/napari/shared-workflows), parsed by [repolex](https://repolex.ai).

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
rlex download napari/shared-workflows
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 85fe6fae344194e67fa0716c05defa366cec46ab
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 85fe6fae344194e67fa0716c05defa366cec46ab
│           └── chunk-001.nq.gz
├── blob
│   ├── 1764263f1118aaf58e9b61d47c52c1495c88cf7a.nq.gz
│   ├── 1daf90845513633dc60349a6bace295ee7e3e638.nq.gz
│   ├── 450b38ad794afdcf042baf092c9c6c40f697dd03.nq.gz
│   ├── 6253991b398ad4805a0187a4ced3f6c1ddb0857e.nq.gz
│   ├── 63bd53d6fbbfd655b347f23f5b7932399f0d99e6.nq.gz
│   ├── 7b64a734cb3caa8476f32ba84db4dbf1c3d08995.nq.gz
│   ├── 7e903279c0e1561228866de19caa3e01d45952b3.nq.gz
│   ├── b32e40a9c4e2b254fb7cb3e41a07f601ba7eb0ac.nq.gz
│   ├── d3b6eb870fff2fcf2bae34e1b039d0a76070f2f7.nq.gz
│   ├── dc7fbeb46bb003d61da950e8dd141922dabeb515.nq.gz
│   ├── f8112b58e1bf88b41ff6dffc224f3614f3117458.nq.gz
│   ├── f8cfa9066ec2a476045c39b7d9e35e5537bc34f7.nq.gz
│   └── ffd28f109944f4ed442b3e312a7e1885d4db82f6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 85fe6fae344194e67fa0716c05defa366cec46ab.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 21 files
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

[napari/shared-workflows](https://github.com/napari/shared-workflows)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
