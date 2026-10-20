# Repolex Knowledge Graph of coleifer/greendb

RDF knowledge graph data for [coleifer/greendb](https://github.com/coleifer/greendb), parsed by [repolex](https://repolex.ai).

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
rlex download coleifer/greendb
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 341ab7d1969341e29a96abf2db8b6869fbf284bc
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 341ab7d1969341e29a96abf2db8b6869fbf284bc
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f3d5449073ff7c4c1ef2d7581337fed3db488a2.nq.gz
│   ├── 39069aff58852bb50c547af63cc649ab88ddae4d.nq.gz
│   ├── 50481c4becf8d0e32ef2fc20d21027c3861abf19.nq.gz
│   ├── 606849326a4002007fd42060b51e69a19c18675c.nq.gz
│   ├── 75e594302f816f924974d7df944cdd3ebf04242d.nq.gz
│   ├── 7da22f1bdc815e2fe01f93f068362eebeec8c55b.nq.gz
│   ├── 8e11faaa4287bb5c6cd375606e44a32face08616.nq.gz
│   ├── 9982eca6a327faf401575bf8b9cc05a660c5c4e8.nq.gz
│   ├── b725d2d6fc00118f560879b97d61d39996da4e29.nq.gz
│   ├── b8e57cdc93438e3d24a7f34448ea4051025aabd2.nq.gz
│   └── ba8cf130be332940d1121f9ca278bfd833c457df.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 341ab7d1969341e29a96abf2db8b6869fbf284bc.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 18 files
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

[coleifer/greendb](https://github.com/coleifer/greendb)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
