---
title: The Cline Workflow
description: Mastering the Plan → Act cycle for systematic AI-assisted development
---

# Chapter 5: The Cline Workflow

## TLDR

**The Core Pattern:** Plan → Act cycle with a new chat for each task. This simple pattern is the foundation of systematic AI-assisted development.

**Why It Works:**
- **New chat per task** prevents context pollution—AI doesn't get confused by unrelated previous work
- **Plan Mode first** ensures AI understands the task before executing
- **Act Mode execution** with terminal approval keeps you in control
- **Minimal prompting** works because AI references your documentation

**The Workflow:**
1. Open new Cline chat
2. Say: "Can we please plan [task name from roadmap]?"
3. Review the plan, ask questions, adjust if needed
4. Switch to Act Mode
5. Approve terminal commands as needed
6. Verify confidence score ≥ 8/10
7. Close chat, move to next task

**Key Insight:** You don't need elaborate prompts. With proper documentation in place (README, ROADMAP, CLAUDE_RULES), a simple "Can we please plan task X?" is enough. The AI reads your docs and understands context automatically.

**Time per Task:** Most subtasks take 30-90 minutes including planning, execution, and verification.

---

## The Core Cycle

### The Pattern

Every task in your ROADMAP follows the same cycle:

```
┌─────────────────────────────────────────────────────────────┐
│                    NEW CLINE CHAT                           │
│                         │                                    │
│                         ▼                                    │
│  ┌─────────────────────────────────────────────────────┐    │
│  │               PLAN MODE                              │    │
│  │  "Can we please plan task X?"                       │    │
│  │  AI reads docs → Creates plan → You review          │    │
│  └─────────────────────────────────────────────────────┘    │
│                         │                                    │
│                    ▼ (When satisfied)                        │
│  ┌─────────────────────────────────────────────────────┐    │
│  │               ACT MODE                               │    │
│  │  AI executes → You approve terminals                │    │
│  │  AI tests → You verify                              │    │
│  └─────────────────────────────────────────────────────┘    │
│                         │                                    │
│                         ▼                                    │
│  ┌─────────────────────────────────────────────────────┐    │
│  │            COMPLETION                                │    │
│  │  Confidence score → Documentation → Close chat      │    │
│  └─────────────────────────────────────────────────────┘    │
│                         │                                    │
│                         ▼                                    │
│                  NEXT TASK (New Chat)                        │
└─────────────────────────────────────────────────────────────┘
```

### Why This Specific Pattern

**Plan Mode First:**
- AI thinks through the approach before writing code
- You catch misunderstandings early
- Adjustments are cheap (just conversation) vs expensive (rewriting code)

**Act Mode Second:**
- Execution happens only after alignment
- You've already agreed on the approach
- AI proceeds with confidence

**New Chat Each Time:**
- Fresh context for focused work
- No pollution from unrelated tasks
- Documentation provides continuity, not chat history

---

## Why New Chat Per Task

This is perhaps the most counterintuitive aspect of the methodology. Why throw away context?

### The Context Pollution Problem

**What happens in long conversations:**

```
Message 1-20: Set up database
  - AI learns: "We're using PostgreSQL with Prisma"
  - AI learns: Variable naming conventions
  - AI learns: Error handling patterns

Message 21-50: Build authentication
  - AI still remembers database setup
  - Context is coherent

Message 51-100: Build matching algorithm
  - AI is getting confused
  - References to "the function" are ambiguous
  - Which error handling pattern again?

Message 101-150: Build user interface
  - AI occasionally contradicts earlier decisions
  - "As we discussed" references wrong discussion
  - Performance degradation (long context)

Message 151+: Debug and fix
  - Complete confusion
  - AI suggests solutions that conflict with architecture
  - You're spending more time correcting AI than coding
```

**This is context pollution.** The conversation becomes a tangled mess where AI can't distinguish between:
- Current task requirements
- Previous task implementations
- Old discussions that were superseded
- Debugging tangents that aren't relevant anymore

### The New Chat Solution

**With new chat per task:**

```
Chat 1: Database Setup
  - Focused context: Just database
  - References: README, ROADMAP, CLAUDE_RULES
  - Output: Working database, documented in task docs
  - CLOSED ✓

Chat 2: Authentication
  - Fresh context: Just authentication
  - References: README, ROADMAP, CLAUDE_RULES, Task 1 docs
  - Output: Working auth, documented
  - CLOSED ✓

Chat 3: Matching Algorithm
  - Fresh context: Just matching
  - References: README, ROADMAP, CLAUDE_RULES, LEARNINGS
  - Output: Working matching, documented
  - CLOSED ✓
```

