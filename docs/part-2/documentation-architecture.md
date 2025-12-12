---
title: Documentation Architecture
description: Creating the project "DNA" that guides all AI-assisted development
---

# Chapter 4: Documentation Architecture

## TLDR

**What:** Create 5-7 key documents before writing any code. These documents become your project's "DNA"—the persistent context that guides both you and AI throughout development.

**Why:** AI has no long-term memory. Without documentation, every conversation starts from zero. With good documentation, AI can reference decisions, patterns, and context from previous work. This is what transforms vibe coding from chaotic to systematic.

**Time Investment:** 2-4 hours after your brainstorming session. This investment pays back 10x in development speed and code quality.

**The Five Core Documents:**
1. **README.md** — Project vision, current phase, architecture overview
2. **ROADMAP.md** — Phases → Tasks → Subtasks (the development plan)
3. **CLAUDE_RULES.md** — Development standards, quality gates, when to ask for help
4. **TASK_TEMPLATE.md** — Standard format for all task documentation
5. **LEARNINGS.md** — Running log of project-specific insights and solutions

**Key Insight:** These documents aren't bureaucracy—they're the difference between AI that "forgets everything" and AI that "knows your project." Every task execution references these docs, creating consistency across hundreds of development sessions.

**Output:** By the end of this chapter, you'll have a complete document set ready for development.

---

## Why Documentation-First Changes Everything

### The Memory Problem

AI coding assistants have a fundamental limitation: **no persistent memory**.

Every conversation with Claude or Cline starts fresh. The AI that helped you design your authentication system yesterday has no knowledge of those decisions today.

**Without documentation:**
```
Day 1: "Let's use PostgreSQL with Prisma"
Day 3: AI suggests: "Should we use MongoDB?"
Day 7: AI implements: SQL queries that partially work
Day 14: Complete confusion about what was decided
```

**With documentation:**
```
Day 1: Decision documented in README.md and CLAUDE_RULES.md
Day 3: AI reads docs → "I see we're using PostgreSQL with Prisma"
Day 7: AI writes: Correct Prisma queries
Day 14: AI references docs → Consistent with all previous work
```

### The Context Loading Pattern

This methodology uses a specific pattern for every task:

```
1. Open new Cline chat (fresh context)
2. AI automatically reads project files
3. AI references: README, ROADMAP, CLAUDE_RULES, LEARNINGS
4. AI understands: Where are we? What's the standard? What have we learned?
5. AI executes: Consistent with all previous work
```

**This is why documentation-first works:**
- Documents persist between sessions
- AI loads context from documents, not chat history
- Decisions made once → referenced forever
- Quality standards defined once → enforced always

### What "Good Documentation" Actually Means

Good project documentation for AI-assisted development is:

**1. Reference-Optimized**
- Structured for quick scanning
- Clear sections and headings
- AI can find specific information quickly

**2. Decision-Documented**
- Not just "what" but "why"
- Trade-offs considered
- Alternatives rejected (and why)

**3. Current-State Aware**
- What phase are we in?
- What's done? What's next?
- What's deferred?

**4. Standard-Defining**
- How should code be written?
- What quality is required?
- When should AI ask for help?

---

## The Five Core Documents

Every project needs these five documents before development begins:

| Document | Purpose | Created When | Updated When |
|----------|---------|--------------|--------------|
| README.md | Project overview & current state | After brainstorming | After each phase |
| ROADMAP.md | Development plan | After brainstorming | After each task |
| CLAUDE_RULES.md | Standards & quality gates | Before coding | Rarely (stable) |
| TASK_TEMPLATE.md | Task format | Before coding | Rarely (stable) |
| LEARNINGS.md | Project insights | Start empty | During each task |

### How They Work Together

```
┌─────────────────────────────────────────────────────────────┐
│                      README.md                               │
│  "What is this project? What phase are we in?"               │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                     ROADMAP.md                               │
│  "What tasks exist? What's the order? What's next?"          │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   CLAUDE_RULES.md                            │
│  "How should I write code? What standards apply?"            │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                  TASK_TEMPLATE.md                            │
│  "How should I document my work on this task?"               │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                    LEARNINGS.md                              │
│  "What project-specific knowledge should I know?"            │
└─────────────────────────────────────────────────────────────┘
```

**Every task execution:**
1. AI reads README → Understands project context
2. AI reads ROADMAP → Knows what to work on
3. AI reads CLAUDE_RULES → Knows quality standards
4. AI uses TASK_TEMPLATE → Documents work consistently
5. AI checks LEARNINGS → Avoids previous mistakes

---

## Document 1: README.md

### Purpose

README.md is your project's **north star**. It answers:
- What is this project trying to achieve?
- What's the full vision (long-term)?
- What are we building right now (current phase)?
- How is the project structured?
- How do I set it up and run it?

### Structure

```markdown
# [Project Name]

One-sentence description of what this project does.

## Vision

[2-3 paragraphs describing the full vision. Don't hold back—describe
what this project could eventually become. This is from your 
brainstorming session's "full scope" discussion.]

## Current Phase: [Phase Name] (v0.1)

We are currently building the MVP to validate [core concept].

### What's Included in This Phase
- [Feature 1]
- [Feature 2]
- [Feature 3]

### What's NOT Included (Deferred)
- [Deferred feature 1] → v1.0
- [Deferred feature 2] → v1.0
- [Deferred feature 3] → Production

### Success Criteria
- [Measurable outcome 1]
- [Measurable outcome 2]

## Architecture Overview

[Brief description of the technical architecture]

### Tech Stack
- **Frontend:** [Framework]
- **Backend:** [Framework]
- **Database:** [Database]
- **Hosting:** [Platform]

### Project Structure
```
[directory tree of key folders/files]
```

## Setup Instructions

### Prerequisites
- [Requirement 1]
- [Requirement 2]

### Installation
```bash
[installation commands]
```

### Running Locally
```bash
[run commands]
```

### Environment Variables
```
[list of required env vars]
```

## Development Workflow

This project uses AI-assisted development with Cline. See:
- `ROADMAP.md` for development plan
- `CLAUDE_RULES.md` for development standards
- `LEARNINGS.md` for project-specific insights

## Future Phases

### v1.0 (After MVP Validates)
[Features planned for v1.0]

### Production (After v1.0 Succeeds)
[Features planned for production release]
```

### Complete README Example

Here's a real README from a conference networking MVP:

