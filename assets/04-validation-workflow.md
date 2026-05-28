---
stage: Validation Workflow
---

# Validation Workflow

Audit existing commit messages for template compliance.

## Audit Steps
1. **Fetch Commits**: Retrieve the target commits (e.g., `git log -n 10 --format="%H %s"`).
2. **Match Template**: Check if each message matches:
   `^(\w+)\(([^)]+)\) -> (\w+): (.+)$`
3. **Verify Placeholders**:
   - `<type>`: Is it a recognized type?
   - `<header>`: Is it a brief phrase?
   - `<author>`: Is it one of `human`, `codex`, `claude`, `gemini`, `agent`?
   - `<desc>`: Is it within the length limit?
4. **Report Results**:
   - **Valid**: List commits that pass.
   - **Invalid**: List commits that fail, highlighting the specific violation.

## Transition
- Provide the user an option to transition to **Rewriting Mode** for invalid commits.
