---
stage: Rewriting Workflow
---

# Rewriting Workflow

Correct existing commit messages to match the template.

## Process
1. **Identify Target Commits**: Use the results from Validation Mode or user input.
2. **Determine New Message**:
   - For each commit, analyze the file changes (`git show --name-only <hash>`).
   - Draft a new message following the template: `"<type>(<header>) -> <author>: <desc>"`
3. **Apply Changes**:
   - For the most recent commit: `git commit --amend -m "<new-message>"`
   - For older commits: Use `git rebase -i` and `reword` commands.
4. **Verification**: Verify that the "one file per commit" rule was already respected (or alert the user if a single commit contains multiple files, as this is harder to rewrite automatically).

## Warning
- Rewriting history can be destructive. Always warn the user and require confirmation unless in Autopilot mode with a clear directive.
