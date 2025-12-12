---
title: The Brainstorming Session
description: Scoping your MVP before writing any code
---

# The Brainstorming Session

## TLDR

Before writing code, have a 30-60 minute conversation with AI to scope your MVP. Describe your full vision, then let AI help you identify what you can realistically build in 2-4 weeks to prove the core concept.

This conversation is the highest-ROI activity in your entire project. It prevents building the wrong thing.

---

## The Conversation

**Step 1: Describe everything you want**

Don't hold back. Tell AI the full vision:

> "I want to build a conference networking app where attendees get AI-powered match recommendations, can schedule meetings, message each other, see analytics on their networking, integrate with LinkedIn and Zoom..."

**Step 2: Ask for MVP scoping**

> "That's my full vision. But I want to validate the concept first. What's the minimum I could build in 2-3 weeks to prove the core idea works?"

**Step 3: Let AI analyze**

AI with extended thinking will:
- Identify your core value proposition (what's actually unique)
- Separate must-haves from nice-to-haves
- Propose a focused MVP
- Estimate timeline and cost

**Step 4: Iterate**

Push back. Ask questions:
- "Is that really minimal enough?"
- "What if we cut X?"
- "Do we need user accounts for MVP?"

Keep narrowing until you have something achievable.

---

## Example Output

After 30 minutes of conversation, you should have:

**Core insight:**
> "The unique value is AI matching. Everything else (messaging, scheduling, analytics) is enhancement. Prove matching works first."

**MVP scope:**
- Upload attendee CSV
- AI generates top 10 matches per person
- Simple page to view your matches
- Basic feedback collection
- No user accounts (magic links)
- No real-time, no messaging, no integrations

**Timeline:** 2-3 weeks

**Cost:** ~$250 in tokens

**Success criteria:** Do people find their matches valuable?

---

## Red Flags During Scoping

**"Everything is essential"**
> "We need video calls AND messaging AND scheduling or it won't work."

Push back: "Can people use Zoom links and manual scheduling for MVP? Let's prove matching works first."

**"It's not that complex"**
> "It's just calendar integration."

Reality check: Calendar integration = OAuth + multiple providers + timezones + recurring events + error handling = 2 weeks alone. Defer it.

**"Users won't understand without X"**
> "We need an onboarding tutorial or users will be confused."

Counter: Ship without it. If users are confused, that tells you exactly what to explain. Don't guess.

**Scope creep during discussion**
> "Oh, and we should also add..."

Stop. Write it down for v1.0. Don't add it to MVP.

---

## What You Walk Away With

By end of brainstorming, document:

**1. MVP Scope (one paragraph)**
> We're building a conference networking MVP that imports attendee data via CSV, generates AI-powered match recommendations, and displays top 10 matches per attendee with explanations. No user accounts, no messaging, no integrations.

**2. Success Criteria (2-3 bullets)**
- 70%+ of test users rate matches as helpful
- At least one organizer expresses purchase intent
- Core matching runs in <2 seconds

**3. Deferred Features (list)**
- User accounts → v1.0
- Real-time updates → v1.0  
- Messaging → v1.0
- Calendar integration → Production
- Mobile apps → Production

**4. Technical Decisions (list)**
- React + Node + PostgreSQL
- Simple tag matching (not vector DB) for MVP speed
- Deploy on Vercel free tier

This becomes the foundation for your README and ROADMAP.

---

## Prompts That Work

**Opening:**
```
I want to build [full description].

My constraints:
- Timeline: [2-4 weeks for MVP]
- Budget: [$200-500 in tokens]
- Skills: [what you can do]

Help me:
1. Identify the core value proposition
2. Scope an MVP that validates just that
3. List what to defer to later phases
4. Estimate timeline and cost
```

**Narrowing:**
```
That still feels big. What's the absolute minimum 
to test whether [core concept] works?
```

**Technical decisions:**
```
For this MVP scope, what tech stack would you 
recommend and why? Keep it simple.
```

---

## Common Mistakes

**Skipping this conversation entirely**
Starting with "build me X" instead of "help me scope X." You'll regret it.

**Not pushing back on AI's first suggestion**
AI often proposes something too big initially. Ask "what can we cut?"

**Forgetting to document the output**
The brainstorming insights are valuable. Write them down before they fade.

**Treating MVP features as temporary**
MVP code should still be good code. You're not throwing it away—you're building on it.

---

**Next:** [Documentation Architecture](/part-2/documentation-architecture) — Setting up the docs that guide development.