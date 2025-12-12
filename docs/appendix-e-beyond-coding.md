---
title: Appendix E - Beyond Coding
description: Adapting this methodology to any complex AI-assisted project across all domains
---

# Appendix E: Applying the Methodology Beyond Coding

## TLDR

**Key Insight:** This methodology works for ANY complex project where AI assists in creation, not just software development.

**Why It Works:**
- Context window limits exist in all domains
- Quality gates needed regardless of output type
- Complex projects need phased development
- Documentation architecture prevents scope creep
- Confidence scoring ensures output quality

**Proven Domains:**
- Education (lesson planning, curriculum design)
- Marketing (campaigns, content systems)
- Business processes (workflow design, documentation)
- Research (analysis pipelines, literature reviews)
- Content creation (courses, books, multimedia)

**Same Principles, Different Outputs:**
- Coding → Interactive lessons
- Database → Curriculum structure
- Tests → Learning assessments
- Deploy → Deliver to students

---

## Why This Methodology is Domain-Agnostic

### The Core Problem is Universal

**In Software Development:**
```
Problem: Build a dashboard with 20 features
AI Response: Generates 10,000 lines of code
Result: Works as demo, breaks in production
Cost: $2000 wasted
```

**In Language Education:**
```
Problem: Create a 40-hour French course with interactive activities
AI Response: Generates course outline with generic activities
Result: Activities lack pedagogical coherence, don't build on each other
Cost: 50 hours of teacher time wasted reviewing/fixing
```

**The Pattern:**
- Scope too large for AI context window
- No quality gates → mediocre output proceeds
- No documentation of decisions
- No phased validation
- Expensive failure

### The Solution is Also Universal

**Core Principles That Transfer:**

1. **MVP-First Scoping**
   - Coding: Build core feature before full app
   - Education: Create one lesson before full course
   - Marketing: Test one campaign before annual plan

2. **Documentation Architecture**
   - Coding: Roadmap, rules, learnings
   - Education: Pedagogical framework, learning objectives, lesson structure
   - Marketing: Brand guidelines, audience personas, content pillars

3. **Confidence Scoring**
   - Coding: Does code work? Tests pass?
   - Education: Does lesson achieve learning objectives? Engagement predicted?
   - Marketing: Does content match brand? Conversion potential?

4. **Phase Audits**
   - Coding: Senior developer reviews code
   - Education: Experienced teacher reviews lesson plans
   - Marketing: Brand manager reviews campaign assets

5. **Context Management**
   - Coding: New chat per task, reference docs
   - Education: New chat per lesson, reference curriculum docs
   - Marketing: New chat per asset, reference brand guidelines

**Same methodology. Different domain vocabulary.**

---

## Deep Example: Professional Language Training

Let's walk through applying this methodology to Richard's actual domain: creating AI-assisted interactive language learning content.

### The Traditional Approach (The Problem)

**Language Training Organization's Vision:**
```
"We want to create a complete 40-hour Business French course with:
- Interactive activities (drag-drop, fill-in-blank, scenarios)
- Grammar explanations adapted to learner level
- Cultural context notes
- Pronunciation guides
- Real business scenarios (meetings, emails, negotiations)
- Assessment activities
- Progress tracking
- Personalized content based on learner industry"
```

**What Usually Happens:**
```
Trainer: "AI, create a 40-hour Business French course..."
AI: [Generates generic course outline]
AI: [Creates activities that don't connect]
AI: [Provides grammatical explanations without pedagogical progression]
Trainer: [Spends 50 hours reviewing and fixing]
Result: Mediocre course that could have been made faster traditionally
```

**Why It Fails:**
- 40 hours is too large for AI context window
- No pedagogical framework documented
- Activities don't build on each other
- No validation after each lesson
- Generic content, not industry-specific
- Trainer doesn't know what's wrong until reviewing everything

### Applying the Methodology (The Solution)

#### Phase 0: The Brainstorming Session

