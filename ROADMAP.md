# Roadmap

> **Tinkr ships every Monday until v1.0.** v0.6.5 is the open-source baseline, not the final product. Each release adds one major capability and several bug fixes.

**Today:** v0.6.5 (Aug 18, 2026) — _first public release_
**Ship target:** v1.0 by Mon Oct 6, 2026 (with a 2-4 week buffer for public feedback)

---

## The version trajectory

```
v0.6.5 ──▶ v0.6.6 ──▶ v0.6.7 ──▶ v0.7   ──▶ v0.8   ──▶ v0.9   ──▶ v1.0
  CLI        CLI+import  CLI       capture  Tauri   market   full
  6 plugins                                          shell   place  product
```

Each step is one week. Each step adds user-facing value. Each step has a public changelog in [`RELEASES.md`](./RELEASES.md).

---

## v0.6.5 — Aug 18, 2026 ✅ SHIPPED

The **first public release**. The CLI works. 6 free plugins ship. 51 KB entries are bundled. The wheel installs cleanly with `pip install tinkr-cli`.

**Not in v0.6.5** (deferred to later releases):
- The Tauri desktop shell (v0.8)
- The capture layer (v0.7)
- The marketplace (v0.9)
- The simulator (v1.5+)

**Why this is the right baseline:** the core APIs are frozen (plugin manifest, Click subcommand interface, HAL, KB schema). New features land in later versions without breaking what works. The CLI is the headless equivalent of the IDE — same plugins, same KB, same projects. The Tauri shell in v0.8 is a thin desktop wrapper around the CLI, not a fork.

---

## v0.6.6 — Aug 25, 2026 (planned)

**Theme:** Bug fixes + multi-source import + brand assets.

- [ ] `tinkr-project-import` v0.4 — more URL sources + a built-in template gallery
- [ ] Brand asset pack (SVG + PNG) downloadable from this repo
- [ ] `tinkr doctor` — diagnose installation issues (Python version, missing drivers, USB permissions)
- [ ] Improved Windows support (USB driver auto-detection)
- [ ] First feedback-loop iteration: triage issues from the v0.6.5 public release

---

## v0.7 — Sep 8, 2026 (planned)

**Theme:** The capture layer. The KB that compounds.

- [ ] `.tinkr/capture/<timestamp>.json` — auto-capture project deploys, debug-fix outcomes, chip identifications
- [ ] `tinkr kb review` — review captured events before they enter the KB
- [ ] `tinkr kb contribute` — submit a captured event to the public KB
- [ ] First-pass KB merging logic (deduplicate + version)
- [ ] First community-contributed KB entries (3-5 from the v0.6.5+ v0.6.6 issue tracker)

**Why this matters:** the capture layer is the moat. Every user's project makes the AI smarter for the next user. The network effect starts compounding at v0.7.

---

## v0.8 — Sep 15, 2026 (planned)

**Theme:** Tauri shell beta. The IDE.

- [ ] Tauri 2 desktop shell (3-pane: file tree / chat / agent + action report)
- [ ] 6 Tauri commands bridging to the CLI (`tinkr ideate ask`, `tinkr port-scan`, etc.)
- [ ] Native menus (File / Edit / View / Project / Plugins / Help)
- [ ] Real port-scan panel
- [ ] Bundled installers (.dmg, .msi, .AppImage)

The CLI remains the headless equivalent. The Tauri shell is a wrapper, not a replacement.

---

## v0.9 — Sep 22, 2026 (planned)

**Theme:** Marketplace scaffolding.

- [ ] Stripe Connect integration
- [ ] 70/30 split (creators keep 70%)
- [ ] Plugin submission flow (`tinkr plugin publish`)
- [ ] Plugin review queue
- [ ] Public plugin listing
- [ ] First 3 paid plugins onboarded (TBD)

The **free core stays MIT forever** (this is the moat). Paid plugins are the business. The marketplace is the distribution.

---

## v1.0 — Oct 6, 2026 (planned)

**Theme:** The full product.

- [ ] CLI + Tauri shell + capture layer + marketplace, all in one release
- [ ] 6 free plugins + 3+ paid plugins + 1+ community plugins
- [ ] 100+ KB entries (community-contributed)
- [ ] v1.0 launch event (Loom + HN Show + r/embedded + maker channels)

**Ship criteria:**
- 100+ installs (the A9 gate)
- 6 free plugins all stable
- 0 P0 bugs
- 50+ KB entries
- 2-min demo video

---

## v1.5+ — 2027 (planned)

**Theme:** Tinkr Pro + paid plugins + creator economy.

- [ ] Tinkr Pro subscription ($9/mo or $90/yr)
- [ ] Per-plugin annual updates (creators can charge for new versions)
- [ ] Managed AI tokens (BYO key optional, with a default Tinkr-powered path)
- [ ] Sim project support (a native circuit simulator, built as a Tinkr plugin)
- [ ] Cloud build (compile + flash via Tinkr's CI, not your laptop)
- [ ] First launch partners onboarded (Espressif + Wemos in parallel)

The **free core stays MIT**. Pro is the convenience layer. Paid plugins are the creator economy. The KB is the moat.

---

## What we will NOT build

These are explicit non-goals, so the community can build them instead:

- **Vendor cloud lock-in** — Tinkr runs on your machine, full stop.
- **A proprietary AI model** — Tinkr uses your key (Anthropic / OpenAI / Ollama). Tinkr's managed-AI tier is convenience, not a gate.
- **A vendor-only chip catalog** — the plugin SDK is MIT, anyone can add a chip.
- **Telemetry** — Tinkr does not phone home. The `tinkr doctor` command is opt-in.
- **A walled-garden project gallery** — projects are git repos, not Tinkr-cloud-locked artifacts.

---

## How to influence the roadmap

- 💡 [Open a feature discussion](https://github.com/tinkr-org/tinkr.build/discussions/categories/ideas)
- 🔌 [Suggest a plugin](https://github.com/tinkr-org/tinkr.build/discussions/categories/plugin-ideas)
- 🐛 [File a bug](https://github.com/tinkr-org/tinkr.build/issues)
- 📚 [Share a KB entry](https://github.com/tinkr-org/tinkr.build/discussions/categories/kb-contributions)
- 📖 [Read the source](https://github.com/tinkr-org/tinkr) (private, opens with v0.9)

The roadmap is a **public commitment**, not a private plan. When we change it, the changelog says so.
