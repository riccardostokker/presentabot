# Proposal

## Why

People and agents need a repeatable way to develop a coherent presentation using reusable visual material, image generation, and an inspectable local source. Presentabot brings those operations together without requiring a hosted editor or prescribing where users keep their presentations.

## What Changes

- Deliver a self-contained TypeScript CLI and local authoring interface using Slidev and UnoCSS.
- Initialize independent presentation folders with mise, TOML settings, Markdown context, native slide source, agent guidance, and ignore rules.
- Supply built-in components, layouts, templates, icons, and reference slides; optionally load organization resources from a user-selected directory.
- Provide OpenAI and Gemini image generation, meaningful asset names, MIME-family folders, and minimal persistent cost accounting.
- Expose the same application operations through MCP, reusing Slidev slide editing where possible.
- Export portable HTML, PDF, and maximally editable PPTX with explicit fallback reporting.
- Follow Stokker repository conventions, use MIT licensing, and publish the software on GitHub.

## Capabilities

### New Capabilities

- `presentation-projects`: Initialization, settings, context, guidance, and portable folders.
- `presentation-authoring`: Shared resources, components, live preview, and agent operations.
- `generation-accounting`: Image generation, asset placement, duplicate prevention, and resettable costs.
- `presentation-export`: Portable deliverables and editable PowerPoint compatibility.

### Modified Capabilities

None; this is a new product.

## Impact

One repository: `riccardostokker/presentabot`, under the personal repository directory. No coupled repository changes are assumed. Runtime dependencies include Slidev/Vue/UnoCSS, Lucide, Mermaid, official provider SDKs, MCP, SQLite, and browser rendering. Exact compatible versions must be verified and locked during implementation.

The repository is currently in proposal authoring. No application code has landed. Hosted collaboration, embedded conversational agents, interchangeable slide engines, mandatory Git, mandatory external resource packages, and persistent preview caches are excluded. Native editable diagram export is an investigation within PPTX compatibility work, not an established capability.