```markdown
# NetworkMatch

AI-powered conference networking that actually connects the right people.

## Vision

NetworkMatch transforms how professionals connect at conferences. Instead of 
random encounters and forgotten business cards, attendees receive AI-powered 
match recommendations that identify the most valuable connections based on 
skills, interests, goals, and potential synergies.

The full vision includes real-time matching, in-app messaging, meeting 
scheduling, AI conversation starters, post-event follow-ups, and integrations 
with calendars, LinkedIn, and CRM systems.

## Current Phase: MVP (v0.1)

We are validating that AI matching actually identifies valuable connections.

### What's Included in This Phase
- CSV import of attendee data (organizer uploads)
- Simple profile: name, role, skills, interests, goals
- AI matching algorithm using tag overlap
- Top 10 matches per attendee with explanations
- Magic link access (no user accounts)
- Export matches as CSV
- Basic feedback collection

### What's NOT Included (Deferred)
- User accounts and authentication → v1.0
- Real-time Slack/Teams integration → v1.0
- In-app messaging → v1.0
- Meeting scheduling → v1.0
- Rich profiles with photos → v1.0
- AI conversation starters → Production
- CRM integration → Production
- Mobile apps → Production

### Success Criteria
- 70%+ of users rate their matches as "helpful"
- At least one organizer expresses willingness to pay
- Core matching algorithm is fast enough (<2s per attendee)

## Architecture Overview

Simple three-tier MVP architecture focused on proving the matching algorithm.

### Tech Stack
- **Frontend:** React 18 + Tailwind CSS
- **Backend:** Node.js + Express
- **Database:** Supabase (PostgreSQL)
- **AI:** Claude API for match explanations
- **Hosting:** Vercel (free tier)

### Project Structure
```
networkmatch/
├── client/              # React frontend
│   ├── src/
│   │   ├── components/  # React components
│   │   ├── pages/       # Page components
│   │   └── utils/       # Helpers
│   └── package.json
├── server/              # Express backend
│   ├── routes/          # API routes
│   ├── services/        # Business logic
│   │   ├── matching.js  # Matching algorithm
│   │   └── ai.js        # Claude integration
│   └── package.json
├── docs/                # Task documentation
├── README.md
├── ROADMAP.md
├── CLAUDE_RULES.md
├── TASK_TEMPLATE.md
└── LEARNINGS.md
```

## Setup Instructions

### Prerequisites
- Node.js 18+
- npm or yarn
- Supabase account (free tier)
- Anthropic API key

### Installation
```bash
git clone https://github.com/yourusername/networkmatch.git
cd networkmatch
npm install
cd client && npm install && cd ..
cd server && npm install && cd ..
```

### Environment Variables
```
# server/.env
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_anon_key
ANTHROPIC_API_KEY=your_anthropic_key

# client/.env
REACT_APP_API_URL=http://localhost:3001
```

### Running Locally
```bash
# Terminal 1: Start backend
cd server && npm run dev

# Terminal 2: Start frontend
cd client && npm start
```

## Development Workflow

This project uses AI-assisted development with Cline. 

**For each task:**
1. Start new Cline chat
2. Say: "Can we please plan [task name from ROADMAP]?"
3. Review plan, ask questions
4. Switch to Act Mode
5. Verify confidence score ≥ 8/10

See `CLAUDE_RULES.md` for development standards.

## Future Phases

### v1.0 (After MVP Validates)
- User authentication (Google OAuth)
- Rich profiles: photos, bio, LinkedIn link
- Improved AI matching with vector embeddings
- Real-time match updates
- In-app messaging between matched users
- Meeting scheduling with calendar integration

### Production (After v1.0 Succeeds)
- Multi-conference support
- AI conversation starters
- Post-event follow-up automation
- CRM integrations (HubSpot, Salesforce)
- Analytics dashboard for organizers
- Mobile apps (iOS, Android)
- Enterprise features: SSO, admin controls
```

---

## Document 2: ROADMAP.md

### Purpose

ROADMAP.md is your **development plan**. It breaks down the project into:
- **Phases** — Major milestones (MVP, v1.0, Production)
- **Tasks** — Logical units of work within a phase
- **Subtasks** — Individual development sessions (sized for context window)

### The Hierarchy

```
Phase (MVP v0.1)
├── Task 1: Project Setup
│   ├── Subtask 1.1: Initialize repository
│   ├── Subtask 1.2: Set up database
│   └── Subtask 1.3: Configure environment
├── Task 2: Core Feature
│   ├── Subtask 2.1: Backend API
│   ├── Subtask 2.2: Frontend component
│   └── Subtask 2.3: Integration
└── Task 3: Testing & Polish
    ├── Subtask 3.1: Unit tests
    └── Subtask 3.2: Documentation
```

### Sizing Subtasks

**Critical Rule:** Each subtask should be completable in one Cline session.

**Why?** Context window constraints. If a subtask requires more context than fits in ~200k tokens (including code references, chat history, documentation), it's too big.

**Rule of thumb:**
- Subtask should take 30-90 minutes
- Should touch ≤5 files significantly
- Should have clearly defined success criteria
- Should be testable in isolation

**Too Big:**
```
❌ Subtask 2.1: Implement entire authentication system
```

**Right Size:**
```
✅ Subtask 2.1: Create user registration endpoint
✅ Subtask 2.2: Create login endpoint with JWT
✅ Subtask 2.3: Create password reset flow
✅ Subtask 2.4: Create auth middleware
✅ Subtask 2.5: Write authentication tests
```

### Structure

```markdown
# [Project Name] Roadmap

## Overview

| Phase | Description | Timeline | Status |
|-------|-------------|----------|--------|
| MVP (v0.1) | [Core validation] | [X weeks] | 🔄 In Progress |
| v1.0 | [Full feature MVP] | [X weeks] | ⏳ Planned |
| Production | [Scale & polish] | [X weeks] | ⏳ Planned |

---

## Phase 1: MVP (v0.1)

**Goal:** [What this phase validates]
**Timeline:** [X weeks]
**Success Criteria:** [Measurable outcomes]

### Task 1.1: [Task Name]

**Description:** [What this task accomplishes]
**Dependencies:** [Any prerequisites]

| Subtask | Description | Status | Notes |
|---------|-------------|--------|-------|
| 1.1.1 | [Subtask description] | ✅ Complete | |
| 1.1.2 | [Subtask description] | 🔄 In Progress | |
| 1.1.3 | [Subtask description] | ⏳ Planned | |

### Task 1.2: [Task Name]

...

---

## Phase 2: v1.0

**Goal:** [What this phase accomplishes]
**Timeline:** [X weeks after MVP validates]
**Prerequisites:** MVP success criteria met

### Task 2.1: [Task Name]

...

---

## Phase 3: Production

**Goal:** [What this phase accomplishes]  
**Timeline:** [X weeks after v1.0]
**Prerequisites:** v1.0 success criteria met

[Tasks will be detailed after v1.0]

---

## Deferred Features

Features explicitly deferred for future consideration:

| Feature | Deferred To | Reason |
|---------|-------------|--------|
| [Feature] | v1.0 | [Why not in MVP] |
| [Feature] | Production | [Why not in v1.0] |
| [Feature] | Maybe Never | [Why not priority] |
```

### Complete ROADMAP Example

