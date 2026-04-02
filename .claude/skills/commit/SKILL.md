---
name: commit
description: Suggest a Conventional Commits message for current git changes and identify which files to stage
---

Run `git diff --stat` and `git status` to see which files changed. Only run `git diff -- <file>` on specific files if the stat alone isn't enough to understand the change. Use the conversation history to understand the motive behind the change — prefer that over re-reading the full diff.

1. Suggest a commit message following Conventional Commits format:

```
<type>(<scope>): <short summary>

[optional body — explain *why*, not *what*]
```

Types: feat, fix, docs, style, refactor, perf, test, chore, ci, revert. Subject ≤ 72 chars, imperative mood, no period. Body only if motive isn't clear from subject.

2. List only the files directly relevant to this change. Unrelated changes stay unstaged for separate commits.

Output the commit message in a code block, then the file list.

3. Ask: "Commit with this message? (yes/no)"

4. On yes: stage the listed files and commit. On no: stop.