**Opening Prompt:**
```markdown
I want to create a 40-hour Business French course for professionals.

Full vision:
- 40 hours of content (20 lessons × 2 hours each)
- Interactive HTML activities (drag-drop, fill-in-blank, matching)
- Grammar progression from A2 to B2 level
- Business scenarios (meetings, presentations, emails, negotiations)
- Industry-specific vocabulary (finance, tech, healthcare)
- Cultural notes for international business
- Pronunciation guides using audio
- Formative assessments after each unit
- Summative assessment at end
- Personalization based on learner's industry

Constraints:
- Timeline: Need pilot lesson in 2 weeks for testing
- Budget: ~$300-500 in AI tokens for development
- Team: Just me (experienced language trainer, not a coder)
- Delivery: HTML activities + PDF materials, deploy via LMS

Help me:
1. Identify core pedagogical value
2. Propose an MVP scope (one pilot lesson)
3. Separate must-have from nice-to-have
4. Estimate timeline and complexity
5. Outline full course roadmap (MVP → v1.0 → Production)
```

**AI Response (with extended thinking):**
```markdown
# Business French Course - MVP Scoping Analysis

## Core Pedagogical Value

After analyzing your vision, the essential value is:

**A coherent lesson that teaches one business skill through 
interactive activities with grammar support.**

Everything else (40 lessons, personalization, audio, assessments) 
are enhancements, but the innovation is showing that AI can create 
pedagogically sound, interactive lessons that actually teach.

## Recommended MVP Scope (v0.1)

**Goal:** Create ONE complete 2-hour lesson that proves the concept

**Timeline:** 2 weeks
**Estimated Cost:** $200-$300 in tokens
**Success Criteria:** Experienced trainer reviews and says "this is 
pedagogically sound and would work with real students"

### MVP - One Pilot Lesson

**Topic:** "Participating in a Business Meeting" (Common, high-value skill)

**Components:**

1. **Lesson Structure Document**
   - Learning objectives (clear, measurable)
   - Grammar point: Modal verbs (pouvoir, devoir, falloir) for suggestions
   - Vocabulary set: 20 meeting-related terms
   - CEFR level: B1
   - Estimated time: 2 hours

2. **Interactive Activities (4 activities)**
   - Warm-up: Match vocabulary to images (HTML drag-drop)
   - Grammar practice: Fill-in modal verbs in meeting contexts
   - Scenario: Read meeting transcript, answer comprehension questions
   - Production: Role-play meeting scenario with prompts

3. **Support Materials**
   - Grammar explanation (1 page PDF)
   - Vocabulary list with translations
   - Cultural notes: French meeting etiquette (1 paragraph)

4. **Assessment**
   - 5-question formative quiz
   - Self-evaluation rubric for role-play

### MVP Non-Features (Explicitly Deferred)

❌ 19 more lessons (build if pilot succeeds)
❌ Industry-specific vocabulary (generic business for pilot)
❌ Audio/pronunciation (text-based for MVP)
❌ Personalization engine (one-size-fits-all)
❌ LMS integration (standalone HTML files)
❌ Summative assessment (formative only)
❌ Progress tracking (manual for pilot)

## Version 1.0 (If MVP Validates)

If trainer review validates the pilot lesson:
- Create Unit 1 (5 lessons on Meeting Skills)
- Add basic audio for key phrases
- Refine activity templates based on pilot learnings
- Create unit assessment

## Production Course (If v1.0 Succeeds)

- Complete 40 hours (20 lessons, 4 units)
- Industry-specific versions (finance, tech, healthcare)
- Full audio integration
- LMS integration (SCORM package)
- Adaptive personalization
- Analytics dashboard

## Technical Recommendations for MVP

**Activity Format: HTML + JavaScript**
- Pros: Works everywhere, no special tools needed
- Cons: Requires some coding (AI can generate)
- Tool: Claude generates interactive HTML files

**Alternative: React Components** (if you want reusable)
- Pros: Better for later scaling
- Cons: More complex setup
- Tool: Claude generates React components, you deploy

**Recommendation:** Start with HTML files (simpler, proves concept faster)

## Pedagogical Framework Document

Before building, we need to document:

**PEDAGOGICAL_PRINCIPLES.md**
- Communicative approach (focus on real-world tasks)
- Task-based learning (activities simulate business contexts)
- Grammar in context (not isolated drills)
- Scaffolding (support → independence)
- Formative feedback throughout

**LESSON_TEMPLATE.md**
- Warm-up (5 min) - Activate prior knowledge
- Presentation (20 min) - New vocabulary/grammar in context
- Practice (40 min) - Guided activities
- Production (40 min) - Free production task
- Assessment (15 min) - Formative quiz

**ACTIVITY_STANDARDS.md**
- Clear instructions in French (B1 level)
- Immediate feedback mechanisms
- Authentic business contexts
- Progressive difficulty
- Cultural authenticity

## Estimated Timeline

### Week 1: Documentation + First Activity
- Day 1-2: Create pedagogical framework docs
- Day 3-4: Generate lesson structure
- Day 5-7: Create and test first two activities

### Week 2: Remaining Activities + Polish
- Day 1-3: Create remaining two activities
- Day 4-5: Create support materials and assessment
- Day 6-7: Internal review and refinement

**Confidence:** 8/10 this is achievable in 2 weeks

## Budget Estimate

- Brainstorming & framework: ~$20
- Lesson structure: ~$30
- Activity generation (4 activities): ~$120-$160
- Support materials: ~$30
- Assessment creation: ~$20
- Refinement: ~$30
- **Total: $250-$290**

Well within your $500 budget.

## Next Steps

If this scope looks good:
1. Confirm pedagogical framework
2. Create documentation structure
3. Generate lesson plan for pilot
4. Begin activity creation with task-based workflow

## Questions

1. Does one pilot lesson feel right for validation?
2. HTML activities or React components?
3. Any must-have features I put in "deferred"?
4. Is "participating in meetings" the right topic for pilot?
```

