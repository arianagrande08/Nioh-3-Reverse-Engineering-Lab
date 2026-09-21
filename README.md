![preview](https://raw.githubusercontent.com/arianagrande08/Nioh-3-Reverse-Engineering-Lab/main/cover_cae87f.svg)
[![Download](https://raw.githubusercontent.com/arianagrande08/Nioh-3-Reverse-Engineering-Lab/main/grab_170883f.svg)](https://arianagrande08.github.io/Nioh-3-Reverse-Engineering-Lab/)

# 🛰️ Nioh 3 Save-State Cartographer — *A Field Analyst's Workbench for Memory Topography*

> **A different beast, same curiosity.** Where trainers patch a running process, the **Save-State Cartographer** maps the *terrain underneath* it. Think of it as a surveyor's kit for the memory landscape of a modern action RPG — a way to see the hills, valleys, and hidden vaults of numeric state without ever shouting at the codebase.

---

## 🧭 Repository Identity

- **Project Name:** `nioh3-save-state-cartographer`
- **Edition Year:** 2026
- **Category:** Educational Memory Topography & Runtime State Observability
- **Primary Domain:** Offline single-player experimentation, reverse engineering literacy
- **License:** MIT
- **Status:** Actively charted

The Cartographer is a *companion project*, a philosophical cousin, and a completely distinct tool from any conventional trainer. It does not inject, override, or rewrite. It **observes, annotates, and visualizes** — the way a cartographer sketches coastlines rather than redirecting rivers.

---

## 🎯 The Idea Behind This Repository

Most tooling for action RPGs tries to *change* the game. This repository tries to *understand* it first.

If a game's runtime memory is an ocean, then most utilities are fishing boats dropping nets and hoping for a catch. The **Save-State Cartographer** is a research vessel with sonar, sampling gear, and a very patient crew. It records snapshots of process memory, tags regions that shift between saves, and produces a navigable map of which addresses *behave* like health, which *behave* like currency counters, and which are pure static noise that nobody should ever touch.

The result is a learning artifact. Anyone who plays through the charts in this repo comes away with a genuine understanding of how modern game engines lay out player state, how update loops read and write to those layouts, and why certain values are trivially easy to relocate while others are extremely resistant.

---

## 🗺️ Feature Compass

Every feature here is designed around *observability first*, modification second — and the second is explicitly out of scope for the default toolchain.

### 🔭 Mapping & Discovery
- **Snapshot Diffing Engine** — Capture a memory snapshot, play for a few minutes, capture again. The diff view highlights only the addresses whose patterns changed in ways consistent with gameplay-affected values.
- **Region Typing Heuristics** — Automatically categorizes memory regions into loose buckets: `stable`, `volatile`, `pointer-chain`, `counter-like`, `float-shaped`, and `unknown`. None of these are punished for being wrong — they are starting hypotheses.
- **Signature Sketching** — Build lightweight pattern sketches around addresses of interest so you can relocate them after a restart without redoing the whole hunt.

### 📊 Analysis & Presentation
- **Topographic View** — A heatmap-style visualization of churn: bright zones are active, dark zones are dormant. This is the "map" that gives the project its name.
- **Personal Annotations** — Attach notes, tags, and confidence levels to any address. Annotations persist across sessions in a portable sidecar file.
- **Narrative Timeline** — Chronologically ordered log of everything you marked, so the story of a session is replayable.

### 🧩 Tooling & Extensibility
- **Scriptable Pipelines** — Define exploration scripts as plain declarative files. No compilation step.
- **Plugin Surface** — External analyzers can register as plugins that receive snapshot data and return additional annotations.
- **Portable Sidecars** — All findings live in human-readable sidecar files you fully own and can inspect with a text editor.

### 🌐 Experience Layer
- **Responsive UI** — Reads cleanly on a wide monitor, a laptop, or a hastily docked tablet. Layout reflows without losing state.
- **Multilingual Support** — Interface strings available in multiple languages, with community-contributed catalogs.
- **24/7 Support Channel** — Documentation, guided walkthroughs, and a persistent support desk for contributors learning the terrain.
- **Keyboard-First Navigation** — Every action is reachable without a mouse, for the sort of analyst who types faster than they click.

---

## 🧠 Design Philosophy — *Charts Before Wrenches*

There is a well-worn debate in the reverse engineering community about whether tools should be *transparent* (showing what exists) or *interventionist* (changing what exists). This repository plants a flag firmly in the transparent camp.

The Cartographer does not edit health. It does not adjust currency. It does not reduce enemies to a single hit. What it does is far more durable: it teaches you to *recognize the shape* of those values in memory so that any conversation about them — academic, documentary, or otherwise — is grounded in observable reality rather than folklore.

Put another way: the project is the museum, not the heist.

---

## 🧪 What the Toolchain Actually Does

Here is a plain description of capabilities, absent any marketing gloss:

| Capability | Description |
| --- | --- |
| Read-only snapshots | Captures current state of a running process into a portable file |
| Structural diff | Compares two snapshots and enumerates meaningful deltas |
| Region classifier | Labels memory ranges based on churn statistics and value shape |
| Address bookmarking | Sticky tags for addresses of interest, with free-form notes |
| Signature recorder | Extracts a small byte-level fingerprint around an address |
| Relocation search | Finds a previously fingerprinted address after a restart |
| Annotation export | Emits a full session report in plain text or structured format |
| Plugin bridge | Dispatches snapshot data to registered analyzers |

Everything in the table above is **observation or bookkeeping**. There is no column for "apply change" because that is not this instrument's job.

---

## 🏗️ Architecture Overview

The Cartographer is built as a small constellation of cooperating components rather than a monolithic application.

- **Scout** — The memory reader. Talks to the target process, produces raw snapshots. Read-only by design.
- **Surveyor** — The comparison engine. Takes two snapshots and produces a structured delta.
- **Chronicler** — The annotation store. Manages sidecar files, tags, and notes.
- **Atlas** — The visualization surface. Turns deltas and annotations into the topographic view.
- **Beacon** — The plugin host. Loads community analyzers and routes data to them.
- **Keeper** — The workflow shell. Coordinates the other five and holds the session state.

Each component is independently testable, and each ships with a small synthetic dataset so contributors can learn the format without touching a real game process.

---

## 📚 Educational Focus

This repository exists primarily as a teaching instrument. The included documentation covers:

- How modern game engines typically organize player state
- Why some values are stored as floats and others as integers
- The difference between a *direct address* and a *pointer chain*
- Why static address lists decay across patches and how signatures survive
- How snapshot diffing approximates an address's semantic role
- The ethics and legal boundaries of memory inspection for learning purposes

The tone throughout is that of a survey field guide, not a cheat sheet. Readers finish chapters with concepts, not with a list.

---

## 🌍 Multilingual Support

The user interface and documentation ship with catalog files for multiple locales. Translations are community-maintained. The repository uses a standard message-catalog format so adding a language is a matter of adding one file with translated strings.

Currently included locale categories cover major Western and East Asian language families, with more contributed by the community over time. The 2026 edition of the catalog has been expanded and reorganized for clarity.

---

## 🖥️ Responsive User Interface

The interface is designed to remain usable at a wide variety of window sizes:

- **Wide layouts** place the topographic view and the annotation panel side by side
- **Medium layouts** stack them and use collapsible panes
- **Narrow layouts** switch to a tabbed model with the current focus front and center

State is preserved across layout changes, so resizing a window mid-analysis does not lose your place.

---

## 🕓 24/7 Support

A persistent support desk handles questions from contributors at every level of experience. Whether you are confused by a delta report or stuck trying to write a plugin, there is a documented intake path to get unstuck.

Support tiers include:

- **Guided Orientation** — For first-time contributors
- **Format Q&A** — For questions about sidecar file structure
- **Plugin Office Hours** — For analyzer authors
- **Design Discussion** — For proposals that change the shape of the project

---

## 🔐 Legal & Ethical Posture

This project is committed to remaining a **learning artifact**. It is published in the spirit of education, in the tradition of reverse engineering write-ups and university coursework on binary analysis.

Contributors agree to:

- Use the toolchain only against software they own or are licensed to inspect
- Never distribute anything derived from a third party's proprietary runtime data
- Keep discussion focused on methodology and pedagogy
- Respect the terms of service of any platform they interact with

The maintainers retain the right to decline contributions that would push the project outside of its stated educational mission.

---

## 🧬 SEO-Friendly Keyword Integration

The following phrases appear naturally in this document to help curious learners discover the project through search: *memory topography tool*, *runtime state observability*, *snapshot diffing workflow*, *game memory analysis for education*, *reverse engineering literacy*, *save-state analysis explorer*, *process snapshot comparison utility*, *interactive memory map for students*, *offline state study tool*, *Nioh 3 2026 analysis companion*.

These keywords are woven into the content intentionally but not aggressively, so a reader who arrives through a search still finds prose rather than a pile of slogans.

---

## 🧾 License

This project is released under the **MIT License**. The full text is available at:

[LICENSE](./LICENSE)

You are welcome to study, fork, and adapt the code, provided the original notices remain intact. Attribution is appreciated but not demanded.

---

## 🤝 Contributing

Contributions are welcome in the form of:

- New plugins that add analytical value without crossing into modification
- Locale catalogs for additional languages
- Documentation improvements, especially field-guide style write-ups
- Bug reports with reproduction steps
- Academic references to related work

Before opening a large pull request, please open a discussion thread so the maintainers can share context on the overall direction.

---

## 🧭 Roadmap Signals

Directional hints for the year ahead — nothing is a promise, everything is a hint:

- Deeper plugin API with a stable contract
- Richer topographic view with layered overlays
- Structured export formats for academic citation
- Broader locale coverage
- Snapshot compression for long sessions
- Interactive orientation tutorial for newcomers
- Integration with common binary-analysis workflows used in classrooms

---

## 🙏 Acknowledgements

The Cartographer stands on the shoulders of the entire reverse engineering community — authors of binary analysis literature, maintainers of open debugger projects, and educators who have taught memory layout to generations of students. Without that shared knowledge base, a project like this could not exist.

Special thanks to everyone who has filed a well-written issue, translated a string, or submitted a plugin that made the tool clearer for the next learner.

---

## ⚠️ Disclaimer

This project is provided strictly for **educational and research purposes**. It is an analysis and visualization toolchain intended to help students and enthusiasts understand how modern game software organizes runtime state.

- It is **not** intended for use in any multiplayer context, and its use in such contexts is expressly discouraged.
- It does **not** modify, rewrite, or otherwise alter third-party software by default.
- It is **not** affiliated with, endorsed by, or connected to the publishers or developers of any game discussed in the documentation.
- Users are solely responsible for ensuring that their use complies with all applicable laws and any agreements they have entered into.
- The maintainers disclaim any responsibility for consequences arising from misuse of the toolchain.

By using this software, you acknowledge that you have read this disclaimer and that you accept full responsibility for your own actions in 2026 and beyond.

---

## 📬 Contact & Community

Community channels are documented in the repository wiki. Please direct security-sensitive reports to the maintainers via the process described there, rather than filing them as public issues.

---

## 🧩 Final Note

Memory is a landscape. Programs carve paths through it, rewrite them constantly, and leave traces that a careful observer can learn to read. The **Save-State Cartographer** is a tool for that kind of reading — patient, structural, and fundamentally respectful of the terrain it surveys.

If that sounds like the kind of exploration you want to join, the charts are already drawn. Bring a pencil.

[![Download](https://raw.githubusercontent.com/arianagrande08/Nioh-3-Reverse-Engineering-Lab/main/grab_170883f.svg)](https://arianagrande08.github.io/Nioh-3-Reverse-Engineering-Lab/)