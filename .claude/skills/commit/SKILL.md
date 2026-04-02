---
name: commit
description: Suggest a Conventional Commits message for current git changes and identify which files to stage
---

Run `git diff --stat` and `git status`. Use conversation history for motive. Suggest a Conventional Commits message and list relevant files to stage. Use AskUserQuestion ("Commit?" / "Yes" / "No"). On yes, stage and commit.