#### Phase 1: Documentation Architecture

**Core Documents (Adapted for Education):**

**1. README.md** → **COURSE_VISION.md**
```markdown
# Business French Course Vision

## The Big Picture
40-hour comprehensive Business French course for professionals...

## Current Phase: MVP (v0.1)
One pilot lesson on "Participating in Business Meetings"
- 2 hours of content
- 4 interactive activities
- B1 level
- Generic business context

## Future Phases
- v1.0: Complete Unit 1 (5 lessons on meetings)
- Production: Full 40-hour course with personalization
```

**2. ROADMAP.md** → **CURRICULUM_ROADMAP.md**
```markdown
# Curriculum Development Roadmap

## MVP Phase (v0.1) - 2 weeks

### Phase 1: Pedagogical Framework (Week 1, Days 1-2)
- Task 1.1: Create PEDAGOGICAL_PRINCIPLES.md
- Task 1.2: Create LESSON_TEMPLATE.md
- Task 1.3: Create ACTIVITY_STANDARDS.md

### Phase 2: Lesson Structure (Week 1, Days 3-4)
- Task 2.1: Define learning objectives
- Task 2.2: Select vocabulary (20 terms)
- Task 2.3: Design grammar progression
- Task 2.4: Plan activity sequence

### Phase 3: Activity Development (Week 1 Day 5 - Week 2 Day 3)
- Task 3.1: Warm-up activity (vocabulary matching)
- Task 3.2: Grammar practice (fill-in-blank)
- Task 3.3: Reading comprehension (meeting transcript)
- Task 3.4: Production activity (role-play prompts)

### Phase 4: Support Materials (Week 2, Days 4-5)
- Task 4.1: Grammar explanation document
- Task 4.2: Vocabulary list with translations
- Task 4.3: Cultural notes

### Phase 5: Assessment & Polish (Week 2, Days 6-7)
- Task 5.1: Formative quiz (5 questions)
- Task 5.2: Self-evaluation rubric
- Task 5.3: Pilot review and refinement
```

