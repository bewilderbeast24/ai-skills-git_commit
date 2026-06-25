---
name: git-commit
description: Ensures proper git commit message structure, including writing, validating, and rewriting messages.
---

## Skill Overview
The `git-commit` skill is designed to maintain a strict and consistent git commit message structure across a repository. It enforces a "one file per commit" rule and follows a specific template for messages: `[CONTEXT:VERSION] type(scope) -> author: description`.

## Workflow Sequence
The skill operates in one of three modes: Write, Validate, or Rewrite.

| Stage | Description | Workflow | Inputs | Outputs |
| :--- | :--- | :--- | :--- | :--- |
| **1. Mode Selection** | Select operation: Write, Validate, or Rewrite. | [01-mode-selection.md](assets/01-mode-selection.md) | User Choice | Selection state |
| **2. Context Setup** | Identify files, author, context, version, and commit context. | [02-context-setup.md](assets/02-context-setup.md) | Git status/logs | Staged files, author, context, version |
| **3a. Writing Workflow** | Generate structured messages for staged files. | [03a-writing-workflow.md](assets/03a-writing-workflow.md) | File changes | Commit messages |
| **3b. Validation Workflow** | Check existing messages against the template. | [03b-validation-workflow.md](assets/03b-validation-workflow.md) | Commit history | Validation report |
| **3c. Rewriting Workflow** | Update existing messages to the new structure. | [03c-rewriting-workflow.md](assets/03c-rewriting-workflow.md) | Existing commits | Rebased commits |
| **4. Outcome** | Execute commit, report validation, or confirm rewrite. | [04-outcome.md](assets/04-outcome.md) | Processed items | Final repo state |

## Pre-stage Checkpoint
### Workflow Selection
Identify the appropriate mode based on the user's immediate need via parsing user intent or where unclear or in doubt from prompt, using `ask_user` tool.

### HITL / Autopilot
- **HITL (Default)**: Confirm generated messages or validation results before applying changes. **The agent must pause and present details for approval**.
- **Autopilot**: Automatically commit or rewrite if the generated content meets the structure criteria without waiting for confirmation.

### Checklist Integration
Before starting, ensure `references/checklist.md` is initialized and stored in `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md`. 

**Check off items as you complete stages.

## Core Operation Flow

### Stages
1. **Mode Selection**: Present options to the user and capture choice among `Write`, `Validate`, or `Rewrite` either by parsing user intent from prompt or by using `ask_user` tool. Update checklist.

    1.1. **Execution: Mode Write**
    - Iterate through staged files. For each file, determine `CONTEXT`, `VERSION`, `type`, and `scope`.
    - Enforce "one file per commit".

    1.2. **Execution: Mode Validate**
    - Match commit messages against the regex pattern for the template.

    1.3. **Execution: Mode Rewrite**
    - Interactive rebase or commit --amend to update messages.

2. **Context Setup**: Load repository state and style guide. Update checklist.

3. **Outcome**: Present final changes, log successful commits, or list validation failures. Update checklist.


## Handover & Confirmation
- **No Placeholders**: All commit messages must be fully populated.
- **One File per Commit**: Enforce this strictly during the Write mode.
- **Template Adherence**: All output must match the `[CONTEXT:VERSION] type(scope) -> author: description` format.
- **Summarise**: Display a summary of the outcome before ending the turn.

## Additional Instructions
All temporary scripts generated while execution of skills (scripts which will be deleted after execution) will be written in `.agents/skills-diary/temp-scripts/<timestamp>/` as directory.
