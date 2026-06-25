# Step: 06-outcome

## Description
Finalize the git-commit operation, report the summarized results, and handover to the user.

## Purpose
- Summarize actions taken.
- Display the final repository state.
- Ensure all skill conditions were met.

## Pre-stage Checkpoint
### Version Control
- Execute `git status` to verify the final tree state.

## Workflow
### Process
- **Summary Generation**: Create a concise summary (e.g., "Committed 3 files", "Validated 10 commits", "Rewrote 2 messages").
- **Details Compilation**: List the final commit messages applied or validated. Log any errors or skipped files.
- **Repository State**: Show the output of `git status`.

### Output Format
- Final summary text provided to the user.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking Outcome / Handover as completed.
### Version Control
- N/A
### Human in the Loop (HITL)
- Present the final summary to the user. Ask if any further git operations are needed before terminating the skill.
### Auto pilot
- Emit the final summary silently and terminate the skill workflow.
