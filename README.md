# Lev Presentations — a presentation design skill for AI agents

`lev-presentations` is a Codex-compatible skill for creating, revising, and auditing lecture, class, and business presentations in a calm editorial style. It combines a defined visual system with content simplification, natural Russian writing, editable slide construction, and mandatory rendered-output verification.

The runtime instructions are in [`SKILL.md`](SKILL.md). [`AGENTS.md`](AGENTS.md) explains the design logic, decision rules, and quality gates for other AI systems and maintainers.

## What the skill covers

- New presentation concepts and complete decks.
- Revision or visual restyling of existing presentations.
- PPTX, PDF, HTML slides, diagrams, speaker notes, and presentation copy.
- Lecture, classroom, workshop, and business material.
- Simplification of dense source material into a visible argument.
- Editing Russian text so it sounds natural when spoken aloud rather than machine-generated.
- Final visual and language quality assurance.

## Design system

The style is built around five colours:

| Role | Hex | Typical use |
| --- | --- | --- |
| Deep base | `#0A3323` | Covers, section transitions, dark text |
| Moss | `#839958` | Rules, labels, secondary data |
| Paper | `#F7F4D5` | Main light background and cards |
| Petal | `#D3968C` | One rare human or emotional accent |
| Midnight water | `#105666` | Diagrams, charts, contrast fields |

Most content slides use paper with deep-green typography. Dark slides are reserved for the cover, transitions, and a strong conclusion. Petal is intentionally scarce: it should focus attention, not become decoration.

Typography uses **Cormorant Garamond** for sparse display moments and **Manrope** for readable body text, data, captions, and navigation. Fallbacks are Georgia and Montserrat. The skill requires Cyrillic support and discourages a third typeface.

## Why this is more than a theme

The skill does not merely assign colours and fonts. It also governs the argument of the presentation:

- one job and one takeaway per slide;
- intuition before mechanism, mechanism before consequence;
- comparisons, sequences, maps, and annotated visuals instead of unnecessary lists;
- more slides rather than unreadably small text;
- direct answers after audience questions;
- editable native shapes, text, charts, and tables;
- a full render inspection followed by a separate language pass.

The result should feel deliberate and quiet, not templated. Botanical or still-life imagery is optional and must support the subject.

## Install

### Git clone

PowerShell:

```powershell
git clone https://github.com/lev4ik52/lev-presentations-skill.git "$env:USERPROFILE\.codex\skills\lev-presentations"
```

macOS/Linux:

```bash
git clone https://github.com/lev4ik52/lev-presentations-skill.git ~/.codex/skills/lev-presentations
```

Restart or reload the agent after installation.

### Download ZIP

1. Choose **Code → Download ZIP** on GitHub.
2. Extract the archive.
3. Rename the folder to `lev-presentations`.
4. Move it to `~/.codex/skills/lev-presentations` (Windows: `%USERPROFILE%\.codex\skills\lev-presentations`).
5. Restart or reload the agent.

### Verify

The installed folder should contain at least:

```text
~/.codex/skills/lev-presentations/
|-- SKILL.md
`-- agents/
    `-- openai.yaml
```

Try:

```text
Use $lev-presentations to turn this lecture outline into a clear 12-slide deck with speaker notes.
```

## Usage examples

```text
Use $lev-presentations to audit this PPTX. Preserve editable content, simplify dense slides, and verify the rendered result.
```

```text
Use $lev-presentations to redesign this business presentation in the paper, moss, and dark-water visual system.
```

```text
Use $lev-presentations to rewrite the Russian slide copy so it sounds natural when spoken and contains no AI-style filler.
```

## Requirements and tool choices

The skill is intentionally tool-agnostic. The agent needs an authoring workflow capable of producing the requested output and, for final delivery, rendering every slide for inspection. Depending on the environment, that may involve PowerPoint, LibreOffice, a presentation library, HTML/CSS, or another slide tool.

The important requirements are outcome-based:

- keep PPTX content natively editable;
- export PDF text as selectable text;
- render and inspect every slide;
- reread the final rendered text;
- disclose when the available toolchain cannot meet the requested format or quality bar.

## Russian-language writing policy

The skill favours short active sentences, precise nouns, concrete verbs, ordinary vocabulary, and useful examples. It explicitly removes ceremonial filler and phrases such as «в современном мире», «важно отметить», «давайте погрузимся», «данный» and «таким образом, мы видим».

This is not a word blacklist. The sentence must be rewritten until it sounds natural aloud. Terminology stays only when it teaches something. Russian typography should consistently use «ёлочки», spaced long dashes, and one number/unit style.

## Privacy and factual integrity

- Do not invent teachers, courses, citations, facts, or source attribution.
- Inspect existing decks before editing them.
- Preserve useful themes, masters, layouts, and editable content where possible.
- Do not pretend a deck was visually verified unless every slide was rendered and inspected.
- Do not hide missing rendering or authoring capabilities.

## How agent skills should be packaged

A portable skill is a folder with a required `SKILL.md` entrypoint:

```text
lev-presentations/
|-- SKILL.md              # discovery metadata and runtime instructions
|-- agents/
|   `-- openai.yaml       # interface metadata and default prompt
|-- AGENTS.md             # implementation guide for AI systems
|-- README.md             # installation and human documentation
`-- LICENSE               # redistribution terms
```

The frontmatter should make activation precise. Runtime instructions should contain only decisions that materially improve the work. Larger implementation explanations belong in supporting documentation so they do not consume context on every invocation.

## Updating

If installed with Git:

```powershell
git -C "$env:USERPROFILE\.codex\skills\lev-presentations" pull --ff-only
```

If installed from ZIP, replace the folder after preserving any local adaptations.

## License

MIT — see [`LICENSE`](LICENSE).
