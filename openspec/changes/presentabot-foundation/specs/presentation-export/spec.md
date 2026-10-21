## ADDED Requirements

### Requirement: Portable Deliverables
Presentabot SHALL export HTML, PDF, and PPTX into outputs without requiring the source checkout or organization resource folder to view the deliverable.

#### Scenario: Independent HTML
- **WHEN** exported HTML is served separately with its collected resources
- **THEN** referenced local fonts, icons, images, and layouts render without the original source directory

#### Scenario: Private Assets
- **WHEN** assets includes unused research documents and reference presentations
- **THEN** those files, CONTEXT.md, guidance, credentials, and local state are excluded unless an asset is explicitly included

### Requirement: Editable PowerPoint Priority
Presentabot SHALL prioritize native editable text and shapes through Slidev's editable exporter and SHALL expose material compatibility losses.

#### Scenario: Standard Components
- **WHEN** a deck uses bundled cards, metrics, and simple text/shape layouts
- **THEN** supported text and shapes remain editable in the PPTX
- **AND** speaker notes are preserved

#### Scenario: Raster Fallback
- **WHEN** a diagram, icon, effect, or slide requires image fallback
- **THEN** the export report identifies the affected content and reason where available
- **AND** it does not describe the entire result as fully editable

#### Scenario: Click Steps
- **WHEN** a user exports without requesting incremental slides
- **THEN** each authored slide produces one PPTX slide

### Requirement: Representative Native Verification
Presentabot SHALL document tested export behavior and material font/layout limitations using representative rendered decks.

#### Scenario: PowerPoint Acceptance
- **WHEN** release acceptance evaluates editable PPTX
- **THEN** actual native object editability and PowerPoint rendering are checked
- **AND** unavailable native verification is reported as incomplete rather than inferred from Linux browser rendering
