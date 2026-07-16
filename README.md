# Git Commands Plugin

Streamline your git workflow with simple commands for committing, pushing, and merging branches.

## Overview

The Git Commands Plugin automates common git operations, reducing context switching and manual command execution. Instead of running multiple git commands, use a single slash command to handle your entire workflow.

## Commands

### `/git-commit`

Creates a git commit with an automatically generated commit message based on staged and unstaged changes.

**What it does:**
1. Analyzes current git status
2. Reviews both staged and unstaged changes
3. Examines recent commit messages to match your repository's style
4. Drafts an appropriate commit message
5. Stages relevant files
6. Creates the commit

**Usage:**
```bash
/git-commit
```

**Features:**
- Automatically drafts commit messages that match your repo's style
- Follows conventional commit practices
- Avoids committing files with secrets (.env, credentials.json)
- When committing on the `dev` branch, appends `#relese#` to the end of the commit message to trigger auto-upgrade

### `/git-push`

Commits changes and pushes the current branch to origin in one step.

**What it does:**
1. Stages and commits changes with an appropriate message
2. Pushes the current branch to origin (sets upstream tracking if needed)

**Usage:**
```bash
/git-push
```

**Features:**
- Commits and pushes in a single step
- When committing on the `dev` branch, appends `#relese#` to the end of the commit message to trigger auto-upgrade

### `/git-merge`

Merges the current branch into a specified target branch.

**What it does:**
1. Records the current branch (source)
2. Checks out the target branch (provided as an argument)
3. Merges the source branch into the target
4. Pushes the target branch to origin
5. Switches back to the original source branch

**Usage:**
```bash
/git-merge <target-branch>
```

**Example:**
```bash
# Merge the current branch (e.g., dev) into main
/git-merge main
```

**Features:**
- Merges the current branch into the target branch given as an argument
- Pushes the target branch after merging
- Returns to the original branch when done
- Stops and reports on merge conflicts instead of forcing

## The `#relese#` trigger

When a commit is made on the `dev` branch (via `/git-commit` or `/git-push`), the commit message ends with `#relese#`. This marker is used by CI to trigger an automatic upgrade/release. Commits on other branches do not include the marker.

## Installation

This is a Claude Code plugin. Enable the `git-commands` directory as a plugin in Claude Code, and the `/git-commit`, `/git-push`, and `/git-merge` slash commands become available.

Alternatively, copy the files from `commands/` directly into your project's `.claude/commands/` directory to use them as loose custom commands.

## Requirements

- Git must be installed and configured
- Repository must be a git repository with a remote named `origin` (for `/git-push` and `/git-merge`)

## Troubleshooting

### `/git-commit` creates empty commit
- Ensure you have unstaged or staged changes
- Run `git status` to verify changes exist

### `/git-push` fails to push
- Ensure the repository has a remote named `origin`
- Run `git remote -v` to verify

### `/git-merge` reports conflicts
- Resolve the conflicts manually, then re-run `/git-merge`
- The command stops without forcing on conflicts

## Author

sumtime

## Version

1.0.0
