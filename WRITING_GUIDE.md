# Writing Guide for Vibe Coding Docs

This guide is mandatory for all contributors (human or AI). Read it before writing anything.

---

## The Core Problem We're Solving

These docs became unreadable because they:
- Explained everything three times
- Used corporate-speak instead of plain English
- Created 80-line templates nobody will use
- Lost the conversational, practical voice

**Fix it by writing like you're explaining to a smart friend over coffee.**

---

## Hard Rules

### 1. Word Limits

| Document Type | Maximum Words |
|---------------|---------------|
| Chapter TLDR | 150 words |
| Full chapter | 1,500 words |
| Template | 30 lines |
| Example conversation | 20 exchanges max |

If you hit the limit, cut. Don't negotiate.

### 2. Say It Once

If a concept appears in the TLDR, don't re-explain it in the body. Reference it:

**Bad:**
> The confidence scoring system requires AI to rate its work out of 10. This means every task gets a score from 1-10 where the AI evaluates its own output. The score must be 8 or higher to proceed, meaning anything below 8/10 requires fixes before moving on.

**Good:**
> Confidence scoring (explained in the TLDR) keeps quality high. If you're below 8/10, fix it before moving on.

### 3. No Throat-Clearing

Delete these phrases on sight:
- "It's important to note that..."
- "In this section, we will explore..."
- "As mentioned previously..."
- "Let's take a deeper look at..."
- "This is a key concept because..."
- "The reason this matters is..."

Just say the thing.

### 4. Conversational Voice

**Bad:**
> The documentation-first paradigm represents a fundamental shift in how we approach AI-assisted development workflows, enabling persistent context that compensates for AI's lack of long-term memory.

**Good:**
> Write your docs before your code. AI forgets everything between sessions—your docs are its memory.

### 5. Short Paragraphs

Three sentences max per paragraph. One idea per paragraph. White space is your friend.

### 6. Examples Are Compact

Show the minimum needed to illustrate the point.

**Bad:** 50-line code example with full error handling, comments, and edge cases

**Good:** 10-line code example showing just the concept

### 7. Templates Are Skeletons

Templates should be fill-in-the-blank simple:

**Bad template:**
```markdown
# Task [X.Y.Z]: [Task Name]

## Overview
**From Roadmap:** [Copy the exact task description from ROADMAP.md]
**Dependencies:** [List all tasks that must be complete before this one]
**Estimated Time:** [Your original time estimate]
**Actual Time:** [How long it actually took - fill in after completion]

## Implementation Summary
[Provide 2-3 detailed paragraphs describing what was implemented, 
the key architectural decisions made, any challenges encountered,
and how they were resolved...]

[...80 more lines...]
```

**Good template:**
```markdown
# Task [X.X]: [Name]
**Status:** [Complete/In Progress] | **Confidence:** [X/10]

## What I Built
[2-3 sentences]

## Key Decisions
- [Decision]: [Why]

## Tests
[Pass/fail status]

## Notes
[Anything useful for later]
```

---

## The "$2000 Mistake" Rule

This metaphor appears ONCE in the entire documentation—in the Introduction.

Everywhere else, reference it briefly or not at all:
> "This prevents the classic 'build everything, validate nothing' trap."

Do not re-explain it. Ever.

---

## Structure Every Chapter Like This

```markdown
# Chapter Title

## TLDR
[100-150 words max. Complete summary. Reader could stop here.]

---

## [Main Concept 1]
[Explanation in 2-3 short paragraphs]

[Brief example if needed]

## [Main Concept 2]
[Same pattern]

---

## Quick Reference
[Checklist, table, or summary—something scannable]
```

That's it. No "Summary" section restating everything. No "What We Learned" recap. No "Next Steps" padding.

---

## Forbidden Patterns

### The Triple Explanation
Explaining something in the TLDR, again in prose, again in an example, again in a summary. Pick ONE place.

### The Hedge Stack
> "It's worth noting that in most cases, generally speaking, you might want to consider..."

Say it directly: "Do X."

### The False Choice
> "You could use Option A, which has these pros and cons, or Option B, which has these other pros and cons, or Option C..."

Just recommend one: "Use Option A. Here's why. (Option B works if [specific condition].)"

### The Exhaustive List
Every possible variation, edge case, and exception. Stop at the 80% case. Trust readers to figure out edge cases or ask.

### The Meta-Commentary
> "In this section, we'll explore..." 
> "Now that we understand X, let's move on to Y..."
> "As we discussed in the previous section..."

Delete all of it. Just write the content.

---

## Voice Check

Before submitting, read your writing aloud. If you sound like:

❌ A consultant justifying their fees → Rewrite
❌ A textbook → Rewrite  
❌ An AI trying to sound smart → Rewrite
✅ A senior dev explaining something at lunch → Ship it

---

## Example Transformation

### Before (Actual text from current docs):

> **Why "Overkill" Commenting Works**
>
> This methodology mandates something controversial: 50% of your code should be comments.
>
> Most developers think this is insane. Here's why it's actually brilliant:
>
> **Traditional View:**
> [40-line code example]
>
> **This Methodology:**
> [60-line code example]
>
> **What we gain:**
> 1. Algorithm rationale - Why skills weighted 2x
> 2. Design decisions - Why not use vector similarity (too slow)
> 3. Future roadmap - Can enhance with ML in v1.0
> 4. Modification history - When this was implemented
> 5. Examples - What the output looks like
> 6. Context - Why we made these choices
>
> **Three months later:**
> [Another paragraph explaining the benefit]
>
> **Versus traditional approach:**
> [Another paragraph comparing]
>
> [Total: 400+ words for one concept]

### After:

> **Comment More Than You Think**
>
> Aim for 50% comments. Sounds excessive—it's not.
>
> Future you (or the next developer, or AI in a future session) needs to know *why* you made decisions, not just *what* the code does.
>
> ```python
> # Skills weighted 2x because professional connections 
> # matter more than hobby overlap at business conferences.
> # Revisit this weight after user feedback in v1.0.
> score = (skills_overlap * 2) + interests_overlap
> ```
>
> That comment takes 10 seconds to write and saves hours of "why does this multiply by 2?" confusion later.
>
> [Total: 90 words]

---

## Final Checklist

Before submitting any documentation:

- [ ] Under word limit?
- [ ] No repeated explanations?
- [ ] Would I actually read this?
- [ ] Templates under 30 lines?
- [ ] Examples minimal but clear?
- [ ] Sounds like a human?

If any answer is "no," edit until it's "yes."

---

## Remember

The methodology is about **practical, budget-conscious development**. The docs should model that: efficient, no waste, gets the job done.

If the docs are bloated, we're not practicing what we preach.