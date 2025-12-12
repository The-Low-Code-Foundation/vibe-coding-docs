---
title: Documentation Architecture
description: The five docs that make AI-assisted development work
---

# Documentation Architecture

## TLDR

Create five documents before writing code. These are AI's memory—without them, every session starts from zero.

Takes 1-2 hours. Pays back immediately.

---

## The Five Documents

| Document | Purpose | Update Frequency |
|----------|---------|------------------|
| README.md | What we're building, current phase | Per phase |
| ROADMAP.md | Tasks and subtasks | Per task |
| CLAUDE_RULES.md | Standards and quality gates | Rarely |
| TASK_TEMPLATE.md | Format for task docs | Never |
| LEARNINGS.md | Solutions and gotchas | During tasks |

AI reads these at the start of every session. They provide the context that chat history can't.

---

## README.md

What the project is and where it stands.

```markdown
# ProjectName

One-sentence description.

## Vision
What this could eventually become (2-3 paragraphs).

## Current Phase: MVP
What we're building NOW:
- Feature 1
- Feature 2

What we're NOT building yet:
- Deferred thing → v1.0
- Other thing → Production

## Tech Stack
- Frontend: React
- Backend: Node/Express
- Database: PostgreSQL

## Setup
[Basic install and run instructions]
```

Keep it under one page. Update when you finish a phase.

---

## ROADMAP.md

The work broken into pieces.

```markdown
# Roadmap

## Phase 1: MVP (2-3 weeks)

### Task 1: Project Setup
- [x] 1.1 Initialize repo
- [x] 1.2 Database setup
- [ ] 1.3 Basic API structure

### Task 2: Core Feature
- [ ] 2.1 Data model
- [ ] 2.2 Business logic
- [ ] 2.3 API endpoints
- [ ] 2.4 Basic UI

### Task 3: Polish
- [ ] 3.1 Error handling
- [ ] 3.2 Tests
- [ ] 3.3 Deploy

## Phase 2: v1.0 (after MVP validates)
[Bullet list of features]

## Deferred
- Thing 1: why deferred
- Thing 2: why deferred
```

**Subtask sizing rule:** Each subtask should take 30-90 minutes. If it's bigger, split it.

---

## CLAUDE_RULES.md

How AI should work on this project.

```markdown
# Claude Rules

## Standards
- Comment heavily (aim for 50% comments)
- Every function needs a docstring
- Handle errors explicitly
- Write tests for business logic

## Confidence Scoring
After each task, rate 1-10:
- 8+ required to proceed
- Below 8: fix before moving on

## Ask Human When
- Security decisions
- Architectural changes
- Ambiguous requirements
- Anything destructive

## Tech-Specific
- [Framework-specific rules]
- [Database conventions]
- [Naming conventions]
```

This is your quality contract. Be specific about what matters to you.

---

## TASK_TEMPLATE.md

How task completion gets documented.

```markdown
# Task [X.X]: [Name]

**Status:** Complete | **Confidence:** X/10

## What I Built
[2-3 sentences]

## Decisions
- [Decision]: [Why]

## Tests
[Status]

## Notes
[Anything useful for later]
```

That's it. 15 lines. Don't over-engineer this.

---

## LEARNINGS.md

Running log of things you've figured out.

```markdown
# Learnings

## 2024-12-10: Database timestamps
Supabase UUIDs don't sort chronologically.
Fix: Add created_at column, sort by that.

## 2024-12-11: CSV parsing
Real CSVs have BOM characters from Excel.
Fix: Strip with csvText.replace(/^\uFEFF/, '')

## 2024-12-12: React state after unmount
API calls completing after unmount cause warnings.
Fix: Cancelled flag in useEffect cleanup.
```

Add entries when you solve something tricky. Future sessions will thank you.

---

## Creating These Quickly

After brainstorming, prompt:

```
Based on our MVP scope discussion, create:
1. README.md with vision, current phase, and tech stack
2. ROADMAP.md with tasks broken into subtasks
3. CLAUDE_RULES.md with development standards

Keep each under 50 lines. Focus on what AI needs 
to stay consistent across sessions.
```

Review and adjust. Should take 30-60 minutes total.

---

## How AI Uses These

Every new task session:

1. AI reads README → "Ah, we're building X, currently in MVP phase"
2. AI reads ROADMAP → "Task 2.3 is next, here's what it involves"
3. AI reads CLAUDE_RULES → "I need to comment heavily and score 8+ confidence"
4. AI checks LEARNINGS → "Oh, there's a CSV gotcha I should know about"

This is why documentation-first works. You're building AI's memory.

---

## Don't Overdo It

The temptation is to create elaborate documentation. Resist.

**Too much:**
- 10 documents
- 100-line templates
- Detailed specs for every feature

**Just right:**
- 5 documents
- ~30 lines each
- Enough context to stay consistent

You can always add detail later. Start lean.

---

**Next:** [The Cline Workflow](/part-3/cline-workflow) — How to actually execute tasks.