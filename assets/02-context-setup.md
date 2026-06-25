---
stage: Context Setup
---

# Context Setup

Gather necessary information from the repository and environment.

## Data Collection
1. **Git Status**: Run `git status --short` to see staged and unstaged files.
2. **Author Identification**:
   - Check if a specific author was mentioned in the request.
   - Possible values: `human`, `codex`, `claude`, `gemini`.
   - Default: `agent`.
3. **Commit History (if Validate/Rewrite)**:
   - Identify the range of commits to inspect (e.g., `git log -n 5 --pretty=format:"%h %s"`).
4. **Style Guide**: Load `references/style-guide.md` for template reference.

## Constraints
- **One File per Commit**: If multiple files are staged for `Write` mode, they MUST be processed sequentially.
- **Unstaged Changes**: Remind the user if there are unstaged changes that might be relevant.

## Transition
- If mode == `Write` -> `assets/03-writing-workflow.md`
- If mode == `Validate` -> `assets/04-validation-workflow.md`
- If mode == `Rewrite` -> `assets/05-rewriting-workflow.md`
