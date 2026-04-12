# Changelog

All notable changes to LeanCTL are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/).

## [0.3.0] — 2026-04-12

### lean-ctx v3.0.2 Integration — Symbol Intelligence & Hybrid Search

Upgrades the lean-ctx core from v3.0.0 to v3.0.2, adding 7 new LLM-accessible tools
and upgrading semantic search with hybrid BM25/dense modes.

---

#### New Tools (LLM-accessible)

- **`symbol_lookup`** — Read a specific symbol (function, struct, class) by name. Returns only the code span — much cheaper than reading the whole file.
- **`file_outline`** — Compact file outline showing all symbols and their signatures.
- **`find_callers`** — Find all callers of a symbol across the project.
- **`find_callees`** — List all callees of a symbol.
- **`extract_routes`** — Extract HTTP routes/endpoints. Supports Express, Axum, Flask, FastAPI, Spring, Rails, and more.
- **`graph_diagram`** — Generate Mermaid diagrams for dependency and call graphs.
- **`compress_memory`** — Compress large memory/config markdown while preserving code fences and URLs.

#### Improved

- **`semantic_search`** — Now supports `bm25`, `dense`, and `hybrid` (default) modes. New filters: `languages` and `path_glob` to scope results.

#### Lifecycle

- **`leanctl upgrade`** — Self-update to the latest release from GitHub (alias: `leanctl update`).
- **`leanctl uninstall`** — Clean removal of all data, config, sessions, and logs.
- **`install.sh`** — SHA256 checksum verification, musl/gnu libc detection, upgrade support.

## [0.2.0] — 2026-04-10

### lean-ctx v3.0.0 Integration — Full Premium Engine

This release fully integrates lean-ctx v3.0.0, bringing 8 new LLM-accessible tools,
automatic session intelligence, and quality-guarded compression to the agent loop.

---

#### New Tools (LLM-accessible)

- **`impact_analysis`** — Graph-based impact analysis: "What breaks when file X changes?" Supports analyze, chain, build, and status actions via the property graph.
- **`architecture`** — Project architecture analysis: module clusters, dependency layers, circular dependency detection, entrypoints.
- **`file_heatmap`** — File access heatmap tracking which files are read most during a session. Helps the agent focus on hot paths.
- **`cost_report`** — Token cost attribution across agents and tools. Shows where tokens are spent.
- **`a2a_task`** — A2A (Agent-to-Agent) task management: create, assign, update, cancel, and track tasks between agents.
- **`agent_coordination`** — Multi-agent coordination bus: register agents, post messages, handoff tasks, diary entries for agent work logs.
- **`sandboxed_execute`** — Execute code in a sandboxed environment. Supports Python, JavaScript, Bash, Rust, and more.

#### Automatic Session Intelligence

- **Session findings** — Tool errors are automatically recorded as session findings for cross-session debugging context.
- **Session decisions** — File edits (write_file, edit_file, multi_edit) are automatically recorded as session decisions.
- **Turn summaries** — Each turn's tool count, duration, and token savings are persisted as findings.
- **Checkpointing** — Compressed context snapshots every 15 tool-loop iterations for recovery.
- **Task persistence** — Current user task is recorded at the start of each turn via `set_task`.

#### Compression Pipeline

- **Quality guard** — Structural integrity checks on compressed output. Rejects destructive compression and falls back to original.
- **Engine-compressed skip list** — All lean-ctx tools skip redundant secondary compression, eliminating double-compression overhead.
- **Signatures mode** — 94.2% token savings when reading files for API surface only.
- **Cache hits** — 99.8% savings on re-reads (9 tokens vs ~3,864 average per file).

#### Under the Hood

- Updated lean-ctx submodule from v1.8.0-318 to v3.0.0
- Enabled `embeddings` feature (ONNX Neural Compression)
- Added `rusqlite` for Property Graph support
- Exported 5 new core modules: `a2a`, `heatmap`, `property_graph`, `deep_queries`, `memory_lifecycle`
- Migrated all direct `lean_ctx::core::*` imports to engine wrapper layer
- Removed dead `engine/share.rs` wrapper (no single-agent use case)
- 72 tests passing (29 new v3 integration tests)

## [0.1.1] — 2026-04-08

### Beta Launch

- Initial public beta release
- Terminal-native AI coding agent with agentic tool use
- Built-in lean-ctx compression (60-99% token savings)
- Supports Ollama, OpenAI, Anthropic, DeepSeek, Groq, Google
- Interactive model picker (Ctrl+P), session history (Ctrl+S)
- Web search, syntax highlighting, undo stack
- Install via `curl | sh`, npm, or AUR
- Zero telemetry, single binary, no runtime dependencies

## [0.1.0] — 2026-04-01

### Initial Release

- Core agent loop with streaming LLM responses
- Tool execution: read_file, write_file, edit_file, multi_edit, search_code, list_files, run_command
- lean-ctx integration for context compression
- Provider management with `leanctl init`
- Session persistence with SQLite
- TUI with Ratatui
