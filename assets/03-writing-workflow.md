---
stage: Writing Workflow
---

# Writing Workflow

Execute the "one file per commit" logic with structured messages.

## Implementation Steps
For each file staged for commit:

1. **Unstage All**: `git reset` (to ensure we control exactly what is added).
2. **Stage Single File**: `git add <file-path>`.
3. **Analyze Change**:
   - Determine `<type-of-addition>` (feat, docs, tests, plan, fix, refactor, etc.).
   - Determine `<one-phrase-header-for-addition>` (e.g., "UI Button", "User Auth", "API Endpoint").
   - Draft `<one-line-description-for-addition>` (max 2 lines).
4. **Construct Message**:
   - Template: `"<type-of-addition>(<one-phrase-header-for-addition>) -> <author>: <one-line-description-for-addition>"`
5. **Verify Against Requirements**:
   - Only 1 file staged? Yes.
   - Author correct? Yes.
   - Message structure correct? Yes.
6. **Commit**: `git commit -m "<structured-message>"`.
7. **Repeat**: Move to the next file in the original staged list.

## Validation
- Ensure no "batch" commits are made.
- If Autopilot is OFF, present the message to the user before committing.
