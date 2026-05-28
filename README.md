# AI Git Commit Skill

A specialized AI-driven skill for the Gemini CLI designed to enforce and automate standardized git commit message structures. This skill ensures repository consistency by implementing a strict "one file per commit" policy and a specific, parsable message template across all development workflows.

## Overview

The AI Git Commit Skill provides a robust framework for managing commit history. It operates through three primary modes—Write, Validate, and Rewrite—to ensure that every addition to the codebase is documented according to the project's architectural standards. By automating the generation and verification of commit messages, it reduces cognitive load for developers while maintaining high-quality version control metadata.

## Core Features

### 1. Standardized Message Template
All commit messages generated or validated by this skill must adhere to the following structure:
`type-of-addition(one-phrase-header-for-addition) -> author: one-line-description-for-addition`

### 2. "One File Per Commit" Enforcement
To maintain a granular and easily reversible history, the skill strictly enforces a policy where each commit contains changes to exactly one file. Batch commits are automatically decomposed into individual commits during the Write workflow.

### 3. Multi-Mode Operation
*   **Write Mode**: Automatically generates structured commit messages for staged files and executes individual commits for each file.
*   **Validate Mode**: Audits existing commit history against the defined regex pattern to identify non-compliant messages.
*   **Rewrite Mode**: Facilitates the correction of existing commit messages using interactive rebase or amendment tools to bring them into compliance.

## Installation

To install this skill into your local environment, use the following command:

```bash
git clone https://github.com/bewilderbeast24/ai-skills-git_commit.git git-commit
```

## Workflow Sequence

The skill follows a structured execution path to ensure data integrity and user control.

### Stage 1: Mode Selection
The agent identifies the required operation (Write, Validate, or Rewrite) based on user intent or direct inquiry. Users can choose between Human-In-The-Loop (HITL) for manual approval or Autopilot for automated execution.

### Stage 2: Context Setup
The skill analyzes the current repository state, including git status, staged changes, and commit logs, to establish the necessary context for the selected mode.

### Stage 3: Execution
*   **Writing**: The agent iterates through staged files, determining the appropriate contribution type and header for each, and generates the final message.
*   **Validation**: The agent performs a regex-based audit of the commit history.
*   **Rewriting**: The agent initiates the necessary git commands to update historical messages.

### Stage 4: Outcome and Reporting
The skill provides a summary of all actions taken, including successful commits, validation reports, or confirmed rewrites.

## Style Guide Specifications

### Contribution Types (`type-of-addition`)
The following types are recognized:
*   `feat`: New features or functionality.
*   `docs`: Documentation changes.
*   `tests`: Adding or modifying tests.
*   `plan`: Architectural planning or design documents.
*   `fix`: Bug fixes.
*   `refactor`: Code changes that neither fix a bug nor add a feature.
*   `style`: Changes that do not affect the meaning of the code (white-space, formatting, etc.).
*   `chore`: Updating build tasks, package manager configs, etc.

### Author Identifiers
The `author` field designates the entity responsible for the commit:
*   `human`: Manual developer contribution.
*   `codex`: AI-assisted generation.
*   `gemini`: Gemini-specific contributions.
*   `agent`: General AI agent (default).

### Validation Regex
Compliance is verified using the following regular expression:
`^(\w+)\(([^)]+)\) -> (\w+): (.+)$`

## Technical Implementation

### Directory Structure
*   `assets/`: Contains detailed workflow instructions and prompts for each stage of execution.
*   `references/`: Stores the style guide and operational checklists.
*   `SKILL.md`: The primary definition file for the Gemini CLI skill.

### Operational Logging
All temporary scripts and execution data are stored within the `.agents/skills-diary/` directory, organized by timestamp and instance name, ensuring a transparent audit trail of the skill's activities.

## License
This project is licensed under the terms provided in the `LICENSE` file.