```markdown
# NetworkMatch Roadmap

## Overview

| Phase | Description | Timeline | Status |
|-------|-------------|----------|--------|
| MVP (v0.1) | Validate AI matching works | 2-3 weeks | 🔄 In Progress |
| v1.0 | Usable product with accounts | 4-6 weeks | ⏳ Planned |
| Production | Scalable, monetizable | 2-3 months | ⏳ Planned |

---

## Phase 1: MVP (v0.1)

**Goal:** Validate that AI can identify valuable professional connections
**Timeline:** 2-3 weeks
**Budget:** ~$250 in API tokens
**Success Criteria:**
- 70%+ of test users rate matches as "helpful"
- Matching completes in <2s per attendee
- At least one conference organizer expresses purchase intent

### Task 1.1: Project Foundation

**Description:** Set up development environment and core infrastructure
**Dependencies:** None (first task)
**Estimated Time:** 2-3 days

| Subtask | Description | Status | Confidence |
|---------|-------------|--------|------------|
| 1.1.1 | Initialize monorepo with client/server structure | ✅ Complete | 9/10 |
| 1.1.2 | Configure Supabase database and environment | ✅ Complete | 8/10 |
| 1.1.3 | Set up basic Express server with health check | ✅ Complete | 9/10 |
| 1.1.4 | Set up React client with routing | ✅ Complete | 8/10 |

### Task 1.2: Attendee Data Management

**Description:** Enable organizers to upload and manage attendee data
**Dependencies:** Task 1.1 complete
**Estimated Time:** 3-4 days

| Subtask | Description | Status | Confidence |
|---------|-------------|--------|------------|
| 1.2.1 | Create attendee database schema | ✅ Complete | 9/10 |
| 1.2.2 | Build CSV upload endpoint with validation | ✅ Complete | 8/10 |
| 1.2.3 | Create attendee list admin view | 🔄 In Progress | - |
| 1.2.4 | Implement magic link generation | ⏳ Planned | - |

### Task 1.3: Matching Algorithm

**Description:** Core AI matching logic
**Dependencies:** Task 1.2 complete
**Estimated Time:** 4-5 days

| Subtask | Description | Status | Confidence |
|---------|-------------|--------|------------|
| 1.3.1 | Implement tag-based matching algorithm | ⏳ Planned | - |
| 1.3.2 | Integrate Claude API for match explanations | ⏳ Planned | - |
| 1.3.3 | Create matches endpoint | ⏳ Planned | - |
| 1.3.4 | Optimize for performance (<2s) | ⏳ Planned | - |

### Task 1.4: Attendee Experience

**Description:** Frontend for attendees to view matches
**Dependencies:** Task 1.3 complete
**Estimated Time:** 3-4 days

| Subtask | Description | Status | Confidence |
|---------|-------------|--------|------------|
| 1.4.1 | Magic link authentication flow | ⏳ Planned | - |
| 1.4.2 | Matches display page | ⏳ Planned | - |
| 1.4.3 | Match detail with explanation | ⏳ Planned | - |
| 1.4.4 | Feedback collection mechanism | ⏳ Planned | - |

### Task 1.5: Testing & Polish

**Description:** Quality assurance and deployment
**Dependencies:** Tasks 1.1-1.4 complete
**Estimated Time:** 2-3 days

| Subtask | Description | Status | Confidence |
|---------|-------------|--------|------------|
| 1.5.1 | Unit tests for matching algorithm | ⏳ Planned | - |
| 1.5.2 | Integration tests for API | ⏳ Planned | - |
| 1.5.3 | Deploy to Vercel | ⏳ Planned | - |
| 1.5.4 | Documentation and README update | ⏳ Planned | - |

---

## Phase 2: v1.0

**Goal:** Transform MVP into usable product people can use daily
**Timeline:** 4-6 weeks after MVP validates
**Prerequisites:** MVP success criteria met

### Task 2.1: User Authentication
- Google OAuth integration
- User profiles with photos
- Session management

### Task 2.2: Enhanced Matching
- Replace tag overlap with vector embeddings
- Implement Qdrant for similarity search
- Add matching preferences

### Task 2.3: Communication Features
- In-app messaging between matches
- Meeting scheduling integration
- Notification system

### Task 2.4: Organizer Dashboard
- Event management
- Analytics on matching success
- Attendee management

---

## Phase 3: Production

**Goal:** Scalable, monetizable SaaS product
**Timeline:** 2-3 months after v1.0
**Prerequisites:** v1.0 success criteria met

[Detailed tasks to be defined after v1.0 success]

High-level areas:
- Multi-tenancy and enterprise features
- Billing and subscription management
- Mobile applications
- Advanced analytics
- CRM integrations
- AI conversation starters

---

## Deferred Features

| Feature | Deferred To | Reason |
|---------|-------------|--------|
| User accounts | v1.0 | MVP validates matching, not auth |
| Real-time updates | v1.0 | Not needed for initial validation |
| Vector embeddings | v1.0 | Tag overlap sufficient for MVP |
| Mobile apps | Production | Web-first for faster iteration |
| CRM integration | Production | Needs enterprise customers first |
| AI chatbot | Maybe Never | May not add value vs simple messaging |

---

## Progress Log

| Date | Milestone | Notes |
|------|-----------|-------|
| 2024-12-01 | Phase 1 started | Initial setup |
| 2024-12-03 | Task 1.1 complete | Foundation ready |
| 2024-12-05 | Task 1.2 started | Working on CSV upload |
```

---

## Dependency Mapping

### Why Dependencies Matter

Some tasks can't start until others complete:

```
Task 1.1 (Setup) ─────────────────────────────────────┐
                                                       │
Task 1.2 (Data) ──────── requires 1.1 ────────────────┤
                                                       │
Task 1.3 (Matching) ──── requires 1.2 ────────────────┤
                                                       │
Task 1.4 (Frontend) ──── requires 1.3 ────────────────┤
                                                       │
Task 1.5 (Testing) ───── requires 1.1-1.4 ────────────┘
```

### Documenting Dependencies

In your ROADMAP, always note:
- What must be complete before this task starts?
- What might this task block?
- Are there parallel opportunities?

**Example:**
```markdown
### Task 1.4: Attendee Experience

**Dependencies:** 
- Hard: Task 1.3 must be complete (needs matching API)
- Soft: Task 1.2 should be stable (uses attendee data)

**Blocks:** Task 1.5 (testing needs UI to exist)

**Parallel Opportunity:** 
- Subtask 1.4.1 (UI shell) can start while 1.3 is finishing
- Stub the API responses to work in parallel
```

---

::: tip Creating These Documents
Don't start from scratch. After your brainstorming session, ask Claude:

"Based on our brainstorming conversation, please create a README.md and ROADMAP.md following this structure: [paste templates above]"

The brainstorming outputs (MVP scope, technical decisions, deferred features) map directly to these documents.
:::

---

---

## Document 3: CLAUDE_RULES.md

### Purpose

CLAUDE_RULES.md defines your **development standards**. It tells AI:
- How should code be written?
- What quality is required?
- When should I ask for help?
- What are the project-specific requirements?

This document is your "tech lead instructions" to a junior developer. Everything you'd tell a new team member about how to work on this project.

### Why This Document Is Critical

Without CLAUDE_RULES, every task starts with AI's defaults:
- Maybe 20% comments, maybe 80%
- Maybe tests, maybe not
- Maybe ask for help on edge cases, maybe plow forward

With CLAUDE_RULES, AI consistently:
- Follows your commenting standard (50% comments)
- Writes tests as specified
- Asks for help when you want it to
- Follows project-specific patterns

### Structure

```markdown
# Claude Rules for [Project Name]

## Project Context

[Brief description of the project and current phase]

---

## Development Standards

### Code Style

- **Commenting:** 50% comments, 50% code (excessive on purpose)
- **Documentation:** Every function must have a docstring
- **Naming:** [camelCase/snake_case/PascalCase conventions]
- **File Structure:** [How files should be organized]

### Required for Every Function

Every function must document:
1. **Purpose:** What does this function do?
2. **Parameters:** What inputs does it accept?
3. **Returns:** What does it output?
4. **Side Effects:** Does it modify external state?
5. **Example:** Show sample usage
6. **Why:** Why was this approach chosen?

### Testing Requirements

- Unit tests required for: [business logic, utilities, etc.]
- Integration tests required for: [API endpoints, etc.]
- Minimum coverage: [X%]
- Test location: [test files location]

---

## Confidence Scoring

### Required for Every Subtask

After completing any subtask, provide:

```markdown
## Confidence Score: X/10