**Each chat:**
- Starts fresh (no pollution)
- Loads context from documentation (consistent)
- Focuses on one task (clarity)
- Produces documentation (continuity for next task)

### What About Continuity?

"But won't AI forget everything from previous tasks?"

**No—because continuity comes from documentation, not chat history.**

When AI starts a new chat, it reads:
- **README.md** — Project overview and current phase
- **ROADMAP.md** — What task we're working on
- **CLAUDE_RULES.md** — Development standards
- **LEARNINGS.md** — Project-specific knowledge
- **Task docs** — What was done in previous tasks

This is actually BETTER than chat history because:
- Documentation is curated (important stuff only)
- Documentation is structured (easy to reference)
- Documentation persists (survives chat closure)
- Documentation is reviewable (you can verify it)

### When to Make Exceptions

Very rarely, you might continue a chat:

**Continue when:**
- Debugging an issue from the same task
- Iterating on a plan before executing
- Fixing something that was just built

**Start new chat when:**
- Moving to a new subtask
- Coming back after a break
- Task is logically complete but needs fixes

**Rule of thumb:** If in doubt, start a new chat. The cost of a slightly longer context load is much less than the cost of confusion.

---

## The Minimal Prompting Technique

### Why Simple Prompts Work

You might expect elaborate prompts like:

```
❌ Over-engineered prompt:

"I need you to implement the user authentication system for my 
conference networking application. We're using React for the 
frontend with styled-components for styling, and Express with 
Node.js for the backend. The database is PostgreSQL accessed 
through Prisma ORM. Please implement email/password authentication 
with JWT tokens, include proper validation, error handling, and 
make sure to add comprehensive comments. The tokens should expire 
after 24 hours and we need refresh token functionality. Also 
implement rate limiting to prevent brute force attacks. Follow 
the patterns established in the existing codebase and make sure 
to write unit tests for all new functionality."
```

This prompt is problematic because:
- It duplicates information already in your docs
- It might contradict decisions documented elsewhere
- It's hard to maintain consistency across tasks
- Different prompts for each task = different standards

### The Better Approach

```
✅ Minimal prompt:

"Can we please plan task 2.3 - Implement User Authentication?"
```

That's it. This works because:

1. **AI reads your ROADMAP.md** and sees:
```markdown
### Task 2.3: Implement User Authentication
Description: Email/password auth with JWT tokens
Dependencies: Task 2.2 complete
```

2. **AI reads your README.md** and understands:
- Tech stack (React, Express, PostgreSQL, Prisma)
- Current phase (MVP)
- Project goals

3. **AI reads your CLAUDE_RULES.md** and follows:
- Commenting standards (50% comments)
- Testing requirements
- Error handling patterns
- When to ask for clarification

4. **AI reads your LEARNINGS.md** and avoids:
- Previous mistakes
- Known gotchas
- Established patterns

**Result:** AI creates a comprehensive plan that's consistent with all your documentation—without you repeating it.

### What AI Does Automatically

When you say "Can we please plan task X?", Cline:

1. **Scans project files** — README, ROADMAP, CLAUDE_RULES, etc.
2. **Identifies task context** — What's this task about?
3. **Loads relevant code** — What files will be affected?
4. **Creates a plan** — Steps to accomplish the task
5. **Asks clarifying questions** — If anything is ambiguous

### When to Provide More Context

Sometimes minimal prompts aren't enough:

**Add context when:**
- Task involves external APIs (provide API docs or links)
- You have specific preferences not in CLAUDE_RULES
- Previous task had issues that affect this one
- Requirements have changed since documentation

**Example with additional context:**
```
"Can we please plan task 3.2 - Claude API Integration?

Note: The API documentation is at https://docs.anthropic.com
We should use claude-sonnet-4-20250514 for cost efficiency.
In the last task, we discovered rate limits require exponential 
backoff—see LEARNINGS.md entry from yesterday."
```

### The "Just Enough" Principle

Provide just enough context for AI to succeed:
- Too little → AI might misunderstand
- Too much → You're doing AI's job, might cause conflicts

