---
title: Templates
description: Copy-paste documents to start your project
---

# Templates

Ready-to-use templates for all five core documents. Copy, customize, go.

---

## README.md

```markdown
# [Project Name]

[One sentence: what this does]

## Vision

[2-3 paragraphs: what this could become. Dream big here.]

## Current Phase: MVP

Building the minimum to validate [core concept].

**Included:**
- [Feature 1]
- [Feature 2]
- [Feature 3]

**Not included (yet):**
- [Deferred 1] → v1.0
- [Deferred 2] → v1.0
- [Deferred 3] → Production

**Success criteria:**
- [How we know MVP worked]

## Tech Stack

- Frontend: [X]
- Backend: [X]
- Database: [X]
- Hosting: [X]

## Setup

```bash
# Clone and install
git clone [repo]
cd [project]
npm install

# Environment
cp .env.example .env
# Edit .env with your values

# Run
npm run dev
```

## Project Structure

```
src/
├── [folder]/    # [Purpose]
├── [folder]/    # [Purpose]
└── [folder]/    # [Purpose]
```
```

---

## ROADMAP.md

```markdown
# Roadmap

## Phase 1: MVP ([X] weeks)

Goal: Validate [core concept]

### Task 1: Project Setup
- [ ] 1.1 Initialize repo and structure
- [ ] 1.2 Database setup
- [ ] 1.3 Basic config and env

### Task 2: [Core Feature]
- [ ] 2.1 [Subtask]
- [ ] 2.2 [Subtask]
- [ ] 2.3 [Subtask]

### Task 3: [Second Feature]
- [ ] 3.1 [Subtask]
- [ ] 3.2 [Subtask]

### Task 4: Polish & Deploy
- [ ] 4.1 Error handling
- [ ] 4.2 Basic tests
- [ ] 4.3 Deploy

## Phase 2: v1.0 (after MVP validates)

- [ ] [Feature]
- [ ] [Feature]
- [ ] [Feature]

## Deferred

| Feature | Target | Reason |
|---------|--------|--------|
| [Feature] | v1.0 | [Why not MVP] |
| [Feature] | Production | [Why not v1.0] |
```

---

## CLAUDE_RULES.md

```markdown
# Claude Rules

## Project Context

[One paragraph: what we're building and current phase]

## Code Standards

- **Comments:** Aim for 50%. Explain "why" not "what"
- **Functions:** Every function gets a docstring
- **Errors:** Handle explicitly, no silent failures
- **Tests:** Required for business logic

## Confidence Scoring

After each task, provide:

```
## Confidence: X/10

**Met:**
- [x] [Criterion]
- [x] [Criterion]

**Deferred:**
- [ ] [Thing] (Phase X)
```

**8/10 minimum to proceed.**

## Ask Human When

- Security decisions
- Architectural changes  
- Ambiguous requirements
- Anything destructive
- Confidence below 8

## Tech-Specific Rules

### [Framework/Language]
- [Rule]
- [Rule]

### Database
- [Rule]
- [Rule]
```

---

## TASK_TEMPLATE.md

```markdown
# Task [X.X]: [Name]

**Status:** [Complete/In Progress] | **Confidence:** [X/10]

## What I Built

[2-3 sentences: what this task accomplished]

## Decisions

- **[Decision]:** [Why]
- **[Decision]:** [Why]

## Tests

[Pass/fail status, brief coverage note]

## Notes

[Anything useful for future tasks]
```

---

## LEARNINGS.md

```markdown
# Learnings

Running log of solutions and gotchas. Check this at the start of each task.

---

## [Date]: [Topic]

**Problem:** [What went wrong]

**Solution:** [How we fixed it]

**Apply to:** [When this is relevant]

---

## Quick Reference

| Issue | Solution | Entry |
|-------|----------|-------|
| [Common issue] | [Quick fix] | [Date] |
```

---

## Filled Example: Conference Networking App

### README.md

```markdown
# NetworkMatch

AI-powered conference networking that connects the right people.

## Vision

Transform conference networking from random encounters to meaningful connections. Attendees get AI-matched with the most relevant people based on skills, interests, and goals. Full vision includes real-time matching, in-app messaging, calendar integration, and post-event follow-ups.

## Current Phase: MVP

Validating that AI matching creates valuable connections.

**Included:**
- CSV upload of attendees
- Simple profiles (name, skills, interests, goals)
- AI matching with top 10 recommendations
- Match explanations
- Basic feedback collection

**Not included (yet):**
- User accounts → v1.0
- Messaging → v1.0
- Calendar integration → Production

**Success criteria:**
- 70%+ of users rate matches as helpful
- At least one organizer wants to pay for it

## Tech Stack

- Frontend: React + Tailwind
- Backend: Node + Express
- Database: Supabase (PostgreSQL)
- AI: Claude API
- Hosting: Vercel

## Setup

```bash
git clone https://github.com/you/networkmatch
cd networkmatch
npm install
cp .env.example .env
# Add your SUPABASE_URL, SUPABASE_KEY, ANTHROPIC_API_KEY
npm run dev
```
```

### ROADMAP.md

```markdown
# Roadmap

## Phase 1: MVP (3 weeks)

Goal: Validate AI matching creates valuable connections

### Task 1: Foundation
- [x] 1.1 Project setup
- [x] 1.2 Supabase database
- [x] 1.3 Basic Express server

### Task 2: Data Management
- [x] 2.1 Attendee schema
- [ ] 2.2 CSV upload endpoint
- [ ] 2.3 Data validation

### Task 3: Matching
- [ ] 3.1 Matching algorithm
- [ ] 3.2 Claude API for explanations
- [ ] 3.3 Matches endpoint

### Task 4: Frontend
- [ ] 4.1 Upload interface
- [ ] 4.2 Matches display
- [ ] 4.3 Feedback form

### Task 5: Polish
- [ ] 5.1 Error handling
- [ ] 5.2 Basic tests
- [ ] 5.3 Deploy to Vercel

## Phase 2: v1.0

- [ ] User authentication
- [ ] Rich profiles with photos
- [ ] In-app messaging
- [ ] Real-time updates
```

---

## Usage Tips

**Starting a project:**
1. Copy all five templates
2. Fill in README with your vision and MVP scope
3. Fill in ROADMAP with tasks from brainstorming
4. Customize CLAUDE_RULES for your tech stack
5. Leave TASK_TEMPLATE and LEARNINGS mostly as-is

**Keep templates lean.**
If you're adding lots of sections, you're over-engineering. The templates here are the right size.

---

**Next:** [Prompts](/part-6/prompts) — Copy-paste prompts for every phase.