### Criteria for X/10:

**Must-Have (Required):**
- [ ] Criterion 1
- [ ] Criterion 2

**Nice-to-Have (Not Required for MVP):**
- [ ] Enhancement 1
- [ ] Enhancement 2

### Evidence:
[Demonstrate each criterion is met]
```

### Thresholds

- **8/10 minimum** to proceed to next subtask
- **7/10 or below:** Must identify gaps and fix before proceeding
- **9/10 expected** for critical components (auth, payments, etc.)

---

## When to Ask Human for Help

### Always Ask When:

1. **Security decisions** - Authentication, authorization, encryption
2. **Data deletion** - Any destructive operations
3. **External API keys** - Never hardcode, always ask about env vars
4. **Architectural changes** - Anything that affects multiple components
5. **Ambiguous requirements** - When spec could be interpreted multiple ways
6. **Breaking changes** - Anything that affects existing functionality

### Proceed Without Asking:

1. Minor bug fixes with clear cause
2. Adding comments to existing code
3. Code formatting and cleanup
4. Adding test cases
5. Documentation updates

---

## Technology-Specific Rules

### [Frontend Framework]

- [Rule 1]
- [Rule 2]

### [Backend Framework]

- [Rule 1]
- [Rule 2]

### Database

- [Rule 1]
- [Rule 2]

---

## Quality Gates

### Before Marking Task Complete:

- [ ] All functions have docstrings
- [ ] Comments explain "why" not just "what"
- [ ] Unit tests pass
- [ ] No console.log statements (unless intentional debugging)
- [ ] Error handling is present
- [ ] Edge cases considered
- [ ] Confidence score documented

### Before Marking Phase Complete:

- [ ] All tasks in phase complete with ≥8/10
- [ ] Integration tested
- [ ] Documentation updated
- [ ] Ready for phase audit
```

### Complete CLAUDE_RULES Example

```markdown
# Claude Rules for NetworkMatch

## Project Context

NetworkMatch is a conference networking MVP (v0.1) that validates AI-powered 
attendee matching. We're building fast to test if matching works, but code 
must be maintainable for v1.0 development.

Current Phase: MVP (v0.1)
Primary Goal: Validate matching algorithm creates valuable connections

---

## Development Standards

### Code Style

- **Commenting:** Aim for 50% comments, 50% code
  - Every function needs a detailed docstring
  - Complex logic needs inline comments explaining "why"
  - Decision points need comments about alternatives considered
  
- **Naming Conventions:**
  - JavaScript: camelCase for variables/functions, PascalCase for components
  - Files: kebab-case for all files (matching-service.js, not matchingService.js)
  - Database: snake_case for PostgreSQL columns
  
- **File Organization:**
  - One React component per file
  - Services contain business logic, routes handle HTTP
  - Utilities in `/utils`, keep them pure functions

### Required for Every Function

```javascript
/**
 * Calculate match score between two conference attendees.
 * 
 * Scoring weights skills 2x higher than interests because
 * professional connections are more valuable at business conferences.
 * 
 * @param {Object} user1 - First attendee with skills and interests arrays
 * @param {Object} user2 - Second attendee with skills and interests arrays
 * @returns {number} Match score (higher = better match, typically 0-20)
 * 
 * @example
 * const score = calculateMatch(
 *   { skills: ['React', 'Node'], interests: ['hiking'] },
 *   { skills: ['React', 'Python'], interests: ['hiking', 'gaming'] }
 * );
 * // Returns: 3 (1 skill overlap * 2 + 1 interest overlap * 1)
 * 
 * Design Decision: Using simple tag overlap instead of vector embeddings
 * for MVP. If matching proves valuable, v1.0 will use Qdrant vectors.
 */
function calculateMatchScore(user1, user2) {
  // ...
}
```

### Testing Requirements

- **Unit tests required for:**
  - Matching algorithm (critical path)
  - Data validation functions
  - Utility functions
  
- **Integration tests required for:**
  - CSV upload endpoint
  - Matches API endpoint
  - Magic link authentication
  
- **Test location:** 
  - `server/__tests__/` for backend
  - `client/src/__tests__/` for frontend
  
- **Coverage target:** 80% for services, 60% for routes

---

## Confidence Scoring

### Required Format

After completing any subtask:

```markdown
## Confidence Score: X/10

### Criteria for X/10:

**Must-Have (Required for MVP):**
- [x] Feature functions as specified
- [x] Unit tests pass
- [x] Error handling present
- [x] Code is commented

**Nice-to-Have (Deferred to v1.0):**
- [ ] Performance optimized
- [ ] Advanced error messages

### Evidence:

Test Results:
```bash
$ npm test -- matching.test.js
✓ Should match users with overlapping skills (3ms)
✓ Should weight skills 2x interests (2ms)
...
12 tests passed
```

Manual Verification:
- Tested with sample data: [describe test]
- Edge cases verified: [list edge cases]
```

### Thresholds

- **8/10 minimum** for standard subtasks
- **9/10 required** for matching algorithm (core feature)
- **7/10 or below** requires immediate fixes before proceeding

---

## When to Ask Human for Help

### Always Ask:

1. **Matching Algorithm Logic**
   - Any changes to how matches are scored
   - Changes to match explanation prompts
   - Performance optimizations that might affect accuracy

2. **Data Handling**
   - CSV parsing decisions for edge cases
   - Data validation rules
   - How to handle malformed attendee data

3. **Security**
   - Magic link token generation
   - Rate limiting decisions
   - Any authentication-related code

4. **External Services**
   - Claude API prompt changes
   - Supabase configuration
   - Vercel deployment settings

5. **Scope Questions**
   - "This would be easier if we also built X"
   - "Should I include Y even though it's not in spec?"
   - "The requirement seems ambiguous about Z"

### Proceed Without Asking:

- Bug fixes with obvious solutions
- Adding test cases
- Improving comments
- Formatting/linting
- Documentation updates
- Performance improvements that don't change logic

---

## Technology-Specific Rules

### React (Frontend)

- Use functional components with hooks (no class components)
- Use Tailwind for styling (no CSS files)
- State management: useState/useContext only (no Redux for MVP)
- API calls: Use fetch in custom hooks
- Loading states: Every API call needs loading/error states

### Express (Backend)

- All routes go through `/server/routes/`
- Business logic in `/server/services/` (not in routes)
- Validation using express-validator
- Error responses: Always return `{ error: string, code: string }`
- Success responses: Always return `{ data: any, message?: string }`

### Supabase (Database)

- Use Prisma ORM for all database operations
- Migrations: Document in `/server/prisma/migrations/`
- Never expose service role key to frontend
- RLS policies: Not needed for MVP (magic link handles auth)

### Claude API

- All prompts in `/server/services/ai.js`
- Log token usage for cost tracking
- Handle rate limits with exponential backoff
- Maximum 1000 tokens per match explanation

---

## Quality Gates

### Before Marking Subtask Complete:

- [ ] Code runs without errors
- [ ] All existing tests still pass
- [ ] New functionality has tests
- [ ] Functions have complete docstrings
- [ ] Complex logic has inline comments
- [ ] No hardcoded secrets or API keys
- [ ] No console.log (except intentional debugging marked TODO)
- [ ] Error cases handled
- [ ] Confidence score documented at 8/10+

### Before Marking Task Complete:

- [ ] All subtasks complete with 8/10+
- [ ] Integration tested (subtasks work together)
- [ ] ROADMAP.md updated with completion status
- [ ] LEARNINGS.md updated if gotchas discovered

### Before Marking Phase Complete:

- [ ] All tasks complete
- [ ] Full integration test
- [ ] Success criteria met
- [ ] Documentation complete
- [ ] Ready for phase audit by separate Claude instance
```

