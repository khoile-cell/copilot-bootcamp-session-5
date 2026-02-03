# Patterns Discovered

## Purpose

This file documents recurring code patterns, architectural decisions, and reusable solutions discovered during development. Each pattern includes context, the problem it solves, the solution, and examples.

**Important**: This file is committed to git and accumulates knowledge over time.

---

## Pattern Template

Use this template when documenting a new pattern:

```markdown
## Pattern: [Pattern Name]

**Context**: [When/where does this pattern apply?]

**Problem**: [What issue does this pattern solve?]

**Solution**: [How does the pattern address the problem?]

**Example**:
```javascript
// Code example showing the pattern in practice
```

**Related Files**:
- [List files where this pattern is used]
- [Or should be used]

**Notes**:
- [Additional considerations]
- [Edge cases]
- [Trade-offs]
```

---

## Example Pattern

## Pattern: Service Initialization - Empty Array vs Null

**Context**: Initializing in-memory data structures in Express.js backend services (e.g., `packages/backend/src/app.js`)

**Problem**: When service data structures are initialized as `null` or `undefined`, endpoint handlers crash with "Cannot read property of null/undefined" errors. This makes GET endpoints fail even when they should return empty results.

**Solution**: Initialize in-memory collections as empty arrays at module level. This allows endpoints to safely iterate, filter, and return data without null checks.

**Example**:
```javascript
// ❌ DON'T: Causes null reference errors
let todos = null;

app.get('/api/todos', (req, res) => {
  res.json(todos); // Crashes if todos is null
});

// ✅ DO: Safe initialization
let todos = [];

app.get('/api/todos', (req, res) => {
  res.json(todos); // Always returns valid array, even when empty
});
```

**Related Files**:
- `packages/backend/src/app.js` - Main application file where todos array is defined
- `packages/backend/__tests__/app.test.js` - Tests that verify GET endpoint returns array

**Notes**:
- This pattern applies to all in-memory collections (users, items, etc.)
- Eliminates need for null checks in most endpoint handlers
- For databases, this pattern doesn't apply - queries naturally return empty arrays
- Trade-off: Slightly more memory usage (negligible for empty array)

---

## Pattern: [Your Next Pattern]

**Context**: [Add context]

**Problem**: [Add problem]

**Solution**: [Add solution]

**Example**:
```javascript
// Add code example
```

**Related Files**:
- [Add files]

**Notes**:
- [Add notes]
