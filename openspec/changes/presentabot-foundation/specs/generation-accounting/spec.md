## ADDED Requirements

### Requirement: Provider Image Generation
Presentabot SHALL support generation and supported editing through OpenAI and Gemini using server-side credentials referenced by environment variable names.

#### Scenario: Generate An Image
- **WHEN** a user or agent submits supported generation settings
- **THEN** the resulting image is written under assets/images with a meaningful safe filename and an extension matching its detected format
- **AND** an existing asset is preserved by choosing a collision-free name

#### Scenario: Unsupported Capability
- **WHEN** a requested capability is unavailable for the selected model
- **THEN** the request fails clearly before submission rather than silently discarding settings

### Requirement: MIME-Based Asset Organization
Presentabot SHALL organize managed assets into images, audio, video, documents, and data subfolders based on detected media type and application-type purpose.

#### Scenario: Asset Import
- **WHEN** a supported file is imported with an incorrect filename extension
- **THEN** its actual supported format determines the destination and correct extension
- **AND** unused category directories need not exist

### Requirement: Minimal Durable Accounting
Presentabot SHALL persist only request identity, provider/model, status, resulting asset path, estimated/final usage-derived costs, counting period, and bookkeeping necessary for their consistency.

#### Scenario: Restart After Submission
- **WHEN** the process restarts after a request may have reached its provider
- **THEN** unresolved expenditure remains visible and the operation is not automatically resubmitted

#### Scenario: Duplicate Invocation
- **WHEN** an invocation repeats a persisted request identity
- **THEN** it returns the existing result or status without another paid submission

### Requirement: User-Resettable Counter
Presentabot SHALL show its own project usage-derived cost estimates and pending/uncertain amounts and provide an explicit user cost reset command.

#### Scenario: Counter Reset
- **WHEN** the user runs `presentabot cost reset`
- **THEN** a new counting period begins at zero without deleting prior accounting history
- **AND** existing in-flight requests remain associated with their original period

#### Scenario: External Agent Usage
- **WHEN** an external agent spends tokens outside Presentabot
- **THEN** that usage is not included or claimed to be tracked
