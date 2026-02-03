# GitHub Copilot Instructions - TODO Application

## Project Context

This is a full-stack TODO application with:
- **Frontend**: React-based user interface
- **Backend**: Express.js REST API
- **Development Approach**: Iterative, feedback-driven development
- **Current Phase**: Backend stabilization and frontend feature completion

## Documentation References

Refer to these documents to understand the project structure and standards:

- [docs/project-overview.md](../docs/project-overview.md) - Architecture, tech stack, and project structure
- [docs/testing-guidelines.md](../docs/testing-guidelines.md) - Test patterns and standards
- [docs/workflow-patterns.md](../docs/workflow-patterns.md) - Development workflow guidance

## Development Principles

Follow these core principles for all development work:

- **Test-Driven Development**: Follow the Red-Green-Refactor cycle
  - Write tests FIRST (Red)
  - Implement code to pass tests (Green)
  - Refactor for quality (Refactor)
- **Incremental Changes**: Make small, testable modifications one at a time
- **Systematic Debugging**: Use test failures as guides to identify and fix issues
- **Validation Before Commit**: Ensure all tests pass and no lint errors exist before committing

## Testing Scope

This project uses **unit tests and integration tests ONLY**:

### Testing Tools
- **Backend**: Jest + Supertest for API endpoint testing
- **Frontend**: React Testing Library for component unit/integration tests
- **UI Verification**: Manual browser testing for full user interface flows

### Testing Restrictions
**DO NOT** suggest or implement:
- End-to-end (e2e) test frameworks (Playwright, Cypress, Selenium)
- Browser automation tools
- Full-stack automated testing

**Reason**: This lab focuses on unit and integration testing patterns without the complexity of e2e testing infrastructure.

### Testing Approach by Context

**Backend API Changes**:
- Write Jest tests FIRST before implementing functionality
- Follow RED-GREEN-REFACTOR: Test fails → Implement → Test passes → Refactor

**Frontend Component Features**:
- Write React Testing Library tests FIRST for component behavior
- Follow RED-GREEN-REFACTOR: Test fails → Implement → Test passes → Refactor
- Follow up with manual browser testing to verify full UI flows

**This is true TDD**: Always write the test first, then write code to make it pass.

## Workflow Patterns

Follow these established workflows for different types of work:

### 1. TDD Workflow (Test-Driven Development)
1. Write or fix tests FIRST
2. Run tests and verify they FAIL (Red)
3. Implement minimum code to pass tests (Green)
4. Verify tests PASS
5. Refactor code for quality
6. Re-run tests to ensure refactor didn't break anything

### 2. Code Quality Workflow
1. Run linter to identify issues
2. Categorize issues by type and severity
3. Fix issues systematically (one category at a time)
4. Re-validate with linter after each batch of fixes
5. Confirm all issues resolved

### 3. Integration Workflow
1. Identify the issue or requirement
2. Debug to understand root cause
3. Write tests to cover the scenario
4. Implement the fix or feature
5. Verify end-to-end functionality

## Agent Usage

Use specialized agents for specific types of work:

### tdd-developer Agent
Use for:
- Writing new tests
- Fixing failing tests
- Implementing features using Red-Green-Refactor cycle
- Test-driven bug fixes

### code-reviewer Agent
Use for:
- Addressing lint errors
- Code quality improvements
- Refactoring suggestions
- Code review and best practices

## Memory System

This project uses a working memory system to track patterns, decisions, and lessons learned during development:

- **Persistent Memory**: This file (`.github/copilot-instructions.md`) contains foundational principles and workflows
- **Working Memory**: `.github/memory/` directory contains discoveries and patterns
- **During active development**: Take notes in `.github/memory/scratch/working-notes.md` (not committed)
- **At end of session**: Summarize key findings into `.github/memory/session-notes.md` (committed)
- **Document recurring code patterns**: Add to `.github/memory/patterns-discovered.md` (committed)
- **Reference these files**: When providing context-aware suggestions

See [.github/memory/README.md](memory/README.md) for detailed usage instructions.

## Workflow Utilities

### GitHub CLI Commands

Use these commands to interact with GitHub issues and track work:

```bash
# List all open issues
gh issue list --state open

# View details of a specific issue
gh issue view <issue-number>

# View issue with all comments
gh issue view <issue-number> --comments
```

**Note**: 
- The main exercise issue will have "Exercise:" in the title
- Exercise steps are posted as comments on the main issue
- Use these commands when `/execute-step` or `/validate-step` prompts are invoked

## Git Workflow

### Conventional Commits

Use conventional commit format for all commits:

- `feat:` - New features
- `fix:` - Bug fixes
- `chore:` - Maintenance tasks
- `docs:` - Documentation changes
- `test:` - Test additions or modifications
- `refactor:` - Code refactoring without feature changes
- `style:` - Code formatting changes

**Example**: `feat: add delete button to todo items`

### Branch Strategy

- **Feature branches**: `feature/<descriptive-name>`
- **Bug fix branches**: `fix/<descriptive-name>`
- **Always branch from**: `main`

### Commit and Push Workflow

1. **Stage all changes**: `git add .`
2. **Commit with conventional format**: `git commit -m "feat: description"`
3. **Push to correct branch**: `git push origin <branch-name>`

**Important**: Always verify you're on the correct branch before committing and pushing.
