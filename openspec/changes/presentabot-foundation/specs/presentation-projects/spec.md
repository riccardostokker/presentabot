## ADDED Requirements

### Requirement: Independent Presentation Initialization
Presentabot SHALL provide `presentabot init [directory]` to initialize a user-selected presentation directory without requiring Git or a software checkout.

#### Scenario: New Presentation
- **WHEN** the user initializes a new directory, including a path with spaces
- **THEN** it contains mise.toml, presentabot.toml, CONTEXT.md, slides.md, .gitignore, and supported agent guidance
- **AND** the mise configuration pins a usable Presentabot distribution and exposes authoring/export tasks without a private Hub dependency
- **AND** no Git repository is created

#### Scenario: Existing Content
- **WHEN** initialization encounters an existing conflicting file
- **THEN** it preserves that file and reports the conflict without destructive partial replacement

### Requirement: Authoritative Settings And Context
Presentabot SHALL keep application settings in TOML, native Slidev settings in slide frontmatter, and the presentation brief and story together in CONTEXT.md.

#### Scenario: Agent Begins Authoring
- **WHEN** an agent loads the root guidance or project context through MCP
- **THEN** it is directed to CONTEXT.md and receives the applicable authoring rules
- **AND** the context includes audience, objective, desired outcome, narrative, constraints, and unresolved questions

#### Scenario: User Versions A Deck
- **WHEN** the user chooses to initialize Git independently
- **THEN** the generated ignore rules exclude local runtime state and generated outputs without excluding authored context, slides, or assets

### Requirement: Portable Ownership
Presentabot SHALL open presentations independently of their location and SHALL keep bundled product resources separate from optional organization resources.

#### Scenario: Presentation Moves
- **WHEN** the presentation is moved and its declared resource dependencies remain available or have been collected
- **THEN** local asset references resolve without dependence on the original absolute directory

#### Scenario: No Organization Configuration
- **WHEN** no organization resource root is configured
- **THEN** bundled components, layouts, templates, and guidance support ordinary authoring
