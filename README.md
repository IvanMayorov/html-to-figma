# HTML to Figma

An agent skill for turning an HTML page or live website into an editable Figma design, or bringing an existing Figma frame back into sync with its source.

Works with any website or framework. No project-specific URLs, layer IDs, colors, fonts or dimensions are embedded. The skill instructions are written in Russian; source pages can use any language.

## What it does

- Measures the rendered page at the target frame width using DOM geometry and computed styles.
- Builds or repairs native editable text, vectors, images, cards and buttons.
- Uses percentage line heights and preserves balanced text wrapping where supported.
- Checks colors, fills, opacity, borders, corner radii, spacing and actual line breaks.
- Removes redundant wrappers and layout grids while retaining useful button/card auto-layout.
- Reviews every section using full-page and enlarged screenshots, then checks fonts, text overflow and layer structure.

Animations may be represented by a reproducible static state. Multiple requested viewport widths are handled separately.

## Requirements

An agent with skill support, browser access for DOM/computed-style inspection, and a Figma integration capable of editing native Design layers. This repository supplies workflow instructions, not a standalone HTML parser, browser extension or Figma plugin. With OpenAI Figma tools, use the corresponding Figma skills as instructed in SKILL.md.

## Install

Clone this repository into your project's skill directory:

```sh
git clone https://github.com/IvanMayorov/html-to-figma.git .agents/skills/html-to-figma
```

For other agents, place the repository in the skill discovery directory they support.

## Use

```text
Use $html-to-figma to match this Figma frame to the entire source page.
Source: https://example.com/page
Figma: <destination file or frame URL>
```

You can also provide a local HTML file or project page. For a new frame, specify the destination and viewport width, or let the agent determine them from the task context.

The workflow does not deploy the source website. Missing fonts, inaccessible assets and unsupported rendering features must be reported rather than silently approximated. Screenshots alone cannot guarantee accurate source typography or CSS recovery.

## Files

- [SKILL.md](SKILL.md): the reusable workflow and completion criteria.
- [references/implementation.md](references/implementation.md): measurement and native Figma editing notes.
- [agents/openai.yaml](agents/openai.yaml): display name and invocation metadata.
