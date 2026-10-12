# Repolex Knowledge Graph of PyCQA/pyflakes

RDF knowledge graph data for [PyCQA/pyflakes](https://github.com/PyCQA/pyflakes), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/pyflakes
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── de74d28a5fa2fcacbe39710a735d5ec714942a53
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── de74d28a5fa2fcacbe39710a735d5ec714942a53
│           └── chunk-001.nq.gz
├── blob
│   ├── 02bb30cd736741fe22a24f5515e663e001835ed6.nq.gz
│   ├── 0451cfd9f1a024b4a6367144f8214335f478a10d.nq.gz
│   ├── 19fe9495c5b68f21f91854d4937352a8d422f296.nq.gz
│   ├── 22a7122dcc632c5411660e4b1646e45fb3b4105d.nq.gz
│   ├── 2d6f6aa1fc9a3c6658d067dacce7300948d66126.nq.gz
│   ├── 2e5fd2c60baadf008a2bf0533d4335f9ac2e813f.nq.gz
│   ├── 31545815a66ecd38002a70a42d0dc286ecd989da.nq.gz
│   ├── 3e0ba211f2eab845b20d6d226e0fe95337403ceb.nq.gz
│   ├── 4efd83eadb0378441e2f1358b68a9b2b7094d1cb.nq.gz
│   ├── 4f71b43ac0b7b57002e5860d24ff15219d7041e9.nq.gz
│   ├── 50cebd8e0ec05331a3d7fb5d66d7f527a26afd16.nq.gz
│   ├── 54a38143441751318e8f77893fe44eeca18ca653.nq.gz
│   ├── 5619c5aec0cc3d8eec53dbaeb643254219275cf8.nq.gz
│   ├── 57a55926383e92c0cf9737c9ea8be41f51ef0f3c.nq.gz
│   ├── 65ed4d8e75019e929bf4012bb13e1a0c7285c0ae.nq.gz
│   ├── 68cd9efbc5dec487ff2b44167cb7e359f7b91f5b.nq.gz
│   ├── 6bc4f267829c7270d051123008b47cc51a9a0621.nq.gz
│   ├── 79532b9e213d220710d59e95926dcae3ed657bc1.nq.gz
│   ├── 7fb40933ac1c65bbf426502800c509e6f01bb2fb.nq.gz
│   ├── 81bcf2078077367d8cc033682180fbf2487afc90.nq.gz
│   ├── 85b1e617e142ae971057162cf0b0f53d414d00e8.nq.gz
│   ├── 863921eaac840009f813bcf595d1da89b12b8b1f.nq.gz
│   ├── 982e6daf485784b5655c3b5a56a2f561492b53ea.nq.gz
│   ├── a01446d5deb24ab35338a94b351df5dfc95a347f.nq.gz
│   ├── a6103ab6239d4e12507c949aec6b002dfb96f6c1.nq.gz
│   ├── aea7245c4eb581455e8f899a2b1595cd863f53b7.nq.gz
│   ├── c8ee484a9072cda1de9e519b1e8c37b155f214ea.nq.gz
│   ├── d80a68465b18175f8683e662196cd0fe5c8bddb9.nq.gz
│   ├── d8810dd442a6dad9b384e1c1856daa58d582ef5f.nq.gz
│   ├── df988c39315dd5d877798ad5f478a4f375d96eac.nq.gz
│   ├── e4d553ac98bb1637dc736edb48f1e4e2842d47c7.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── eac19180a4ca11a44691923f6aa7b6ae2d527cf8.nq.gz
│   └── fbbb20536ddf6571bab060d05ca44b7b346f984c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── de74d28a5fa2fcacbe39710a735d5ec714942a53.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 42 files
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

[PyCQA/pyflakes](https://github.com/PyCQA/pyflakes)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
