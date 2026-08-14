# Brand — Tinkr

> **Tinkr** is `t●nkr` — amber dot, otherwise cyan. **Build it.**

This file is the public-facing brand spec. The full internal spec (with mockups 01-17, v7 PCB trace mark construction, and motion guidelines) lives in the private `tinkr-org/tinkr` repo at `brand/01-positioning.md` and `brand/mockups/`.

---

## Wordmark

```
t●nkr
```

- The `i` dot is replaced with a **filled circle (●)** in **amber `#FB923C`**.
- All other letters are **cyan `#5EEAD4`**.
- The dot has a subtle outer glow (`box-shadow: 0 0 0.35em var(--amber)`) to suggest an LED on a circuit board.
- Typeface: **Inter** (UI), **JetBrains Mono** (code/wordmark in dark contexts).

### HTML snippet

```html
<span class="brand-wordmark">t<span class="brand-dot"></span>nkr</span>
```

```css
.brand-wordmark { color: var(--cyan); font-weight: 600; letter-spacing: 0.01em; }
.brand-dot {
  display: inline-block;
  width: 0.42em; height: 0.42em;
  background: var(--amber);
  border-radius: 50%;
  margin: 0 0.06em;
  vertical-align: 0.06em;
  box-shadow: 0 0 0.35em var(--amber);
}
```

---

## Mark (v7 PCB Trace Network)

The Tinkr mark is a **stylized PCB (printed circuit board) trace network**:

- 17+ bright **cyan** traces with 45° chamfered corners
- 24 hollow **pin circles** at trace ends
- 12 filled **junction nodes** at intersections
- 10 dynamic **data-packet nodes** flowing on Bezier-curve motion paths
- 1 **amber** center LED with a soft halo

See `brand/v7-mark/` in the source repo for the SVG source and PNG exports at 1x, 2x, 4x.

The mark is **not** animated in the wordmark — the amber dot is static. Animation is reserved for the standalone mark (in splash screens, hero sections, and the desktop app) where data-packet nodes flow along the traces.

### Mark — do

- Use on **white** or **near-black** (`#0E1116` or darker) backgrounds.
- Maintain at least **16 px** of clear space around the mark.
- Use the SVG source for retina displays; the PNG set is for favicons and social cards.

### Mark — don't

- Don't recolor the mark. The cyan/amber pair is the brand.
- Don't rotate the mark. The 45° chamfers are the visual signature.
- Don't place the mark on a colored background that doesn't contrast with the cyan.

---

## Colors

| Name | Hex | Use |
|---|---|---|
| **Cyan** | `#5EEAD4` | Primary surface, traces, "go" affordances, active states |
| **Amber** | `#FB923C` | Accent, the `i` dot, the center LED, warnings, pay-attention moments |
| **Violet** | `#A78BFA` | Secondary, plugin metadata, "thinking" states, AI surfaces |
| **Ink** | `#0E1116` | Background (dark contexts), code blocks |
| **Paper** | `#FAFAF7` | Background (light contexts), cards, surfaces |
| **Mist** | `#6B7280` | Secondary text, disabled states, dividers |

### Light theme defaults

```css
:root {
  --cyan: #5EEAD4;
  --amber: #FB923C;
  --violet: #A78BFA;
  --ink: #0E1116;
  --paper: #FAFAF7;
  --mist: #6B7280;
}
```

### Dark theme

In dark contexts, swap `--paper` and `--ink`. The cyan and amber stay the same — they read on both backgrounds.

---

## Typography

| Use | Typeface | Fallback |
|---|---|---|
| **UI** | Inter | `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif` |
| **Code** | JetBrains Mono | `"SF Mono", Menlo, Consolas, monospace` |
| **Wordmark** | Inter (700) | as above |

Sizes: H1 2.25rem, H2 1.875rem, H3 1.5rem, body 1rem, code 0.875rem.

---

## Voice & tone

- **Direct, not promotional.** "Build it." not "Build the future of hardware."
- **Show, don't tell.** The 5-command quickstart is the demo. The FAQ answers the doubts.
- **Honest about scope.** v0.6.5 is the first public release, not the final product. The roadmap is public. The WIP is public.
- **No "we" / "us" / "our community" puffery.** Use "Tinkr" or "the project" instead.

---

## Hard rules (the "don't" list)

These rules apply to **every public surface**: README, BRAND, RELEASES, ROADMAP, PLUGINS, COMMUNITY, docs, issue templates, marketing copy, public social posts, and any future public-facing artifact.

### 1. Never name competitors or study targets in feature descriptions

