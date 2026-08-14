# Plugins

> **Tinkr is a plugin platform with a CLI on top.** Every capability — chip support, ideation, project import, simulators, AI integrations — is a plugin. The CLI itself is a build of the core + 6 first-party plugins.

**Source of truth:** [`tinkr-org/tinkr`](https://github.com/tinkr-org/tinkr) (private, opens with v0.9)
**Plugin format:** `tinkr.plugin.toml` (frozen in v0.6.5)
**License for first-party plugins:** MIT
**Marketplace:** 70/30 split (creators keep 70%) — ships with v0.9

---

## The 6 free plugins (ship in v0.6.5)

| Plugin | Version | What it does | Maintainer |
|---|---|---|---|
| `tinkr-esp32` | 0.4.2 | ESP32 family (ESP32, ESP32-S2, ESP32-S3, ESP32-C3, etc.) with MicroPython + Arduino | Tinkr |
| `tinkr-rp2040` | 0.1.0 | Raspberry Pi Pico with MicroPython + CircuitPython | Tinkr |
| `tinkr-nrf52` | 0.1.0 | Nordic nRF52 with CircuitPython | Tinkr |
| `tinkr-micropython-runtime` | 0.1.0 | Cross-board MicroPython support (shared runtime) | Tinkr |
| `tinkr-ideate` | 0.1.0 | 8-point ideation decision schema, made clickable | Tinkr |
| `tinkr-project-import` | 0.3.0 | Import projects from public guide URLs (more sources + built-in templates in v0.6.6) | Tinkr |

All first-party plugins are MIT-licensed and live in the `plugins/` directory of the source tree. They're bundled into the `tinkr-cli` wheel by default — `pip install tinkr-cli` includes all 6.

---

## How plugins work

A Tinkr plugin is a **Python package** with a `tinkr.plugin.toml` manifest at the root:

```toml
[plugin]
name = "tinkr-my-plugin"
version = "0.1.0"
description = "What this plugin does (one line)"
license = "MIT"

[entry]
module = "tinkr_my_plugin"
register = "register"

[commands]
group = "my-plugin"  # adds `tinkr my-plugin ...` subcommand group

[capabilities]
flash = "tinkr_my_plugin.adapters:MyChipFlash"
repl = "tinkr_my_plugin.adapters:MyChipRepl"
```

The plugin then ships:

- **A `register()` function** that hooks into the CLI lifecycle
- **Click subcommands** (one per public surface)
- **HAL adapters** (the hardware-abstraction-layer interface for chip families)
- **KB contributions** (optional, recommended)

The full plugin authoring guide is in [`docs/writing-a-plugin.md`](./docs/writing-a-plugin.md) (coming with v0.6.6). For now, the canonical reference is the `tinkr-esp32` source at `plugins/tinkr_esp32/` in the private repo.

---

## Plugin categories

| Category | What it adds | Example |
|---|---|---|
| **Chip family** | HAL adapter + port-scan + flash + REPL for a chip family | `tinkr-esp32`, `tinkr-rp2040` |
| **Runtime** | Cross-board support layer (MicroPython, Zephyr, etc.) | `tinkr-micropython-runtime` |
| **Workflow** | A new top-level `tinkr <workflow>` command group | `tinkr-ideate` |
| **Importer** | `tinkr project new --from-<source>` | `tinkr-project-import` |
| **Simulator** | `tinkr sim` subcommand for circuit simulation | _planned: `tinkr-sim`, v1.5+_ |
| **AI** | `tinkr ideate` extension or model provider | _planned, v1.5+_ |

A plugin can be in multiple categories. The categories are just a mental model, not a hardcoded tag.

---

## The 70/30 split (marketplace, v0.9+)

When the marketplace ships, paid plugins can be sold. The split:

- **Creator keeps 70%** of every sale
- **Tinkr keeps 30%** to cover marketplace infra, payment processing, and review

This is locked. The marketplace is the **distribution** layer; the 70/30 split is the **business model**. The free core stays MIT forever — the marketplace is for **paid extensions**, not for the core itself.

**Per-plugin annual updates** (v1.5+): a creator can charge an annual fee for new versions of their plugin. The 70/30 split applies per renewal. Old versions stay free for everyone who bought them.

**Creator program** (v1.5+): anyone can apply. Approval is by the Tinkr team. The criteria: the plugin works, the docs are good, the KB entries are useful, and the license is compatible.

---

## Roadmap for plugins

- **v0.6.5 (✅):** 6 free first-party plugins ship in the wheel
- **v0.6.6 (Aug 25):** `tinkr-project-import` v0.4 (more URL sources + built-in templates)
- **v0.7 (Sep 8):** capture layer hooks for plugin-defined events
- **v0.8 (Sep 15):** Tauri shell plugin panel (UI for managing installed plugins)
- **v0.9 (Sep 22):** marketplace scaffolding + first 3 paid plugins onboarded
- **v1.5+ (2027):** creator program opens, per-plugin annual updates, AI plugin category

---

## Writing your own plugin

See [`docs/writing-a-plugin.md`](./docs/writing-a-plugin.md) (coming with v0.6.6). For now, the fastest way to start is to read the `tinkr-esp32` source at `plugins/tinkr_esp32/` in the private repo and copy the structure.

The plugin manifest format is **frozen in v0.6.5**. Plugins written today will work unchanged through v0.6.6, v0.7, v0.8, v0.9, and v1.0. New plugin features (e.g., the `ai` block for AI plugins) will be added in **additive** ways, not breaking ones.

---

## Reporting plugin issues

- **Bug in a first-party plugin:** file an issue here with the plugin name in the title (e.g., `[tinkr-esp32] port-scan crashes on Linux`)
- **Bug in a community plugin:** file an issue in the plugin's own repo
- **Plugin idea (new chip, integration, etc.):** [Start a discussion](https://github.com/tinkr-org/tinkr.build/discussions/categories/plugin-ideas)
- **Want to publish a paid plugin:** wait for v0.9 (Sep 22). We'll open the creator program then.