---

## Document 4: TASK_TEMPLATE.md

### Purpose

TASK_TEMPLATE.md provides the **standard format for all task documentation**. Every subtask produces documentation following this template, ensuring:
- Consistent documentation across all work
- Easy review and audit
- Future developers can understand what was done

### Structure

```markdown
# Task Template

Use this format for documenting all subtask completion.

---

## [Subtask X.Y.Z]: [Subtask Name]

### Overview

**From Roadmap:** [Copy task description from ROADMAP]
**Dependencies:** [What must be complete first]
**Estimated Time:** [Original estimate]
**Actual Time:** [How long it actually took]

### Implementation Summary

[2-3 paragraph description of what was implemented and key decisions]

### Files Modified

| File | Change Type | Description |
|------|-------------|-------------|
| path/to/file.js | Created | [What this file does] |
| path/to/other.js | Modified | [What changed and why] |

### Key Decisions

1. **[Decision]:** [What was decided and why]
2. **[Decision]:** [What was decided and why]

### Testing

#### Unit Tests
```bash
[test command and output]
```

#### Manual Testing
- [ ] [Test case 1] - [Result]
- [ ] [Test case 2] - [Result]

### Confidence Score: X/10

**Criteria for X/10:**

Must-Have (Required):
- [x] [Criterion 1]
- [x] [Criterion 2]
- [ ] [Criterion not met - explain why acceptable]

Nice-to-Have (Deferred):
- [ ] [Enhancement for later]

**Evidence:**
[Screenshots, test outputs, or descriptions proving criteria met]

### Notes for Future Development

[Any gotchas, considerations for future work, or things to improve in v1.0]

### Next Steps

[What comes next based on this subtask completion]

---
```

### Complete TASK_TEMPLATE Example

Here's a completed task document:

```markdown
# Subtask 1.3.1: Implement Tag-Based Matching Algorithm

### Overview

**From Roadmap:** Create the core matching algorithm that identifies top 10 
matches for each attendee based on skills and interests overlap.

**Dependencies:** Task 1.2 complete (attendee data in database)
**Estimated Time:** 4 hours  
**Actual Time:** 5.5 hours (additional time for edge case handling)

### Implementation Summary

Implemented a tag-based matching algorithm in `/server/services/matching.js`. 
The algorithm calculates match scores between all attendee pairs using weighted 
overlap of skills and interests tags.

Key design decision: Skills are weighted 2x compared to interests because 
professional skill overlap creates more valuable networking opportunities at 
business conferences than hobby overlap. This weighting can be adjusted in 
v1.0 based on user feedback.

Performance: The algorithm runs in O(n²) time where n is the number of 
attendees. For MVP scale (100-500 attendees), this is acceptable (<2 seconds). 
For v1.0 with larger events, we'll need to implement vector similarity with 
Qdrant instead.

### Files Modified

| File | Change Type | Description |
|------|-------------|-------------|
| server/services/matching.js | Created | Core matching algorithm |
| server/services/matching.test.js | Created | Unit tests (12 tests) |
| server/routes/matches.js | Modified | Added `/api/matches/:attendeeId` endpoint |
| server/utils/scoring.js | Created | Helper functions for score calculation |

### Key Decisions

1. **Skills weighted 2x interests:** Professional connections are more valuable 
   at business conferences. Can adjust in v1.0 based on feedback.

2. **Simple tag overlap vs ML:** Chose simple overlap for MVP speed. If matching 
   proves valuable, v1.0 will use vector embeddings for semantic similarity.

3. **Top 10 limit:** Returns exactly 10 matches to avoid overwhelming users. 
   Can make configurable in v1.0.

4. **Tie-breaking:** When scores are equal, breaks ties by alphabetical name 
   for consistency. More sophisticated tie-breaking (e.g., goal alignment) 
   deferred to v1.0.

### Testing

#### Unit Tests
```bash
$ npm test -- matching.test.js

 PASS  server/services/matching.test.js
  Matching Algorithm
    ✓ should return empty array for attendee with no matches (3ms)
    ✓ should weight skills 2x compared to interests (2ms)
    ✓ should return top 10 matches only (4ms)
    ✓ should handle attendees with no skills (1ms)
    ✓ should handle attendees with no interests (2ms)
    ✓ should calculate correct score for full overlap (2ms)
    ✓ should calculate correct score for partial overlap (1ms)
    ✓ should not match attendee with themselves (1ms)
    ✓ should handle case-insensitive tag matching (3ms)
    ✓ should handle duplicate tags gracefully (2ms)
    ✓ should break ties consistently (2ms)
    ✓ should complete in <2s for 500 attendees (1847ms)

Test Suites: 1 passed, 1 total
Tests:       12 passed, 12 total
```

#### Manual Testing
- [x] Tested with 5 sample attendees - scores calculated correctly
- [x] Verified top 10 limit works
- [x] Tested edge case: attendee with unique skills (no matches)
- [x] Performance test: 500 attendees in 1.8 seconds

### Confidence Score: 9/10

**Criteria for 9/10:**

Must-Have (Required):
- [x] Algorithm returns top 10 matches per attendee
- [x] Skills weighted 2x compared to interests
- [x] Performance <2s for 500 attendees
- [x] All unit tests pass (12/12)
- [x] Edge cases handled (no skills, no interests, no matches)
- [x] Code fully commented with docstrings
- [x] No console.log statements
- [x] Error handling for invalid attendee IDs

Nice-to-Have (Deferred to v1.0):
- [ ] Vector similarity matching (using simple overlap for MVP)
- [ ] Configurable weights (hardcoded 2x for now)
- [ ] Semantic tag matching (exact match only for MVP)
- [ ] Caching for repeated queries

**Evidence:**

Test output shown above. Performance verified with 500 sample attendees.

Sample output for verification:
```json
{
  "attendeeId": "uuid-123",
  "matches": [
    { "matchedWith": "uuid-456", "score": 8, "rank": 1 },
    { "matchedWith": "uuid-789", "score": 7, "rank": 2 },
    // ... 8 more
  ],
  "calculationTime": "1823ms"
}
```

### Notes for Future Development

1. **Performance Ceiling:** O(n²) algorithm will hit performance issues above 
   ~1000 attendees. Plan to migrate to Qdrant vector similarity in v1.0 which 
   is O(n log n).

2. **Tag Normalization:** Currently doing exact match after lowercasing. 
   Consider adding:
   - Synonym handling ("JS" = "JavaScript")
   - Fuzzy matching for typos
   - Tag categories (skills vs interests automatic)

3. **Weight Adjustment:** The 2x weight for skills is a hypothesis. Add A/B 
   testing capability in v1.0 to optimize weights based on user feedback.

### Next Steps

1. ✅ Subtask 1.3.1 complete (this task)
2. → Subtask 1.3.2: Integrate Claude API for match explanations
3. → Subtask 1.3.3: Create matches API endpoint
4. → Subtask 1.3.4: Optimize for production performance
```

---

## Document 5: LEARNINGS.md

### Purpose