Don't name other tools, platforms, or services when describing what Tinkr does. Use generic terms instead.

- ❌ "Import from Schematik, Wokwi, GitHub, and templates in v0.6.6"
- ✅ "Import from more public guide URLs + built-in templates in v0.6.6"

- ❌ "How is Tinkr different from PlatformIO / Arduino IDE / esptool.py?" (with a comparison table)
- ✅ "How is Tinkr different from other hardware tools?" (with a pain-to-fix table)

- ❌ "A Wokwi-style circuit simulator, built as a Tinkr plugin"
- ✅ "A native circuit simulator, built as a Tinkr plugin"

**What "name a competitor" means:** any mention of a specific third-party tool, platform, or service in a feature description, comparison, or example. This includes "vs X" framing.

**What to use instead:**
- "Other platforms" / "other tools" / "the alternatives"
- "Existing tools" / "the existing ecosystem"
- "Public guide URLs" (not "Schematik URLs" or "Wokwi URLs")
- "AI providers" / "model providers" (not "Anthropic / OpenAI / Ollama")
- "Cloud build services" (not "GitHub Actions / CircleCI / Vercel")
- "Marketplace platforms" (not specific marketplace names)

### 2. Exception: technical / runtime / hardware names

Some names are **technical terms**, not competitive references. These are fine:

- **Programming languages / frameworks:** "Arduino" (the language, not the IDE), "MicroPython", "CircuitPython", "C++", "Python"
- **Hardware names:** "Arduino Uno", "Arduino Nano", "Arduino Mega", "ESP32", "RP2040", "Pico", "nRF52"
- **Protocols / standards:** "I²C", "SPI", "UART", "USB", "WiFi", "Bluetooth", "Zephyr"
- **Generic open-source projects Tinkr depends on:** "Click", "Pydantic", "Tauri" (when listing tech stack, not when comparing)

**Rule of thumb:** if the name appears in a sentence about **what runs on the chip** (languages, hardware, protocols), it's fine. If it appears in a sentence about **what Tinkr does vs. other tools**, it's not.

### 3. Exception: internal / developer docs

This rule applies to **public surfaces only**. Internal developer documentation may name competitors freely:

- `architecture/decisions.md` ✅
- `architecture/competitive-research/*.md` ✅
- `MEMORY.md` (agent memory) ✅
- Source code comments ✅
- `HARNESS.md` (per-chat priming) ✅

These are for the developer, not the public. They can analyze competitors, study what others do, and reference specific tools by name. The public doesn't see them.

### 4. The "what Tinkr does" framing

When describing a Tinkr feature, the framing should be:

- ✅ "Tinkr does X" (capability)
- ✅ "You can use Tinkr to X" (user benefit)
- ✅ "X is a pain today; Tinkr fixes it by Y" (problem → solution)
- ❌ "Tinkr is better than Y at X" (comparison)
- ❌ "Unlike Y, Tinkr does X" (comparison)
- ❌ "If you use Y, switch to Tinkr" (competitive framing)

The FAQ is allowed to answer "is this for me?" and "how is this different?" — but the answers should describe Tinkr's value prop, not enumerate competitors.

### 5. Trademark

In addition to the Tinkr mark, do not use the marks of any other product in a way that suggests endorsement or partnership. This is enforced regardless of whether the comparison is positive or negative.

---

## Trademark

"Tinkr" and `t●nkr` are not yet registered trademarks. The amber dot wordmark is the distinctive mark. Don't use it for:

- Hardware products that don't integrate with the Tinkr CLI
- Paid plugins that don't pass the Tinkr marketplace review (when v0.9 ships)
- Projects that fork the source and change the brand without acknowledging the lineage

Everything else is fair game. Fork, ship, attribute. See [`LICENSE`](./LICENSE) for the legal text.

---

## Asset downloads

Coming with v0.6.6:

- `brand/v7-mark/tinkr-mark.svg` — the canonical mark, 24×24 viewBox
- `brand/v7-mark/tinkr-mark@1x.png` — 24×24 PNG
- `brand/v7-mark/tinkr-mark@2x.png` — 48×48 PNG
- `brand/v7-mark/tinkr-mark@4x.png` — 96×96 PNG
- `brand/wordmark/tinkr-wordmark.svg` — `t●nkr` in SVG
- `brand/wordmark/tinkr-wordmark-dark.svg` — for dark backgrounds
- `brand/social/tinkr-social-card.png` — 1200×630 for social sharing

For now, use the HTML snippet above. The asset pack ships with the v0.6.6 release on Aug 25.
