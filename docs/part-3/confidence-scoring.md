---
title: Confidence Scoring
description: The quality gate that keeps your project solid
---

# Confidence Scoring

## TLDR

After every task, rate your confidence from 1-10. If it's below 8, fix it before moving on.

This one habit prevents the cascade failure where broken foundations corrupt everything built on top.

---

## How It Works

When you finish a task, ask yourself (or have AI ask itself):

> "How confident am I that this is done right?"

**8/10 means:** It works, it's tested, errors are handled, code is clean. Solid enough to build on.

**9/10 means:** All of the above, and it's genuinely good work. You'd show it to someone.

**7/10 means:** Something's off. Maybe tests are thin, edge cases unhandled, or you're not sure about a decision. Fix it.

**6/10 or below:** Stop. Something is fundamentally wrong.

---

## The Format

Keep it simple:

```markdown
## Confidence: 8/10

**Must-haves (met):**
- [x] Core functionality works
- [x] Errors handled
- [x] Tests pass
- [x] Code readable

**Deferred:**
- [ ] Rate limiting (Phase 2)
- [ ] Advanced validation (v1.0)
```

That's it. 10 lines. Don't over-engineer this.

---

## What Counts as 8/10

The bar isn't perfection. It's "solid enough to build on."

**8/10 code:**
- Does what it's supposed to do
- Handles the obvious error cases
- Has tests for the important paths
- Is readable by someone else (or AI next session)
- Doesn't have known bugs you're ignoring

**8/10 is NOT:**
- Every edge case handled
- 100% test coverage
- Perfectly optimized
- Production-hardened

Those are 9/10 or 10/10. For MVP, 8/10 is the target.

---

## When You're Below 8

Don't negotiate with yourself. If you're at 7/10, something's wrong.

**Common gaps:**
- "Tests pass but I'm not sure they test the right things" → Write better tests
- "It works but error handling is sketchy" → Add error handling
- "I'm not sure about this architectural decision" → Think it through or ask
- "There's a bug I haven't fixed" → Fix the bug

**The conversation:**
```
AI: "Confidence: 7/10. The login works but I haven't 
tested what happens when the database is unavailable."

You: "Add that test and handling before we continue."

AI: [adds test, adds handling]

AI: "Confidence: 8/10. Database errors now return 503 
with retry guidance. Test added."
```

Now you can move on.

---

## Why This Matters

Without confidence scoring, broken code accumulates:

```
Task 1: Auth (buggy) → "good enough, continue"
Task 2: Database (built on buggy auth) → "some issues, continue"  
Task 3: API (built on buggy database) → "not sure why this fails"
Task 4: UI (nothing works) → "everything is broken"
```

With confidence scoring:

```
Task 1: Auth → 7/10 → Fix → 8/10 → Continue
Task 2: Database → 8/10 → Continue
Task 3: API → 8/10 → Continue
Task 4: UI → Works because foundation is solid
```

The extra hour fixing Task 1 saves days debugging Task 4.

---

## Honest Self-Assessment

The scoring only works if you're honest.

**Temptation:** "It's probably fine, I'll call it 8/10 and move on."

**Reality check:** Would you bet $100 that this task is solid? If not, it's not 8/10.

**AI tends to be optimistic.** When AI says 8/10, verify. Run the tests. Try the edge cases. Check the error handling yourself.

---

## Quick Reference

| Score | Meaning | Action |
|-------|---------|--------|
| 9-10 | Excellent | Continue, maybe celebrate |
| 8 | Solid | Continue |
| 7 | Gaps exist | Fix before continuing |
| 6 | Significant issues | Stop and fix |
| ≤5 | Fundamentally broken | Reconsider approach |

---

**Next:** [Phase Audits](/part-4/phase-audits) — Fresh eyes between major milestones.