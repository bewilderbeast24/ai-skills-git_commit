# Step: 01-mode-selection

## Description
Identify the user's intent to determine the operational path for git-commit.

## Purpose
- Prompt the user to select one of the three operational modes: Write, Validate, or Rewrite.
- Capture this selection in a machine-readable format.

## Pre-stage Checkpoint
### Version Control
- Check `git status` to ensure you are in a valid repository.
- If repo is not a git repository, make it one by initializing a repo using `git init`.

## Workflow
### Process
- If the intent is unclear from the user instructions, use `ask_user` with a choice question to capture the desired mode:
  - **Label**: `Write`, **Description**: `Create new commits for staged files.`
  - **Label**: `Validate`, **Description**: `Check existing commit messages for compliance.`
  - **Label**: `Rewrite`, **Description**: `Update existing messages to match the template.`
- Store the instruction type / selection in the session context.

### Output Format
- Selected Mode state variable in memory.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking the Mode Selection phase as completed.
### Version Control
- N/A
### Human in the Loop (HITL)
- Wait for the user to make a choice in the `ask_user` prompt. Transition to [02-context-setup.md](02-context-setup.md) based on user input.
### Auto pilot
- If autopilot mode is requested and intent is extremely clear, select the mode automatically without prompt.
