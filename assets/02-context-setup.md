# Step: 02-context-setup

## Description
Gather necessary information from the repository and environment based on the selected mode.

## Purpose
- Retrieve current staged files and author information.
- Fetch commit history if validating or rewriting.
- Load the specific style guide rules.

## Pre-stage Checkpoint
### Version Control
- Run `git status --short` to evaluate staged/unstaged changes.

## Workflow
### Process
- **Data Collection**:
  - **Author Identification**: Check if a specific author name was mentioned (`human`, `codex`, `claude`, `gemini`). Default is `agent`.
  - **Commit History**: If Mode is Validate/Rewrite, identify the range of commits to inspect (e.g., `git log -n 5 --pretty=format:"%h %s"`).
  - Load `references/style-guide.md` for template details.
- **Constraints Application**:
  - Remind user if there are unstaged changes.
  - Inform user about "One File per Commit" constraint if in Write mode.

### Output Format
- Context dictionary loaded in agent memory.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking Context Setup as completed.
### Version Control
- N/A
### Human in the Loop (HITL)
- Confirm context is correct with the user before proceeding to execution if requested, otherwise proceed to the mode-specific execution step.
### Auto pilot
- Automatically transition to [03a-writing-workflow.md](03a-writing-workflow.md), [03b-validation-workflow.md](03b-validation-workflow.md), or [03v-rewriting-workflow.md](03c-rewriting-workflow.md) depending on the selected mode.
