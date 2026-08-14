# Community

> **The community is the moat.** Every KB entry makes the AI smarter. Every plugin makes the CLI more capable. Every bug report makes the next release better. We're building this together.

This file is the **map** of how to get involved. Pick the channel that fits.

---

## 1. Bug reports 🐛

**For:** "Something doesn't work the way I expected."

[File an issue](https://github.com/tinkr-org/tinkr.build/issues/new?template=bug.yml) with:

- `tinkr --version` output
- `tinkr plugin list` output
- The exact command you ran
- What you expected vs. what happened
- The relevant log snippet (use `tinkr --verbose <command> 2>&1 | tee tinkr.log`)

A good bug report reproduces in under 5 minutes. We'll prioritize the ones that do.

---

## 2. Feature requests 💡

**For:** "It would be cool if Tinkr did X."

[Start a discussion in the Ideas category](https://github.com/tinkr-org/tinkr.build/discussions/categories/ideas) with:

- What you want to do (the user story)
- Why it matters (the impact)
- What you tried first (the workaround)
- What you imagine the command would look like (optional but helpful)

We read every discussion. The ones that get 👍 from the community get prioritized.

---

## 3. Plugin ideas 🔌

**For:** "Tinkr should support chip X" / "Tinkr should integrate with service Y."

[Start a discussion in the Plugin ideas category](https://github.com/tinkr-org/tinkr.build/discussions/categories/plugin-ideas) with:

- The chip / service / integration
- A link to the chip vendor or service docs
- A sketch of what the plugin would expose (`tinkr <chip> port-scan`, `tinkr <service> auth`, etc.)
- Whether you'd be willing to write it (or want to find a collaborator)

The plugin SDK is MIT and the format is frozen. Most plugins are 1-2 days of work for someone who knows the chip.

---

## 4. KB contributions 📚

**For:** "I learned something the next person should know."

[Start a discussion in the KB contributions category](https://github.com/tinkr-org/tinkr.build/discussions/categories/kb-contributions) with:

- **Recipe:** a step-by-step process that works ("flash MicroPython to an ESP32-S3 in 4 commands")
- **Fact:** a single useful nugget ("ESP32-C3 USB-CDC needs `tinkr repl --dtr 0` on macOS Sonoma")
- **Error:** a common error and its fix ("OSError: [Errno 5] EIO on ttyACM0 — bad USB cable")
- **Pattern:** a design idea that applies to many projects ("read the I²C bus before assuming the device is dead")

We'll author the best ones into the public KB with attribution.

---

## 5. Q&A and show-and-tell 💬

**For:** "How do I...?" / "I built this with Tinkr, look!"

- [Q&A category](https://github.com/tinkr-org/tinkr.build/discussions/categories/q-a) — usage questions, no question too small
- [Show and tell](https://github.com/tinkr-org/tinkr.build/discussions/categories/show-and-tell) — projects you built, plugins you wrote, workflows you discovered

The community helps each other. The Tinkr team reads and answers when we can.

---

## 6. Writing plugins 🛠

**For:** "I want to add a chip / integration / workflow as a first-party-quality plugin."

The plugin SDK is MIT and the manifest format is frozen. The fastest way to start:

1. Read the `tinkr-esp32` source in the private repo (`plugins/tinkr_esp32/`)
2. Read [`docs/writing-a-plugin.md`](./docs/writing-a-plugin.md) (coming with v0.6.6)
3. Copy the `tinkr-esp32` structure, rename, replace the chip-specific bits
4. Run `tinkr plugin list` to confirm it loads
5. Run `tinkr <your-plugin> port-scan` to confirm it works
6. Open a PR

First-party plugins ship in the `tinkr-cli` wheel. Community plugins ship in their own PyPI packages and install via `pip install tinkr-<your-plugin>`.

---

## 7. Code of conduct

This project follows the [Contributor Covenant](https://www.contributor-covenant.org/) (see [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md)). Be kind. Assume good faith. Disagree on the substance, not the person. The Tinkr team enforces this — report violations to conduct@tinkr.build.

---

## 8. Release cadence

We ship **every Monday** until v1.0. See [`RELEASES.md`](./RELEASES.md) for the changelog. Watch this repo (Releases only) for email notifications, or subscribe to the [PyPI release RSS](https://pypi.org/rss/project/tinkr-cli/releases.xml).

---

## 9. Roadmap

See [`ROADMAP.md`](./ROADMAP.md). The roadmap is a public commitment. When we change it, the changelog says so.

---

## 10. The Tinkr team

Tinkr is a solo-founder project right now. The team is:

- **Ronie Joseph** — founder, primary maintainer
- **The community** — bug reporters, KB contributors, plugin authors, discussion answerers

We don't have a Discord, a Matrix, or a Slack yet. **GitHub Discussions is the kitchen table** for v0.6.5. If the community outgrows it, we'll add channels in v0.8 / v0.9 when there's a real need.

---

## 11. License

Tinkr is MIT. Your contributions are MIT. See [`LICENSE`](./LICENSE) for the legal text. Fork, ship, attribute.

---

**Welcome to Tinkr. Build it.** 🟠
