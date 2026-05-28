# Step: 05-rewriting-workflow

## Description
Correct existing invalid commit messages to strictly match the required template format.

## Purpose
- Identify non-compliant commits.
- Generate corrected messages.
- Rewrite git history safely.

## Pre-stage Checkpoint
### Version Control
- Verify the current branch status before rebasing.

## Workflow
### Process
- **Identify Target Commits**: Load commits from Validation Mode or user specification.
- **Determine New Message**:
  - Analyze the file changes via `git show --name-only <hash>`.
  - Draft a new message: `"<type>(<header>) -> <author>: <desc>"`
- **Apply Changes**:
  - For the most recent commit: Formulate `git commit --amend -m "<new-message>"`.
  - For older commits: Formulate an interactive rebase (`git rebase -i`) using `reword`.
- **Verification**: Ensure the target commit contains only one file. Warn if multiple files are present.

### Output Format
- Modified git history.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking the Execute Mode phase as completed.
### Version Control
- `git commit --amend` or `git rebase -i`
### Human in the Loop (HITL)
- Rewriting history is destructive. Present the proposed new messages and git commands to the user and wait for explicit confirmation before executing. Once done, transition to [04-outcome.md](04-outcome.md).
### Auto pilot
- Execute the amend or rebase automatically, provided that the new message is fully compliant. Once done, transition to [04-outcome.md](04-outcome.md).
