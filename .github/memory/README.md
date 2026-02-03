# Working Memory System

## Purpose

This memory system tracks patterns, decisions, and lessons learned during development. Think of it as the project's development journal - a place where discoveries are documented so they can inform future work and help AI assistants provide better, context-aware suggestions.

## Two Types of Memory

### 1. Persistent Memory
**Location**: `.github/copilot-instructions.md`

**Contains**:
- Foundational development principles
- Established workflows and patterns
- Core project architecture decisions
- Testing and quality standards

**When to update**: When you establish new project-wide standards or fundamental workflows that should always be followed.

### 2. Working Memory
**Location**: `.github/memory/`

**Contains**:
- Session-specific discoveries
- Emergent code patterns
- Debugging insights
- Active work notes

**When to update**: Throughout development as you learn and discover new patterns.

## Directory Structure

```
.github/memory/
├── README.md                    # This file - explains the system
├── session-notes.md             # Historical session summaries (committed)
├── patterns-discovered.md       # Accumulated code patterns (committed)
└── scratch/
    ├── .gitignore              # Ignores all files in scratch/
    └── working-notes.md        # Active session notes (NOT committed)
```

### File Purposes

#### `session-notes.md` (Committed to Git)
- **Purpose**: Historical record of completed development sessions
- **Content**: Summaries of what was accomplished, key findings, and outcomes
- **Updated**: At the END of each development session
- **Audience**: Future developers (including your future self) and AI assistants

#### `patterns-discovered.md` (Committed to Git)
- **Purpose**: Document recurring code patterns and architectural decisions
- **Content**: Pattern templates with context, problems, solutions, and examples
- **Updated**: When you discover a reusable pattern or make an architectural decision
- **Audience**: Developers implementing new features and AI assistants generating code

#### `scratch/working-notes.md` (NOT Committed)
- **Purpose**: Active thinking space for current work
- **Content**: Raw notes, findings, blockers, and next steps for the current session
- **Updated**: Throughout your active development session
- **Audience**: Just you and AI during the current session
- **Important**: This file is intentionally NOT committed to keep git history clean

## How to Use During Development Workflows

### During TDD (Test-Driven Development)

1. **Starting a TDD session**:
   - Open `scratch/working-notes.md`
   - Document your current task and approach

2. **As tests fail/pass**:
   - Note unexpected failures in "Key Findings"
   - Document why certain test patterns work in "Decisions Made"

3. **When discovering patterns**:
   - If a test pattern proves useful, add it to `patterns-discovered.md`
   - Example: "Service initialization pattern", "Error handling in async tests"

4. **End of session**:
   - Summarize the TDD work in `session-notes.md`
   - Clear or update `scratch/working-notes.md` for next session

### During Linting and Code Quality Workflows

1. **Before fixing lint errors**:
   - Note the types and frequency of errors in `scratch/working-notes.md`

2. **While fixing systematically**:
   - Document any patterns in errors (e.g., "Always forget to handle null returns")
   - Note decisions about code style preferences

3. **After cleanup**:
   - Add recurring error patterns to `patterns-discovered.md`
   - Update session notes with quality improvements made

### During Debugging

1. **When encountering a bug**:
   - Document symptoms in `scratch/working-notes.md` → "Blockers"
   - Note hypotheses and tests in "Approach"

2. **As you debug**:
   - Track findings in "Key Findings"
   - Document the root cause when found

3. **After fixing**:
   - Add the bug pattern to `patterns-discovered.md` if it's likely to recur
   - Summarize the debugging process in `session-notes.md`

## How AI Reads and Applies These Patterns

When you interact with GitHub Copilot or other AI assistants:

1. **AI reads persistent memory first**:
   - Understands project standards from `.github/copilot-instructions.md`
   - Learns established workflows and principles

2. **AI reads working memory for context**:
   - Reviews `patterns-discovered.md` for project-specific code patterns
   - Checks `session-notes.md` for historical context
   - References `scratch/working-notes.md` for current session context

3. **AI applies this knowledge**:
   - Suggests code that matches discovered patterns
   - Avoids previously encountered pitfalls
   - Provides context-aware debugging help
   - Offers solutions consistent with project decisions

### Example AI Usage

**Without memory**:
```
You: "Help me initialize the todos array"
AI: "You can initialize it as: const todos = null;"
```

**With memory** (after documenting the pattern):
```
You: "Help me initialize the todos array"
AI: "Based on the project's service initialization pattern, use:
const todos = [];
This prevents null reference errors as documented in patterns-discovered.md."
```

## Workflow Integration

### Start of Session

```bash
# 1. Review what was done last time
cat .github/memory/session-notes.md

# 2. Check documented patterns
cat .github/memory/patterns-discovered.md

# 3. Open working notes for this session
code .github/memory/scratch/working-notes.md
```

### During Session

- Keep `scratch/working-notes.md` open in a tab
- Update it as you work
- Reference it when talking to AI assistants

### End of Session

1. Review `scratch/working-notes.md`
2. Extract key findings → Add to `session-notes.md`
3. Extract reusable patterns → Add to `patterns-discovered.md`
4. Clear or archive `scratch/working-notes.md`

## Best Practices

### Do ✅
- Write in clear, complete sentences
- Include code examples in patterns
- Date your session notes
- Update patterns as you learn more
- Reference file paths and line numbers
- Keep working notes messy - they're for exploration

### Don't ❌
- Don't commit `scratch/working-notes.md` (it's in .gitignore)
- Don't duplicate information between files
- Don't write vague notes like "fixed bug" - explain what and why
- Don't let patterns go undocumented when you discover them
- Don't skip session summaries - they're valuable historical context

## Getting Started

1. **Read this README** - You're doing it! ✓
2. **Review the example session** in `session-notes.md`
3. **Review the example pattern** in `patterns-discovered.md`
4. **Open** `scratch/working-notes.md` and start your first session
5. **At session end**, summarize your findings into the committed files

## Questions?

This memory system is designed to be lightweight and practical. If you find yourself not using it, that's feedback! Adjust the system to match how you actually work. The goal is to capture valuable knowledge without creating documentation burden.

Happy coding! 🚀
