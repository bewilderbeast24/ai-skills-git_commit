---
stage: Mode Selection
---

# Mode Selection

Identify the user's intent to determine the operational path.

## Selection Process
1. Use `ask_user` with a choice question to capture the desired mode:
   - **Label**: `Write`, **Description**: `Create new commits for staged files.`
   - **Label**: `Validate`, **Description**: `Check existing commit messages for compliance.`
   - **Label**: `Rewrite`, **Description**: `Update existing messages to match the template.`

2. Store the selection in the session context.

3. Transition to `assets/02-context-setup.md`.