LEARNINGS.md is your **project-specific knowledge base**. It captures:
- Solutions to problems you've solved
- Gotchas and edge cases discovered
- Decisions and their rationale
- Anything a future task should know

This document grows throughout development. AI references it at the start of each task to avoid repeating mistakes or rediscovering solutions.

### How AI Uses LEARNINGS.md

**Pattern:**
1. AI starts new task
2. AI reads LEARNINGS.md
3. AI sees: "PostgreSQL has a gotcha with UUID ordering"
4. AI avoids that gotcha in current task

Without LEARNINGS, AI might hit the same issue every task. With LEARNINGS, knowledge compounds.

### Structure

```markdown
# Project Learnings

Running log of project-specific knowledge, solutions, and gotchas.
Updated during each task. Read at start of each new task.

---

## [Date]: [Topic]

**Context:** [When/why this came up]

**Learning:** [What we discovered]

**Solution:** [How we solved it]

**Future Reference:** [When this applies]

---

## [Date]: [Topic]

...
```

### Usage Rules

1. **Add entries during development** - When you solve something tricky, document it
2. **Keep entries concise** - Future AI needs quick reference, not essays
3. **Include code samples** - Show the solution, not just describe it
4. **Tag with context** - When does this apply?

### Complete LEARNINGS Example

```markdown
# NetworkMatch Learnings

Running log of project-specific knowledge, solutions, and gotchas.
Reference at start of each new task.

---

## 2024-12-03: Supabase UUID vs PostgreSQL UUID

**Context:** Setting up attendee table, UUIDs weren't sorting consistently

**Learning:** Supabase generates UUIDs using `gen_random_uuid()` but these 
don't sort chronologically. For pagination/ordering, need to use `uuid_generate_v1()` 
or add a separate `created_at` column.

**Solution:** Added `created_at TIMESTAMP DEFAULT NOW()` and use that for ordering 
instead of UUID.

```sql
CREATE TABLE attendees (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  created_at TIMESTAMP DEFAULT NOW(), -- Use this for ordering
  ...
);
```

**Future Reference:** Any table where we might need chronological ordering.

---

## 2024-12-04: CSV Parsing Edge Cases

**Context:** Testing CSV upload with real conference data

**Learning:** Real attendee CSVs have many edge cases:
- BOM characters at start of file (Excel exports)
- Mixed line endings (Windows vs Mac)
- Quoted fields with commas inside
- Empty rows at end
- Header row variations ("Email" vs "email" vs "E-mail")

**Solution:** Using Papa Parse with these options:

```javascript
Papa.parse(csvText, {
  header: true,
  skipEmptyLines: true,
  transformHeader: (h) => h.toLowerCase().replace(/[^a-z]/g, ''), // Normalize headers
  transform: (value) => value.trim() // Trim whitespace
});
```

Also pre-processing to strip BOM:
```javascript
const cleanCsv = csvText.replace(/^\uFEFF/, '');
```

**Future Reference:** Any CSV import feature.

---

## 2024-12-05: Claude API Rate Limits

**Context:** Generating match explanations for 200 attendees

**Learning:** Claude API has rate limits that cause 429 errors when generating 
many explanations sequentially. Each attendee needs 10 explanations = 2000 
API calls for 200 attendees.

**Solution:** 
1. Batch explanations (request 5 at once in single prompt)
2. Add exponential backoff on 429
3. Cache explanations in database

```javascript
async function withRetry(fn, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fn();
    } catch (err) {
      if (err.status === 429 && i < maxRetries - 1) {
        await sleep(Math.pow(2, i) * 1000); // 1s, 2s, 4s
        continue;
      }
      throw err;
    }
  }
}
```

**Future Reference:** Any feature making multiple Claude API calls.

---

## 2024-12-06: Match Score Caching Strategy

**Context:** Calculating matches for 500 attendees taking 2+ seconds

**Learning:** Recalculating all match scores on every request is wasteful. 
Scores only change when attendee data changes.

**Solution:** Cache match scores in database with invalidation:

```javascript
// Cache structure
{
  attendee_id: uuid,
  matches: json,  // Top 10 with scores
  calculated_at: timestamp,
  invalidated: boolean
}

// Invalidate when attendee updates
// Recalculate on next request if invalidated or older than 1 hour
```

**Future Reference:** Any expensive calculation that doesn't change frequently.

---

## 2024-12-07: Magic Link Token Security

**Context:** Implementing passwordless auth for attendees

**Learning:** Initial implementation used UUID for magic links, but UUIDs can be 
guessed with enough attempts. Need cryptographically secure tokens.

**Solution:** Using `crypto.randomBytes` for tokens:

```javascript
const crypto = require('crypto');

function generateMagicToken() {
  // 32 bytes = 256 bits of entropy, URL-safe encoding
  return crypto.randomBytes(32).toString('base64url');
}

// Tokens expire in 24 hours
// One-time use (delete after first use)
// Rate limit: max 3 tokens per email per hour
```

**Future Reference:** Any authentication or security tokens.

---

## 2024-12-08: React State Update After Unmount

**Context:** Match loading component showing console warnings

**Learning:** API call completing after component unmounts causes 
"Can't perform React state update on unmounted component" warning.

**Solution:** Using cleanup function in useEffect:

```javascript
function useMatches(attendeeId) {
  const [matches, setMatches] = useState(null);
  
  useEffect(() => {
    let cancelled = false;
    
    fetchMatches(attendeeId).then(data => {
      if (!cancelled) {  // Only update if still mounted
        setMatches(data);
      }
    });
    
    return () => { cancelled = true; };  // Cleanup on unmount
  }, [attendeeId]);
  
  return matches;
}
```

**Future Reference:** Any async operation in React components.

---

## Quick Reference

### Common Gotchas

| Issue | Solution | See Entry |
|-------|----------|-----------|
| CSV BOM characters | Strip with regex | 2024-12-04 |
| UUID ordering | Use created_at column | 2024-12-03 |
| Claude 429 errors | Exponential backoff | 2024-12-05 |
| React unmount warnings | Cancelled flag in useEffect | 2024-12-08 |

### Patterns We Use

| Pattern | Location | Notes |
|---------|----------|-------|
| API retry with backoff | server/utils/retry.js | Max 3 retries |
| Cache invalidation | server/services/cache.js | TTL + event-based |
| Magic link auth | server/services/auth.js | 24h expiry |
```

---

## Using LEARNINGS Effectively

### When to Add Entries

Add a learning when you:
- Solve a bug that took significant debugging
- Discover an edge case not obvious from documentation
- Make a decision that future tasks should know about
- Find a pattern that should be reused
- Hit a limitation that required a workaround

### When AI Should Reference

AI should check LEARNINGS when:
- Starting any new task (always)
- Encountering an error (might be documented)
- Implementing something similar to past work
- Making decisions that might conflict with past decisions

### Keep It Useful

**Good Entry:**
```markdown
## 2024-12-04: PostgreSQL JSONB Array Queries

**Learning:** Querying JSON arrays in PostgreSQL requires specific syntax
**Solution:** Use `@>` operator for contains: `WHERE skills @> '["React"]'::jsonb`
**Future Reference:** Any query filtering by skills or interests arrays
```

**Bad Entry:**
```markdown
## 2024-12-04: Fixed Bug

Fixed the thing that was broken. Used some code to fix it.
```

The good entry is searchable, specific, and actionable. The bad entry adds noise.

