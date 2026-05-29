# Git Commit Style Guide

## Commit Requirements
- **One File per Commit**: Each commit MUST contain exactly one file. Batch commits are strictly forbidden.

## Message Template
`"[CONTEXT:VERSION] type(scope) -> author: description"`

## Placeholders
- `CONTEXT`: The project phase, milestone, or high-level goal (e.g., `BASIC`, `WORKFLOW-EXPANSION`, `MERGE`).
- `VERSION`: The version number, PR reference, or sub-milestone (e.g., `1.0`, `1.1`, `#2`).
- `type`: The contribution type.
  - Examples: `feat`, `docs`, `tests`, `fix`, `refactor`, `style`, `chore`, `deprecate`, `branch`.
- `scope`: A brief heading for the file or change in parentheses.
  - Examples: `UI Button`, `User Auth`, `Data Model`, `stage-01`, `README`.
- `author`: Responsibility for the commit.
  - Possible values: `human`, `codex`, `claude`, `gemini`, `agent` (default), or a specific username.
- `description`: A brief description (max 1.5 - 2 lines).

## Regex for Validation
`^\[([^:]+):([^\]]+)\] (\w+)\(([^)]+)\) -> (\w+): (.+)$`