**3. CLAUDE_RULES.md** → **AI_CONTENT_STANDARDS.md**
```markdown
# AI Content Development Standards

## Pedagogical Requirements

### Every Activity Must:
- [ ] Have clear learning objective (from CEFR descriptors)
- [ ] Use authentic business context
- [ ] Provide scaffolding (support → independence)
- [ ] Include immediate feedback
- [ ] Be appropriate for B1 level
- [ ] Take 15-30 minutes to complete

### French Language Standards:
- [ ] Natural, contemporary French
- [ ] Business register (formal but not stilted)
- [ ] Clear instructions in French (B1 level vocabulary)
- [ ] Example sentence provided for complex structures
- [ ] Cultural authenticity (no false friends, cultural errors)

### Technical Standards (HTML Activities):
- [ ] Works on all modern browsers
- [ ] Mobile-responsive design
- [ ] Clear visual hierarchy
- [ ] Accessible (keyboard navigation, screen reader friendly)
- [ ] No external dependencies (self-contained)

### Confidence Scoring (Adapted):

Every activity must be scored:

**8/10 Minimum Criteria:**
- ✅ Learning objective clear and measurable
- ✅ Activity achieves objective
- ✅ Instructions clear (tested with B1 learner)
- ✅ Feedback immediate and helpful
- ✅ French language natural and error-free
- ✅ Cultural context accurate
- ✅ Technical functionality works
- ✅ Completion time appropriate (15-30 min)

**9/10 Criteria (for critical activities):**
- All 8/10 criteria PLUS:
- ✅ Exceptional engagement/motivation
- ✅ Authentic real-world relevance
- ✅ Innovative activity design

### When to Ask Human Expert:

**Automatic Review Needed:**
1. Unsure about CEFR level appropriateness
2. Cultural reference might be inaccurate
3. Grammar explanation seems unclear
4. Activity seems too easy or too hard
5. Confidence score < 8/10

**How to Flag:**
```markdown
## Expert Review Requested

Activity: [Name]
Issue: [Specific concern]
Context: [Why this is uncertain]

Questions:
1. [Specific question]
2. [Another question]

Current confidence: 7/10
Needs: Experienced trainer review
```
```

**4. TASK_TEMPLATE.md** → **ACTIVITY_TASK_TEMPLATE.md**
```markdown
# Activity Task Template

## Activity: [Name]

### Learning Objective
[One sentence: "By the end of this activity, learners will be able to..."]

### CEFR Level: [A2/B1/B2]

### Activity Type: [Vocabulary practice / Grammar drill / Reading / Speaking / Writing]

### Estimated Time: [15-30 minutes]

### Context
[Business situation where this skill is needed]

---

## Activity Design

### Instructions (in French)
[What learners will see]

### Content
[The actual activity content - vocabulary list, sentences, scenarios, etc.]

### Feedback Mechanism
[How learners know if they're correct]

### Scaffolding Provided
[Support elements: word bank, example, grammar hint, etc.]

---

## Implementation (HTML)

### Code Structure
[Skeleton of HTML structure]

### Interactive Elements
[Drag-drop? Buttons? Input fields?]

### Styling Notes
[Visual design considerations]

---

## Testing

### Functionality Tests
- [ ] Drag-drop works smoothly
- [ ] Feedback displays correctly
- [ ] All answers validated properly
- [ ] Mobile responsive
- [ ] Works in Chrome, Firefox, Safari

### Pedagogical Tests
- [ ] Instructions clear to B1 learner
- [ ] Activity achievable in estimated time
- [ ] Difficulty appropriate for level
- [ ] Feedback helps learning (not just "correct/incorrect")

---

## Confidence Score: [X/10]

### Criteria Met (Must-Have):
- [ ] Learning objective achieved
- [ ] Instructions clear
- [ ] French language correct
- [ ] Cultural context accurate
- [ ] Technical functionality works
- [ ] Time estimate realistic

### Criteria Met (Nice-to-Have):
- [ ] Exceptional engagement potential
- [ ] Innovative design
- [ ] Additional scaffolding options

### Evidence:
[Screenshots, test results, feedback from pilot tester]

### Justification:
[Why this score? What would make it higher?]

---

## Notes for Future Activities
[Lessons learned, patterns to reuse, things to avoid]
```