**Ask yourself:** "Is this information in my docs?" If yes, don't repeat it. If no, either add it to docs OR mention it in the prompt.

---

## Plan Mode Workflow

### What Happens in Plan Mode

When you start in Plan Mode, Cline:

1. **Reads project documentation**
2. **Analyzes relevant code files**
3. **Creates a proposed plan**
4. **Presents it for your review**

### The Plan Structure

A typical plan looks like:

```markdown
## Plan for Task 2.3: Implement User Authentication

### Understanding
Based on ROADMAP.md, this task involves:
- Creating login/register endpoints
- JWT token generation and validation
- Password hashing with bcrypt

Tech stack from README.md:
- Backend: Express + Prisma
- Database: PostgreSQL

### Proposed Approach

1. **Create User model in Prisma**
   - email (unique)
   - passwordHash
   - createdAt, updatedAt

2. **Create auth service** (`server/services/auth.js`)
   - hashPassword()
   - verifyPassword()
   - generateToken()
   - verifyToken()

3. **Create auth routes** (`server/routes/auth.js`)
   - POST /api/auth/register
   - POST /api/auth/login
   - POST /api/auth/refresh

4. **Create auth middleware**
   - requireAuth middleware for protected routes

5. **Write tests**
   - Unit tests for auth service
   - Integration tests for endpoints

### Questions Before Proceeding

1. Should refresh tokens be stored in database or use rotating tokens?
2. What should token expiration be? (24h mentioned in earlier docs)
3. Any rate limiting requirements for MVP?

### Estimated Time
2-3 hours

Would you like me to proceed with this approach, or should we adjust anything?
```

### Reviewing the Plan

When you see the plan, check for:

**✅ Alignment with documentation:**
- Does it match what ROADMAP specifies?
- Does it follow CLAUDE_RULES standards?
- Is it consistent with previous decisions?

**✅ Completeness:**
- Are all requirements addressed?
- Are edge cases considered?
- Are tests included?

**✅ Scope:**
- Is it staying within MVP bounds?
- Is it not doing extra work?
- Is it sized appropriately?

### Adjusting the Plan

If something's off, just say so:

```
"Good plan, but a few adjustments:

1. Let's use 24h expiry for tokens, with refresh tokens stored in 
   database (we'll want to revoke them later)
   
2. Skip rate limiting for MVP - we'll add it in Phase 2

3. Password requirements: minimum 8 characters, one uppercase, 
   one number (add validation)

With those changes, please proceed."
```

AI will acknowledge adjustments and either:
- Update the plan for your confirmation
- Proceed directly if changes are minor

### When Plan Mode Is Valuable

Plan Mode is especially valuable when:

- **Complex tasks** — Multiple components or files
- **Architectural decisions** — Choices that affect future work
- **Unclear requirements** — You need to discuss before building
- **Learning** — You want to understand the approach

For trivial tasks, you might say:
```
"Can we please plan task 4.1 - Update README with setup instructions?

This is straightforward, so if the plan looks obvious, 
go ahead and switch to Act Mode."
```

---

## Act Mode Workflow

### Switching to Act Mode

Once you're satisfied with the plan:

```
"The plan looks good. Please proceed with Act Mode."
```

Or simply:
```
"Looks good, proceed."
```

Cline switches modes and begins execution.

### What Happens in Act Mode

In Act Mode, Cline:

1. **Creates/modifies files** according to the plan
2. **Runs terminal commands** (with your approval)
3. **Tests the implementation**
4. **Documents the work**
5. **Provides confidence score**

### Monitoring Execution

While AI executes, you'll see:

- **File changes** — Watch what's being created/modified
- **Terminal requests** — Commands AI wants to run
- **Progress updates** — What step is being executed
- **Questions** — If AI encounters ambiguity

### Your Role During Execution

You're not passive. During Act Mode:

- **Approve terminal commands** — AI can't run them without you
- **Answer questions** — If AI asks for clarification
- **Spot check changes** — Glance at code being written
- **Intervene if needed** — Stop if something's wrong

### When to Intervene

Stop execution if you see:

- **Wrong direction** — AI misunderstood something
- **Dangerous command** — Command that could cause damage
- **Scope creep** — AI building more than requested
- **Quality issues** — Obviously bad code patterns

How to intervene:
```
"Stop for a moment. I see you're creating a MongoDB connection,
but we decided on PostgreSQL. Let's review the plan."
```

