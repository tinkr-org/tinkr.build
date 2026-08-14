# Getting started with Tinkr

> **2 minutes from `pip install` to a REPL on real hardware.** This is the full walkthrough. The README quickstart is the 30-second version.

## Prerequisites

- **Python 3.11+** — check with `python3 --version`
- **A data-capable USB cable** — charge-only cables won't enumerate the board
- **An ESP32, Raspberry Pi Pico, or nRF52 board** — the three supported families in v0.6.5
- **macOS 12+ / Ubuntu 20.04+ / Windows 10+ (with WSL2 recommended)**

## Step 1 — Install

```bash
pip install tinkr-cli
```

This installs the `tinkr` command and all 6 first-party plugins. Verify:

```bash
tinkr --version
# 0.6.5
```

```bash
tinkr plugin list
# 6 plugins: tinkr-esp32, tinkr-rp2040, tinkr-nrf52, tinkr-micropython-runtime, tinkr-ideate, tinkr-project-import
```

## Step 2 — Add a chip plugin (already included, but for the future)

The first-party plugins are bundled in v0.6.5, so you don't need this step yet. But the pattern is:

```bash
tinkr plugin add tinkr-esp32
# (would download from PyPI / GitHub; in v0.6.5 it's already in the wheel)
```

## Step 3 — Ideate a project

The 8-point ideation schema is Tinkr's secret weapon. It works for any product, project, or system — not just hardware.

```bash
tinkr ideate ask --chip esp32
```

This walks you through 8 decisions:

1. **watch_for** — what does the system watch for?
2. **model** — which model / algorithm / approach?
3. **precision** — how accurate does it need to be?
4. **power_mode** — what's the power budget?
5. **alerts** — what alerts, and where?
6. **privacy** — what's the privacy model?
7. **update** — how is it updated?
8. **ownership** — where does the project live?

You can also run `tinkr ideate ask --chip <chip>` non-interactively, or `--product` for software-only projects.

## Step 4 — Discover your board

Plug your board in via USB. Then:

```bash
tinkr port-scan
```

This enumerates all serial devices on your machine and identifies which one is the board. Output is NDJSON (one event per line) so scripts can pipe it.

For chip-specific help (e.g., "is this an ESP32-S3 or an ESP32-C3?"), use:

```bash
tinkr esp32 identify
```

## Step 5 — Import a project

If you have a public guide URL, import it:

```bash
tinkr project new --from-url <URL>
```

This creates a Tinkr project in your current directory:

```
<project-name>/
├── README.md             # what the project does
├── tinkr.toml            # Tinkr project manifest
├── src/
│   └── main.<ext>        # the firmware source (auto-detected)
└── .tinkr/
    ├── source.json       # provenance (URL, import date, hash)
    └── ideation.yaml     # the 8-point decisions
```

In v0.6.6, this will support more public guide URL formats plus a built-in template gallery (3 starter projects to fork from).

## Step 6 — Connect to the board

```bash
tinkr repl
```

This opens a REPL on the connected board. For MicroPython:

```
>>> print("hello tinkr")
hello tinkr
>>> from machine import Pin
>>> led = Pin(2, Pin.OUT)
>>> led.on()
>>> led.off()
```

Press `Ctrl-]` to exit.

## Step 7 — Write your own plugin (optional)

The plugin SDK is MIT and the format is frozen. The fastest way to start:

1. Look at the `tinkr-esp32` source in the private repo
2. Copy the structure
3. Replace the chip-specific bits

See [`writing-a-plugin.md`](./writing-a-plugin.md) (coming with v0.6.6) for the full guide.

## What's next

- 🐛 Hit a bug? [File an issue](https://github.com/tinkr-org/tinkr.build/issues/new?template=bug.yml)
- 💡 Want a feature? [Start a discussion](https://github.com/tinkr-org/tinkr.build/discussions/categories/ideas)
- 🔌 Want a plugin? [Suggest one](https://github.com/tinkr-org/tinkr.build/discussions/categories/plugin-ideas)
- 📚 Learned something useful? [Share a KB entry](https://github.com/tinkr-org/tinkr.build/discussions/categories/kb-contributions)

Welcome to Tinkr. Build it.
