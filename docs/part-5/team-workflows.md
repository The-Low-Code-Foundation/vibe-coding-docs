---
title: Team Workflows
description: Adapting the methodology for multiple developers
---

# Team Workflows

## TLDR

The methodology scales to teams with minimal adaptation. Key additions: shared documentation standards, clear task ownership, and AI-assisted code review.

---

## What Changes with Teams

**Solo workflow:**
- You own everything
- Docs serve your future self + AI
- No coordination needed

**Team workflow:**
- Shared ownership
- Docs serve everyone + AI
- Coordination required

The core principles stay the same. The documentation just becomes more critical.

---

## Shared Documentation

**CLAUDE_RULES becomes team contract:**

Everyone follows the same standards. AI produces consistent code regardless of who's prompting.

```markdown
# Team Standards

## Code Style
- Prettier for formatting (auto)
- ESLint for linting (auto)
- Comments: all functions, non-obvious logic

## Git
- Branch naming: feature/task-X.X-short-description
- Commit messages: "Task X.X: Description"
- PRs require: tests pass, one approval, AI review

## Task Ownership
- One person per task
- Update ROADMAP when starting/finishing
- Don't work on others' active tasks
```

**ROADMAP shows ownership:**

```markdown
### Task 2.1: User Authentication
Owner: Sarah
Status: In Progress
Branch: feature/task-2.1-auth

### Task 2.2: Database Schema
Owner: Mike  
Status: Complete
Confidence: 8/10

### Task 2.3: API Endpoints
Owner: Unassigned
Status: Not Started
```

Everyone knows who's doing what. No conflicts.

---

## Task Assignment

**Keep tasks independent when possible.**

```
Good:
├── Task 2.1: Auth (Sarah) - standalone
├── Task 2.2: Database (Mike) - standalone
├── Task 2.3: API (unassigned) - needs 2.1, 2.2
└── Task 2.4: UI (unassigned) - needs 2.3
```

Sarah and Mike work in parallel. Task 2.3 waits until dependencies are complete.

**When tasks must overlap:**

Clear communication. Define interfaces first.

```markdown
## Interface Agreement: Auth → API

Auth (Sarah) will export:
- requireAuth middleware
- User type definition
- Token validation function

API (Mike) will expect:
- req.user.id after auth middleware
- 401 response format: { error: string }

Agreed: 2024-12-10
```

Both sides code to the interface. Integration works.

---

## Code Review with AI

**AI as first reviewer:**

Before human review, run AI audit:

```
Review this PR for:
- Bugs or logic errors
- Security issues  
- Consistency with CLAUDE_RULES
- Test coverage gaps

Be specific. Reference file and line numbers.
```

AI catches mechanical issues. Human reviewer focuses on design and approach.

**Human reviewer focus:**
- Does this solve the right problem?
- Is the approach sensible?
- Any concerns AI wouldn't catch?
- Knowledge transfer—do I understand this code?

**PR template:**

```markdown
## Task
Task X.X: [Name]

## Changes
[Brief description]

## Confidence
X/10 - [Brief justification]

## Testing
- [ ] Unit tests pass
- [ ] Manual testing done
- [ ] AI review completed

## Notes for Reviewer
[Anything they should know]
```

---

## Handling Conflicts

**Documentation conflicts:**

Two people update ROADMAP simultaneously. Git merge conflict.

Fix: One source of truth. Use a task board (Linear, Notion, GitHub Projects) as primary, generate ROADMAP from it if needed.

**Architectural conflicts:**

Sarah thinks we should use approach A. Mike thinks B.

Fix: Document the decision. Either works, but pick one and stick with it.

```markdown
# LEARNINGS.md

## 2024-12-10: API Response Format
Decided: Always return { data, error, message } structure.
Alternatives considered: Just { data } or { result }.
Decision by: Team consensus
Reason: Consistent client-side handling.
```

Now it's documented. Future decisions reference this.

---

## Onboarding New Team Members

**Day 1:**
1. Read README (5 minutes)
2. Read CLAUDE_RULES (10 minutes)
3. Set up dev environment (30 minutes)
4. Read one completed task doc (5 minutes)

**First task:**
- Assign something small and standalone
- Pair with experienced team member first session
- Review their task doc carefully
- Provide feedback on adherence to standards

**Ramp-up:**
- Week 1: Small tasks with review
- Week 2: Medium tasks with light review
- Week 3+: Normal workflow

Good documentation makes onboarding fast. New person reads docs, understands context, contributes quickly.

---

## Communication Patterns

**Async by default:**
- Task docs capture decisions
- LEARNINGS captures knowledge
- PRs have context in description
- Questions go in PR comments or chat

**Sync when needed:**
- Architectural decisions
- Interface agreements
- Blocked dependencies
- Complex debugging

Don't meet to share information that could be written. Meet to discuss and decide.

---

## Quality at Scale

**Individual responsibility:**
Each person maintains confidence scoring for their tasks. Below 8/10 doesn't get PR'd.

**Team responsibility:**
Phase audits involve whole team. Everyone reviews audit findings. Annex tasks get distributed.

**Lead responsibility:**
Spot-check confidence scores. Are people being honest? Are standards maintained across the team?

---

## Quick Team Checklist

Before scaling from solo to team:

- [ ] CLAUDE_RULES covers team standards
- [ ] ROADMAP supports ownership tracking
- [ ] Git workflow documented
- [ ] PR template created
- [ ] AI review prompt ready
- [ ] Onboarding doc written

Most methodology stays identical. The documentation just needs to be clear enough for multiple people to follow.

---

**Next:** [Templates](/part-6/templates) — Ready-to-use documents for your projects.