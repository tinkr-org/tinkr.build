# Tinkr

> **Build it.** A hardware IDE for ESP32, MicroPython, RP2040, and nRF52. Open-source, MIT, runs on your machine — no cloud required.

[![PyPI](https://img.shields.io/pypi/v/tinkr-cli?label=PyPI&color=FB923C)](https://pypi.org/project/tinkr-cli/)
[![License: MIT](https://img.shields.io/badge/License-MIT-5EEAD4.svg)](./LICENSE)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-A78BFA.svg)](https://www.python.org/downloads/)
[![Releases: weekly](https://img.shields.io/badge/Releases-weekly-5EEAD4.svg)](./RELEASES.md)

**Latest release: [v0.6.5](https://github.com/tinkr-org/tinkr.build/releases/tag/v0.6.5)** — the first public release. _You are here._
Next: **v0.6.6 on Mon Aug 25** (bug fixes + multi-source project import).

---

## What is Tinkr?

Tinkr is a **hardware IDE** — a CLI today, a Tauri desktop app in v0.8 — that helps you go from "I want to build X" to "X is on the board and blinking." It works like this:

1. **Ideate** a project through the 8-point schema (any product, any system, not just hardware).
2. **Discover** your board on the USB port.
3. **Import** a project from a public guide URL (more sources + built-in templates coming in v0.6.6).
4. **Connect** to the board over REPL.
5. **Capture** what you learned (v0.7) — the knowledge base compounds with every project.
6. **Extend** with plugins — Tinkr ships 6 free ones, you can write your own.

The CLI is the headless equivalent of the IDE. Same plugins, same projects, same knowledge — just no GUI yet.

---

## Why Tinkr?

| Pain today | How Tinkr fixes it |
|---|---|
| "I have 4 different tools for 4 different boards." | One CLI, one plugin per chip family, one `tinkr` command for everything. |
| "My code works on my desk but breaks in the field." | The capture layer (v0.7) saves the working incantation the first time, so it's a one-liner the second. |
| "I want to use AI to help me but I don't want to send my hardware secrets to the cloud." | Tinkr is local-first. The IDE is a binary on your machine. Your code never leaves. |
| "The tool I like got acquired and killed." | Tinkr is MIT-licensed, the core APIs are frozen, and the project continues via weekly releases. |
| "Every new board is a fresh setup." | One plugin per family. `tinkr plugin add tinkr-esp32` and you're done. |

---

## Quickstart (2 minutes)

```bash
# 1. Install (Python 3.11+; macOS / Linux / Windows)
pip install tinkr-cli

# 2. Add a plugin (the CLI is a build of the core + plugins)
tinkr plugin add tinkr-esp32

# 3. Ideate a project (the 8-point decision schema, made clickable)
tinkr ideate ask --chip esp32

# 4. Discover your hardware on USB
tinkr port-scan

# 5. Import a project from a public guide URL
tinkr project new --from-url <URL>

# 6. Connect to the board
tinkr repl
```

That's the whole tour. Six commands, two minutes, you're in a REPL on real hardware. See [`docs/getting-started.md`](./docs/getting-started.md) for the full walkthrough.

---

## Requirements

- **Python 3.11+** (CPython; PyPy not yet tested)
- **OS:** macOS 12+, Ubuntu 20.04+, Windows 10+ (WSL2 recommended for Windows)
- **USB:** a data-capable USB cable (charge-only cables won't enumerate the board)
- **Disk:** ~80 MB for the CLI + 6 plugins; KB entries grow with usage
- **No account required.** No cloud required. No telemetry.

---

## Plugins (6 free, MIT)

Tinkr ships with 6 free plugins. See [`PLUGINS.md`](./PLUGINS.md) for the full list and how to write your own.

| Plugin | Version | What it does |
|---|---|---|
| `tinkr-esp32` | 0.4.2 | ESP32 family (ESP32, ESP32-S2, ESP32-S3, ESP32-C3, etc.) with MicroPython + Arduino |
| `tinkr-rp2040` | 0.1.0 | Raspberry Pi Pico with MicroPython + CircuitPython |
| `tinkr-nrf52` | 0.1.0 | Nordic nRF52 with CircuitPython |
| `tinkr-micropython-runtime` | 0.1.0 | Cross-board MicroPython support (shared runtime) |
| `tinkr-ideate` | 0.1.0 | 8-point ideation decision schema, made clickable |
| `tinkr-project-import` | 0.3.0 | Import projects from public guide URLs (more sources + built-in templates in v0.6.6) |

List installed plugins: `tinkr plugin list`.
Add a new plugin: `tinkr plugin add <name>`.
Write your own: see [`docs/writing-a-plugin.md`](./docs/writing-a-plugin.md) (coming with v0.6.6).

---

## Roadmap

Weekly releases, every Monday. v0.6.5 is the open-source baseline, not the final product. Full roadmap in [`ROADMAP.md`](./ROADMAP.md).

| Version | Date | What it ships |
|---|---|---|
| **v0.6.5** | ✅ **Aug 18, 2026** | CLI + 6 free plugins + 51 KB entries. **You are here.** |
| v0.6.6 | Aug 25 | Bug fixes + `tinkr-project-import` v0.4 (more sources + built-in templates) |
| v0.7 | Sep 8 | Capture layer. The KB that compounds from your real usage. |
| v0.8 | Sep 15 | Tauri shell beta. The 3-pane IDE with the agent + the chat panel. |
| v0.9 | Sep 22 | Marketplace scaffolding. Stripe-powered, 70/30 creator split. |
| v1.0 | Oct 6 | The full CLI + Tauri shell + capture layer + marketplace. |
| v1.5+ | 2027 | **Tinkr Pro** subscription, paid plugin marketplace, per-plugin annual updates. |

Every release has a public changelog in [`RELEASES.md`](./RELEASES.md).

---

## FAQ

### Is Tinkr for me?

If you've ever used a serial monitor, written a `.ino` file, debugged an I²C address collision, or wanted to share a working project with a friend — yes.

If you just want to flash a known firmware to a known board with no customization — no. Use the vendor's tool.

### How is Tinkr different from other hardware tools?

| Pain today | How Tinkr fixes it |
|---|---|
| "Every tool is its own walled garden." | One CLI, one plugin per chip family, one `tinkr` command for everything. |
| "I have to remember which tool works for which board." | The `tinkr plugin add <chip>` pattern is universal. |
| "My notes and projects are scattered across 3 apps." | KB entries + project memory, in one CLI, on your machine. |
| "I need an internet connection just to flash a board." | Tinkr is local-first. No cloud, no telemetry, no login. |
| "I want to use AI but I don't trust the cloud with my hardware." | Tinkr's capture layer (v0.7) runs on your machine. BYO AI key. |

### Where's the GUI?

Coming in **v0.8 (Sep 15)**. The CLI is the headless equivalent — same plugins, same projects, same KB. The Tauri shell is a thin desktop wrapper around the CLI, with a 3-pane IDE (file tree / chat / agent + action report).

### Is my chip supported?

If it's ESP32, RP2040, or nRF52 — yes.
If it's AVR (Arduino Uno / Nano / Mega) — not yet. File a request; AVR is on the queue.
If it's STM32, PIC, or other — file a request. Plugin authoring is documented and the capture layer makes it easier over time.

### Is the cloud required?

**No.** Tinkr is local-first. Your code, your KB, your projects — all on your machine. The only network calls are `pip install` and `tinkr plugin add` (which fetch from PyPI / GitHub). There is no Tinkr account, no telemetry, no analytics.

### Why is the source repo private?

The full source lives at [`tinkr-org/tinkr`](https://github.com/tinkr-org/tinkr) (private, development surface). It contains internal planning docs, the agent's long-term memory, and the 26 locked architecture decisions. We open it once the marketplace is live (v0.9) and the plugin API is exercised by community plugins.

You don't need the source to use Tinkr — `pip install tinkr-cli` is the whole install.

### Is Tinkr Pro required?

**No.** The free tier includes:
- 4 free plugin projects per user
- 4 free sim projects per user (sim ships in v2.0)
- Unlimited KB entries
- Unlimited community plugins

**Tinkr Pro** (v1.5+) adds: managed AI tokens, pay-per-flash hardware deploy, premium plugin marketplace access. The 70/30 split (creators keep 70%) is locked.

### Can I write my own plugin?

**Yes.** Plugins are Python packages with a `tinkr.plugin.toml` manifest. The format is frozen (won't break in v0.6.5 + v0.6.6 + v0.7). See [`docs/writing-a-plugin.md`](./docs/writing-a-plugin.md).

### How does the capture layer work?

It watches for: project deploys, debugging sessions that end in a fix, new chips identified, common errors. When something interesting happens, Tinkr offers to save it to the KB. One click. The KB compounds.

Ships in v0.7 (Sep 8).

### What's a KB entry?

A small YAML file describing a recipe, a fact, an error pattern, or a design pattern. Examples:

- **Recipe:** "How to flash MicroPython to an ESP32-S3 in 4 commands"
- **Fact:** "ESP32-C3 USB-CDC needs `tinkr repl --dtr 0` on macOS Sonoma"
- **Error:** "OSError: [Errno 5] EIO on ttyACM0 — bad USB cable"
- **Pattern:** "Read the I²C bus before assuming the device is dead"

51 entries ship with v0.6.5. The capture layer (v0.7) will let you add your own.

### How do I report a bug?

[File an issue](https://github.com/tinkr-org/tinkr.build/issues/new?template=bug.yml). Include:
- Output of `tinkr --version`
- Output of `tinkr plugin list`
- The command you ran
- What you expected vs. what happened
- The relevant log snippet

### How do I request a feature / plugin / chip?

[Start a discussion](https://github.com/tinkr-org/tinkr.build/discussions/categories/ideas). Use the right category — Ideas, Show and tell, KB contributions, Plugin ideas, or Q&A. See [`COMMUNITY.md`](./COMMUNITY.md) for the full map.

### Is the source code auditable?

Yes — every `tinkr-cli` release is built from the public `tinkr-org/tinkr` repo at a known commit. The build is reproducible (`pip install tinkr-cli==0.6.5` always installs the same code). When the source repo opens at v0.9, every prior release will be verifiable.

---

## Get involved

- 🐛 **[File a bug](https://github.com/tinkr-org/tinkr.build/issues/new?template=bug.yml)** — clear, reproducible, with `tinkr --version` and `tinkr plugin list`
- 💡 **[Request a feature](https://github.com/tinkr-org/tinkr.build/discussions/categories/ideas)** — ideas, "what if we...", things you'd like to see
- 🔌 **[Suggest a plugin](https://github.com/tinkr-org/tinkr.build/discussions/categories/plugin-ideas)** — chips, integrations, features
- 📚 **[Share a KB entry](https://github.com/tinkr-org/tinkr.build/discussions/categories/kb-contributions)** — recipes, facts, errors, patterns (form provided)
- 🛠 **[Write a plugin](https://github.com/tinkr-org/tinkr.build/blob/main/docs/writing-a-plugin.md)** — the API is frozen and documented
- 💬 **[Join the discussion](https://github.com/tinkr-org/tinkr.build/discussions)** — Q&A, show-and-tell, the kitchen table

The community is the moat. Every KB entry makes the AI smarter. Every plugin makes the CLI more capable. We're building this together.

---

## For the curious

- **The 6-step loop** — every Tinkr work block runs SENSE → ORIENT → PROPOSE → EXECUTE → VERIFY → UPDATE. It's the spine.
- **The 8-point schema** — `tinkr ideate` is built on 8 universal questions (watch_for, model, precision, power_mode, alerts, privacy, update, ownership). They apply to any product, project, or system, not just hardware.
- **The project-as-memory** — the project's long-term memory is the source of truth. Every chat starts with `🟢` and gets full state. No "what did we do last week?"
- **The capture layer** — when a project deploys, a debugging session ends in a fix, or a new chip is identified, Tinkr offers to capture it for the KB. One click. The system compounds.

---

## Brand

- **Wordmark:** `t●nkr` (amber "i" dot, otherwise cyan)
- **Mark:** v7 PCB trace network — 17+ bright cyan traces, 12 junction nodes, 1 amber center LED
- **Tagline:** Build it.
- **Colors:** cyan `#5EEAD4`, amber `#FB923C`, violet `#A78BFA`
- **Type:** Inter (UI), JetBrains Mono (code)
- See [`BRAND.md`](./BRAND.md) for the full usage guidelines and the SVG / PNG asset pack.

---

## License

[MIT](./LICENSE). Use it, fork it, ship it. Attribution appreciated but not required.

---

## Links

- 📦 **PyPI:** [pypi.org/project/tinkr-cli](https://pypi.org/project/tinkr-cli/)
- 🛠 **Source code:** [github.com/tinkr-org/tinkr](https://github.com/tinkr-org/tinkr) _(private, opens with v0.9)_
- 📚 **Docs:** [github.com/tinkr-org/tinkr.build/tree/main/docs](./docs)
- 🎨 **Brand assets:** [github.com/tinkr-org/tinkr.build/tree/main/brand](./brand)
- 💬 **Discussions:** [github.com/tinkr-org/tinkr.build/discussions](https://github.com/tinkr-org/tinkr.build/discussions)
- 🐛 **Issues:** [github.com/tinkr-org/tinkr.build/issues](https://github.com/tinkr-org/tinkr.build/issues)
- 📺 **Releases + changelog:** [github.com/tinkr-org/tinkr.build/releases](https://github.com/tinkr-org/tinkr.build/releases)

---

**Tinkr** — _Build it._ 🟠
