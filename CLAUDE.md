# AG Obsidian Vault — Claude Context

This file is auto-loaded by Claude Code on every session in this repository.

## Vault Purpose

Personal knowledge management and second brain for a Full-Stack 3D Graphics & Simulation Engineer.
Primary domains: WebGL/WebGPU, 3D Gaussian Splatting, NeRF, GIS/Geospatial, OpenUSD, Computer Vision.
Goal: T-shaped mastery — broad engineering foundation with deep technical expertise in graphics/spatial.

Owner: Anwesh Gangula (Full-Stack 3D Engineer at Optellix, working on Strayos — a mining 3D visualization platform).

## Folder Structure

```
notes/
├── 00 _System/     Vault infrastructure: templates, schemas, scripts, Claude reference files
├── 10 Inbox/       Zero-friction capture staging (7-day purge rule)
├── 20 Journal/     Dated notes: daily logs, weekly reviews, periodic snapshots
├── 30 Projects/    Active work with defined end-states (PARA P)
├── 40 Areas/       Ongoing domain knowledge (PARA A) — 8 domains (see below)
├── 50 Knowledge/   Evergreen synthesis layer: concepts/, mocs/, resources/ (PARA R)
├── 60 Agents/      AI infrastructure: personas, prompts, Repomix bundles
└── 90 Archive/     Completed projects and deprecated content
```

**Old numbered folders** (`00-09 _Management/`, `10-19 Calendar/`, etc.) still exist during migration.
Week 1 of a 4-week incremental migration. Do not reference old paths in new content.

## Domain Areas (40 Areas/)

| Folder | Covers |
|---|---|
| `3d-graphics/` | WebGL, WebGPU, Three.js, GLSL, R3F, Vulkan, OpenGL |
| `geospatial/` | GIS, OpenLayers, Mapbox, FlatGeobuf, CesiumJS, PROJ |
| `graphics-math/` | Linear algebra, SDFs, raymarching, PBR, quaternions |
| `ai-ml/` | 3DGS, NeRF, diffr rendering, LLM tooling, Computer Vision |
| `software-arch/` | Patterns, TypeScript, design systems, SOLID, OOP |
| `career/` | CV, strategy, employer records (Optellix/Strayos) |
| `life-os/` | Principles, finance, health, habits |
| `pkm/` | This vault's architecture, Obsidian docs, plugin notes |

## Note Conventions

### Required frontmatter (all non-daily notes)
```yaml
type: note | concept | moc | project | resource | template
status: fleeting | processing | evergreen | archived
domain: 3d-graphics | geospatial | graphics-math | ai-ml | software-arch | career | life-os | pkm
tags: []
created: YYYY-MM-DD
modified: YYYY-MM-DD
```

### Status definitions
- `fleeting` — raw capture or work-in-progress; not yet synthesized
- `processing` — has been moved to permanent location; Prose Tax in progress
- `evergreen` — contains synthesis paragraph; stable and linkable
- `archived` — no longer active

### The Prose Tax
A note reaches `status: evergreen` only when it contains a synthesis paragraph that answers:
**"What does this mean for how I build things?"**
A list of facts is NOT synthesis. A code snippet alone is NOT synthesis. An original claim is synthesis.

### Note granularity
Concept documents — not atomic Zettelkasten. One note = one bounded concept.
5-bullet rule: when a daily note has 5 bullets on the same sub-topic, create a concept doc.

### Tag taxonomy
```
tech/webgl   tech/threejs   tech/glsl   tech/gaussian-splatting   tech/nerf
tech/gis     tech/openlayers tech/flatgeobuf   tech/openUSD
tech/linear-algebra   tech/sdf   tech/raymarching   tech/pbr
ai/llm   ai/rag   ai/agents   ai/prompting
concept/algorithm   concept/architecture   concept/math   concept/pattern   concept/performance
```

### Daily note capture convention
Use `$` prefix on bullets to mark promotion candidates.
Example: `$ [WebGL: BVH faster than stencil for >1000 objects in clipping scenarios]`

## Claude's Role in This Vault

### Do without asking
- Read any note and answer questions about its content
- Draft Prose Tax synthesis paragraphs given raw bullet captures
- Suggest backlinks and MOC connections for a note
- Write new concept note drafts from provided bullet captures
- Synthesize across notes in a domain
- Analyze vault structure and suggest improvements

### Always ask first
- Write or modify vault files (even drafts)
- Delete any existing content
- Anything that will trigger Obsidian Git auto-commit

### Tone and calibration
- Treat the owner as a senior software engineer learning new graphics/spatial domains
- Connect new graphics/spatial concepts back to software engineering fundamentals
- Dense and precise over verbose — this owner values synthesis over summaries
- No hedging on technical topics — give an opinion with reasoning

## Slash Commands Available

Run these in the Claude Code CLI from this repo's root:

| Command | Usage |
|---|---|
| `/promote` | Process $ bullets from a daily note → promotion plan |
| `/synthesize` | Domain knowledge summary + gaps + next priority |
| `/moc` | Draft MOC structure for a domain folder |
| `/connect` | Find unlinked related notes for a given note |
| `/brief` | Project stand-up summary |
| `/write-note` | Draft a concept note from raw bullets |
| `/vault-review` | Full weekly review: inbox + stale notes + synthesis |

Full command prompts: `.claude/commands/[command-name].md`

## Reference Files

- Writing conventions: `notes/00 _System/claude/writing-guide.md`
- Domain contexts: `notes/00 _System/claude/domains/[domain].md`
- Vault architecture: `notes/40 Areas/pkm/vault-architecture-v2.md`
- Project board: `notes/30 Projects/_index.md`
