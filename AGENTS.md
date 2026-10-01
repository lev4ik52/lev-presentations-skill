# Guide for AI agents and maintainers

This repository contains the `lev-presentations` skill. `SKILL.md` is the normative runtime instruction set. This guide explains how an AI system should interpret the style, make presentation decisions, preserve evidence and editability, and verify the final artifact.

## Mission

Create presentations that are calm, readable, editorial, and easy to teach or present. The visual system is recognisable, but clarity is more important than decorative consistency. The skill should improve both the argument and the artifact.

A successful result is not merely a source file. It is an editable deck whose rendered slides were inspected and whose final visible language was reread.

## Activation

Use the skill when the user asks to:

- create a lecture, class, workshop, or business presentation;
- revise, redesign, simplify, or audit a deck;
- produce PPTX, PDF, HTML slides, diagrams, notes, or presentation copy;
- apply Lev's visual system;
- remove artificial or formulaic Russian from slides;
- assess visual hierarchy, editability, or delivery readiness.

Do not activate it for an ordinary document that is not intended to be presented, a generic image-generation request, or a slide task whose user explicitly requires a different established design system.

## Source and scope decisions

For a new presentation, establish the facts that materially affect the structure:

- topic and required scope;
- audience and prior knowledge;
- learning or business objective;
- delivery context and duration;
- required sources and citations;
- desired output formats;
- output location.

Ask only when missing information would change the result. Never invent a teacher, organisation, course, citation, or factual claim.

For an existing deck, inspect it before proposing edits. Identify its usable theme, masters, layouts, media, charts, speaker notes, and editable elements. Preserve valuable structure instead of rebuilding by default.

## Visual grammar

### Colour hierarchy

Use the palette by role, not randomly:

- `#F7F4D5` paper is the default content surface.
- `#0A3323` deep base provides primary text and major dark fields.
- `#839958` moss handles quiet structure, labels, rules, and secondary data.
- `#105666` midnight water separates diagram systems and adds cool contrast.
- `#D3968C` petal marks one exceptional human detail, number, quote, or warning.

Limit a slide to the background plus one or two meaningful accents. Petal should lose its special status if repeated; therefore use it rarely. Dark slides are punctuation: cover, section transition, and perhaps one conclusion.

### Typography hierarchy

Cormorant Garamond is an accent face, not a body face. Use it for a cover, section title, short quotation, or one large proposition. Manrope carries paragraphs, data, chart labels, tables, navigation, and captions.

Preserve a title/body ratio of roughly 2.5–3×. Use weight and spacing before adding more font sizes. Confirm Cyrillic coverage. When the preferred fonts are unavailable, substitute Georgia and Montserrat consistently and disclose the substitution if it affects the deliverable.

### Composition

Prefer one dominant hierarchy, generous margins, and deliberate asymmetry. Diagrams should reveal relationships at a glance. Images must serve the topic; still-life and botanical imagery are not mandatory motifs. Avoid generic gradients, glossy corporate stock, dense card grids, arbitrary icons, and visual filler.

## Content architecture

The deck should make an argument visible:

1. Begin with a concrete intuition, problem, or question.
2. Explain the mechanism or organising idea.
3. Show a consequence, example, comparison, or application.
4. Resolve audience questions directly rather than deferring answers.

Give each slide one job and one takeaway. Convert a list into a comparison, sequence, map, or annotated visual only when that representation clarifies a relationship. A plain list is acceptable when items genuinely have no stronger structure.

Do not shrink text to rescue an overloaded slide. Split the thought, remove repetition, or move detail to notes. Respect the requested duration and avoid expanding the deck beyond what can be presented.

## Russian-language editing

Write for speech, not for an abstract report. Prefer short active sentences, precise nouns, concrete verbs, ordinary vocabulary, examples, and numbers. Remove filler, stacked abstractions, ceremonial conclusions, and unsupported superlatives.

Phrases identified in `SKILL.md` are warning signs, not a mechanical blacklist. Rewrite the whole sentence until a presenter could say it naturally. Avoid synthetic symmetry, especially repetitive three-item lists that exist only for rhythm.

Keep necessary terminology and explain it where it first matters. Apply consistent Russian typography: «ёлочки», spaced long dashes, and one style for numbers and units.

## Editable artifact requirements

For PPTX output:

- use native text boxes, shapes, charts, and tables;
- keep meaningful objects editable and logically grouped;
- preserve useful masters and layouts in existing decks;
- avoid full-slide bitmap backgrounds that imitate editability;
- verify font substitution or embedding before delivery.

For PDF output, visible text should remain selectable. For HTML slides, preserve semantic text and accessible contrast. If the available toolchain cannot satisfy the requested format, state the limitation and provide the best editable source rather than faking completion.

## Verification protocol

Verification is part of creation, not an optional review pass.

1. Render every slide to an image or otherwise inspect its final visual form.
2. Review the deck as a whole for pacing, repetition, and contrast between slide types.
3. Inspect each slide for clipping, overlaps, alignment, margins, contrast, and readable small text.
4. Extract or reread text from the final rendered artifact, not only the source representation.
5. Run a separate language pass for typos, awkward phrases, filler, unexplained abbreviations, and AI-sounding Russian.
6. If anything changes, rebuild and repeat the relevant visual and language checks.

Do not claim that a deck was verified when only the source code or object model was inspected.

## Porting to another agent framework

The behaviour is framework-agnostic. A port should preserve:

- precise activation criteria;
- the five-role colour system;
- the two-font hierarchy and fallbacks;
- one-job/one-takeaway slide discipline;
- natural Russian-language editing;
- native editability and selectable PDF text;
- rendered-slide inspection and final-text rereading;
- factual integrity and honest capability disclosure.

Map `agents/openai.yaml` to the target framework's interface metadata. Keep the runtime entrypoint concise and store this detailed explanation as maintainer context rather than loading it for every request.

## Maintenance checklist

When changing the skill:

- preserve the `lev-presentations` folder and frontmatter name;
- keep the description discriminating enough for automatic discovery;
- treat palette roles as semantic guidance rather than a mandatory colour quota;
- do not add a decorative rule unless it has a concrete failure mode;
- keep content and language guidance aligned with actual presentation use;
- test both a new-deck request and an existing-deck audit when practical;
- render representative slides and inspect the output;
- validate the package structure before release;
- document material behaviour changes.

## Definition of done

A task is complete when the requested formats exist, the presentation has a coherent argument, the visual hierarchy follows the intended style without becoming decorative, native editability is preserved where required, every slide was inspected in rendered form, the visible text passed a separate language review, and limitations or substitutions were disclosed.