---

::: tip The LEARNINGS Compound Effect
After 3-4 weeks of development, your LEARNINGS.md becomes incredibly valuable.
Every new task benefits from all previous debugging and discovery work.

This is how you build an AI that "knows your project"—not through magic, 
but through systematic knowledge capture.
:::

---

## Optional Documents

Beyond the five core documents, complex projects may benefit from additional documentation:

### TECHNICAL_DECISIONS.md

**When to Use:** Projects with significant architectural decisions that need detailed rationale.

**Purpose:** Captures the "why" behind major technical choices. More detailed than README architecture section.

```markdown
# Technical Decisions

## Decision 1: [Technology/Approach]

**Date:** [When decided]
**Status:** Accepted / Superseded / Deprecated

### Context
[What situation required this decision]

### Options Considered
1. **[Option A]:** [Description]
   - Pros: [advantages]
   - Cons: [disadvantages]
   
2. **[Option B]:** [Description]
   - Pros: [advantages]
   - Cons: [disadvantages]

### Decision
[What we decided and why]

### Consequences
[What this enables, what this prevents, what we'll need to watch for]

---

## Decision 2: [Technology/Approach]
...
```

**Example Entry:**
```markdown
## Decision: Use Tag Overlap vs Vector Embeddings for Matching

**Date:** 2024-12-01
**Status:** Accepted (for MVP, revisit in v1.0)

### Context
Need to match conference attendees based on skills and interests. Matching 
quality directly impacts product value.

### Options Considered

1. **Simple Tag Overlap**
   - Pros: Simple to implement, fast, easy to debug
   - Cons: No semantic understanding ("JavaScript" ≠ "JS")
   
2. **Vector Embeddings (Qdrant)**
   - Pros: Semantic similarity, handles synonyms
   - Cons: Complex setup, slower, harder to debug
   
3. **LLM-Based Matching**
   - Pros: Most sophisticated matching
   - Cons: Slow, expensive, unpredictable

### Decision
Use simple tag overlap for MVP. If matching proves valuable and users 
complain about quality, upgrade to vector embeddings in v1.0.

### Consequences
- Fast MVP development (2 days vs 1 week)
- Must handle case normalization manually
- Need to revisit after user feedback
- Can't match "React developer" with "Frontend engineer" semantically
```

### ARCHITECTURE.md

**When to Use:** Projects with complex system architecture that needs visual/detailed explanation.

**Purpose:** Deep dive into system design, data flow, component relationships.

```markdown
# Architecture

## System Overview

[High-level diagram or description]

## Components

### [Component 1]
**Responsibility:** [What it does]
**Dependencies:** [What it needs]
**Exposes:** [What it provides]

### [Component 2]
...

## Data Flow

[How data moves through the system]

## Security Architecture

[How security is handled]

## Scalability Considerations

[How the system would scale]
```

### API_SPEC.md

**When to Use:** Projects with APIs that need detailed documentation.

**Purpose:** API contract documentation for frontend developers or external consumers.

```markdown
# API Specification

## Base URL
`https://api.example.com/v1`

## Authentication
[How to authenticate]

## Endpoints

### POST /auth/login
Login with email and password.

**Request:**
```json
{
  "email": "user@example.com",
  "password": "secret"
}
```

**Response (200):**
```json
{
  "data": {
    "token": "jwt_token_here",
    "expiresAt": "2024-12-10T12:00:00Z"
  }
}
```

**Errors:**
- 400: Invalid request body
- 401: Invalid credentials
- 429: Rate limited

### GET /matches/:attendeeId
...
```

### DEFERRED_FEATURES.md

**When to Use:** When you have many features to track across phases.

**Purpose:** Detailed tracking of all deferred features with context.

```markdown
# Deferred Features

## v1.0 Features

### User Authentication
**Priority:** High
**Why Deferred:** MVP validates matching without accounts
**Prerequisites:** None
**Estimated Effort:** 1 week
**Notes:** Plan to use OAuth (Google/GitHub) not email/password

### Rich Profiles
**Priority:** Medium
**Why Deferred:** Basic profiles sufficient for MVP matching
**Prerequisites:** User authentication
**Estimated Effort:** 3-4 days
**Notes:** Photos, bio, LinkedIn integration

## Production Features

### Mobile Apps
**Priority:** Medium
**Why Deferred:** Need to validate web version first
**Prerequisites:** v1.0 complete and successful
**Estimated Effort:** 6-8 weeks
**Notes:** Consider React Native for code sharing

## Maybe Never

### AI Chatbot
**Priority:** Low
**Why Deferred:** Users might prefer simple messaging
**Prerequisites:** Evidence that users want this
**Estimated Effort:** 2-3 weeks
**Notes:** Validate need before building
```

---

## Prompts to Generate Documents

You don't need to write these documents from scratch. After your brainstorming session, use these prompts with Claude:

### Generating README.md

```markdown
Based on our brainstorming session, please create a README.md for this project.

