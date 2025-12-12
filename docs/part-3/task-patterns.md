---
title: Task Documentation
description: How to document completed tasks
---

# Task Documentation

## TLDR

When you finish a task, write a short doc: what you built, why you made key decisions, and your confidence score.

Keep it brief. This is a reference, not a novel.

---

## The Standard Format

```markdown
# Task 2.3: User Authentication

**Status:** Complete | **Confidence:** 8/10

## What I Built
Login and register endpoints with JWT tokens. Passwords hashed 
with bcrypt (cost factor 12). Tokens expire in 24 hours.

## Decisions
- **24h token expiry, no refresh:** Simpler for MVP. Users can 
  re-login daily. Add refresh tokens in v1.0 if needed.
- **Generic error messages:** "Invalid credentials" for both wrong 
  email and wrong password. Prevents user enumeration.

## Tests
8/8 passing. Covers: valid login, invalid email, invalid password,
missing fields, token expiration.

## Notes
- Rate limiting deferred to Phase 2
- Added bcrypt cost factor finding to LEARNINGS.md
```

That's it. Takes 5 minutes to write. Infinitely useful later.

---

## What to Include

**What you built:** 2-3 sentences. What does this task accomplish?

**Key decisions:** The non-obvious choices. What did you decide and why?

**Tests:** Are they passing? What do they cover?

**Confidence score:** Your honest assessment. 8/10 minimum to proceed.

**Notes:** Anything useful for future tasks. Gotchas, deferred items, things to remember.

---

## What NOT to Include

- Exhaustive file lists (if someone needs this, they can check git)
- Step-by-step implementation details (the code is the implementation)
- Repeated information from ROADMAP (just reference it)
- Evidence screenshots (unless something is hard to verify otherwise)
- "Next steps" (that's what ROADMAP is for)

---

## Confidence Scoring

Be honest with yourself.

**8/10 means:** It works correctly, handles errors, has tests, code is clean. Good enough to build on.

**9/10 means:** All of the above plus it's genuinely well-crafted. You're proud of it.

**7/10 means:** It mostly works but something's off. Don't move on. Figure out what's missing and fix it.

**6/10 or below:** Stop. Something is fundamentally wrong. Debug before continuing.

**Quick criteria template:**
```markdown
**8/10 requires:**
- [x] Core functionality works
- [x] Errors handled
- [x] Tests pass
- [x] Code is readable
- [ ] Nice-to-haves (deferred)
```

---

## Where to Store Task Docs

Simple approach:
```
docs/
└── tasks/
    ├── 1.1-project-setup.md
    ├── 1.2-database.md
    ├── 2.1-core-feature.md
    ├── 2.2-api-endpoints.md
    └── ...
```

Name them by task number. Keep them in one place. Done.

---

## For Complex Projects

If you're building something intricate (Electron apps, complex refactors), you might want more detail:

**Add a CHANGELOG section:**
```markdown
## Changelog
- Tried approach A, hit issue X
- Switched to approach B, worked
- Found edge case with Y, added handling
```

This helps when you need to debug or understand why things evolved a certain way.

But for most projects, the standard format is enough. Don't over-document.

---

## The Point

Task docs exist for one reason: so future you (or future AI) can understand what was done and why.

If you accomplish that in 15 lines, great. If you need 30, fine. But you probably don't need 100.

---

**Next:** [Confidence Scoring](/part-3/confidence-scoring) — The quality gate that keeps everything solid.