---
title: The Cline Workflow
description: Plan → Act → Verify, one task at a time
---

# The Cline Workflow

## TLDR

**New chat for every task.** This prevents context pollution.

**Minimal prompting.** "Can we plan task 2.3?" is enough—AI reads your docs for context.

**Plan before Act.** Review the approach before AI starts coding.

**Approve commands.** You see every terminal command before it runs.

**Verify and score.** Check the work, assign confidence, close chat, next task.

---

## The Cycle

```
1. Open new Cline chat
2. "Can we please plan task X.X?"
3. AI reads docs, proposes approach
4. Review plan, ask questions, adjust
5. "Proceed" → Act Mode
6. Approve terminal commands as needed
7. AI completes work, provides confidence score
8. Verify it works
9. Close chat
10. Next task
```

Every task follows this cycle. No exceptions.

---

## Why New Chat Per Task

Long conversations accumulate garbage:
- Old debugging tangents
- Superseded decisions
- Conflicting context

By message 100, AI is confused.

New chat = fresh start. Your documentation provides continuity, not chat history.

**The pattern:**
- Task 1 → New chat → Complete → Close
- Task 2 → New chat → Complete → Close
- Task 3 → New chat → Complete → Close

Each task gets AI's full attention without pollution from previous work.

---

## Minimal Prompting

You don't need elaborate prompts. This works:

> "Can we please plan task 2.3?"

AI will:
1. Read your ROADMAP.md to find task 2.3
2. Read README.md for project context
3. Check CLAUDE_RULES.md for standards
4. Look at LEARNINGS.md for gotchas
5. Propose an approach

If your docs are good, the prompt can be simple.

**When to add context:**
- External APIs: "Here's the API docs: [link]"
- Changed requirements: "Actually, we decided to use X instead of Y"
- Specific constraints: "This needs to work offline"

Otherwise, trust your docs.

---

## Plan Mode

When you prompt, AI enters Plan Mode:

```
You: "Can we plan task 2.3 - user authentication?"

AI: "Based on the ROADMAP, this task involves:
- Creating login/register endpoints
- JWT token generation
- Password hashing with bcrypt

Proposed approach:
1. Add User model with email/passwordHash
2. Create auth service for hashing/tokens
3. Add POST /auth/login and /auth/register routes
4. Write tests

Questions:
- Token expiration: 24 hours okay?
- Should I add refresh tokens or keep MVP simple?
- Rate limiting now or defer to Phase 2?"
```

Answer the questions. Adjust the plan if needed.

**Don't skip this.** Catching misunderstandings now is cheap. Fixing code later is expensive.

---

## Act Mode

Once the plan is right:

> "Looks good. Proceed."

AI switches to Act Mode and starts working:
- Creates/modifies files
- Runs commands (with your approval)
- Writes tests
- Documents the work

**Terminal approval:**

```
Cline wants to run: npm install bcrypt jsonwebtoken
[Approve] [Reject] [Edit]
```

Quick approvals for standard stuff (npm install, npm test).
Careful review for anything destructive (rm, database operations, git push).

---

## Completion

When AI finishes, it should provide:

```markdown
## Confidence: 8/10

**Done:**
- Login endpoint working
- Register endpoint working
- JWT tokens generating correctly
- Tests passing (8/8)

**Deferred:**
- Rate limiting (Phase 2 per roadmap)
- Refresh tokens (v1.0)

**Notes:**
- Used 24h token expiry as discussed
- Added entry to LEARNINGS about bcrypt cost factor
```

**Your job:**
1. Verify it actually works (run the app, test manually)
2. Check confidence score makes sense
3. If below 8/10, fix before moving on
4. Close chat, open next task

---

## Visual Verification

For UI tasks, ask AI what you should see:

> "Before we close, describe what I should see when I test the login flow."

```
AI: "At localhost:3000/login you should see:
- Email and password fields
- 'Sign In' button
- After correct login: redirect to dashboard
- After wrong password: 'Invalid credentials' error

Try email: test@example.com, password: test123"
```

Test it. Report any differences. Fix before closing.

---

## When Things Go Wrong

**AI seems confused:**
Your docs might be incomplete or contradictory. Check them.

**AI does something unexpected:**
Stop Act Mode, discuss in Plan Mode, then resume.

**Confidence is below 8:**
Don't move on. Ask AI what's missing and fix it.

**Task is taking way too long:**
It's probably too big. Split it into smaller subtasks.

---

## Quick Reference

| Phase | What Happens |
|-------|--------------|
| New chat | Fresh context, AI reads docs |
| Plan Mode | AI proposes approach, you review |
| Act Mode | AI executes, you approve commands |
| Completion | Confidence score, verification |
| Close | Done. Next task gets new chat |

---

**Next:** [Task Patterns](/part-3/task-patterns) — How to document completed tasks.