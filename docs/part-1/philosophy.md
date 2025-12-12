---
title: Philosophy & Approach
description: Understanding why structure and MVP-first thinking are essential for AI-assisted development
---

# Chapter 1: Philosophy & Approach

## TLDR

**Core Philosophy:** Treat AI as a capable junior developer who needs structure, clear direction, and quality gates - not as magic, not as autocomplete.

**MVP-First Principle:** Always scope a minimal viable product before building full vision. Validate core concept with $200-$500 before investing $2000+.

**Documentation-First Approach:** Create project "DNA" (roadmap, templates, rules, learning logs) BEFORE coding. This guides AI and prevents confusion.

**Key Insight:** The most important conversation happens before any code is written - getting AI to help identify what's realistic for an MVP vs what's a multi-phase vision.

**Why Most Fail:**
- No quality gates → broken code proceeds unchecked
- No context management → AI forgets early decisions
- No MVP scoping → waste resources on unvalidated concepts
- No documentation → unmaintainable code

**The Solution:** A systematic methodology with built-in quality controls, phased development, and realistic scoping.

---

## The Fundamental Shift: From Magic to Methodology

### What AI Coding Actually Is

When you use Claude Sonnet 4.5 or Opus 4 to write code, you're not invoking magic. You're also not just using fancy autocomplete. You're working with:

**A highly capable reasoning system that can:**
- Understand complex technical requirements
- Make architectural decisions with proper analysis
- Write production-quality code following patterns
- Debug issues systematically with step-by-step thinking
- Learn project-specific patterns from documentation
- Identify when a vision is too ambitious for one phase

**But it has critical limitations:**
- **Context window constraints** - Can "forget" things outside its current window (~200k tokens)
- **No inherent quality control** - Will produce bad code if not guided to verify
- **No long-term memory** - Unless you build systems to provide it (documentation)
- **Needs structure** - Vague prompts produce vague, inconsistent results
- **No business judgment** - Won't naturally say "this is too ambitious"

**The breakthrough comes when you design a system that:**
- Plays to AI's strengths (reasoning, pattern matching, code generation)
- Compensates for AI's weaknesses (memory, quality control, scope judgment)
- Treats AI as a collaborator that needs guidance, not a servant or a master

### The Junior Developer Metaphor

The best mental model for AI coding assistants:

**Think of Claude as a talented junior developer who:**

✅ **Can do:**
- Write code very quickly
- Learn patterns from documentation
- Debug systematically when given direction
- Implement features following specifications
- Generate tests and documentation
- Work 24/7 without breaks

❌ **Cannot do (without help):**
- Know your business domain without explanation
- Maintain context across weeks of work
- Judge when a project is too ambitious
- Know when to escalate to senior developer
- Understand implicit requirements
- Automatically maintain high standards

