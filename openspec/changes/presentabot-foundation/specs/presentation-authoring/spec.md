## ADDED Requirements

### Requirement: Native Slidev Source
Presentabot SHALL use slides.md as the canonical deck entry and support native imports when users split slides into files.

#### Scenario: Live Edit
- **WHEN** a human or MCP client edits a slide
- **THEN** the appropriate authored Markdown source changes and the live preview updates
- **AND** no independent duplicate deck representation is maintained

### Requirement: Reusable Visual Resources
Presentabot SHALL provide reusable Vue components, presentation-wide layouts, UnoCSS styling, Lucide icons, Mermaid diagrams, and reference slides.

#### Scenario: Consistent Deck
- **WHEN** the user selects a visual theme and composes cover, comparison, metric, and closing slides
- **THEN** typography, spacing, palette, and repeated decorations remain consistent

#### Scenario: Organization Resources
- **WHEN** a configured organization resource supplies a component or layout
- **THEN** it can be selected by explicit identity and any collision requires explicit replacement

### Requirement: Agent Authoring Operations
Presentabot SHALL expose application capabilities through MCP and deliver reusable guidance through supported native agent surfaces.

#### Scenario: Story To Slides
- **WHEN** an agent reads CONTEXT.md and requests components, references, and slide edits
- **THEN** it can assemble, render, inspect, and revise the same deck visible to the user

#### Scenario: Conflicting Edit
- **WHEN** a mutation is based on an obsolete source revision
- **THEN** the mutation fails with enough context to reread and retry without overwriting a newer edit

### Requirement: Authoring Dashboard
Presentabot SHALL provide slide navigation, preview, resource/asset browsing, generation status, and a live cost display without persistent preview caching.

#### Scenario: Authoring And Presentation
- **WHEN** the user switches from authoring to presentation or export
- **THEN** authoring controls and cost displays are absent from the presented slides
