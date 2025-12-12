---
title: Prompts
description: Copy-paste prompts for every phase of development
---

# Prompts

Tested prompts for each stage. Copy, paste, customize the bracketed parts.

---

## Brainstorming Prompts

**Initial scoping:**
```
I want to build [describe your full vision].

Constraints:
- Timeline: [2-4 weeks for MVP]
- Budget: [$200-500 in tokens]
- My skills: [what you can do]

Help me:
1. Identify the core value proposition
2. Scope an MVP that validates just that
3. List what to defer to later
4. Estimate timeline and cost
```

**Narrowing scope:**
```
That still feels big. What's the absolute minimum to test 
whether [core concept] works? What can we cut?
```

**Technical decisions:**
```
For this MVP scope, recommend a tech stack. 
Keep it simple—I want to move fast.
Explain trade-offs briefly.
```

**Finalizing:**
```
Summarize what we decided:
1. MVP scope (one paragraph)
2. Tech stack
3. What's deferred
4. Timeline and cost estimate
```

---

## Documentation Prompts

**Generate README:**
```
Create a README.md for this project.

Project: [name]
MVP scope: [what we're building]
Tech stack: [technologies]
Full vision: [eventual goals]

Keep it under 50 lines. Include: vision, current phase, 
tech stack, setup instructions.
```

**Generate ROADMAP:**
```
Create a ROADMAP.md breaking the MVP into tasks and subtasks.

MVP features: [list]
Timeline: [X weeks]

Each subtask should take 30-90 minutes.
Use checkbox format for tracking.
```

**Generate CLAUDE_RULES:**
```
Create CLAUDE_RULES.md for this project.

Tech stack: [technologies]
My standards: [any specific preferences]

Include: code standards, confidence scoring format,
when to ask for help, tech-specific rules.
Keep it under 40 lines.
```

---

## Task Execution Prompts

**Starting a task:**
```
Can we please plan task [X.X] - [task name]?
```

That's it. AI reads your docs for context.

**With additional context:**
```
Can we please plan task [X.X] - [task name]?

Additional context:
- [Relevant detail]
- [Changed requirement]
```

**Proceeding to execution:**
```
Looks good. Proceed.
```

**Requesting changes:**
```
Adjust the plan:
- [Change 1]
- [Change 2]

Then proceed.
```

---

## Review Prompts

**Visual verification:**
```
Before we close, describe what I should see when I:
1. [Action 1]
2. [Action 2]
3. [Action 3]

I'll verify and report back.
```

**Confidence check:**
```
What's your confidence score for this task?
List what's done and what's deferred.
```

**Task documentation:**
```
Create the task doc for what we just completed.
Use the format from TASK_TEMPLATE.md.
```

---

## Audit Prompts

**Phase audit:**
```
You're a senior developer reviewing this codebase.

Context: This is the [MVP/v1.0] phase of [brief description].

Review for:
- Bugs or logic errors
- Security issues
- Missing error handling
- Code quality problems
- Test coverage gaps

Rate 1-10. List specific issues with file references.
Be critical—I want to find problems.
```

**Focused audit:**
```
Review just the authentication code in [path].

Check for:
- Security vulnerabilities
- Missing error cases
- Test coverage

List specific issues.
```

**Re-audit after fixes:**
```
I've fixed the issues from the last audit.
Please re-review and confirm the score.
```

---

## Debugging Prompts

**When stuck:**
```
I'm stuck on this issue:

[Describe the problem]
[Include error message if any]

What I've tried:
- [Attempt 1]
- [Attempt 2]

Help me debug this systematically.
```

**When AI is looping:**
```
We've been going in circles. Let's step back.

The core problem is: [describe]
The goal is: [describe]

What's a different approach we haven't tried?
```

---

## Recovery Prompts

**Scope check:**
```
I feel like we've drifted from the original scope.

Original MVP scope: [from README]
What we've built: [current state]

Are we still on track? What should we cut?
```

**Documentation refresh:**
```
Review these docs for accuracy:
- README.md
- ROADMAP.md
- CLAUDE_RULES.md

What's outdated? What's missing?
Suggest specific updates.
```

**Fresh start:**
```
I'm starting fresh on task [X.X].

Context: [Brief state of project]
Goal: [What this task should accomplish]

Please read the project docs and propose a plan.
```

---

## Prompts to Avoid

**Too vague:**
```
❌ "Fix the bug"
❌ "Make it better"
❌ "Do whatever you think"
```

**Too verbose:**
```
❌ [500 words of context AI can find in your docs]
```

**Priming for bad output:**
```
❌ "This is probably easy..."
❌ "Just quickly..."
❌ "Tell me my code is good"
```

Keep prompts direct and specific. Let docs provide context.

---

**Next:** [Case Studies](/part-6/case-studies) — Real projects built with this methodology.