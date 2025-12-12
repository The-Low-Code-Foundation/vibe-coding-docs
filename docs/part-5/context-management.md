---
title: Context Management
description: Keeping AI focused and consistent across sessions
---

# Context Management

## TLDR

AI can hold ~200k tokens in context. That sounds like a lot until you're debugging a large codebase.

Manage context by: working in focused tasks, starting fresh chats, and letting documentation (not chat history) carry continuity.

---

## The Context Window

Think of context as AI's working memory. It includes:
- Your conversation so far
- Files AI has read
- Code it's analyzing
- Documentation it's referencing

When this fills up, AI starts "forgetting" earlier content. Quality degrades.

**Signs you've hit context limits:**
- AI contradicts earlier decisions
- AI re-asks questions you already answered
- AI "forgets" patterns it was following
- Responses get slower or more generic

---

## The New Chat Solution

Don't fight context limits. Work with them.

**One task = one chat.**

```
Task 1: Database setup
└─ New chat → Complete → Close

Task 2: Auth endpoints  
└─ New chat → Complete → Close

Task 3: User interface
└─ New chat → Complete → Close
```

Each task gets AI's full attention without pollution from previous work.

**But what about continuity?**

That's what your documentation is for. AI reads README, ROADMAP, CLAUDE_RULES, and LEARNINGS at the start of each session. Decisions persist in docs, not chat history.

---

## Sizing Tasks for Context

Each subtask should be completable without hitting context limits.

**Rules of thumb:**
- Task touches ≤5 files significantly
- Task takes 30-90 minutes
- Task has a clear "done" state

**Too big:**
> "Implement the entire authentication system"

AI will load auth routes, user models, middleware, tests, existing code... context fills up.

**Right size:**
> "Create the login endpoint"

Focused. AI loads what it needs. Completes cleanly.

---

## What to Load, What to Skip

AI doesn't need to read your entire codebase for every task.

**Always load:**
- README.md (project context)
- ROADMAP.md (what we're doing)
- CLAUDE_RULES.md (standards)
- LEARNINGS.md (gotchas)
- Files directly relevant to the task

**Let AI find:**
- Related files it needs to reference
- Dependencies and imports

**Don't pre-load:**
- Entire directories "just in case"
- Old task documentation not relevant to current work
- Test files unless you're working on tests

Trust AI to ask for what it needs. It's smarter than bulk-loading everything.

---

## When Context Gets Polluted

Sometimes a chat goes sideways—long debugging sessions, tangents, confusion.

**Symptoms:**
- AI keeps suggesting things you've rejected
- AI seems confused about basic project facts
- Responses are inconsistent with earlier work

**Fix:** Start a new chat.

Don't try to "fix" a polluted context by adding more messages. That makes it worse. Close it, open fresh, re-state what you need.

---

## Large Codebases

For big projects (10k+ lines), extra discipline helps:

**Modular structure:**
```
src/
├── auth/       # Self-contained
├── matching/   # Self-contained  
├── api/        # Self-contained
└── ui/         # Self-contained
```

When working on auth, AI only needs to understand auth/. Good boundaries = manageable context.

**Task documentation:**
Each completed task doc tells AI what exists without loading all the code:

```markdown
## Task 2.3: Auth Middleware
Created requireAuth middleware in src/auth/middleware.js.
Validates JWT, attaches user to request.
Used in: all /api/protected/* routes.
```

AI reads this and knows auth exists without loading the file.

---

## Context-Efficient Prompting

**Verbose prompt (wastes context):**
```
I need you to create a function that takes two users as input 
where each user has a skills array and an interests array and 
the function should calculate how many skills they have in common
and how many interests they have in common and then return a 
score where skills are weighted twice as much as interests 
because professional connections are more valuable...
```

**Efficient prompt:**
```
Create a match scoring function.
- Input: two users with skills[] and interests[]
- Output: score (skills overlap * 2 + interests overlap)
- See CLAUDE_RULES for commenting standards
```

Say what you need. AI has your docs for context.

---

## Quick Reference

| Situation | Action |
|-----------|--------|
| Starting new task | New chat |
| Chat getting long | New chat |
| AI seems confused | New chat |
| Debugging same issue | Continue chat |
| Quick follow-up | Continue chat |

When in doubt, start fresh. The cost of reloading context is lower than the cost of confused AI.

---

**Next:** [Common Pitfalls](/part-5/pitfalls-recovery) — What goes wrong and how to fix it.