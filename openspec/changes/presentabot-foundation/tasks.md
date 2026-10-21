# Tasks

## 1. Integration And Tooling

- [ ] 1.1 Assign one implementation writer to Hub-created presentabot.wt/foundation on feat/presentabot-foundation from published dev; verify ownership and start this change before editing application source.
- [ ] 1.2 Establish pinned TypeScript, pnpm, mise, selected project skeletons, and native public GitHub CI for Linux and Windows; verify public tasks require no private tools or credentials.
- [ ] 1.3 Resolve and lock actual Slidev editable-PPTX/MCP APIs and the distributable Presentabot runtime; verify installed consumers do not need the source checkout.

## 2. Presentation Initialization And Settings

- [ ] 2.1 Implement src/project settings and init operations plus CLI parsing; add tests for arbitrary paths, spaces, conflicts, and no Git creation, and document init usage.
- [ ] 2.2 Implement bundled presentation templates for mise.toml, presentabot.toml, CONTEXT.md, slides.md, and .gitignore; prove generated mise tasks launch the installed runtime.
- [ ] 2.3 Implement canonical agent guidance and supported provider rendering without private Hub runtime dependencies; verify discovery and context pointers and document supported clients.

## 3. Resources And Slide Authoring

- [ ] 3.1 Implement explicit shared-resource resolution and bundled themes/addons under src/resources; test collisions and overrides and document resource ownership.
- [ ] 3.2 Supply layouts, cards, metrics, timelines, callouts, Lucide, Mermaid, and reference slides with representative examples; verify consistent rendered appearance.
- [ ] 3.3 Integrate Slidev source editing and live preview under src/presentation; test native imports, original-file writes, stale revisions, and process cleanup; document limitations.

## 4. Generation And Costs

- [ ] 4.1 Implement detected-MIME asset routing and meaningful collision-safe names under src/assets; test naming, path containment, formats, and imports and document placement.
- [ ] 4.2 Implement explicit OpenAI/Gemini adapters under src/generation with current capability contracts; add offline tests and document credential/model settings.
- [ ] 4.3 Implement minimal SQLite accounting, atomic request identities, uncertainty, and user-reset periods under src/accounting; test duplicates, restart boundaries, and in-flight reset behavior and document data retention.
- [ ] 4.4 Wire generation operations to assets and accounting without persisted prompts, response dumps, a queue, or cache; verify all success/failure transitions using offline provider fixtures.

## 5. User And Agent Interfaces

- [ ] 5.1 Implement dashboard preview, slide/resource/asset navigation, generation status, and cost display; add browser stories and document user workflow.
- [ ] 5.2 Implement MCP registration/resources over the common application facade, reuse Slidev editing, and scope access to the selected project; test protocol operations and context discovery and document client setup.
- [ ] 5.3 Expose CLI serve/export/cost operations and explicit user reset; test command behavior and keep README examples aligned with implemented commands.

## 6. Export

- [ ] 6.1 Implement portable HTML/PDF/PPTX export and selective asset collection under src/export; test private asset exclusion and independent output use and document format behavior.
- [ ] 6.2 Implement editable-first component choices, one-slide default, notes, font/fallback reporting, and representative export fixtures; inspect actual PPTX objects and document compatibility.
- [ ] 6.3 Assess editable Mermaid node/connector export against native Slidev support; record feasibility and seek direction before a separate renderer or expanded compatibility commitment.

## 7. Combined Validation And Documentation

- [ ] 7.1 Account for the entire combined source inventory, examples, templates, docs, README, and obsolete proposal mechanisms; explicitly declare SOURCE COMPLETE only after the sole writer hands off.
- [ ] 7.2 Run relevant repository gates and justified combined development-profile lanes, repair failures, and verify required Linux/Windows provider results without substituting one platform for another.
- [ ] 7.3 Validate live provider behavior only with explicitly available authorized test credentials/spend; report any unavailable external evidence and retain deterministic credential-free required tests.
- [ ] 7.4 Verify representative exported PPTX in native PowerPoint for editability, notes, fonts, and wrapping; report unavailable platform access instead of claiming verification.
- [ ] 7.5 Verify packaged installation and generated presentation mise workflow without a source checkout; update installation instructions, MIT notices, and tested compatibility documentation.

## Workflow Follow-Up

- Finish the change only when every tracked task is complete; archive requirements through the Hub lifecycle.
- Publish owned feature revisions after required relevant gates and hooks; publication alone does not establish delivery readiness.
- Ready review, integration, and release follow the standing authorization and protection rules; no benchmarks or recurring monitoring are requested.
