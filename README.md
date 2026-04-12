```
  ██╗     ███████╗ █████╗ ███╗   ██╗     ██████╗████████╗██╗     
  ██║     ██╔════╝██╔══██╗████╗  ██║    ██╔════╝╚══██╔══╝██║     
  ██║     █████╗  ███████║██╔██╗ ██║    ██║        ██║   ██║     
  ██║     ██╔══╝  ██╔══██║██║╚██╗██║    ██║        ██║   ██║     
  ███████╗███████╗██║  ██║██║ ╚████║    ╚██████╗   ██║   ███████╗
  ╚══════╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═══╝     ╚═════╝   ╚═╝   ╚══════╝
          Context-Engineered AI Coding CLI
```

<h3 align="center">The Only Coding CLI That Steers How Much Your LLM Thinks — Powered by <a href="https://github.com/yvgude/lean-ctx">lean-ctx</a></h3>

<p align="center">
  <strong>40+ Tools · Thinking Steering · Hybrid Semantic Search · Symbol Intelligence · Multi-Provider</strong>
</p>

<p align="center">
  <a href="https://github.com/yvgude/lean-ctl/releases/latest"><img src="https://img.shields.io/github/v/release/yvgude/lean-ctl?color=%2300b894&label=release" alt="Release"></a>
  <a href="https://www.npmjs.com/package/leanctl-bin"><img src="https://img.shields.io/npm/v/leanctl-bin?label=npm&color=%23cb3837" alt="npm"></a>
  <a href="https://www.npmjs.com/package/leanctl-bin"><img src="https://img.shields.io/npm/dt/leanctl-bin?color=%23cb3837&label=npm%20downloads" alt="npm downloads"></a>
  <a href="https://aur.archlinux.org/packages/leanctl-bin"><img src="https://img.shields.io/aur/version/leanctl-bin?color=%231793d1" alt="AUR"></a>
  <a href="https://github.com/yvgude/lean-ctx"><img src="https://img.shields.io/badge/engine-lean--ctx%20v3.0.2-blue" alt="lean-ctx"></a>
  <a href="https://discord.gg/pTHkG9Hew9"><img src="https://img.shields.io/badge/Discord-Join-5865F2?logo=discord&logoColor=white" alt="Discord"></a>
  <a href="https://x.com/leanctx"><img src="https://img.shields.io/badge/𝕏-Follow-000000?logo=x&logoColor=white" alt="X/Twitter"></a>
  <img src="https://img.shields.io/badge/Telemetry-Zero-brightgreen?logo=shield&logoColor=white" alt="Zero Telemetry">
</p>

<p align="center">
  <a href="https://leanctl.com">Website</a> ·
  <a href="#-install">Install</a> ·
  <a href="#-how-thinking-steering-works">How It Works</a> ·
  <a href="#-features">Features</a> ·
  <a href="#-supported-providers">Providers</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="https://discord.gg/pTHkG9Hew9">Discord</a>
</p>

---

<br>

> **leanctl** is a terminal-native AI coding agent that **automatically steers LLM thinking budgets** based on task complexity — so simple tasks stay fast and cheap, while complex tasks get the deep reasoning they need.

<br>

## ⚡ How Thinking Steering Works

```
  User: "fix the typo in line 42"
    → Intent: TaskType::QuickFix
    → Budget: Minimal (1024 tokens)
    → Result: Fast, cheap, accurate

  User: "debug why the distributed cache eviction is wrong"
    → Intent: TaskType::Debug
    → Budget: High (8192 tokens)
    → Result: Deep analysis, thorough investigation

  User: "redesign the auth architecture for microservices"
    → Intent: TaskType::Architecture
    → Budget: Maximum (16384 tokens)
    → Result: Comprehensive design with trade-offs
```

| Task Type | Thinking Budget | Token Savings vs Max |
|:---|:---|:---:|
| Quick fixes, renames, formatting | Minimal (1K) | **94%** |
| Bug fixes, small features | Low (2K) | **88%** |
| Debugging, refactoring | Medium (4K) | **75%** |
| Architecture, complex analysis | High-Max (8-16K) | Optimal |

