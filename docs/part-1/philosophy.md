---
title: Philosophy & Approach
description: The mindset that makes AI-assisted development actually work
---

# Philosophy & Approach

## TLDR

**Treat AI like a talented junior developer.** It can write code fast, but it needs clear direction, quality checks, and documentation to reference.

**Validate before you invest.** Spend $200 proving your core concept works before spending $2000 building everything.

**Document first.** AI has no memory between sessions. Your docs *are* its memory.

**Check quality as you go.** AI rates its own work. Below 8/10? Fix it before moving on.

**Audit between phases.** Fresh AI eyes catch what you missed.

---

## The Junior Developer Mental Model

Claude can write code faster than you. But like any talented junior dev, it:

**Can do:**
- Write code quickly
- Follow patterns from documentation
- Debug when given direction
- Generate tests

**Can't do (alone):**
- Judge if a project is too ambitious
- Remember decisions from last week
- Know when to stop and ask
- Maintain consistent standards

**Your job:** Be the senior dev. Set direction, define standards, verify quality.

---

## Validate First, Build Second

Most AI coding fails because people try to build everything at once.

**The pattern:**
> "Build me a Slack clone with video, threading, apps, search..."
> 
> *6 weeks and $3000 later: half-built mess*

**Better pattern:**
> "I want to build a Slack clone."
>
> AI: "That's huge. What's the ONE thing that would make yours different?"
>
> "AI-powered message summarization."
>
> AI: "Let's build just that first. If people love the summaries, then build the chat platform around it."

**Result:** $250 and 3 weeks to validate whether anyone wants AI summaries. If yes, continue. If no, you learned cheap.

This "MVP-first" conversation is the most important part of any project. It happens before you write any code.

---

## Documentation Is AI's Memory

AI forgets everything between sessions. Your documentation is the only continuity.

**Without docs:**
- Day 1: "Let's use PostgreSQL"
- Day 7: AI suggests MongoDB
- Day 14: Confusion

**With docs:**
- Day 1: Decision goes in README
- Day 7: AI reads README, stays consistent
- Day 14: Still consistent

**The five docs you need:**

1. **README.md** — What we're building, what phase we're in
2. **ROADMAP.md** — Tasks broken into subtasks
3. **CLAUDE_RULES.md** — Standards and quality requirements
4. **TASK_TEMPLATE.md** — Format for task documentation
5. **LEARNINGS.md** — Solutions to problems we've hit

Create these before coding. Update them as you go.

---

## Confidence Scoring

Every completed task needs a score out of 10.

```markdown
## Confidence: 8/10

**Must-have (met):**
- [x] Login works
- [x] Errors handled
- [x] Tests pass

**Nice-to-have (skipped):**
- [ ] Rate limiting (Phase 2)
```

**The rule:** Below 8/10? Fix it. Don't move on with broken foundations.

This prevents the cascade failure where broken auth leads to broken database leads to broken everything.

---

## Phase Audits

After finishing a major phase (like MVP), get fresh eyes on it.

**Process:**
1. Push code to GitHub
2. Start new Claude conversation
3. "You're a senior dev. Audit this code."
4. Fix what it finds
5. Then continue

The auditor catches accumulated issues that you stopped noticing. It's like code review, but AI can review everything at once.

---

## Comment More Than Feels Natural

Aim for 50% comments. Yes, really.

```python
# Skills weighted 2x because professional connections 
# matter more than hobby overlap at business events.
# TODO: Make this configurable after user research.
score = (skills_overlap * 2) + interests_overlap
```

Three months later, you'll know exactly why that `* 2` exists. Without the comment, you'd be guessing.

The goal isn't minimal code. It's **maximum clarity for future readers**—including AI in future sessions.

---

## Quick Reference

| Principle | Action |
|-----------|--------|
| Junior dev mental model | You direct, AI executes |
| Validate first | MVP before full build |
| Doc-first development | Five docs before coding |
| Confidence scoring | 8/10 minimum to proceed |
| Phase audits | Fresh AI reviews each phase |
| Heavy commenting | 50% comments, explain "why" |

---

**Next:** [Tool Selection](/part-1/tool-selection) — Choosing the right AI tools for this workflow.