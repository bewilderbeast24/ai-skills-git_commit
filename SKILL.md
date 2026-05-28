---
name: git-commit
description: Ensures proper git commit message structure, including writing, validating, and rewriting messages.
---

## Skill Overview
The `git-commit` skill is designed to maintain a strict and consistent git commit message structure across a repository. It enforces a "one file per commit" rule and follows a specific template for messages: `<type-of-addition>(<one-phrase-header-for-addition>) -> <author>: <one-line-description-for-addition>`.

## Workflow Sequence
The skill operates in one of three modes: Write, Validate, or Rewrite.

| Stage | Description | Workflow | Inputs | Outputs |
| :--- | :--- | :--- | :--- | :--- |
| **1. Mode Selection** | Select operation: Write, Validate, or Rewrite. | [01-mode-selection.md](assets/01-mode-selection.md) | User Choice | Selection state |
| **2. Context Setup** | Identify files, author, and commit context. | [02-context-setup.md](assets/02-context-setup.md) | Git status/logs | Staged files, author |
| **3a. Writing Mode** | Generate structured messages for staged files. | [03-writing-workflow.md](assets/03-writing-workflow.md) | File changes | Commit messages |
| **3b. Validation Mode** | Check existing messages against the template. | [04-validation-workflow.md](assets/04-validation-workflow.md) | Commit history | Validation report |
| **3c. Rewriting Mode** | Update existing messages to the new structure. | [05-rewriting-workflow.md](assets/05-rewriting-workflow.md) | Existing commits | Rebased commits |
| **4. Outcome** | Execute commit, report validation, or confirm rewrite. | [06-outcome.md](assets/06-outcome.md) | Processed items | Final repo state |

## Pre-stage Checkpoint
### Workflow Selection
Identify the appropriate mode based on the user's immediate need.

### HITL / Autopilot
- **HITL (Default)**: Confirm generated messages or validation results before applying changes.
- **Autopilot**: Automatically commit or rewrite if the generated content meets the structure criteria.

## Core Operation Flow
### 1. Mode Selection
Use `ask_user` to determine the mode:
- **Write**: Create new commits for staged changes.
- **Validate**: Audit recent commits for compliance.
- **Rewrite**: Correct the structure of existing commits.

### 2. Context Setup
Analyze the repository state:
- For **Write**: List staged and unstaged changes. Remind user of the "one file per commit" rule.
- For **Validate/Rewrite**: Determine the range of commits (e.g., last 5, current branch).
- Identify **Author**: Default to `agent` if not specified or detected.

### 3. Mode Execution
Refer to the specific asset file for the selected mode logic:
- **Write**: Iterate through staged files. For each file, determine `<type-of-addition>` and `<one-phrase-header-for-addition>`.
- **Validate**: Match commit messages against the regex pattern for the template.
- **Rewrite**: Interactive rebase or commit --amend to update messages.

### 4. Outcome
Present final changes, log successful commits, or list validation failures.

## Handover & Confirmation
- **No Placeholders**: All commit messages must be fully populated.
- **One File per Commit**: Enforce this strictly during the Write mode.
- **Template Adherence**: All output must match the `<type>(<header>) -> <author>: <desc>` format.

## Additional Instructions
None