AI will stop, acknowledge the issue, and either correct course or ask for guidance.

---

## Terminal Approval Best Practices

### The Approval Flow

When AI needs to run a terminal command, you'll see something like:

```
Cline wants to run this command:
npm install bcrypt jsonwebtoken @prisma/client

[Approve] [Reject] [Edit]
```

Your options:
- **Approve** — Run as-is
- **Reject** — Don't run, explain why
- **Edit** — Modify command before running

### Commands to Approve Quickly

**Safe to approve without deep review:**

```bash
# Package installations (review list briefly)
npm install [packages]
pip install [packages]

# Running tests
npm test
pytest

# Development servers
npm run dev
python manage.py runserver

# Linting/formatting
npm run lint
black .

# Type checking
npx tsc --noEmit

# Database migrations (dev only)
npx prisma migrate dev
```

### Commands to Review Carefully

**Review before approving:**

```bash
# Any file deletion
rm -rf [anything]
find . -delete

# Git operations
git reset --hard
git push --force
git clean -fd

# Database operations
DROP TABLE
DELETE FROM [table]
TRUNCATE

# System-level operations
sudo [anything]
chmod -R 777

# Network operations
curl [unknown URLs]
wget [unknown URLs]

# Package manager globals
npm install -g
pip install --system
```

### Commands to Reject

**Reject and discuss:**

```bash
# Production database access from dev
psql production_database

# Installing suspicious packages
npm install [package-you-don't-recognize]

# Exposing secrets
echo $API_KEY

# Modifying system files
rm /etc/[anything]
```

**When rejecting:**
```
"Rejecting this command. Why are we accessing production database 
from development environment? Let's discuss."
```

### Red Flags in Commands

Watch for:
- **Production references** in dev context
- **Recursive deletes** without specific paths
- **Force flags** (--force, -f) on destructive operations
- **Unknown packages** being installed
- **Hardcoded secrets** in commands
- **System paths** being modified

---

## Visual Verification

### When Tests Aren't Enough

Automated tests catch functional issues but miss:
- **UI rendering problems** — Component displays but looks wrong
- **UX issues** — Flow works but feels broken
- **Visual bugs** — Layout issues, missing styles
- **State issues** — UI doesn't update as expected

### Prompting for Visual Checks

After AI completes a UI task:

```
"Before we finalize, can you describe what I should see when I:
1. Open the login page
2. Enter valid credentials
3. Submit the form

I'll verify visually and let you know."
```

AI responds:
```markdown
## Expected Visual Flow

### 1. Login Page (localhost:3000/login)
- Centered card with logo at top
- Email input field with placeholder "Email address"
- Password input with "Password" placeholder  
- "Remember me" checkbox
- Blue "Sign In" button (full width)
- "Forgot password?" link below button

### 2. After Entering Credentials
- Email shows entered value
- Password shows dots (obscured)
- No validation errors visible yet

### 3. After Clicking Submit
- Button shows "Signing in..." with spinner
- After 1-2 seconds:
  - Success: Redirects to /dashboard
  - Failure: Red error message above form

Please verify and let me know if anything differs.
```

### How to Report Visual Issues

If something differs:
```
"Visual check results:

✅ Login page layout looks correct
✅ Form styling is good
❌ After submit, button doesn't show spinner (just freezes)
❌ Error message appears below the button, not above

Please fix these UI issues."
```

AI will address the specific visual problems.

### Screenshot Documentation

For important UI states, consider:
```
"This looks good. For documentation purposes, I'm taking a 
screenshot of the login flow. Please note in the task docs 
that visual verification passed."
```

---

## Task Completion

### The Completion Checklist

Before closing a chat, verify:

**1. Functional Requirements Met**
- Does the feature work as specified?
- Have you tested the happy path?
- Have you tested error cases?

**2. Quality Requirements Met**
- Code is properly commented?
- Tests are written and passing?
- Error handling is present?
- No console errors or warnings?

**3. Documentation Updated**
- Task documentation created?
- LEARNINGS.md updated if needed?
- ROADMAP.md status updated?

**4. Confidence Score Acceptable**
- Score is 8/10 or higher?
- Criteria clearly defined?
- Evidence provided?

### Confidence Score Review

At the end of each task, AI should provide:

```markdown
## Confidence Score: 8/10

### Criteria for 8/10:

**Must-Have Requirements:**
- [x] User can register with email/password
- [x] User can login and receive JWT
- [x] Invalid credentials return proper error
- [x] Tokens expire after 24 hours
- [x] Unit tests pass (12/12)
- [x] Code is fully commented
- [x] Error messages are user-friendly

**Nice-to-Have (Not Required for MVP):**
- [ ] Refresh token rotation
- [ ] Rate limiting
- [ ] Password strength meter UI

### Evidence:
[Test output, manual verification notes, etc.]

### Notes:
Rate limiting deferred to Phase 2 per ROADMAP.
Refresh token rotation can be added if security audit requires it.
```

### When Score Is Too Low

If score is below 8/10:

```markdown
## Confidence Score: 6/10

### What's Missing:
- Token expiration not tested
- No integration tests
- Error handling incomplete for network failures

### To Reach 8/10:
1. Add token expiration tests
2. Write 3 integration tests for auth endpoints
3. Add try/catch for network errors in login

Shall I continue to address these gaps?
```

**Your response:**
```
"Yes, please address all three gaps. We need 8/10 before 
proceeding to the next task."
```

### Closing the Chat

Once everything checks out:

```
"Looks good. Confidence score of 8/10 is acceptable for this task.

Please provide final summary for documentation, then we're done."
```

AI provides summary:
```markdown
## Task 2.3 Complete: User Authentication

### Implemented:
- User registration (email/password)
- User login with JWT (24h expiry)
- Auth middleware for protected routes
- Comprehensive error handling
- 15 unit tests, 5 integration tests

### Files Created/Modified:
- server/services/auth.js (new)
- server/routes/auth.js (new)
- server/middleware/requireAuth.js (new)
- server/prisma/schema.prisma (modified - added User model)
- server/__tests__/auth.test.js (new)

### Confidence: 8/10

### Notes for Future Tasks:
- Rate limiting should be added in Phase 2
- Consider 2FA if security audit requests it

Ready for Task 2.4.
```

**Then close the chat and open a new one for the next task.**

---

## Complete Walkthrough: Three Tasks Start to Finish

Let me walk through three consecutive tasks to show the full pattern.

### Task 1: Database Setup

**Opening the chat:**
```
You: Can we please plan task 1.1 - Initialize Database?
```

**AI Plan:**
```
Based on ROADMAP.md, this task involves:
- Setting up PostgreSQL with Prisma
- Creating initial schema
- Configuring environment variables

Proposed steps:
1. Install Prisma dependencies
2. Initialize Prisma with PostgreSQL
3. Create basic schema (User model placeholder)
4. Run initial migration
5. Create seed data script

Questions:
- Is Supabase the PostgreSQL provider? (Mentioned in README)
- Should I set up both dev and test databases?

Estimated time: 45 minutes
```

**You respond:**
```
Yes, Supabase for prod/staging, local PostgreSQL for dev.
Let's skip test database for MVP.
Please proceed.
```

**AI executes in Act Mode:**
- Installs Prisma
- Creates schema
- Runs migration
- Creates seed script

**Terminal approvals:**
```
npm install prisma @prisma/client [Approve]
npx prisma init [Approve]
npx prisma migrate dev --name init [Approve]
```

**Completion:**
```markdown
## Confidence Score: 9/10

All requirements met:
- [x] Prisma configured
- [x] Schema created
- [x] Migration successful
- [x] Seed script works
- [x] Environment documented

Ready for Task 1.2.
```

**You:** "Looks good. Closing this chat."

---

### Task 2: User Authentication (Building on Task 1)

**New chat:**
```
You: Can we please plan task 1.2 - Implement User Authentication?
```

**AI (reads previous task docs automatically):**
```
Based on ROADMAP and previous task completion:
- Database is set up with Prisma
- User model needs to be expanded
- Need: register, login, JWT tokens

Proposed approach:
1. Expand User model with auth fields
2. Create auth service (hash, verify, tokens)
3. Create auth routes
4. Create auth middleware
5. Write tests

I see from LEARNINGS.md that we should use bcrypt with 
cost factor 12 for password hashing.

Shall I proceed with this plan?
```

**You:** "Good. Proceed."

**AI executes...**

**At one point, AI asks:**
```
Question: Should the JWT secret come from environment variable?
I didn't see it defined in .env.example.
```

