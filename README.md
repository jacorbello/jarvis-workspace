# Jarvis Workspace

This repository serves as a controlled workspace for Jarvis AI assistant to draft, stage, and propose changes through a human-gated workflow.

## Directory Structure

```
jarvis-workspace/
├── docs/           # Documentation
│   ├── system/        # System documentation
│   ├── architecture/  # Architecture docs
│   ├── runbooks/      # Operational runbooks
│   └── notes/         # General notes
├── plans/          # Planning documents
│   ├── proposals/     # Improvement proposals
│   ├── roadmaps/      # Project roadmaps
│   └── migrations/    # Migration plans
├── code/           # Code artifacts (Phase 3+)
│   ├── tools/         # Utility tools
│   ├── experiments/   # Experimental code
│   └── prototypes/    # Prototypes
├── prompts/        # Prompt templates
│   ├── agents/        # Agent personas
│   └── templates/     # Reusable templates
└── adr/            # Architecture Decision Records
```

## Workflow

1. Jarvis generates content and requests approval to stage
2. Changes are committed to a feature branch
3. PR is opened for human review
4. Human merges after review

## Allowlisted Paths (Phase 1)

- `docs/**`
- `plans/**`
- `prompts/**`
- `adr/**`

## Security

- All writes go through Tools Gateway with validation
- Secret scanning on all commits
- Human approval required for staging and PR creation
