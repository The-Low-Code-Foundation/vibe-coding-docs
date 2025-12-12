---
title: The Brainstorming Session
description: How to have a productive ideation conversation with AI to scope your MVP and plan your project
---

# Chapter 3: The Brainstorming Session

## TLDR

**What:** A structured conversation with Claude (web interface or Cline Plan Mode) before writing any code. This is where you transform a vague idea into a scoped, realistic project plan.

**Why:** The single most important conversation in your entire project. Getting this right saves thousands of dollars and weeks of development time. Getting it wrong leads to abandoned projects and wasted resources.

**How Long:** 30-90 minutes depending on project complexity.

**Output:** Clear MVP scope, phased roadmap, technical decisions, realistic timeline, and cost estimates.

**Key Insight:** You're not asking AI to build your vision—you're asking AI to help you discover what's realistic to build FIRST, so you can validate the concept before heavy investment.

**The Pattern:**
1. Describe your full vision (don't hold back)
2. Ask AI to identify the core value proposition
3. Let AI propose an MVP that proves just the core concept
4. Iterate until you have a realistic 2-4 week scope
5. Document the decisions for development phase

---

## Why This Conversation Matters

### The $2000 Mistake

Without a brainstorming session, developers typically:

```
Developer: "Build me a Slack competitor with video calls, 
            threaded messages, file sharing, app integrations,
            search, admin controls, and mobile apps"
            
AI: "Sure! Let me start with the database schema..."

[6 weeks later]
- $3000 in API tokens spent
- Half-built features everywhere
- Core messaging doesn't work reliably
- Can't demo anything to users
- Project abandoned
```

### The $250 Success

With a proper brainstorming session:

```
Developer: "I want to build a Slack competitor..."

AI: "That's an ambitious vision! Slack took years and 
     hundreds of millions to build. Let's identify what 
     you could validate in 2-4 weeks.
     
     What's the ONE thing that would make your version 
     different or better than Slack?"

Developer: "AI-powered message summarization. People miss 
           important messages in busy channels."

AI: "Perfect. That's your core innovation. Let's build an 
    MVP that ONLY proves AI summarization works:
    
    MVP (2-3 weeks, ~$250):
    - Simple channel view (read-only import from Slack)
    - AI summarization of channel activity
    - 'Catch me up' button for each channel
    - No user accounts, no real-time, no file sharing
    
    If people love the summaries, THEN build the chat platform."
```

**Result:** $250 to validate "do people want AI channel summaries?" instead of $3000 building a chat platform nobody might use.

---

## Step-by-Step Guide

### Step 1: Preparation Checklist

Before starting the conversation, gather:

- [ ] **Your vision** — What do you ultimately want to build?
- [ ] **Target users** — Who is this for?
- [ ] **Problem statement** — What pain are you solving?
- [ ] **Competitive landscape** — What exists today?
- [ ] **Your constraints** — Time, budget, technical skills?
- [ ] **Success definition** — What would make this "work"?

You don't need perfect answers. The AI will help you clarify.

### Step 2: Choose Your Tool

**Claude Web Interface (Recommended for Brainstorming)**
- Better for long-form conversation
- Extended thinking gives deeper analysis
- Can reference uploaded documents
- No token pressure from IDE context

**Cline Plan Mode (Alternative)**
- Good if you want to immediately reference codebase
- Useful for refactoring existing projects
- Keeps everything in one tool

### Step 3: Opening Prompt Template

Copy and customize this:

```markdown
I want to build [PROJECT DESCRIPTION].

**Target Users:** [WHO IS THIS FOR]

**Problem:** [WHAT PAIN ARE YOU SOLVING]

**My Full Vision:**
[DESCRIBE EVERYTHING YOU EVENTUALLY WANT - don't hold back]

**My Constraints:**
- Timeline: [HOW LONG CAN YOU SPEND ON MVP]
- Budget: [TOKEN BUDGET, e.g., "$200-$500 for MVP"]
- Technical: [YOUR SKILLS - "I can code" or "I need AI to write everything"]

**What I Need From You:**
1. Identify the core value proposition (what makes this unique/valuable)
2. Propose an MVP that validates ONLY the core concept
3. Estimate realistic timeline and cost for MVP
4. Outline what would come in v1.0 and production phases
5. Flag any technical decisions I should make upfront

Please think through this carefully before responding.
```

### Step 4: The Conversation Pattern

**Phase A: Vision Clarification (5-10 minutes)**

AI will ask clarifying questions like:
- "When you say X, do you mean Y or Z?"
- "Who specifically is the target user?"
- "What exists today that partially solves this?"
- "What would make someone choose your solution over alternatives?"

**Answer honestly.** The AI is trying to understand your actual need, not just build what you describe.

**Phase B: Core Value Identification (10-15 minutes)**

AI will analyze and propose what's essential:

```
Based on your vision, I see three potential core value propositions:

1. **The AI summarization** — This is truly unique. No competitor does this well.

2. **The threading model** — But Slack already does this. Not differentiated.

3. **The integrations** — But this requires the chat platform to exist first.

My recommendation: Focus MVP entirely on #1 (AI summarization).
If that works, you can build the chat platform around it.
If it doesn't work, you've saved months of development.

Does this analysis resonate with you?
```

**Phase C: MVP Scoping (15-30 minutes)**

This is the critical phase. AI proposes an MVP, you push back, AI adjusts.

**You might say:**
- "That's still too big. What's the absolute minimum?"
- "Actually, I need user accounts even for MVP because..."
- "Can we skip the UI and just build the API first?"
- "What if we used [existing service] instead of building that?"

**AI will respond with trade-offs:**
```
Option A: No user accounts
- Pro: 1 week faster, ~$100 less
- Con: Can't personalize summaries, can't track usage

Option B: Basic email/password auth
- Pro: Can personalize, can track who uses what
- Con: +3-4 days, +$50

Option C: OAuth only (Google/GitHub login)
- Pro: No password management, trusted auth
- Con: Slightly more complex setup, limits user base

For an MVP where you're testing "do summaries work?", I'd recommend 
Option C. You get user identity for personalization without building 
auth from scratch. Thoughts?
```

**Phase D: Technical Decisions (10-20 minutes)**

AI will surface decisions that need to be made:

```
Before we finalize the MVP scope, let's make some technical decisions 
that will affect the entire project:

**1. Database**
- PostgreSQL: Proven, relational, good for structured data
- MongoDB: Flexible schema, good if data structure might change
- Supabase: PostgreSQL + real-time + auth built-in

Recommendation for MVP: Supabase. Gets you database + auth + real-time 
for future phases. One service to manage.

**2. AI Provider for Summarization**
- OpenAI: Fastest, most capable, most expensive
- Anthropic Claude: Great reasoning, good for nuanced summaries
- Open source (Llama): Cheapest, requires self-hosting

Recommendation: Claude API for summaries. Better at understanding 
context and nuance in conversations.

**3. Frontend**
- React: Most popular, huge ecosystem
- Vue: Simpler, good for smaller projects
- Svelte: Newest, very performant

Recommendation: React. More resources, easier to hire if needed.

Do you agree with these, or want to discuss alternatives?
```

**Phase E: Roadmap Creation (10-15 minutes)**

AI synthesizes everything into a phased plan:

```markdown
# Project Roadmap

## MVP Phase (v0.1) — 2-3 weeks, $200-$300

**Goal:** Validate that AI channel summarization is valuable

**Features:**
- Import Slack channel export (JSON file upload)
- AI generates daily summary of channel activity  
- "Catch me up" button shows summary
- Simple UI to browse summaries
- Google OAuth for user identity

**Not Included (deferred):**
- Real-time Slack connection
- Multiple workspaces
- Custom summary preferences
- Team features

**Success Criteria:**
- Users say summaries are accurate and useful
- At least 3 test users would "pay for this"

---

## Version 1.0 — 4-6 weeks after MVP validates

**Goal:** Make it actually usable day-to-day

**Features:**
- Real-time Slack integration (OAuth)
- Multiple channels
- User preferences (summary frequency, focus areas)
- Basic team/workspace support

---

## Production — 2-3 months after v1.0

**Goal:** Scalable, monetizable product

**Features:**
- Full team management
- Billing and subscriptions
- Advanced summarization (threads, mentions, action items)
- Microsoft Teams support
- Mobile apps
```

### Step 5: Document the Decisions

Before ending, ask AI to summarize:

```
Can you create a summary document of everything we decided?

Include:
1. Project vision (full scope)
2. MVP scope (what we're building first)
3. Technical decisions made
4. Deferred features list
5. Success criteria for MVP
6. Rough timeline and cost estimate
```

This becomes the foundation for your README.md and ROADMAP.md.

---

## Real Example: Conference Networking App

Here's an actual brainstorming session (condensed):

**You say:**
```
I want to build a conference networking platform where attendees can:
- Create rich profiles with skills, interests, and goals
- Get AI-powered matching with relevant attendees, exhibitors, speakers
- Schedule video meetings through the platform
- Have AI-assisted icebreaker conversations via chatbot
- See networking analytics and recommendations
- Get post-event follow-up reminders
- Integrate with Zoom, Calendar, LinkedIn, and CRM systems

Target Users: Conference organizers and attendees at tech conferences

Problem: People go to conferences, have random conversations, and 
don't connect with the most relevant people. They leave with a 
stack of business cards they never follow up on.

Constraints:
- Timeline: I want an MVP in 2-3 weeks
- Budget: ~$300 for MVP
- Technical: I can code, comfortable with React and Node
```

**AI responds:**
```
This is a great vision! Conference networking is genuinely broken, 
and AI matching could solve it. Let me analyze what's core vs 
what's enhancement.

**Core Value Proposition Analysis:**

The UNIQUE value here is: "AI matching people who should meet"

Everything else is either:
- Enhancement (video meetings, chatbot)
- Integration (Zoom, LinkedIn, CRM)
- Polish (analytics, reminders)

**My Recommendation:**

Your MVP should ONLY prove that AI matching works. If the matching 
is bad, none of the other features matter. If the matching is great, 
you'll have users begging for the other features.

**Proposed MVP (v0.1):**

Week 1: Core matching engine
- Simple profile form: name, role, skills (tags), interests (tags), 
  "I want to meet people who..." (free text)
- Import attendee list via CSV (organizer uploads)
- AI matching using vector similarity (Qdrant or Pinecone)
- Display top 10 matches for each attendee

Week 2: Basic usability
- Simple UI to view your matches
- Brief explanation of WHY each person is a match
- Export matches as CSV
- Basic responsive design

Week 3: Polish
- Email notification with your top matches
- Simple feedback mechanism ("Was this match helpful?")
- Bug fixes and testing

**What This Validates:**
- Can AI actually identify good matches?
- Do attendees find the matches valuable?
- Do organizers want this for their events?

**What We're NOT Building (yet):**
- Video meetings (use Zoom links for now)
- AI chatbot (people can message on LinkedIn)
- Calendar integration (manual for MVP)
- Rich profiles (basic tags are enough to test matching)
- Analytics dashboard (we'll track manually)
- Mobile app (responsive web is fine)

**Technical Decisions Needed:**

1. Vector database for matching: Qdrant (free tier) vs Pinecone (easier)
2. Hosting: Vercel (free) vs Railway ($5/month)
3. Database: Supabase (free tier, includes auth)

**Estimated Cost:** $200-$300 in tokens + ~$10/month infrastructure

Does this scope feel right? Any features you feel MUST be in MVP?
```

**You respond:**
```
This makes sense. Two questions:

1. Do we need user accounts for MVP? Could organizers just share 
   a link and attendees see matches without logging in?

2. The "why this is a match" explanation feels important. Is that 
   hard to generate?
```

**AI responds:**
```
Great questions. Let me think through both:

**1. User Accounts**

Option A: No accounts (magic link per attendee)
- Organizer uploads CSV with emails
- System generates unique link per attendee
- Attendee clicks link, sees their matches
- Pro: No auth code, faster to build
- Con: Can't update profile, less secure

Option B: Simple auth (email link, no password)
- Same as above, but attendee can "claim" their profile
- Can update their bio and preferences
- Pro: Personalization possible
- Con: +2 days development

Option C: Full auth (email/password or OAuth)
- Pro: Most secure, best UX for returning users
- Con: +4-5 days, more complexity

**Recommendation:** Start with Option A for MVP. 
If people love the matches, add auth in v1.0.
For a 2-week test, magic links are sufficient.

**2. Match Explanations**

This is actually easy to generate! When the AI creates matches, 
we can prompt it to explain:

"You should meet Sarah because: You're both interested in AI 
product management, she has experience scaling teams (which 
you mentioned you want to learn), and you're both speaking on 
Day 2 so you could meet at the speaker lounge."

The explanation comes from the same AI that does the matching. 
It just requires a good prompt template. Maybe +2-3 hours of 
prompt engineering, no extra architecture.

**Revised MVP Scope:**
- Magic link access (no auth)
- AI matching with explanations
- Top 10 matches displayed
- CSV import/export
- Feedback mechanism

Timeline: 2 weeks
Cost: ~$250

Want me to create the full documentation structure for this?
```

**You respond:**
```
Yes, this is perfect. Let's go with magic links and include the 
match explanations. Can you create the documentation summary?
```

**AI creates:**
```markdown
# Conference Networking MVP - Project Summary

## Vision (Full Scope)
AI-powered conference networking platform with matching, video meetings, 
AI chatbot, analytics, integrations, and mobile apps.

## MVP Scope (v0.1)
Validate that AI matching actually connects relevant people.

### Features
- Organizer uploads attendee CSV
- Simple profile: name, role, skills, interests, goals
- AI generates top 10 matches per attendee with explanations
- Magic link access (no accounts)
- Export matches as CSV
- Simple feedback collection

### Technical Stack
- Frontend: React + Tailwind
- Backend: Node.js + Express
- Database: Supabase (PostgreSQL)
- Vector DB: Qdrant (free tier)
- AI: Claude API for matching + explanations
- Hosting: Vercel (free)

### Timeline
- Week 1: Core matching engine + basic UI
- Week 2: Polish, testing, feedback mechanism

### Budget
- Tokens: ~$200-$250
- Infrastructure: ~$10/month

### Success Criteria
1. Matches rated "helpful" by >70% of users
2. At least one organizer says "I'd pay for this"
3. No critical bugs in matching logic

### Deferred to v1.0
- User accounts with auth
- Real-time updates
- Calendar integration
- Video meeting scheduling
- Rich profiles with photos

### Deferred to Production
- Mobile apps
- Zoom/Teams integration
- CRM integration
- Analytics dashboard
- Multi-event support
```

---

## Common Patterns and Responses

### Pattern 1: "Everything Is Essential"

**You say:**
```
Actually, I need ALL of these features for MVP. Without video 
meetings, people can't actually network. Without the chatbot, 
they won't know what to say. It's all connected.
```

**AI should respond:**
```
I understand these features feel connected, but let me challenge 
this thinking:

**The dependency isn't what you think:**

- Without GOOD MATCHES, video meetings connect wrong people
- Without GOOD MATCHES, chatbot helps wrong conversations  
- Without GOOD MATCHES, nothing else matters

But if matches ARE good:
- People will use Zoom links (they already know Zoom)
- People will write their own messages (they're adults)
- People will manually check calendars (they do this anyway)

**The real question:**
Before we invest in video, chatbot, and calendar integration—
are you confident the AI matching will work?

If yes: Let's build everything
If no: Let's prove matching first

Which is it? Because in my experience, AI matching is the 
NOVEL part that needs validation. Video conferencing is a 
solved problem.
```

### Pattern 2: "I Don't Know What's Core"

**You say:**
```
I'm not sure what the core value is. I just know people don't 
network well at conferences. How do I figure out what to build?
```

**AI should respond:**
```
Let's work backwards from the problem. Walk me through a 
conference networking failure:

1. **Before the conference:** What do people wish they knew?
2. **During the conference:** What goes wrong?
3. **After the conference:** What do people regret?

Once you describe these, I can identify where intervention 
has the most impact.

For example:
- If the problem is "I didn't know who was attending" → Solution: Pre-event directory
- If the problem is "I met random people" → Solution: AI matching
- If the problem is "I forgot to follow up" → Solution: Automated reminders
- If the problem is "Conversations were awkward" → Solution: Icebreaker AI

Each of these is a different MVP. Which problem do you feel 
most strongly about?
```

### Pattern 3: "Too Technical, Not Enough Product"

**You say:**
```
I want to use vector embeddings stored in Qdrant with a 
two-phase retrieval system using BM25 for initial recall and 
then reranking with a cross-encoder model hosted on...
```

**AI should respond:**
```
I appreciate the technical depth! But let me redirect slightly:

**Technical decisions should follow product decisions.**

Before choosing Qdrant vs Pinecone vs Weaviate, let's clarify:
- What are you matching? (People? Documents? Products?)
- What does "good match" mean for your users?
- How many items are we matching? (100? 10,000? 1M?)
- How fast does matching need to be? (Real-time? Daily batch?)

Once I understand the product needs, I can help you choose 
the right technical approach.

For example:
- If you're matching 500 conference attendees once per event, 
  you might not need vectors at all—simple tag overlap works.
  
- If you're matching millions of users in real-time, you 
  definitely need optimized vector search.

What's your actual use case?
```

### Pattern 4: "Unrealistic Timeline"

**You say:**
```
I need this done by next week because the conference is in 
10 days and I already promised the organizer.
```

**AI should respond:**
```
I understand the deadline pressure. Let's see what's actually 
achievable in 7 days:

**Realistic 7-Day MVP:**

Day 1-2: Core matching
- CSV upload 
- Simple matching algorithm (tag overlap, not AI for speed)
- Basic match display

Day 3-4: Minimal UI
- One page showing matches
- Mobile-responsive

Day 5-6: Integration
- Magic link delivery via email
- Organizer admin view

Day 7: Testing + buffer

**What this includes:**
✅ Attendees can see top 10 matches
✅ Works on mobile
✅ Organizer can upload attendees

**What this DOESN'T include:**
❌ AI-powered matching (use simple tag overlap instead)
❌ Match explanations
❌ Feedback collection
❌ Pretty UI (functional only)

**The trade-off:**
Simpler matching algorithm is less accurate but achievable. 
You can use the conference to gather feedback, then build 
the AI version for the next event.

Does this reduced scope work? Or should we discuss pushing 
the deadline?
```

---

## Templates for Project Types

### SaaS Application Template

```markdown
I want to build a [TYPE] SaaS product.

**Target Users:** [SPECIFIC CUSTOMER SEGMENT]

**Problem:** [PAIN POINT THEY HAVE TODAY]

**Competition:** [WHAT EXISTS, WHY IT'S NOT GOOD ENOUGH]

**My Differentiation:** [WHAT MAKES MINE BETTER]

**Full Vision:**
- Core feature: [MAIN THING THE PRODUCT DOES]
- User management: [TEAMS, ROLES, ETC.]
- Integrations: [WHAT IT CONNECTS TO]
- Analytics: [WHAT USERS WANT TO TRACK]
- Monetization: [FREE, FREEMIUM, SUBSCRIPTION]

**Constraints:**
- Timeline: [2-4 weeks for MVP]
- Budget: [$200-$500 for MVP tokens]
- Technical: [YOUR CODING ABILITY]

Please help me identify:
1. The core value proposition
2. An MVP that proves the core concept
3. Technical stack recommendations
4. Phase breakdown (MVP → v1.0 → Production)
```

### Mobile App Template

```markdown
I want to build a [TYPE] mobile app.

**Target Users:** [WHO AND HOW THEY'LL FIND IT]

**Problem:** [WHAT THIS SOLVES]

**Full Vision:**
- Core functionality: [MAIN FEATURE]
- Offline support: [YES/NO/PARTIAL]
- Notifications: [WHAT KIND]
- Social features: [SHARING, FRIENDS, etc.]
- Monetization: [FREE, ADS, SUBSCRIPTION, IAP]

**Platform Priority:**
- [ ] iOS first
- [ ] Android first
- [ ] Both simultaneously (React Native/Flutter)
- [ ] Web PWA first, native later

**Constraints:**
- Timeline: [X weeks]
- Budget: [$X tokens + $X/month infrastructure]
- Technical: [YOUR MOBILE EXPERIENCE]

Please help me scope an MVP that validates the core concept 
with the minimum possible features.
```

### Internal Tool Template

```markdown
I want to build an internal tool for [COMPANY/TEAM].

**Users:** [WHO IN THE ORG WILL USE THIS]

**Current Process:** [HOW THEY DO IT TODAY]

**Pain Points:**
- [PAIN 1]
- [PAIN 2]
- [PAIN 3]

**Desired Features:**
- [FEATURE 1]
- [FEATURE 2]
- [FEATURE 3]

**Integration Needs:**
- [ ] Existing database
- [ ] Slack/Teams
- [ ] Email
- [ ] Existing tools: [LIST]

**Constraints:**
- Must work with: [EXISTING SYSTEMS]
- Security: [REQUIREMENTS]
- Timeline: [X weeks]

What's the simplest version that solves the biggest pain point?
```

### API Service Template

```markdown
I want to build an API that [WHAT IT DOES].

**Target Consumers:** [WHO WILL CALL THIS API]

**Use Case:** [WHAT PROBLEM IT SOLVES FOR THEM]

**Core Endpoints Needed:**
- [ENDPOINT 1]
- [ENDPOINT 2]
- [ENDPOINT 3]

**Data Sources:**
- [ ] Own database
- [ ] Third-party APIs: [LIST]
- [ ] User-provided data
- [ ] AI/ML processing

**Performance Requirements:**
- Expected QPS: [X]
- Latency requirement: [Xms]
- Uptime requirement: [X%]

**Monetization:**
- [ ] Free tier + paid
- [ ] Usage-based pricing
- [ ] Subscription
- [ ] Internal only

Please help me design an MVP API that proves the core value, 
with clear expansion path for additional endpoints.
```

---

## Red Flags That Scope Needs Adjustment

Watch for these signals during brainstorming:

### 🚩 "And then we'll add..."

If scope keeps growing after initial plan, stop and re-anchor:

```
I notice we've added 5 features since the original MVP scope. 
Let me update the timeline:

- Original MVP: 2 weeks
- With additions: 6 weeks

Want to proceed with 6 weeks, or cut back to 2?
```

### 🚩 "Users won't understand without..."

Often a sign of over-engineering:

```
You mentioned users won't understand the product without a 
tutorial system. But have you tested this assumption?

Alternative: Ship without tutorial. If users are confused, 
that feedback tells you exactly what to explain in v1.0.

Don't assume what users need—validate.
```

### 🚩 "It's not that complex..."

Complexity always hides:

```
You said "it's just calendar integration." Let me unpack:

Calendar integration includes:
- OAuth with Google (1-2 days)
- OAuth with Outlook (1-2 days)  
- Reading calendar events (1 day)
- Creating calendar events (1 day)
- Handling timezones (1 day)
- Recurring events (1 day)
- Edge cases and testing (2 days)

"Just" calendar integration is 7-10 days.

Is this essential for MVP, or can users manually 
check their calendars for now?
```

### 🚩 "We'll figure that out later"

Deferring critical decisions creates technical debt:

```
You said "we'll figure out authentication later." But auth 
affects:
- Database schema (user table)
- API design (how to identify users)
- Frontend (login flow)
- Security (tokens, sessions)

If we build without auth and add it later, we'll rewrite 
~30% of the code. Better to make this decision now:

Option A: No auth (magic links)
Option B: Simple auth (add now)
Option C: Full auth (add now)

Which one, and why?
```

### 🚩 Multiple "just in case" features

```
I've noted these "just in case" features:
- Extra admin controls "in case we need them"
- Audit logging "in case there's an issue"
- Export formats "in case someone wants CSV"
- API versioning "in case we change it"

For MVP, I recommend: Build none of these.

If you need audit logs, add them.
If someone asks for CSV, add it.
If the API changes, version it then.

"Just in case" features have an opportunity cost: 
they delay validating your core idea.

Do you feel strongly about any of these?
```

---

## Outputs From a Successful Session

### What You Should Have

After 30-90 minutes of brainstorming, you should have:

**1. Clear MVP Scope Document**
```markdown
# [Project Name] - MVP Scope

## One-Line Description
[What this does for whom]

## MVP Features (v0.1)
- [Feature 1]
- [Feature 2]
- [Feature 3]

## Explicitly NOT Included
- [Deferred feature 1]
- [Deferred feature 2]

## Success Criteria
- [Measurable outcome 1]
- [Measurable outcome 2]

## Timeline & Budget
- Weeks: [X]
- Token budget: [$X]
```

**2. Technical Decisions Document**
```markdown
# Technical Decisions

## Stack
- Frontend: [X] because [reason]
- Backend: [X] because [reason]
- Database: [X] because [reason]
- Hosting: [X] because [reason]

## Key Trade-offs Made
- Chose [A] over [B] because [reason]
- Deferred [C] until v1.0 because [reason]
```

**3. Phased Roadmap**
```markdown
# Roadmap

## MVP (v0.1) - [X weeks]
[Features and goals]

## Version 1.0 - [After MVP validates]
[Features and goals]

## Production - [After v1.0 succeeds]
[Full feature set]
```

**4. Deferred Features List**
```markdown
# Deferred Features

## v1.0 (After MVP)
- [ ] [Feature]: [Why deferred]
- [ ] [Feature]: [Why deferred]

## Production (After v1.0)
- [ ] [Feature]: [Why deferred]
- [ ] [Feature]: [Why deferred]

## Maybe Never
- [ ] [Feature]: [Why probably not needed]
```

### Quality Checklist

Before ending brainstorming, verify:

- [ ] MVP can be built in 2-4 weeks
- [ ] MVP budget is $200-$500 tokens
- [ ] Core value proposition is clearly identified
- [ ] Success criteria are measurable
- [ ] Technical stack is decided
- [ ] Deferred features are documented (not forgotten)
- [ ] You understand WHY each MVP feature is essential
- [ ] You understand WHY each deferred feature can wait

---

## Transitioning to Documentation Phase

Once brainstorming is complete, you're ready for the next step: creating your documentation architecture.

**Your brainstorming outputs become:**

| Brainstorming Output | Becomes Documentation |
|---------------------|----------------------|
| MVP Scope | README.md (current phase section) |
| Full Vision | README.md (vision section) |
| Technical Decisions | CLAUDE_RULES.md (standards) |
| Phased Roadmap | ROADMAP.md |
| Deferred Features | ROADMAP.md (future phases) |

**Don't skip this transition.** The brainstorming conversation generated ideas—documentation architecture turns those ideas into persistent, referenceable project structure.

---

::: tip Key Takeaway
The brainstorming session isn't about getting AI to agree with your vision—it's about discovering what's realistic to build FIRST. A good session challenges your assumptions and produces a scope you're confident you can execute in 2-4 weeks for $200-$500.
:::

---

**Next:** [Chapter 4: Documentation Architecture](/part-2/documentation-architecture) — Creating the project "DNA" that guides all development.
