# Design

## Context

See proposal.md for scope. User-owned presentations may live anywhere, including Downloads or an independently versioned directory. The software repository contains only code, bundled defaults, examples, and its own development guidance.

## Goals / Non-Goals

Goals: native Slidev authoring, strong agent context, reusable visual resources, transparent generation costs, and practical editable PowerPoint delivery.

Non-goals: a second slide engine, a second deck state authority, a hosted service, automatic Git creation, or accounting for external agent usage.

## Decisions

### Presentation Contract

Proposed commands: `presentabot init [directory]`, `presentabot serve [directory]`, `presentabot export [directory]`, `presentabot cost show`, and `presentabot cost reset`. Directory omission selects the current directory. Commands are proposed, not available.

Initialization creates `mise.toml`, `presentabot.toml`, `CONTEXT.md`, `slides.md`, `.gitignore`, and canonical/provider agent guidance. The runtime creates `assets/`, `outputs/`, and `.presentabot/state.sqlite` as needed. There is no persistent cache. Optional `slides/` uses native Slidev imports without a second generated deck authority.

Presentation mise configuration pins the installed/released Presentabot tool and required runtime through its actual supported distribution mechanism. It exposes native tasks for live authoring and export; it does not copy the software repository's development toolchain, require a source checkout, or run Git initialization. Resolve the tool distribution before shipping this template.

TOML owns Presentabot settings and credential variable names. Native slide frontmatter owns Slidev settings. Secrets are never stored in either. `CONTEXT.md` owns audience, goal, desired outcome, central message, constraints, narrative arc, slide intent, and open questions. Root agent guidance directs agents to read and maintain it.

### Resources And Rendering

Bundle defaults within Presentabot; no separate kit installation is required. Optional organization resources use a user-selected root with assets, components, layouts, styles, templates, references, and canonical agent guidance. Shared resource identity and replacements are explicit; collisions fail instead of silently merging arbitrary files. Resolve immutable resource versions for portable exports.

Use Vue and native UnoCSS, not an additional Tailwind pipeline. Theme owns branding and defaults; addon owns reusable components and additional layouts. Components include cards, metrics, callouts, timelines, image/text compositions, and Lucide icons. Mermaid owns text-authored diagrams. Reference slides provide usable source, previews, and explanatory metadata.

One application facade owns settings, resource resolution, assets, generation, accounting, preview, and export. CLI, dashboard, and MCP delegate to it. Slidev remains the source/parser/rendering owner. Reuse its editing implementation and verify edits retain source-file identity; no competing Markdown representation.

Dashboard includes preview, slide navigation, resource gallery, asset browser, active generation status, and live project cost counter. MCP exposes context/resources, slide edits, preview capture, generation/status, cost inspection, and exports. Cost reset is an explicit user command, not automatic agent maintenance. Scope mutations to the selected project and reject stale source revisions.

### Assets And State

Store imported and generated media in `assets/images`, `assets/audio`, `assets/video`, `assets/documents`, or `assets/data`, based on detected MIME type; create folders only when needed. Split application MIME types by document/data purpose. Use descriptive safe names, true extensions, and numeric collision suffixes. Never overwrite previous generations implicitly.

SQLite stores only generation identity, provider/model, status, output asset path, estimated/final usage-derived cost, and counting period. Minimum bookkeeping for atomic transitions and reset boundaries is permitted. Do not store slide copies, prompts, full API responses, thumbnails, an asset catalog, or a persistent queue. No default provenance sidecars are required.

Persist a request identity before submission. Repeated requests with the same identity do not launch another paid call. Interrupted submissions remain uncertain and are never blindly retried. Reset starts a new counting period while retaining history; running requests retain their original period. Show usage-derived costs as estimates, including unresolved charges. No external agent cost attribution.

### Export Compatibility

Use native Slidev HTML/PDF/editable-PPTX export, pinning and verifying supported APIs. Prefer editable text and simple shapes in bundled layouts. Generated illustrations stay images with separate text. Report element/slide rasterization and font dependencies. Preserve notes; default PPTX to one slide per authored slide. Assess targeted native diagram export and report the tradeoff before expanding into a separate rendering system.

Export only referenced/explicitly included assets. Do not copy CONTEXT.md, guidance, private reference documents, credentials, or runtime state. HTML must run without the original checkout or shared resource directory. Browser-only interactivity cannot be promised in static formats.

## Ownership And Dependency Order

One future writer owns all source, tests, templates, configuration, examples, README, and docs. Intended integration workspace: `personal/presentabot.wt/foundation`; branch: `feat/presentabot-foundation`, created through Hub from published dev. This proposal is authored in the primary repository before handoff. No other source slices or external owners exist.

Implement settings/templates first; then resources and Slidev integration; then generation/accounting; then dashboard/MCP/export. Each slice includes its tests and documentation. Only the combined tree can become SOURCE COMPLETE. Project-wide validation follows complete source and writer handoff; relevant local gates and writer-run tests still precede commits.

## Risks / Trade-offs

- PPTX may rasterize diagrams or alter text wrapping: test actual exported objects and native PowerPoint rendering, and expose limitations rather than claiming complete editability.
- Shared Vue resources execute code: require explicit trusted selection and pinned dependencies; do not treat presentation rendering as sandboxed.
- Provider timeout may hide a charge: retain uncertainty and require deliberate retry with a new request identity.
- Provider SDK/pricing drift: pin actual model IDs, preserve cost evidence minimally, and validate adapters against current official documentation.
- Native agent discovery differs: render supported provider surfaces from canonical guidance and test supported clients without requiring private Hub access for consumers.

## Migration And Delivery

Bootstrap base is explicitly approved as dev; destination is public `riccardostokker/presentabot`. No existing data migration exists. Initial repository publication is authorized; ready product delivery and release remain subject to applicable validation and authorization. No benchmarks were requested. Installed hook files do not establish native agent trust.