**5. LEARNINGS.md** → **CONTENT_LEARNINGS.md**
```markdown
# Content Development Learnings

## Pedagogical Insights

### 2024-12-12: Vocabulary Activity Design
**Discovery:** Learners get confused when vocabulary matching has more than 10 items.
**Solution:** Break into two activities: 8 items each, with thematic grouping.
**Apply to:** All future vocabulary matching activities.

### 2024-12-13: Grammar Explanations
**Discovery:** B1 learners need example sentence BEFORE rule explanation.
**Solution:** Always: Example → Pattern → Rule → Practice
**Apply to:** All grammar activities going forward.

## Technical Insights

### 2024-12-12: Drag-Drop Implementation
**Discovery:** Native HTML drag-drop has accessibility issues.
**Solution:** Use click-to-select approach with keyboard support.
**Code snippet:** [see /activities/vocabulary-match-v2.html]
**Apply to:** All interactive activities.

### 2024-12-13: Mobile Layout
**Discovery:** 3-column layout breaks on mobile devices.
**Solution:** Use CSS Grid with auto-fit: minmax(250px, 1fr)
**Apply to:** All activity layouts.

## Cultural/Linguistic Insights

### 2024-12-14: Meeting Vocabulary
**Discovery:** "RDV" (rendez-vous) not commonly used for internal meetings.
**Correction:** Use "réunion" for internal, "rendez-vous" for client meetings.
**Apply to:** Review all meeting-related content.

### 2024-12-14: Formality Levels
**Discovery:** "Tu" vs "vous" distinction critical in business scenarios.
**Solution:** All activities use "vous" unless context explicitly informal.
**Apply to:** Consistent across all lessons.
```

#### Phase 2: Execution with Cline

**Task 3.1: Create Vocabulary Matching Activity**

**Cline Prompt:**
```
Can we please plan task 3.1 - Create vocabulary matching warm-up activity?

Context:
- Lesson: Participating in Business Meetings
- Objective: Recognize 20 key meeting vocabulary terms
- CEFR Level: B1
- Format: HTML drag-drop or click-select matching
- Time: 10-15 minutes

Reference documents:
- CURRICULUM_ROADMAP.md (for lesson context)
- ACTIVITY_TASK_TEMPLATE.md (for structure)
- AI_CONTENT_STANDARDS.md (for quality standards)
- PEDAGOGICAL_PRINCIPLES.md (for teaching approach)

Please create a plan that includes:
1. Vocabulary selection (10 key terms, not 20 - manageable for activity)
2. Matching format (French term → English translation? Or term → definition?)
3. HTML implementation approach
4. Feedback mechanism
5. Confidence scoring criteria
```

**Cline Plan Mode Response:**
```markdown
# Plan: Vocabulary Matching Activity

## Vocabulary Selection

**Rationale:** Starting with 8 terms (not 10) based on cognitive load research.
More manageable for warm-up activity.

**Selected Terms:**
1. l'ordre du jour (m.) - agenda
2. le compte-rendu (m.) - minutes/meeting notes
3. le procès-verbal (m.) - formal minutes
4. la réunion (f.) - meeting
5. le participant (m.) - participant
6. présider - to chair (a meeting)
7. convoquer - to call/convene (a meeting)
8. reporter - to postpone

**Grouping:** All nouns first, then verbs (easier cognitive pattern)

## Activity Design

**Format:** French term → English translation
**Why:** B1 learners need receptive vocabulary before production

**Interface:**
- Left column: 8 French terms (randomized order)
- Right column: 8 English translations (randomized order)
- Click-select approach (accessibility-friendly)
- Visual feedback: green for correct, red for incorrect
- "Check Answers" button (not instant feedback - allows reflection)

## HTML Implementation

**Structure:**
- Semantic HTML5 (article, section elements)
- CSS Grid for layout (mobile-responsive)
- Vanilla JavaScript (no dependencies)
- Self-contained file (~200 lines total)

**Accessibility:**
- Keyboard navigation (tab, enter, arrow keys)
- Screen reader friendly (aria-labels)
- High contrast colors
- Focus indicators

## Feedback Mechanism

**On "Check Answers":**
- Correct matches: Green highlight + "Correct!"
- Incorrect matches: Red highlight + show correct answer
- Score displayed: "7/8 - Excellent!"
- Encouragement message based on score:
  - 8/8: "Parfait! You know these terms well."
  - 6-7/8: "Très bien! Review the terms you missed."
  - 4-5/8: "Bon travail! Practice these terms more."
  - <4/8: "Keep practicing! Review the vocabulary list."

## Confidence Scoring Criteria

**Must-Have for 8/10:**
- ✅ 8 appropriate B1 vocabulary terms
- ✅ Accurate translations
- ✅ Randomized order (different each time)
- ✅ Clear visual feedback
- ✅ Mobile responsive
- ✅ Accessible (keyboard + screen reader)
- ✅ Completion time: 8-12 minutes
- ✅ Instructions in French (B1 level)

**Nice-to-Have for 9/10:**
- ✅ Audio pronunciation (defer to v1.0)
- ✅ "Try again" without page reload
- ✅ Hint system

**Target:** 8/10 (sufficient for MVP)

## Questions Before Starting

1. French instructions ok? Or need English option?
   - Suggest: French only (B1 level should understand)
   
2. Include example at top showing how to use?
   - Recommend: Yes, one example pre-filled

3. Vocabulary list reference document?
   - Will need separate PDF with all 20 lesson terms

Ready to proceed to Act Mode?
```

