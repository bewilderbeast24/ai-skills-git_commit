# Step: 03a-writing-workflow

## Description
Execute the "one file per commit" logic with structured messages for files staged.

## Purpose
- Process staged files individually.
- Construct the correct commit message format.
- Execute git commits locally.

## Pre-stage Checkpoint
### Version Control
- Check `git status` to retrieve the staged files list.

## Workflow
### Process
- For each file staged for commit:
  - **Unstage All**: `git reset` (to ensure control over the index).
  - **Stage Single File**: `git add <file-path>`.
  - **Analyze Change**:
    - Use identified `CONTEXT` and `VERSION`.
    - Determine `type` (e.g., feat, docs, tests, fix, refactor, deprecate, branch).
    - Determine `scope` (e.g., "UI Button", "User Auth").
    - Draft `description` (max 2 lines).
  - **Construct Message**:
    - Template: `"[CONTEXT:VERSION] type(scope) -> author: description"`
  - **Verify Against Requirements**:
    - Only 1 file staged? Yes.
    - Author correct? Yes.
    - Message structure correct? Yes.

### Output Format
- Executed commits in the local git repository.

## Post-stage Checkpoint
### Progress Tracking
Update `.agents/skills-diary/git-commit/[<instance-name>]/checklist.md` by marking the Execute Mode phase as completed.
### Version Control
- `git commit -m "<structured-message>"`
### Human in the Loop (HITL)
- Present the drafted message to the user before committing, asking for confirmation. Upon confirmation, execute the commit. Repeat for all files. Once finished, transition to [04-outcome.md](04-outcome.md).
### Auto pilot
- Commit automatically if the structured message validates successfully. Once finished, transition to [04-outcome.md](04-outcome.md).
