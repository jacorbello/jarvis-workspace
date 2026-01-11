# Jarvis Deliverable Contract

This document defines the contract that all Jarvis outputs must follow.

## Core Principles

1. **Every run produces a deliverable** - No run completes without writing to jarvis-workspace
2. **No localhost links** - All outputs are Git artifacts with real, shareable paths
3. **Complete context** - Each deliverable stands alone with full information
4. **Session-scoped** - Responses always correlate to the correct session and run

## Deliverable Types

### Markdown (`deliverable.md`)
- Plans, analyses, documentation, reports
- Must include all sections inline (no "see previous" references)
- Use relative links to supporting files in the same run bundle

### Code (`deliverable.<ext>`)
- Source files, scripts, configurations
- Include inline comments explaining key decisions
- Supporting files go in the same run bundle

### Mixed (multiple files)
- Primary file is always `deliverable.md` with an index
- Supporting files listed in manifest.json

## Run Bundle Structure

```
runs/<session_id>/<run_id>/
├── manifest.json       # Required: metadata about this run
├── deliverable.md      # Primary output (or deliverable.<ext>)
└── [supporting files]  # Optional: code, images, data
```

## Manifest Requirements

Every run bundle MUST include a `manifest.json` with:
- `session_id`: The LibreChat conversation thread ID
- `run_id`: Unique identifier for this specific run (UUID)
- `timestamp`: ISO 8601 timestamp
- `status`: pending | in_progress | completed | failed
- `deliverable.type`: markdown | code | plan | analysis | mixed
- `deliverable.path`: Relative path to primary deliverable
- `deliverable.summary`: 1-3 sentence summary for chat display

## Response Format

When Jarvis completes a run, the chat response MUST be:

```
[Brief summary - 1-3 sentences]

Deliverable: runs/<session_id>/<run_id>/deliverable.md
```

The full content lives in jarvis-workspace. The chat only shows a summary + path.

## Forbidden Patterns

1. **No localhost URLs** - Never include `http://localhost:*` or `127.0.0.1:*`
2. **No ephemeral links** - No temporary URLs that expire
3. **No "see previous"** - Each deliverable must be complete
4. **No streaming partials** - Wait for complete output before writing

## Validation

Before a run is marked complete:
1. manifest.json validates against run_manifest.schema.json
2. deliverable file exists at the specified path
3. No localhost/ephemeral links in any file
4. Summary is present and concise

## Session Correlation

- `session_id` is stable for the entire LibreChat conversation
- `run_id` is unique per user message
- Responses MUST match the requesting session_id + run_id
- Mismatched responses are rejected
