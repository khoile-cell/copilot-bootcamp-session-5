---
description: "Execute instructions from the current GitHub Issue step"
agent: "tdd-developer"
tools: ["search", "read", "edit", "execute", "web", "todo"]
---

# Execute Step Instructions

Execute the activities from a GitHub Issue step systematically.

## Step to Execute

Issue number (optional): ${input:issue-number:Enter issue number or leave blank to auto-detect}

## Instructions

1. **Find the Exercise Issue**
   - If issue number not provided, use `gh issue list --state open` to find the issue with "Exercise:" in the title
   - Use the Workflow Utilities commands from project instructions (.github/copilot-instructions.md)

2. **Get Issue Content**
   - Run `gh issue view <issue-number> --comments` to get the full issue with all comments
   - Parse the latest step instructions from the comments

3. **Execute Activities Systematically**
   - Find each `⌨️ Activity:` section in the step
   - Execute each activity in order
   - Follow all instructions precisely
   - Apply testing scope constraints from project instructions:
     * NO e2e test frameworks (Playwright, Cypress, Selenium)
     * Use existing test infrastructure (Jest, React Testing Library)
     * Recommend manual browser testing for full UI flows

4. **Completion**
   - DO NOT commit or push changes - that's the job of `/commit-and-push`
   - After completing all activities, inform the user to run `/validate-step`
   - Report what was accomplished

## Key Principles

- Work systematically through each activity
- Follow TDD principles (Red-Green-Refactor)
- Make incremental, testable changes
- Run tests frequently to validate progress
- Keep testing scope to unit and integration tests only
