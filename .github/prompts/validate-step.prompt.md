---
description: "Validate that all success criteria for the current step are met"
agent: "code-reviewer"
tools: ["search", "read", "execute", "web", "todo"]
---

# Validate Step Completion

Check that all success criteria for a step are met before moving forward.

## Step to Validate

Step number (REQUIRED): ${input:step-number:Enter step number (e.g., 5-0, 5-1, 5-2)}

## Instructions

1. **Find the Exercise Issue**
   - Use `gh issue list --state open` to find the issue with "Exercise:" in the title
   - Get the issue number

2. **Get Issue Content with Comments**
   - Run `gh issue view <issue-number> --comments`
   - This retrieves all step instructions posted as comments

3. **Locate the Target Step**
   - Search through the issue content for "# Step ${step-number}:" or "Step ${step-number}:"
   - Extract the complete step instructions

4. **Find Success Criteria**
   - Locate the "## Success Criteria" section within the step
   - Extract all criteria (usually marked with checkboxes ✅)

5. **Validate Each Criterion**
   - Check each criterion against the current workspace state
   - Use file searches, directory listings, git status, etc.
   - Mark each as ✅ (complete) or ❌ (incomplete)

6. **Report Results**
   - Provide a clear summary showing:
     * All criteria with completion status
     * Specific files or evidence for completed items
     * Detailed guidance for any incomplete items
     * Next steps to complete the validation

## Validation Checklist

- [ ] Found the exercise issue
- [ ] Located the correct step instructions
- [ ] Extracted all success criteria
- [ ] Checked each criterion systematically
- [ ] Provided actionable feedback for incomplete items
