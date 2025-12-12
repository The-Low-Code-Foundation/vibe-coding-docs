---
title: Tool Selection & Setup
description: Choosing the right AI coding tools for structured, production-ready development
---

# Chapter 2: Tool Selection & Setup

## TLDR

**Recommended Primary Tool: Cline (VS Code extension)**
- Best for methodical, structured workflows
- Plan Mode → Act Mode separation works perfectly with task-based approach
- Terminal command approval enables human oversight
- Handles complex projects with multiple documentation references

**Alternative: Claude Code (Terminal-based)**
- Better for quick, exploratory work
- "Magic touch" - good for rapid prototyping
- Less suitable for highly structured workflows
- Works well for experienced developers

**Critical Requirement: Extended Thinking**
- Not optional - fundamental to methodology
- Enables brainstorming, planning, and complex reasoning
- Without it, you get shallow analysis and poor decisions
- Available in Claude Sonnet 4.5+ and Opus 4

**Proven Results:**
This methodology built [RISE](https://github.com/The-Low-Code-Foundation/rise) - a complete desktop application for low-code AI development - in 4 weeks for ~$400 in tokens.

---

## Real-World Example: Building RISE

Before diving into tool comparison, let's see concrete proof this methodology works.

### RISE: Rapid Integrated Scalable Environment

**What It Is:**
A desktop application for low-code AI-assisted development. It's a tool for building applications with AI... that was itself built with AI using this exact methodology.

**Complexity Level:**
- Electron desktop application
- Multi-process architecture (main + renderer)
- WebPack configuration
- Multiple UI components
- File system operations
- Build and deployment pipelines

**Project Stats:**
- **Timeline:** MVP in 4 weeks
- **Token Cost:** ~$400 (Sonnet 4.5)
- **Lines of Code:** ~15,000 (including tests)
- **Documentation:** 50%+ comments, comprehensive docs
- **Quality:** Production-ready with test coverage
- **Maintainability:** Another developer could take over immediately

**View the actual code:** [github.com/The-Low-Code-Foundation/rise](https://github.com/The-Low-Code-Foundation/rise)

### What Made RISE Possible

**1. MVP Scoping**
Full vision was ambitious (low-code platform with AI, templates, deployment, etc.). Started with MVP: core project generation with AI assistance.

**2. Tool Choice: Cline**
Cline's structured workflow was critical because:
- Electron apps have complex multi-file dependencies
- WebPack config required careful planning
- IPC communication between processes needed reasoning
- Terminal approval prevented costly build mistakes

**3. Documentation Architecture**
- ROADMAP.md with phases → tasks → subtasks
- CLAUDE_RULES.md with Electron-specific standards
- LEARNINGS.md captured solutions to problems
- Each task documented with confidence scores

**4. Phase Audits**
After completing core functionality:
- Pushed to GitHub
- Used Claude web to audit codebase
- Identified missing error handling
- Created annex tasks
- Fixed before continuing

**Result:** A working, documented, maintainable desktop application.

**This proves:** Complex projects with serious architecture are achievable with this methodology.

---

## Why Tool Selection Matters

Different AI coding tools have different strengths:

| Tool | Workflow | Best For | This Methodology |
|------|----------|----------|------------------|
| Cline | Plan → Act | Structured development | ✅ Recommended |
| Claude Code | Terminal-first | Exploration, prototyping | ⚠️ Works but less ideal |
| Cursor | Inline + chat | Traditional coding | ❌ Not structured enough |
| GitHub Copilot | Autocomplete | Code completion | ❌ Too limited |
| Claude Web | Chat-based | Brainstorming, audits | ✅ For specific phases |

---

## Cline: The Recommended Tool

### What It Is

Cline is a VS Code extension that provides an agentic coding assistant with:
- **Plan Mode:** AI thinks through approach before acting
- **Act Mode:** AI executes the planned changes
- **Terminal Approval:** Human confirms commands before execution
- **File System Access:** Full read/write to project
- **Context Awareness:** Reads project documentation naturally

### Why It Excels for This Methodology

**1. Plan Mode → Act Mode Matches Task Workflow**

Our methodology:
```
Task → Plan (what to do) → Execute (do it) → Verify (check quality)
```

Cline's workflow:
```
Prompt → Plan Mode (AI proposes approach) → Act Mode (AI executes) → Terminal approval
```

**Perfect alignment.**

**Example from RISE development:**
```
You: "Can we please plan out task 3: Implement project generation"

Cline (Plan Mode):
[Reads ROADMAP.md]
[Reads task-2-results.md] 
[Reads CLAUDE_RULES.md]

"I'll implement project generation based on user templates.

Plan:
1. Create templates/ directory structure
2. Implement template parser
3. Add file generation logic
4. Create error handling for missing templates
5. Write unit tests for parser
6. Document in task-3.md with confidence score

Questions before starting:
- Should templates support nested directories?
- Error handling: fail loudly or use defaults?
- Template variable syntax: {{variable}} or ${variable}?"

You: "Yes to nested dirs, fail loudly, use {{variable}} syntax"

Cline: "Understood. Ready to execute. Switch to Act Mode?"

You: "Yes, go ahead"

Cline (Act Mode):
[Creates templates/directory.js]
[Creates templates/parser.js]
[Creates templates/generator.js]
[Writes tests]
[Stops before: npm test]

Cline: "I want to run: npm test"

You: [Approve]

Cline: [Runs tests]
       "Tests passing (18/18)
        
        Documenting in task-3.md...
        
        Confidence Score: 8/10
        - Template parsing works ✅
        - Nested directories supported ✅
        - Error handling implemented ✅
        - Tests passing ✅
        - Missing: Template validation (nice-to-have)
        
        Ready for task 4."
```

**This is exactly our methodology in action.**

**2. Terminal Command Approval Prevents Expensive Mistakes**

During RISE development, terminal approval caught:

```
Cline: "I want to run: rm -rf node_modules package-lock.json"
You: [Wait, why? Let me check...]
You: [Modify command to just: rm package-lock.json]
```

Without approval: Potentially destructive command runs automatically.
With approval: You maintain control.

**Critical for:**
- npm install commands (verify package names)
- Database migrations (review before running)
- Build commands (check configuration first)
- Deployment scripts (never auto-deploy!)

**3. Context Integration**

Cline naturally reads project files:
```
Cline: [I need to understand the architecture]
Cline: [Reads docs/ARCHITECTURE.md]
Cline: [Reads docs/LEARNINGS.md]
Cline: [References previous task docs]
Cline: [Checks CLAUDE_RULES.md for standards]
```

You don't have to manually paste context. Cline finds what it needs.

**4. New Chat Per Task Pattern**

```
Task 2 complete:
[Close Cline chat]

Open new Cline chat:
You: "Can we please plan task 3?"
Cline: [Fresh context, reads docs, proceeds]
```

Clean slate each time. No context pollution.

### Cline Setup

**Install:**
1. Open VS Code
2. Extensions → Search "Cline"
3. Install "Cline - AI Assistant"

**Configure:**
```json
// settings.json
{
  "cline.apiProvider": "anthropic",
  "cline.apiKey": "sk-ant-...",
  "cline.model": "claude-sonnet-4-20250514",
  "cline.autoApproveCommands": false,  // Require approval
  "cline.enableThinking": true
}
```

**Verify:**
```
1. Open Cline panel (View → Cline)
2. Test: "Please read README.md and tell me what this project does"
3. Verify Cline can access files
```

---

## Claude Code: The Alternative

### What It Is

Terminal-based AI coding tool from Anthropic. You interact via command line:

```bash
$ claude "add authentication to this Express app"
```

### Advantages

**1. Speed and Directness**
```bash
$ claude "fix the bug in auth.js"
[Claude immediately starts working]
```

No Plan → Act ceremony. Just go.

**2. Thinking Levels**
```bash
$ claude "think about the architecture"
$ claude "think hard about this algorithm"  
$ claude "think harder through this refactor"
$ claude "ultrathink this complex design"
```

Explicit control over reasoning depth.

**3. Terminal-Native**
Developers who live in terminal may prefer this workflow.

### Disadvantages for This Methodology

**1. Less Structured**
No explicit Plan → Act separation. You have to manually say "plan first":
```bash
$ claude --plan "how should we implement task 3?"
$ claude --act "implement task 3 based on plan"
```

**2. Less Approval Workflow**
By default, more autonomous. You can add approval but it's not as natural as Cline.

**3. Documentation Integration**
Can read files, but less integrated feeling. You often have to explicitly tell it:
```bash
$ claude "read ROADMAP.md then plan task 3"
```

### When to Use Claude Code

**Best for:**
- Quick fixes and iterations
- Exploratory coding sessions
- Experienced developers who want speed
- Terminal-first workflows

**Example workflow:**
```bash
# Quick bug fix
$ claude "the login isn't working, debug it"

# Exploratory architecture
$ claude "ultrathink about how to structure the matching algorithm"

# Rapid iteration
$ claude "add error handling to all API endpoints"
```

**Not ideal for:** 
- Highly structured, documentation-heavy projects
- When you need strong approval workflows
- Beginners who need more guardrails

---

## Claude Web Interface: Specialized Uses

### Primary Use: Phase Audits

After completing a phase:

**Step 1: Push to GitHub**
```bash
git add .
git commit -m "Phase 1 complete"
git push origin main
```

**Step 2: Create Claude Project**
```
1. Go to claude.ai
2. Projects → New Project
3. Add GitHub integration
4. Sync your repository
```

**Step 3: Audit Prompt**
```
You are a senior software engineer conducting a code audit.

This repository contains the completed MVP phase (v0.1) of [project].
It was built using AI-assisted development with the following standards:
[paste relevant CLAUDE_RULES.md sections]

Please:
1. Review all code for quality, security, and best practices
2. Check test coverage and documentation
3. Identify any bugs or issues
4. Rate overall quality X/10
5. If < 9/10, provide specific "annex tasks" to fix issues

Be thorough but constructive. Goal is production-ready code.
```

**Step 4: Review Results**
```
Claude (acting as senior dev):

"# Phase Audit Results

## Overall Score: 7/10

### Issues Found:

❌ Critical:
1. API endpoints missing rate limiting (security risk)
2. Password reset not implemented (in requirements)

❌ Important:
3. Error messages expose internal details
4. No database migration docs

⚠️ Minor:
5. Some TypeScript 'any' types
6. Console.log statements in production code

### Annex Tasks:

Task 1.A: Rate Limiting (Critical - 2 hours)
Task 1.B: Password Reset (Critical - 4 hours)
Task 1.C: Secure Errors (Important - 2 hours)
Task 1.D: Migration Docs (Important - 1 hour)
Task 1.E: TypeScript Cleanup (Minor - 2 hours)

After fixes: Should reach 9/10"
```

### Secondary Use: Initial Brainstorming

Before starting project:

```
Claude Web with Extended Thinking:

"I want to build [full vision description].

Can you:
1. Analyze the complexity
2. Identify core value proposition
3. Propose realistic MVP scope
4. Outline v1.0 and production phases
5. Estimate timeline and costs"
```

Get MVP scoping before moving to Cline for execution.

---

## Extended Thinking: The Critical Requirement

### Why It's Non-Negotiable

This methodology requires AI to:
- **Analyze complexity** (MVP scoping)
- **Make architecture decisions** (database choice, patterns)
- **Debug systematically** (trace issues step-by-step)
- **Evaluate its own work** (confidence scoring)
- **Reason about trade-offs** (performance vs simplicity)

All of these require **deep reasoning**, not just pattern matching.

### Example: With vs Without Extended Thinking

**Task:** "Design the user matching algorithm"

**Without Extended Thinking:**
```
AI: "Here's a matching algorithm using cosine similarity:

function matchUsers(user1, user2) {
  // Compare skills and interests
  return cosineSimilarity(user1.vector, user2.vector)
}
"
```

**With Extended Thinking:**
```
AI: [Internal reasoning]
     - Need to match 1000+ users
     - Real-time matching vs pre-computation?
     - Data structure: vectors (slow) vs sets (fast)?
     - Storage: Postgres vs Qdrant vs in-memory?
     - Scale considerations...
     [Analyzes trade-offs]
     
"For the matching algorithm, I analyzed several approaches:

1. Vector Similarity (Qdrant)
   Pros: Sophisticated matching, handles nuance
   Cons: 2-3 second latency for 1000 users
   Verdict: Too slow for MVP

2. Set Overlap (in-memory)
   Pros: <100ms for 1000 users, simple
   Cons: Less sophisticated matching
   Verdict: Good enough for MVP

3. Hybrid (Set pre-filter + Vector refinement)
   Pros: Balance of speed and quality
   Cons: More complexity
   Verdict: Save for v1.0

Recommendation: Set overlap for MVP
- Fast enough (user won't wait)
- Simple enough (less to debug)
- Validates concept quickly
- Can enhance in v1.0 after MVP proves valuable

Implementation:
function matchUsers(user1, user2) {
  const skillsOverlap = intersection(user1.skills, user2.skills)
  const interestsOverlap = intersection(user1.interests, user2.interests)
  
  // Weight skills 2x (professional networking more valuable)
  return (skillsOverlap.length * 2) + interestsOverlap.length
}

This meets MVP needs: O(n) complexity, <100ms, simple to debug."
```

**The difference:**
- Without: Generic solution, no analysis
- With: Reasoned choice considering constraints, trade-offs, future path

### How to Enable Extended Thinking

**Claude.ai Web:**
```
Settings → Extended Thinking → Enable
```

**Cline:**
Automatically uses extended thinking when configured with Claude models.

**Claude Code:**
Use thinking keywords:
```bash
$ claude "think about..."        # Basic thinking
$ claude "think hard about..."   # More thinking
$ claude "think harder about..." # Even more
$ claude "ultrathink about..."   # Maximum thinking
```

**API:**
```python
response = client.messages.create(
    model="claude-sonnet-4-20250514",
    thinking={
        "type": "enabled",
        "budget_tokens": 10000
    },
    messages=[...]
)
```

### Cost of Extended Thinking

**Token breakdown for typical task:**
- Thinking tokens: ~2000-5000 (internal reasoning)
- Output tokens: ~3000-8000 (response)
- Total: ~5000-13000 tokens per task

**Cost per task:**
- Simple: ~$0.05-$0.10
- Medium: ~$0.15-$0.25
- Complex: ~$0.30-$0.50

**Full MVP (20-40 tasks):**
- Total tokens: ~200,000-500,000
- Cost: $10-$25 (thinking) + $15-$30 (output) = **$25-$55 in token costs**
- Plus human oversight time: ~20-40 hours

**Total MVP cost: ~$200-$500**

**Worth it?** Absolutely. The alternative (no thinking) produces bad architecture that costs more to fix than the thinking tokens cost.

---

## Setup Checklist

### Required

- [ ] Claude Pro/Team/API subscription
- [ ] Extended thinking enabled
- [ ] Cline installed in VS Code
- [ ] Cline configured with API key
- [ ] Git installed and configured
- [ ] GitHub account
- [ ] Project directory structure created

### Recommended

- [ ] GitHub Desktop (for easier Git workflow)
- [ ] Terminal emulator (for Claude Code if using)
- [ ] Documentation templates ready (Part II covers this)

### Optional

- [ ] Docker (if building containerized apps)
- [ ] Postman (for API testing)
- [ ] Database tools (TablePlus, DBeaver, etc.)

---

## Decision Tree: Which Tool?

```
Are you building a production application?
├─ YES
│  └─ Do you need extensive documentation?
│     ├─ YES → Use Cline (recommended)
│     └─ NO → Use Cline anyway (you'll thank yourself later)
│
└─ NO (just prototyping)
   └─ Use Claude Code for speed

Are you following this methodology exactly?
├─ YES → Use Cline (designed for it)
└─ NO → Use whatever you prefer

Do you need terminal command approval?
├─ YES → Use Cline
└─ NO → Claude Code works

Are you a beginner with AI coding?
├─ YES → Use Cline (more guardrails)
└─ NO → Either works

Is this a complex multi-module project?
├─ YES → Use Cline (better context handling)
└─ NO → Either works
```

**Bottom line: Use Cline for 90% of cases.**

---

## Cost Estimation

### Per-Task Costs (Sonnet 4.5)

| Task Type | Thinking Tokens | Output Tokens | Cost |
|-----------|----------------|---------------|------|
| Simple CRUD | 1,000 | 3,000 | $0.05 |
| Auth System | 3,000 | 8,000 | $0.15 |
| Complex Algorithm | 5,000 | 10,000 | $0.25 |
| Refactor | 4,000 | 12,000 | $0.30 |

### Project Costs

| Project Size | Timeline | Tasks | Token Cost | Human Time | Total Cost |
|--------------|----------|-------|------------|------------|------------|
| Simple Dashboard | 2 weeks | 15 | $150-$250 | 15 hours | $900-$1,000 |
| Complex App | 4 weeks | 30 | $300-$500 | 30 hours | $1,800-$2,000 |
| Enterprise System | 8 weeks | 60 | $600-$1000 | 60 hours | $3,600-$4,000 |

*Human time at $50/hour for oversight and verification*

### ROI Comparison

**Traditional development:**
- 2-week project: $8,000-$12,000
- 4-week project: $16,000-$32,000

**This methodology:**
- 2-week project: $900-$1,000 (89% savings)
- 4-week project: $1,800-$2,000 (91% savings)

**Plus benefits:**
- Extensive documentation included
- Comprehensive tests included
- Faster iteration cycles
- Easy to pause/resume

---

## Real-World Validation

### RISE Development: By the Numbers

**Project:** Desktop application (Electron)
**Complexity:** High (multi-process, WebPack, build pipeline)

**Timeline:**
- Week 1: Brainstorming + Documentation (10 hours)
- Week 2-4: Development (60 hours total)
- Week 4: Audit + Polish (10 hours)
- **Total: 4 weeks, 80 hours**

**Costs:**
- Sonnet tokens: ~$400
- Opus tokens (complex reasoning): ~$50
- Human oversight: 80 hours @ $50 = $4,000
- **Total: $4,450**

**Deliverables:**
- Complete desktop application
- 15,000+ lines of code
- Comprehensive tests
- Extensive documentation (50%+ comments)
- Production-ready deployment

**Traditional cost estimate:** $20,000-$30,000

**Savings: 75-85%**

**View the results:** [github.com/The-Low-Code-Foundation/rise](https://github.com/The-Low-Code-Foundation/rise)

---

## Summary

**Recommended Stack:**
1. **Cline** (primary development)
2. **Claude Web** (brainstorming + audits)
3. **Claude Sonnet 4.5** (main model)
4. **Extended Thinking** (always enabled)

**Why This Works:**
- Proven with real projects (RISE, dashboards, etc.)
- Structured workflow matches methodology
- Terminal approval maintains control
- Cost-effective ($200-$500 per MVP)
- Production-ready output

**Next:** [Part II: The Brainstorming Session](/part-2/brainstorming) - The conversation that prevents expensive mistakes.

---

::: tip See It In Action
[RISE on GitHub](https://github.com/The-Low-Code-Foundation/rise) shows exactly what this methodology produces:
- Complete desktop application
- Extensive documentation
- Task-based development visible in commits
- Confidence scoring in task files
- Production-ready code quality

This is not theory. This is proven.
:::
