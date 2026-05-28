# Git Commit Style Guide

## Commit Requirements
- **One File per Commit**: Each commit MUST contain exactly one file. Batch commits are strictly forbidden.

## Message Template
`"<type-of-addition>(<one-phrase-header-for-addition>) -> <author>: <one-line-description-for-addition>"`

## Placeholders
- `<type-of-addition>`: The contribution type.
  - Examples: `feat`, `docs`, `tests`, `plan`, `fix`, `refactor`, `style`, `chore`.
- `<one-phrase-header-for-addition>`: A brief heading for the file or change.
  - Examples: `UI Button`, `User Auth`, `Data Model`.
- `<author>`: Responsibility for the commit.
  - Possible values: `human`, `codex`, `claude`, `gemini`, `agent` (default).
- `<one-line-description-for-addition>`: A brief description (max 1.5 - 2 lines).

## Regex for Validation
`^(\w+)\(([^)]+)\) -> (\w+): (.+)$`