**Your role is:**
- Senior developer / tech lead
- Provide clear specifications
- Set quality standards (in Claude Rules)
- Review work at quality gates
- Make architectural decisions (with AI's help)
- Decide when MVP is sufficient

**This is why the methodology works:**
- You're not asking AI to be a senior architect
- You're providing the structure a junior developer needs
- You're building in the verification a junior developer requires
- You're creating the documentation a junior developer references

### Why "Vibe Coding" Often Fails

The term "vibe coding" emerged in 2025 to describe natural language-driven development. The problem? Most practitioners interpret this as:

```
Developer: "Build me a Twitter clone with real-time updates,
            image uploads, hashtags, trending, DMs, and notifications"
            
AI: "Sure! Let me start building..."
[Generates 10,000 lines of code over 3 days]

Developer: "Wow, this looks amazing!"
[One week later: Everything breaks mysteriously]

Developer: "AI coding doesn't work."
```

#### Why This Pattern Fails

**1. No MVP Scoping - The $2000 Mistake**

The developer asked for Twitter (a multi-billion dollar product that took years to build). AI started building everything without questioning scope.

**Better approach:**
```
Developer: "I want to build a Twitter clone..."

AI with Extended Thinking: "That's an ambitious vision! A full Twitter 
clone would take 6-12 months and significant investment. Let's identify 
an MVP that proves the core concept.

The essential value proposition of Twitter is: short-form posts that 
users can see and interact with.

Proposed MVP (v0.1) - 2-3 weeks, ~$200-$300 in tokens:
- User authentication (email/password)
- Create text posts (280 char limit)
- View feed of all posts (chronological)
- Basic like functionality
- Single-user deployment (no scaling needed)

Version 1.0 (if MVP succeeds):
- User profiles with bio
- Follow/unfollow functionality
- Personal feed of followed users
- Reply functionality
- Image uploads

Production Phase (if v1.0 succeeds):
- Real-time updates via WebSockets
- Hashtag system
- Trending algorithm
- Direct messages
- Notification system
- Multi-region scaling

Does this phased approach work for you?"
```

**Result:** You spend $250 to validate "can I build a social feed that people will use?" instead of $2000 building features for a product you haven't validated.

**2. No Quality Gates - Broken Code Proceeds**

Without confidence scoring, AI moves from authentication → posts → likes → images even though authentication has a critical bug that breaks everything.

**Better approach:**
- Each subtask requires 8/10 confidence score
- AI must define criteria for 8/10
- AI must verify criteria are met
- Cannot proceed to next subtask until threshold met

**3. No Context Management - AI Forgets**

One long conversation:
- Message 1: "Let's use PostgreSQL"
- Message 50: AI suggests "Should we use MongoDB?"
- Message 100: AI implements SQL queries assuming MongoDB

**Better approach:**
- New chat for each task
- Each task references: roadmap, templates, learnings doc
- AI stays focused on current task
- Previous decisions documented, not just in chat history

**4. No Documentation - Unmaintainable Code**

Three weeks later, developer looks at code:
- "Why does this function do this?"
- "What was I thinking here?"
- "Which database does this connect to?"
- "Can I change this without breaking everything?"

**Better approach:**
- Claude Rules mandate 50% comments, 50% code
- Every function has docstring
- Every decision has comment explaining "why"
- Changel

ogs document all modifications
- README explains architecture

---

## The MVP-First Philosophy (The Game-Changer)

### The Core Principle

**Before writing any code, have this conversation:**

"AI, I want to build [ambitious vision]. Help me identify what's realistic for an MVP that proves the core concept."

This single conversation can save you:
- Thousands of dollars in wasted tokens
- Weeks of development time
- The frustration of abandoning a half-built project
- The opportunity cost of not validating your idea quickly

### Why This Matters: A Real Example

**The Vision:**
"I want to build a conference networking platform where attendees can:
- Create rich profiles with skills and interests
- Get AI-powered matching with relevant attendees/exhibitors/speakers
- Schedule video meetings through the platform
- Have AI-assisted conversations via chatbot
- See networking analytics and recommendations
- Get post-event follow-up reminders
- Integrate with Zoom, Calendar, LinkedIn, and CRM systems"

**Without MVP Scoping:**
- Developer starts building all features
- 6 weeks later, has partially-working system
- Spent $3000 in API tokens
- Core matching algorithm doesn't work well
- Realizes they should have tested matching first
- Can't easily rip out and rebuild core feature
- Project abandoned

**With MVP Scoping (The Right Way):**

**AI Analysis:** "This is a comprehensive vision that could take 4-6 months to build completely. Let me analyze the core value proposition...

The essential innovation here is: AI-powered matching of people at conferences.

Everything else (video meetings, chatbot, analytics, integrations) is enhancement, but the matching is the unique value.

Let's validate the matching works FIRST.

**Proposed MVP (v0.1)** - 2-3 weeks, $200-$300:
- Simple profile creation (name, skills, interests, goals)
- Import attendee list (CSV upload)
- AI matching algorithm (using Qdrant vector similarity)
- Display top 10 matches per attendee
- Simple UI to view matches
- Export matches as CSV

Success criteria: Do people actually find their top matches valuable?

**Version 1.0** (if MVP validates matching):
- User authentication
- Rich profiles with photos
- Real-time updates
- In-app messaging
- Meeting scheduling

**Production** (if v1.0 is successful):
- Video call integration
- AI chatbot
- Analytics dashboard
- CRM integrations
- Multi-conference support"

**Result:**
- Spent $250 to validate matching algorithm works
- Took 3 weeks instead of 6 months
- Got real feedback: "Matching is great! But we also need..."
- Now knows what to build next
- Has working proof-of-concept to show investors/users

### The Budget Reality

| Approach | Timeline | Cost | Outcome |
|----------|----------|------|---------|
| Build Everything | 3-6 months | $3000-$10000 | Maybe works, probably doesn't |
| MVP First | 2-4 weeks | $200-$500 | Proves concept or invalidates quickly |
| MVP → v1.0 | 1-3 months | $800-$2000 | Working product if MVP validated |
| MVP → v1.0 → Production | 3-6 months | $2000-$5000 | Production-ready if v1.0 succeeded |

**The difference:** You spend $200-$500 before deciding whether to invest $2000+.

### How to Have the MVP Scoping Conversation

**Step 1: Describe Your Full Vision**

Don't hold back. Tell AI everything you want to build eventually.

**Example:**
```
"I want to build a project management platform that:
- Uses AI to break down projects into tasks automatically
- Predicts timeline based on team capacity
- Integrates with GitHub, Jira, Slack, and email
- Generates status reports automatically
- Identifies blockers using sentiment analysis
- Provides resource allocation optimization
- Has mobile apps and browser extensions"
```

**Step 2: Ask for MVP Analysis**

```
"This is my full vision. However, I want to be realistic about what 
we can build first. Can you:

1. Identify the core value proposition
2. Propose an MVP that validates just the core concept
3. Estimate complexity and timeline for MVP
4. Outline what would come in v1.0 and production phases
5. Help me understand what I can build in 2-4 weeks"
```

**Step 3: Let Extended Thinking Work**

Claude will think through:
- What's the unique value vs commodity features?
- What's the minimum to prove that value works?
- What dependencies exist between features?
- What's realistic in 2-4 weeks?
- What can be deferred?

**Step 4: Review Phased Roadmap**

AI will propose:
```markdown
# MVP Phase (v0.1) - 2-3 weeks
Core: AI breaks project descriptions into tasks

Features:
- Input: Project description (text)
- Processing: AI generates task breakdown
- Output: Task list with estimates
- No user accounts, no integrations, no timeline prediction

Goal: Validate that AI can create useful task breakdowns

# Version 1.0 - If MVP proves valuable
Add: User accounts, save projects, basic GitHub integration,
simple timeline view

# Production - If v1.0 is successful  
Add: Full integrations, team features, mobile apps, resource optimization
```

**Step 5: Adjust Based on Reality**

Maybe you say:
```
"Actually, user accounts are critical even for MVP because I need to 
demo to investors with their data. Can we include basic auth?"
```

AI adjusts:
```
"Yes, we can add basic email/password auth to MVP. This adds ~3-4 days 
to timeline and ~$50 to token cost. Still reasonable for MVP scope."
```

### The Documentation That Comes From This

After the MVP scoping conversation, you'll have:

**1. README with Phased Vision**
```markdown
# Project Vision

## The Big Picture
[Full vision with all features]

## Current Phase: MVP (v0.1)
[What we're building NOW]

## Future Phases
- v1.0: [Features that come after MVP validates]
- Production: [Full feature set]
```

**2. Roadmap with Realistic Scope**
```markdown
# MVP Roadmap (v0.1)

Estimated Timeline: 2-3 weeks
Estimated Token Cost: $200-$300
Success Criteria: Core feature demonstrates value

## Phase 1: Core Feature (Week 1)
- Task 1.1: Set up basic project structure
- Task 1.2: Implement core algorithm
- Task 1.3: Add basic testing

## Phase 2: User Interface (Week 2)
- Task 2.1: Create simple input form
- Task 2.2: Display results
- Task 2.3: Add export functionality

## Phase 3: Polish (Week 3)
- Task 3.1: Error handling
- Task 3.2: Documentation
- Task 3.3: Deployment
```

**3. Deferred Features List**
```markdown
# Features Deferred to Later Phases

## v1.0 (Post-MVP if successful)
- User authentication
- Save/load projects
- Team collaboration
- GitHub integration

## Production (Post-v1.0 if successful)
- Jira/Slack integrations
- AI timeline prediction
- Mobile apps
- Resource optimization
```

This documentation serves two purposes:
1. **Keeps current work focused** - You don't get distracted building deferred features
2. **Preserves full vision** - When MVP succeeds, you know exactly what to build next

---

## The Documentation-First Paradigm

### Traditional Software Development

```
Requirements → Design → Code → Test → Document
```

**Problem:** Documentation is afterthought. By the time you document, you've forgotten why decisions were made.

### Traditional AI Coding

```
Idea → Prompt AI → Code → Hope it works
```

**Problem:** No documentation at all. Code works or doesn't, but you don't know why.

### This Methodology

```
Idea → Brainstorm with AI → Create Documentation Architecture → Code with Reference to Docs → Update Learnings
```

**Key Documents Created Before Coding:**

1. **README.md**
   - Full vision (v0.1 → v1.0 → Production)
   - Current phase scope
   - Architecture overview
   - Setup instructions

2. **ROADMAP.md**
   - Phases → Tasks → Subtasks
   - Each subtask sized for context window
   - Dependencies documented
   - Success criteria per phase

3. **CLAUDE_RULES.md**
   - Development standards (commenting, testing, etc.)
   - Confidence scoring requirements
   - When to ask for human help
   - Quality gates

4. **TASK_TEMPLATE.md**
   - Standard format for all tasks
   - Confidence scoring section
   - Unit testing requirements
   - Checklist structure

5. **LEARNINGS.md**
   - Running log of project-specific insights
   - Solutions to difficult problems
   - Decisions and rationale
   - Patterns that emerge

### Why Documentation-First Works

**For AI:**
- Has clear reference for all decisions
- Doesn't have to rely on conversation history
- Can check "what did we decide about authentication?"
- Maintains consistency across tasks

**For You:**
- Can see progress clearly
- Can audit AI's adherence to standards
- Can hand off to another developer easily
- Can resume work after breaks

**For Future:**
- Another developer can take over
- AI in future tasks can reference past decisions
- You can remember why you made choices
- Code modifications have documented rationale

### The "Excessive Documentation" Philosophy

This methodology mandates something controversial:

**50% of your code should be comments.**

Most developers think this is insane. Here's why it's actually brilliant:

**Traditional View:**
```python
def calculate_match_score(user1, user2):
    """Calculate match score between users."""
    skills_overlap = len(set(user1.skills) & set(user2.skills))
    interests_overlap = len(set(user1.interests) & set(user2.interests))
    return (skills_overlap * 2) + interests_overlap
```

**This Methodology:**
```python
def calculate_match_score(user1, user2):
    """
    Calculate match score between two conference attendees.
    
    Scoring algorithm rationale:
    - Skills overlap weighted 2x because shared professional expertise
      creates more valuable networking opportunities than hobbies
    - Interests overlap weighted 1x as conversation starter
    - Range: 0 to ~20 for typical users
    - Scores > 10 indicate strong potential match
    
    Why we chose this simple approach for MVP:
    - Vector similarity (Qdrant) was too slow for 1000+ attendees
    - Set overlap provides good-enough results for MVP validation
    - Can enhance with ML in v1.0 if MVP proves valuable
    
    Args:
        user1: User object with .skills and .interests arrays
        user2: User object with .skills and .interests arrays
        
    Returns:
        Integer match score (higher = better match)
        
    Example:
        >>> user_a = User(skills=['Python', 'AI'], interests=['hiking'])
        >>> user_b = User(skills=['Python', 'ML'], interests=['hiking', 'cycling'])
        >>> calculate_match_score(user_a, user_b)
        5  # (1 skill overlap * 2) + (1 interest overlap * 1) + (0 goals overlap * 1.5)
        
    Modified:
        2024-12-10: Initial implementation
    """
    # Count overlapping skills (professional expertise)
    skills_overlap = len(set(user1.skills) & set(user2.skills))
    
    # Count overlapping interests (personal hobbies)
    interests_overlap = len(set(user1.interests) & set(user2.interests))
    
    # Weight skills 2x higher than interests
    # Rationale: Professional connections more valuable at business conferences
    return (skills_overlap * 2) + interests_overlap
```

**What we gain:**
1. **Algorithm rationale** - Why skills weighted 2x
2. **Design decisions** - Why not use vector similarity (too slow)
3. **Future roadmap** - Can enhance with ML in v1.0
4. **Modification history** - When this was implemented
5. **Examples** - What the output looks like
6. **Context** - Why we made these choices

**Three months later:**
- You need to improve matching
- You read comments
- You understand: "Oh, we avoided vectors because of speed. Let me test if Qdrant is fast enough now."
- You make informed decision

**Versus traditional approach:**
- You see code: `(skills * 2) + interests`
- You think: "Why 2x? Is this arbitrary? Can I change it?"
- You modify blindly
- You break something

### The Cost-Benefit of Documentation

**Cost:**
- AI generates ~50% more tokens (more comments)
- Files are longer

**Benefit:**
- Future modifications are 10x faster
- Bugs are easier to diagnose
- Handoff to developers is seamless
- You remember your own decisions
- AI in future tasks has full context

**Bottom line:** Pay 50% more tokens now to save 10x time later.

---

## Quality Gates: The Confidence Scoring System

### The Problem with Unchecked AI

AI will happily proceed from broken authentication → broken database → broken API even though nothing works.

Why? Because you didn't build in verification.

### The Solution: Confidence Scoring

Every subtask requires AI to:

**1. Rate Its Own Work (Out of 10)**
```markdown
## Confidence Score: 8/10
```

**2. Define Success Criteria**
```markdown
### Criteria for 8/10:

Must-Have (Required):
- Feature is functional
- Unit tests pass
- Error handling present
- Code is commented
- No console errors

Nice-to-Have (Not Required for MVP):
- Performance optimization
- Advanced error messages
- Loading animations
```

**3. Demonstrate Criteria Are Met**
```markdown
### Evidence:

✅ Feature functional: User can log in successfully
✅ Unit tests: 12/12 passing (see test results below)
✅ Error handling: Invalid credentials return proper error
✅ Comments: All functions documented
✅ No errors: Clean console on login flow

❌ Performance: Could optimize (deferred to v1.0)
❌ Advanced errors: Basic messages only (sufficient for MVP)
```

**4. Cannot Proceed if < 8/10**

If score is 7/10, AI must:
- Identify what's missing
- Fix issues
- Re-score
- Not proceed until 8+

### Example: Task with Confidence Scoring

```markdown
# Task 2.3: Implement User Login

## Overview
Create login endpoint that accepts email/password and returns JWT token.

## Implementation
[... code here ...]

## Confidence Score: 9/10

### Criteria for 9/10

Must-Have (All Met):
✅ Login endpoint functional at POST /api/auth/login
✅ Validates email format
✅ Checks password against bcrypt hash
✅ Generates JWT with 24h expiration
✅ Returns proper error codes (401, 400, 500)
✅ Unit tests: 15/15 passing
✅ Integration test: Full login flow works
✅ Code commented: Every function documented
✅ Error handling: All failure cases handled
✅ Security: No password in logs or responses

Nice-to-Have (Not All Met):
✅ Rate limiting: Max 5 attempts per minute per IP
✅ Login attempt logging
❌ 2FA support (deferred to v1.0 per roadmap)
❌ OAuth integration (deferred to v1.0 per roadmap)

### Test Results
```bash
$ npm test -- auth.test.js

  Authentication Tests
    ✓ Should accept valid email/password (45ms)
    ✓ Should reject invalid email format (12ms)
    ✓ Should reject wrong password (38ms)
    ✓ Should reject non-existent email (15ms)
    ✓ Should return JWT token on success (52ms)
    ✓ Should enforce rate limiting (178ms)
    ...
    
  15 passing (892ms)
```

### Justification

Score is 9/10 because:
- All MVP requirements met
- Security is solid
- Testing is comprehensive
- Rate limiting exceeds MVP needs (bonus)

Not 10/10 because:
- 2FA and OAuth deferred (documented in roadmap)
- Could add more advanced rate limiting (not needed for MVP)

Ready to proceed to Task 2.4.

### Human Verification Needed

Please test login manually:
1. Navigate to http://localhost:3000/login
2. Try email: test@example.com, password: wrongpassword (should fail)
3. Try email: test@example.com, password: Test123! (should succeed)
4. Verify you see dashboard after successful login

If any issues, please describe and I'll debug.
```

### Why This Works

**Built-in Quality Control:**
- AI must think about whether work is done
- Can't move forward with broken code
- Defines what "done" means
- Documents evidence

**Human Oversight:**
- You see clear score
- You see criteria
- You can disagree ("Actually, this is only 7/10 because...")
- You make final call

**Future Reference:**
- Confidence scores document quality progression
- Can see "which tasks had issues"
- Can identify patterns

---

## The Phase Audit Process

### The Problem

Even with confidence scoring per task, issues can accumulate:
- Task 1 is 8/10
- Task 2 is 8/10
- Task 3 is 8/10
- But together they don't integrate well

### The Solution: Independent Audit

After each major phase (MVP, v1.0, Production):

**Step 1: Push to GitHub**
```bash
git push origin main
```

**Step 2: Open New Claude Web Interface Project**
- Start fresh Claude.ai web session
- Create new Project
- Sync GitHub repository

**Step 3: Audit Prompt**
```markdown
You are a senior software engineer auditing this codebase.

Context:
- This is the MVP phase (v0.1) of [project description]
- It was built using AI-assisted development
- All code in this repo is Phase 1 completion

Your task:
1. Review all code in the repository
2. Check: code quality, test coverage, documentation, architecture
3. Identify any issues, bugs, or improvements needed
4. Rate overall phase completion: X/10
5. If < 8/10, create a list of "annex tasks" to fix issues

Please be thorough but constructive. The goal is production-ready code.
```

**Step 4: Review Audit Results**

Claude (as senior developer) might respond:
```markdown
# Phase 1 Audit Results

## Overall Score: 7/10

### Strengths
✅ Core authentication logic is solid
✅ Test coverage is excellent (92%)
✅ Code is well-commented
✅ README is comprehensive

### Issues Found

❌ **Critical:**
1. Password reset flow not implemented (mentioned in Claude Rules but missing)
2. API endpoints missing rate limiting (security risk)

❌ **Important:**
3. Error messages expose too much information (security concern)
4. Database migrations not documented

⚠️ **Minor:**
5. Some TypeScript any types should be properly typed
6. Console.log statements left in production code

### Recommended Annex Tasks

**Annex Task 1.A: Password Reset Flow**
Priority: Critical
Effort: ~4 hours
Description: Implement password reset with email verification

**Annex Task 1.B: API Rate Limiting**
Priority: Critical
Effort: ~2 hours
Description: Add rate limiting middleware to all API endpoints

**Annex Task 1.C: Secure Error Messages**
Priority: Important
Effort: ~2 hours
Description: Sanitize error messages to not expose internals

**Annex Task 1.D: Migration Documentation**
Priority: Important
Effort: ~1 hour
Description: Document all database migrations in MIGRATIONS.md

**Annex Task 1.E: TypeScript Cleanup**
Priority: Minor
Effort: ~2 hours
Description: Remove any types, add proper interfaces

### After Fixes

If annex tasks completed, phase should be 9/10 and ready for v1.0.
```

**Step 5: Complete Annex Tasks**

You go back to Cline and systematically complete each annex task using the normal workflow.

**Step 6: Re-Audit**

After fixes, you re-audit:
```markdown
# Phase 1 Re-Audit

## Overall Score: 9/10

All critical and important issues resolved. Minor issues acceptable for MVP.

### Verified
✅ Password reset flow implemented and tested
✅ Rate limiting on all endpoints
✅ Error messages sanitized
✅ Migrations documented
✅ TypeScript improved (5 any types remain in vendor code - acceptable)

## Recommendation

**Phase 1 is production-ready for MVP.**

Safe to proceed to Phase 2 (v1.0 features).
```

### Why This Works

**Independent Verification:**
- Different AI instance (no context pollution)
- Acts as "fresh eyes"
- Senior developer perspective
- Catches issues the executor missed

**Prevents Compounding:**
- Fix phase 1 issues before building phase 2
- Don't build on shaky foundation
- Quality gates between major milestones

**Documentation:**
- Audit results become part of project docs
- Future developers see what was caught
- Quality progression is visible

---

## Summary: The Complete Philosophy

1. **MVP-First Scoping**
   - Validate core concept before heavy investment
   - Document full vision, build incrementally
   - $200 to prove vs $2000 to fail

2. **Documentation-First Development**
   - Create project "DNA" before coding
   - Roadmap, templates, rules, learnings
   - 50% comments, 50% code (excessive on purpose)

3. **Confidence Scoring**
   - Every subtask scores itself out of 10
   - Must define and demonstrate criteria
   - Cannot proceed if < 8/10

4. **Phase Audits**
   - Independent AI review between phases
   - Catch accumulated issues
   - Fix before building next phase

5. **Context Management**
   - New chat per task
   - Reference documentation, not history
   - Prevent AI confusion

6. **Treat AI as Junior Developer**
   - Capable but needs guidance
   - Provide structure and standards
   - Review and verify work
   - Make architectural decisions together

**Next:** [Chapter 2: Tool Selection](/part-1/tool-selection) - Choosing the right AI coding tool for structured development.