**You respond:**
```
Yes, add JWT_SECRET to .env.example and reference process.env.JWT_SECRET.
Generate a random secret for the example.
```

**AI continues and completes.**

**Completion:**
```markdown
## Confidence Score: 8/10

- [x] All auth features working
- [x] Tests passing (15 unit, 5 integration)
- [x] Code commented
- [x] JWT_SECRET in environment

Learning added to LEARNINGS.md:
"JWT secret must be 256-bit random string. Example generation:
node -e \"console.log(require('crypto').randomBytes(32).toString('hex'))\""

Ready for Task 1.3.
```

---

### Task 3: User Profile Page (Building on Task 2)

**New chat:**
```
You: Can we please plan task 1.3 - Create User Profile Page?
```

**AI (now has context from two previous task docs):**
```
Based on ROADMAP and previous completions:
- Database ready ✓
- Authentication working ✓
- Now need: Frontend profile page

From README.md, frontend is React with Tailwind.

Proposed approach:
1. Create ProfilePage component
2. Create useCurrentUser hook (fetches authenticated user)
3. Create profile display layout
4. Add protected route
5. Write component tests

Questions:
- Should profile be editable in MVP? (ROADMAP says display only)
- Any specific design mockups, or should I create clean minimal UI?

Estimated time: 1.5 hours
```

**You respond:**
```
Display only for MVP is correct.
No mockups - clean minimal UI is fine.
Proceed with the plan.
```

**AI executes...**

**Visual verification:**
```
You: Before finalizing, what should I see when I navigate to /profile 
while logged in?

AI: You should see:
- Header with app logo and logout button
- Centered profile card with:
  - User email displayed
  - Account creation date
  - "Edit Profile" button (disabled, shows "Coming in v1.0" on hover)
- Clean white background with subtle shadow on card

If you navigate to /profile while logged out, you should be 
redirected to /login.
```

**You verify:**
```
Visual check passed. Everything displays correctly.
"Edit Profile" tooltip says "Coming soon" not "Coming in v1.0" - 
that's fine, maybe even better.

Proceed with completion.
```

**Completion:**
```markdown
## Confidence Score: 8/10

Profile page complete:
- [x] ProfilePage component created
- [x] Shows current user info
- [x] Protected route implemented
- [x] Visual verification passed
- [x] Component tests passing

Ready for Phase 1 completion audit.
```

---

## Key Patterns to Remember

### The Successful Pattern

```
1. NEW CHAT for each task (fresh context)
2. MINIMAL PROMPT: "Can we please plan task X?"
3. REVIEW plan, adjust if needed
4. ACT MODE execution with terminal approval
5. VISUAL VERIFICATION for UI tasks
6. CONFIDENCE SCORE must be 8/10+
7. CLOSE CHAT, move to next task
```

### Common Mistakes to Avoid

| Mistake | Problem | Solution |
|---------|---------|----------|
| Long running chats | Context pollution | New chat per task |
| Elaborate prompts | Duplication, conflicts | Trust your docs |
| Skipping Plan Mode | Misaligned execution | Always plan first |
| Auto-approving all commands | Security risks | Review each command |
| Accepting low confidence | Accumulated tech debt | Require 8/10+ |
| No visual verification | UI bugs ship | Always verify visually |

### Signs the Workflow Is Working

✅ Tasks complete in predictable time (30-90 min)
✅ AI references your docs correctly
✅ Few surprises during execution
✅ Confidence scores are consistently 8+
✅ Previous task decisions carry forward
✅ You're not repeating yourself

### Signs Something's Wrong

❌ AI seems confused about project context
❌ Having to explain the same things repeatedly
❌ Confidence scores frequently below 8
❌ Tasks taking much longer than estimated
❌ AI contradicting previous decisions

**If you see these signs:** Check your documentation. Usually the issue is docs being incomplete or outdated.

---

::: tip The Workflow in Practice
After a few tasks, this workflow becomes second nature:

"New chat. Plan task. Review. Act. Verify. Close. Repeat."

The simplicity is the point. You're not prompt engineering—you're executing a well-documented plan with a capable assistant.

The magic isn't in the prompts. It's in the documentation structure that makes simple prompts work.
:::

---

**Next:** [Chapter 6: Task Documentation Patterns](/part-3/task-patterns) — How to document tasks effectively for simple and complex projects.