> Lab-proven: Thinking steering reduced output tokens by 54-95% and thinking tokens by 48-100%.

<br>

## 📦 Install

```bash
# macOS / Linux — one-liner
curl -fsSL https://leanctl.com/install.sh | sh

# npm (all platforms)
npm install -g leanctl-bin

# Arch Linux (AUR)
yay -S leanctl-bin

# Upgrade existing installation
leanctl upgrade
```

<br>

## 🚀 Quick Start

```bash
# 1. Configure your AI provider (interactive)
leanctl init

# 2. Start coding
cd your-project
leanctl
```

<br>

## 🧠 Features

### 40+ LLM-Accessible Tools

| Category | Tools | What They Do |
|:---|:---|:---|
| **File Intelligence** | `read_file`, `file_outline`, `symbol_lookup` | Read files, get outlines, look up symbols by name |
| **Code Navigation** | `find_callers`, `find_callees`, `search_code` | Navigate call graphs, find references |
| **Semantic Search** | `semantic_search` (hybrid) | BM25 + dense vector search with language filters |
| **Architecture** | `extract_routes`, `graph_diagram`, `related_files` | HTTP endpoints, Mermaid diagrams, dependency analysis |
| **Editing** | `write_file`, `edit_file`, `multi_edit` | Precise code modifications |
| **Shell** | `run_command` | Compressed output with 90+ patterns |
| **Memory** | `project_knowledge`, `compress_memory` | Cross-session knowledge, markdown compression |
| **Multi-Agent** | `agent_coordination`, `task` | Agent bus, sub-agent spawning |

### Context Engine (lean-ctx v3.0.2)

- **8 read modes** — `full`, `map`, `signatures`, `diff`, `aggressive`, `entropy`, `lines:N-M`, `reference`
- **Session caching** — re-reads cost ~13 tokens instead of thousands
- **90+ compression patterns** — git, npm, cargo, docker, test runners
- **Adaptive compression** — Thompson Sampling bandits learn optimal settings per language

### Multi-Provider Support

| Provider | Models | Thinking Steering |
|:---|:---|:---:|
| **Anthropic** | Claude 4, Claude 3.5 Sonnet | ✅ `budget_tokens` |
| **OpenAI** | GPT-4.1, o3, o4-mini | ✅ `reasoning_effort` |
| **Google** | Gemini 2.5 Pro/Flash | ✅ `thinking_budget` |
| **Ollama** | Any local model | — |

<br>

## 📥 Downloads

Pre-built binaries for every release:

| Platform | Binary | Checksum |
|:---|:---|:---:|
| macOS Apple Silicon | [`leanctl-aarch64-apple-darwin.tar.gz`](https://github.com/yvgude/lean-ctl/releases/latest) | ✅ SHA256 |
| macOS Intel | [`leanctl-x86_64-apple-darwin.tar.gz`](https://github.com/yvgude/lean-ctl/releases/latest) | ✅ SHA256 |
| Linux x86_64 | [`leanctl-x86_64-unknown-linux-musl.tar.gz`](https://github.com/yvgude/lean-ctl/releases/latest) | ✅ SHA256 |

Linux binaries are statically linked (musl) — they work on **every** Linux distribution.

<br>

## 🔗 Links

- **Website**: [leanctl.com](https://leanctl.com)
- **Core Engine**: [lean-ctx](https://github.com/yvgude/lean-ctx) — MIT-licensed, fully open source
- **Discord**: [Join the community](https://discord.gg/pTHkG9Hew9)
- **X/Twitter**: [@leanctx](https://x.com/leanctx)

<br>

## 📜 License

LeanCTL is proprietary software. The binary is **free to use** for personal and commercial projects.

The underlying engine [lean-ctx](https://github.com/yvgude/lean-ctx) is MIT-licensed and fully open source.
