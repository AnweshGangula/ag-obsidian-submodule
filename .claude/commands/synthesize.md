Generate a synthesis of current knowledge in a domain.

Domain or folder to synthesize: $ARGUMENTS
(If not provided, ask which domain to synthesize — valid domains: 3d-graphics, geospatial, graphics-math, ai-ml, software-arch, career, life-os, pkm)

Steps:
1. Read all notes in `notes/40 Areas/[domain]/` — focus on notes with `status: evergreen` or `status: processing`
2. Read the domain context file at `notes/00 _System/claude/domains/[domain].md` if it exists
3. Read the learning roadmap at `notes/Full-Stack 3D Engineering Roadmap — Graphics, Simulation & Digital Twins.md` (for technical domains) to understand the target learning state

Then write a synthesis with these three sections:

**What I know deeply**
2-3 paragraphs on the areas with strong, synthesized notes — where the vault has real depth.

**What I know shallowly or have gaps**
Honest assessment of topics that appear in notes but are still `status: fleeting` or have thin synthesis. What is covered but not understood?

**Next learning priority**
Based on the roadmap and the gap analysis: one specific recommendation for what to learn/synthesize next, and which existing notes to build on.

Keep the whole output under 500 words. Be direct — this is a gap analysis, not a flattering summary.

Do NOT modify any files. Output only to this conversation.