**After Review, Act Mode:**
```
You: "French instructions only is fine. Yes to example. We'll create vocabulary PDF in Task 4.2. Please proceed."

[Cline creates activity-1-vocabulary-match.html]
[Cline tests functionality]
[Cline documents in task-3-1-activity.md]
[Cline assigns confidence score: 8/10]
```

**Result:** One complete, tested, pedagogically-sound activity created in 30-45 minutes.

#### Phase 3: Quality Assurance (Adapted)

**Phase Audit Process for Education:**

After completing all 4 activities:

1. **Push to GitHub** (or share folder)

2. **Expert Teacher Review** (human or AI as "senior educator")

**Audit Prompt:**
```markdown
You are an experienced Business French teacher with 10+ years experience.

I've created a pilot lesson "Participating in Business Meetings" with 4 activities.

Please review the lesson for:
1. Pedagogical soundness (clear objectives, appropriate scaffolding)
2. CEFR level accuracy (truly B1 or misaligned?)
3. Cultural authenticity (business context accurate?)
4. Activity sequencing (logical progression?)
5. Language accuracy (natural French, no errors)
6. Engagement potential (will students be motivated?)

Rate overall: X/10

If < 9/10, provide specific "improvement tasks" to fix issues.
```

**Audit Results:**
```markdown
# Lesson Pilot Audit

## Overall Score: 8/10

### Strengths
✅ Clear learning objectives
✅ Appropriate activity progression
✅ Language is natural and error-free
✅ Cultural context accurate (French business meetings)
✅ Activities technically functional

### Issues Found

❌ **Important:**
1. Vocabulary Activity: "procès-verbal" too formal for B1 lesson
   - Replace with "prendre des notes" (to take notes)
   
2. Grammar Activity: Modal verb explanation assumes knowledge of subjunctive
   - Simplify: focus only on indicative mood for B1

⚠️ **Minor:**
3. Role-play prompts: 4 scenarios feels rushed for 40 minutes
   - Recommend: 2 scenarios with more depth

4. Cultural notes: Mention of "tutoiement" in workplace needs context
   - Add 2-3 sentences about when "tu" acceptable

### Improvement Tasks

**Task 5.A: Revise Vocabulary List** (15 min)
- Remove "procès-verbal"
- Add "prendre des notes"
- Update matching activity

**Task 5.B: Simplify Grammar Explanation** (30 min)
- Remove subjunctive reference
- Add more example sentences (indicative only)
- Update practice activity

**Task 5.C: Reduce Role-Play Scenarios** (20 min)
- Keep 2 best scenarios
- Add reflection questions for each

**Task 5.D: Expand Cultural Notes** (15 min)
- Add context about workplace informality
- Include example situations

### After Improvements
Expected score: 9/10 (ready for pilot with students)
```

---

## Other Domain Examples

### Marketing Campaign Development

**Traditional Problem:**
"Create a full year of content for 5 social channels" → Overwhelming, inconsistent, generic

**Methodology Applied:**

