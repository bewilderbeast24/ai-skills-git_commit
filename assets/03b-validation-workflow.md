# Step: 03b-validation-workflow

## Description
Audit existing commit messages in the repository to ensure template compliance.

## Purpose
- Retrieve recent commits.
- Match them against the enforced regex template.
- Identify conforming and non-conforming commits.

## Pre-stage Checkpoint
### Version Control
- Determine log range and execute `git log -n <limit> --format="%H %s"`.

## Workflow
### Process
- **Fetch Commits**: Retrieve the target commits.
- **Match Template**: Check if each message matches the regex: `^\[([^:]+):([^\]]+)\] (\w+)\(([^)]+)\) -> (\w+): (.+)$`
- **Verify Placeholders**:
  - `CONTEXT`: Must be a recognized context.
  - `VERSION`: Must be a recognized version.
  - `type`: Must be a recognized type.
  - `scope`: Must be a brief phrase.
  - `author`: Must be one of `human`, `codex`, `claude`, `gemini`, `agent`, or a recognized author.
  - `description`: Must be within length limits.
- **Report Results**:
  - Valid commits.
  - Invalid commits, highlighting the violation reason.

### Output Format
- Validation report text buffer.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking the Execute Mode phase as completed.
### Version Control
- N/A
### Human in the Loop (HITL)
- Output the report to the user. Provide an option to transition to [03c-rewriting-workflow.md](03c-rewriting-workflow.md) to fix invalid commits, or transition to [04-outcome.md](04-outcome.md) to complete.
### Auto pilot
- Log the validation report and transition to [04-outcome.md](04-outcome.md).
