---
description: "Analyze changes, generate commit message, and push to feature branch"
tools: ["read", "execute", "todo"]
---

# Commit and Push Changes

Analyze changes, generate a meaningful commit message, and push to a feature branch.

## Branch Information

Branch name (REQUIRED): ${input:branch-name:Enter the feature branch name (e.g., feature/my-feature)}

## Instructions

1. **Analyze Changes**
   - Run `git diff` to see what has changed
   - Review the scope and purpose of the changes

2. **Generate Commit Message**
   - Use conventional commit format (see Git Workflow in .github/copilot-instructions.md):
     * `feat:` - New features
     * `fix:` - Bug fixes
     * `chore:` - Maintenance tasks
     * `docs:` - Documentation changes
     * `test:` - Test additions or modifications
     * `refactor:` - Code refactoring
   - Create a descriptive message that explains what changed and why

3. **Branch Management**
   - Check if the branch exists: `git branch -a | grep ${branch-name}`
   - If it doesn't exist: `git checkout -b ${branch-name}`
   - If it exists: `git checkout ${branch-name}`
   - CRITICAL: ONLY use the user-provided branch name - DO NOT commit to main

4. **Commit and Push**
   - Stage all changes: `git add .`
   - Commit with the generated message: `git commit -m "message"`
   - Push to the branch: `git push origin ${branch-name}`

## Validation

- Confirm the branch name before proceeding
- Verify git operations complete successfully
- Report the final commit message and push status
- If pushing to a new branch, note that GitHub Actions may post next step instructions