Project Summary:
- Name: [Project name]
- MVP scope: [What we're building first]
- Full vision: [What this could become]
- Tech stack: [Decided technologies]

Use this structure:
[Paste README template from earlier in this chapter]

Include:
- Clear vision section (full scope)
- Current phase section (MVP only)
- Deferred features (what's NOT in MVP)
- Architecture overview
- Setup instructions (can be placeholder for now)
- Future phases section
```

### Generating ROADMAP.md

```markdown
Based on our brainstorming session, please create a ROADMAP.md.

Project: [Name]
MVP Features: [List from brainstorming]
Timeline: [X weeks]

Break down the MVP into:
- Tasks (logical groups of work)
- Subtasks (individual Cline sessions, 30-90 minutes each)

Each subtask should:
- Be completable in one session
- Touch ≤5 files
- Have clear success criteria
- Be testable in isolation

Use this structure:
[Paste ROADMAP template from earlier in this chapter]
```

### Generating CLAUDE_RULES.md

```markdown
Please create CLAUDE_RULES.md for this project.

Project Context:
- Building: [What the project is]
- Phase: [MVP/v1.0/Production]
- Tech stack: [Technologies used]

I want the AI to:
- Write comprehensive comments (50% comments, 50% code)
- Document every function with docstrings
- Use confidence scoring (8/10 minimum)
- Ask for help on: [security decisions, architectural changes, etc.]
- Follow these patterns: [any specific patterns]

Use this structure:
[Paste CLAUDE_RULES template from earlier in this chapter]
```

### Generating TASK_TEMPLATE.md

```markdown
Create a TASK_TEMPLATE.md that will be used for documenting all subtask 
completion in this project.

The template should include:
- Task overview (from roadmap reference)
- Implementation summary
- Files modified
- Key decisions
- Testing (unit and manual)
- Confidence scoring format
- Notes for future development
- Next steps

Use this structure:
[Paste TASK_TEMPLATE from earlier in this chapter]
```

### Generating LEARNINGS.md (Starter)

```markdown
Create an initial LEARNINGS.md file for this project.

Project: [Name]
Tech stack: [Technologies]

Include:
- Header explaining what this file is for
- Structure for entries (date, context, learning, solution, future reference)
- One placeholder entry showing the format
- Quick reference section (empty, to be filled)

The file should be ready for adding entries during development.
```

---

## Creating Your Document Set

### Workflow Overview

Here's the complete workflow from brainstorming to ready-for-development:

```
1. BRAINSTORMING SESSION (30-90 min)
   └── Output: MVP scope, technical decisions, deferred features
   
2. DOCUMENT GENERATION (1-2 hours)
   ├── Generate README.md from brainstorming
   ├── Generate ROADMAP.md with tasks/subtasks
   ├── Generate CLAUDE_RULES.md with standards
   ├── Generate TASK_TEMPLATE.md 
   └── Create empty LEARNINGS.md
   
3. REVIEW & REFINE (30-60 min)
   ├── Review each document
   ├── Adjust task sizing
   ├── Clarify ambiguous sections
   └── Ensure consistency across docs
   
4. START DEVELOPMENT
   └── First task: "Can we please plan Task 1.1?"
```

### Document Set Verification Checklist

Before starting development, verify:

**README.md:**
- [ ] Vision clearly states full scope
- [ ] Current phase clearly states MVP scope
- [ ] Deferred features listed with phase assignments
- [ ] Tech stack documented
- [ ] Project structure documented
- [ ] Setup instructions present (can be basic)

**ROADMAP.md:**
- [ ] All phases listed with goals
- [ ] MVP broken into tasks
- [ ] Tasks broken into subtasks
- [ ] Subtasks sized for single session (30-90 min)
- [ ] Dependencies noted
- [ ] Status tracking ready

**CLAUDE_RULES.md:**
- [ ] Commenting standards defined
- [ ] Testing requirements specified
- [ ] Confidence scoring format shown
- [ ] "Ask for help" scenarios listed
- [ ] Technology-specific rules included
- [ ] Quality gates defined

**TASK_TEMPLATE.md:**
- [ ] Template structure complete
- [ ] Example provided
- [ ] Confidence scoring section included

**LEARNINGS.md:**
- [ ] Structure for entries defined
- [ ] Ready for first entry

---

## Technology-Specific Variations

### React + Node.js Stack

```markdown
# CLAUDE_RULES.md - React/Node Additions

## React Rules
- Functional components only (no class components)
- Use hooks: useState, useEffect, useContext
- Custom hooks for shared logic (useApi, useAuth, etc.)
- Tailwind for styling
- Component file structure: ComponentName/index.tsx, ComponentName.test.tsx

## Node.js Rules  
- Express for API
- Routes handle HTTP, services handle logic
- Environment variables via dotenv
- Use async/await, not callbacks
- Error middleware at end of chain
```

### Python + FastAPI Stack

```markdown
# CLAUDE_RULES.md - Python/FastAPI Additions

## Python Rules
- Type hints required on all functions
- Pydantic models for request/response schemas  
- Use async def for endpoints
- Black for formatting, isort for imports
- Pytest for testing

## FastAPI Rules
- Routers go in /routers directory
- Services go in /services directory
- SQLAlchemy for ORM
- Alembic for migrations
- Use dependency injection for database sessions
```

### Desktop App (Electron) Stack

```markdown
# CLAUDE_RULES.md - Electron Additions

## Electron Rules
- Main process code in /main
- Renderer process code in /renderer
- IPC for main↔renderer communication
- Preload scripts for security
- Context isolation enabled

## Special Considerations
- Consider using triple-doc pattern (README, CHANGELOG, IMPLEMENTATION per subtask)
- Test on all target platforms
- Handle native module compatibility
```

---

## From Brainstorming to Documents: Example Flow

Here's how the NetworkMatch project went from brainstorming to documents:

### Brainstorming Output (Summary)

```
MVP Scope:
- CSV import for attendees
- Tag-based matching
- Top 10 matches with explanations
- Magic link access
- Feedback collection

Technical Decisions:
- React + Node
- Supabase (PostgreSQL)
- Claude API for explanations
- Vercel hosting

Deferred:
- User accounts → v1.0
- Vector matching → v1.0
- Mobile apps → Production
```

### Document Generation Session

**Prompt:**
```
Based on this brainstorming summary, please create:
1. README.md
2. ROADMAP.md  
3. CLAUDE_RULES.md

[Pasted templates and brainstorming summary]
```

**Result:** AI generated initial versions of all three documents in ~10 minutes.

### Review & Refinement

After AI generated documents, I reviewed and adjusted:

1. **ROADMAP subtask sizing:** Task 1.3 (Matching) was too big—split into 4 subtasks
2. **CLAUDE_RULES specifics:** Added Express error response format
3. **README clarity:** Expanded "What's NOT Included" section

### Ready for Development

Total time from end of brainstorming to ready-for-development: **~2 hours**

---

## Common Documentation Mistakes

### Mistake 1: Vague Subtasks

**Bad:**
```markdown
| Subtask | Description |
|---------|-------------|
| 1.2.1 | Work on matching |
```

**Good:**
```markdown
| Subtask | Description |
|---------|-------------|
| 1.2.1 | Implement tag-based matching algorithm that returns top 10 matches |
```

**Why it matters:** AI needs clear success criteria. "Work on matching" could mean anything.

### Mistake 2: Missing "Why" in CLAUDE_RULES

**Bad:**
```markdown
- Use PostgreSQL
```

**Good:**
```markdown
- Use PostgreSQL (not MongoDB) because:
  - Structured data (attendees, matches) benefits from relational model
  - Supabase provides PostgreSQL with built-in auth
  - Team has more PostgreSQL experience
```

**Why it matters:** Future tasks might question the decision without context.

### Mistake 3: Forgetting to Update LEARNINGS

If you solve a tricky bug but don't document it, you (or AI) might hit it again.

**Good practice:** At end of each task, ask AI:
```
Were there any gotchas or lessons from this task that should go in LEARNINGS.md?
```

### Mistake 4: Over-Detailed Documents

Documents that are too long become useless—AI won't read through 50 pages.

**Rule of thumb:**
- README: 1-3 pages
- ROADMAP: As long as needed for tasks, but subtask descriptions short
- CLAUDE_RULES: 2-4 pages
- LEARNINGS: Grows over time, but entries stay concise

---

## Summary: Your Documentation Checklist

Before starting any development, ensure you have:

### Five Core Documents

| Document | Status | Notes |
|----------|--------|-------|
| README.md | [ ] | Vision, current phase, setup |
| ROADMAP.md | [ ] | Phases, tasks, subtasks |
| CLAUDE_RULES.md | [ ] | Standards, quality gates |
| TASK_TEMPLATE.md | [ ] | Format for task docs |
| LEARNINGS.md | [ ] | Empty, ready for entries |

### Quality Verification

| Check | Status |
|-------|--------|
| Subtasks are 30-90 min each | [ ] |
| Success criteria are measurable | [ ] |
| Deferred features documented | [ ] |
| Tech decisions have rationale | [ ] |
| Confidence scoring explained | [ ] |

### Ready for Development When

- [ ] "Can we please plan Task 1.1?" would make sense to AI
- [ ] AI can find all context it needs in documents
- [ ] You could hand project to another developer with just these docs

---

::: tip The Documentation Investment
These 2-4 hours of documentation seem like a lot upfront. But consider:

- Every task execution goes faster because AI has context
- Every debugging session benefits from LEARNINGS
- Every scope question points to ROADMAP
- Every quality question points to CLAUDE_RULES

You're not writing documentation for documentation's sake. You're building the 
structure that makes AI-assisted development actually work.
:::

---

**Next:** [Chapter 5: The Cline Workflow](/part-3/cline-workflow) — How to execute tasks using the Plan → Act cycle with your documentation in place.