**MVP:** One week of content for one channel proving tone/engagement
**Documentation:**
- BRAND_GUIDELINES.md (voice, values, visual identity)
- AUDIENCE_PERSONAS.md (who we're talking to)
- CONTENT_PILLARS.md (themes we focus on)
- POST_TEMPLATE.md (structure for each post type)
- CAMPAIGN_LEARNINGS.md (what works, what doesn't)

**Confidence Scoring:**
- On-brand voice? 8/10 minimum
- Engagement predicted? Evidence from similar posts
- Clear CTA? Measurable goal?

**Phase Audit:** Brand manager reviews week of content before expanding

---

### Business Process Documentation

**Traditional Problem:**
"Document all our processes" → Never finishes, outdated immediately

**Methodology Applied:**

**MVP:** One critical process fully documented with flowcharts
**Documentation:**
- PROCESS_FRAMEWORK.md (how we document processes)
- DEPARTMENT_GLOSSARY.md (terms and definitions)
- PROCESS_TEMPLATE.md (structure for each process doc)
- PROCESS_LEARNINGS.md (patterns discovered)

**Confidence Scoring:**
- Process accurate? Validated with team
- Flowchart clear? Stakeholders understand
- Edge cases covered? 80% of scenarios

**Phase Audit:** Process owner reviews before documenting next process

---

### Research Literature Review

**Traditional Problem:**
"Review 200 papers on topic" → Inconsistent analysis, missing connections

**Methodology Applied:**

**MVP:** 20 papers thoroughly analyzed with framework
**Documentation:**
- RESEARCH_FRAMEWORK.md (what we're looking for)
- ANALYSIS_TEMPLATE.md (how each paper analyzed)
- SYNTHESIS_STRUCTURE.md (how papers connect)
- RESEARCH_LEARNINGS.md (patterns emerging)

**Confidence Scoring:**
- Analysis thorough? Key findings extracted
- Connections identified? Papers related properly
- Critical evaluation? Limitations noted

**Phase Audit:** Senior researcher reviews analysis of 20 before expanding to 200

---

## Adaptation Framework

### How to Adapt This Methodology to Your Domain

#### Step 1: Identify Your "Code"

**What are you building with AI?**
- Coding → Applications
- Education → Lessons, courses
- Marketing → Campaigns, content
- Research → Analysis, reports
- Business → Processes, documentation

#### Step 2: Define Your Quality Criteria

**What makes output "good" in your domain?**
- Coding → Works, tested, maintainable
- Education → Achieves learning objectives, engages students
- Marketing → On-brand, engaging, converts
- Research → Rigorous, connected, insightful
- Business → Accurate, clear, actionable

#### Step 3: Adapt Core Documents

| Coding Document | Your Domain Equivalent |
|-----------------|------------------------|
| README.md | [DOMAIN]_VISION.md |
| ROADMAP.md | [PROJECT]_ROADMAP.md |
| CLAUDE_RULES.md | [DOMAIN]_STANDARDS.md |
| TASK_TEMPLATE.md | [UNIT]_TEMPLATE.md |
| LEARNINGS.md | [PROJECT]_LEARNINGS.md |

#### Step 4: Define Confidence Scoring

**For your domain, what's 8/10?**

Example templates:

**Education:**
```markdown
### 8/10 Criteria for Lesson:
- ✅ Learning objective clear and measurable
- ✅ Activity achieves objective
- ✅ Appropriate for level
- ✅ Engages students
- ✅ Accurate content
- ✅ Time estimate realistic
```

**Marketing:**
```markdown
### 8/10 Criteria for Campaign Asset:
- ✅ On-brand voice and visual identity
- ✅ Clear value proposition
- ✅ Target audience appropriate
- ✅ Strong CTA
- ✅ Platform-optimized
- ✅ Legal/compliance checked
```

**Research:**
```markdown
### 8/10 Criteria for Literature Analysis:
- ✅ Key findings extracted
- ✅ Methodology evaluated
- ✅ Limitations noted
- ✅ Connections to other papers identified
- ✅ Relevance to research question clear
- ✅ Critical evaluation present
```

#### Step 5: Adapt Workflows

**Cline Workflow (Universal):**
```
Phase X, Task Y:
1. Open new chat
2. "Can we please plan [TASK] according to [STANDARDS.md]?"
3. Review plan
4. Execute
5. Score confidence
6. Human verification for critical items
7. Document learnings
```

**This works for any domain.**

---

## Universal Principles (The Core Truth)

### What's Always True Across Domains

**1. Context Windows Are Limited**
- Can't create 40 hours of content in one conversation
- Can't write 200-page report in one go
- Can't design year-long campaign in single prompt
- **Solution:** Break into manageable chunks (lessons, sections, weeks)

**2. Quality Degrades Without Gates**
- Code without tests breaks
- Lessons without review don't teach
- Content without brand review is off-message
- **Solution:** Confidence scoring + phase audits

**3. Complex Projects Need Documentation**
- Code needs architecture docs
- Lessons need pedagogical framework
- Campaigns need brand guidelines
- **Solution:** Documentation architecture

**4. Scope Creep is Universal**
- Feature creep in coding
- Activity creep in lessons
- Channel creep in marketing
- **Solution:** MVP-first scoping

**5. AI Needs Structure**
- Vague prompts → vague output
- No framework → inconsistent output
- No validation → mediocre output
- **Solution:** Templates, standards, rubrics

### What Changes Across Domains

**Vocabulary:**
- Coding: Functions, tests, deployment
- Education: Objectives, scaffolding, assessment
- Marketing: Campaigns, assets, conversion
- Research: Analysis, synthesis, methodology

**Expertise Required:**
- Coding: Software engineering principles
- Education: Pedagogical theory
- Marketing: Brand strategy
- Research: Domain knowledge

**Validation Methods:**
- Coding: Unit tests, integration tests
- Education: Expert teacher review, student pilot
- Marketing: Brand guidelines, engagement metrics
- Research: Peer review, methodological rigor

**But the PROCESS is identical.**

---

## Template: Adapting to Your Domain

### Your Domain: _______________

**1. What are you creating with AI?**
[Description of outputs]

**2. What makes output "high quality" in your domain?**
[Quality criteria]

**3. Who validates quality?**
[Expert reviewer type]

**4. MVP Scope Exercise:**

Full Vision: [Describe complete project]

MVP (provable in 2-4 weeks): [Minimal proof of concept]

Success Criteria: [How you know MVP worked]

**5. Documentation Needed:**

| Purpose | Document Name | Contents |
|---------|---------------|----------|
| Project vision | [NAME] | [What goes in it] |
| Work breakdown | [NAME] | [How you break it down] |
| Quality standards | [NAME] | [What good looks like] |
| Unit template | [NAME] | [Template for one unit of work] |
| Learnings log | [NAME] | [Insights captured] |

**6. Confidence Scoring Criteria:**

8/10 in my domain means:
- ✅ [Criterion 1]
- ✅ [Criterion 2]
- ✅ [Criterion 3]
- ✅ [Criterion 4]
- ✅ [Criterion 5]

**7. Phase Audit Process:**

Who reviews? [Expert type]
What do they check? [Review criteria]
When? [After how much work]

---

## Summary

This methodology is **fundamentally domain-agnostic** because:

✅ Context window limits affect all domains
✅ Quality gates needed universally
✅ Complex projects always need phasing
✅ Documentation prevents scope creep everywhere
✅ AI needs structure regardless of output type

**The principles transfer perfectly. Only the vocabulary changes.**

**To adapt:**
1. Define your "code" (what you're building)
2. Define quality criteria for your domain
3. Create domain-specific documentation templates
4. Define confidence scoring rubric
5. Identify domain expert for audits
6. Use exact same workflow (plan → execute → score → audit)

**Result:** You can apply this methodology to build ANYTHING complex with AI assistance.

---

::: tip Real-World Validation
Richard successfully uses this methodology for:
- Software development (RISE, dashboards, APIs)
- Language training content (interactive lessons, activities)

Same process. Different outputs. Both work.
:::

::: warning The Key Insight
If AI struggles with context windows in your domain, and you need to build something complex with multiple interconnected parts, **this methodology will help you**.

It's not about coding. It's about managing complexity with AI assistance.
:::
