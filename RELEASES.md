# Releases

> **Every Monday. Tinkr ships weekly until v1.0.** The current version is the canonical truth; this file is the human-readable changelog.

**Latest:** [v0.6.5](https://github.com/tinkr-org/tinkr.build/releases/tag/v0.6.5) — _Aug 18, 2026_
**Next:** v0.6.6 — _Aug 25, 2026_ (planned)
**Cadence:** weekly (every Monday)
**Install:** `pip install tinkr-cli` (or pin a specific version: `pip install tinkr-cli==0.6.5`)

---

## Format

Each release entry has:

- **Date** (target / actual)
- **Headline** (one sentence: what's the win?)
- **What's new** (3-7 bullets, user-facing)
- **Bug fixes** (3-7 bullets, with the affected command)
- **Breaking changes** (only if any; if a plugin manifest version changes, that's breaking)
- **Install / upgrade** (the pip command)
- **Migrating** (only if needed; usually not)

---

## v0.6.5 — Aug 18, 2026 (first public release)

**Headline:** Tinkr is open source. 6 free plugins, 51 KB entries, weekly releases from here.

### What's new

- **6 free plugins** ship in the wheel: `tinkr-esp32`, `tinkr-rp2040`, `tinkr-nrf52`, `tinkr-micropython-runtime`, `tinkr-ideate`, `tinkr-project-import`
- **51 KB entries** (34 facts, 5 errors, 5 patterns, 7 recipes) for the knowledge base
- **6-step loop** baked into the project: SENSE → ORIENT → PROPOSE → EXECUTE → VERIFY → UPDATE
- **8-point ideation schema** as a first-class command: `tinkr ideate ask --chip <chip>`
- **`tinkr project new --from-url`** — import a project from a public guide URL
- **`tinkr port-scan`** — discover boards on USB without a plugin-specific command
- **`tinkr repl`** — open a REPL on the connected board
- **158 tests pass** (1 skipped — socat PTY, expected without hardware)

### Bug fixes

- Plugin dir naming convention unified (Python package constraint, dash vs underscore)
- HAL `DeviceAdapter` switched from abstract methods to default-raise stubs (plugins only override what they support)

### Install / upgrade

```bash
pip install --upgrade tinkr-cli
```

### Migrating

No breaking changes from v0.6.x. Fresh install is recommended.

---

## v0.6.6 — Aug 25, 2026 (planned)

**Headline:** Bug fixes + multi-source project import (more sources + built-in templates).

### What's new (planned)

- `tinkr-project-import` v0.4 — more URL sources + a built-in template gallery
- Brand asset pack downloads (SVG + PNG)
- `tinkr doctor` — diagnose installation issues
- First issue-template-driven feedback loop (bug/feature/plugin/KB categories in GitHub Discussions)
- Improved Windows support (USB driver auto-detection)

### Bug fixes (planned)

- Anything caught by real-hardware testing on v0.6.5 (see `RELEASES.md` v0.6.5 for the test plan)

---

## Roadmap (public)

| Version | Date | Headline |
|---|---|---|
| v0.6.5 | Aug 18, 2026 | First public release ✅ |
| v0.6.6 | Aug 25, 2026 | Bug fixes + multi-source import |
| v0.7 | Sep 8, 2026 | Capture layer (KB compounds) |
| v0.8 | Sep 15, 2026 | Tauri shell beta (the IDE) |
| v0.9 | Sep 22, 2026 | Marketplace scaffolding (70/30 split) |
| v1.0 | Oct 6, 2026 | Full product |
| v1.5+ | 2027 | Tinkr Pro + paid plugins |

See [`ROADMAP.md`](./ROADMAP.md) for the full details.

---

## Subscribe to releases

- **Watch this repo** (Releases only) — GitHub will email you on every release
- **PyPI release RSS** — https://pypi.org/rss/project/tinkr-cli/releases.xml
- **GitHub Releases atom feed** — https://github.com/tinkr-org/tinkr.build/releases.atom
