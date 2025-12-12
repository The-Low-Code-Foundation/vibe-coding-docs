---
title: Tool Selection
description: Choosing the right AI coding tool for structured development
---

# Tool Selection

## TLDR

**Use Cline** (VS Code extension) for most projects. Its Plan Mode → Act Mode workflow matches this methodology perfectly, and terminal approval keeps you in control.

**Use Claude Code** (terminal) for quick exploration or if you prefer command-line workflows.

**Use Claude Web** for brainstorming sessions and phase audits—not for writing code.

**Extended thinking is required.** Without it, AI makes shallow decisions that cost you later.

---

## Cline: The Default Choice

Cline is a VS Code extension that works in two modes:

**Plan Mode:** AI reads your project, proposes an approach, asks clarifying questions.

**Act Mode:** AI executes the plan, creating/editing files and running commands.

This matches our workflow exactly:
1. "Can we plan task 3?" → Plan Mode
2. Review the plan, adjust if needed
3. "Proceed" → Act Mode
4. Approve terminal commands as they come
5. Verify the result

**Why terminal approval matters:**

```
Cline wants to run: rm -rf node_modules && npm install
[Approve] [Reject] [Edit]
```

You see every command before it runs. This prevents disasters and keeps you aware of what's happening.

**Setup:**
1. Install "Cline" from VS Code extensions
2. Configure with your Anthropic API key
3. Enable extended thinking
4. Set `autoApproveCommands: false`

---

## Claude Code: The Alternative

Terminal-based tool. You type natural language, it writes code.

```bash
$ claude "add authentication to this Express app"
```

**Advantages:**
- Faster for quick tasks
- No VS Code dependency
- Explicit thinking levels (`think hard`, `ultrathink`)

**Disadvantages for this methodology:**
- Less structured Plan → Act separation
- You have to manually enforce approval workflows
- Context loading is more manual

**Use it when:** You're doing exploratory work, quick fixes, or you just prefer terminal.

**Skip it when:** You're doing structured, multi-phase development.

---

## Claude Web: For Specific Phases Only

**Use for brainstorming** (before development):
> "I want to build X. Help me scope an MVP."

Extended thinking shines here. Let AI reason through complexity before you commit to building.

**Use for phase audits** (between development phases):
1. Push code to GitHub
2. Start fresh Claude conversation
3. "You're a senior dev. Review this repo for issues."
4. Fix what it finds

**Don't use for:** Writing code during active development. The web interface isn't designed for file management and iterative coding.

---

## Extended Thinking: Non-Negotiable

Extended thinking is when AI reasons through a problem before responding. Without it:

**Simple prompt → shallow answer:**
> "Design a matching algorithm"
> 
> AI: "Here's cosine similarity..." [generic solution]

**With extended thinking:**
> AI thinks: "1000 users, needs to be fast, they mentioned budget constraints, vector DB might be overkill for MVP..."
>
> AI: "For your MVP scale, simple tag overlap will be faster and cheaper than vector similarity. Here's why, and here's when you'd upgrade..."

Extended thinking catches problems before they become expensive.

**Enable it:**
- Claude Web: Settings → Extended Thinking → On
- Cline: Automatic with Claude models
- Claude Code: Use `think hard` or `ultrathink` keywords

---

## Cost Expectations

| Task Type | Tokens | Cost (Sonnet) |
|-----------|--------|---------------|
| Simple task | 5-10k | $0.05-0.10 |
| Medium task | 15-25k | $0.15-0.25 |
| Complex task | 30-50k | $0.30-0.50 |

**Typical MVP (25-35 tasks):** $200-400

The methodology adds ~20% cost overhead (more documentation, confidence scoring). It saves 10x that in avoided rework.

---

## Quick Decision

```
Building something production-worthy?
├─ Yes → Cline
└─ No, just exploring → Claude Code

Need structured workflow with approval?
├─ Yes → Cline
└─ No, I want speed → Claude Code

Brainstorming or auditing?
└─ Claude Web
```

For 90% of readers following this guide: **use Cline.**

---

## Proof It Works

This methodology built [RISE](https://github.com/The-Low-Code-Foundation/rise)—a desktop Electron app—in 4 weeks for ~$400 in tokens. Production-ready, documented, maintainable.

Not a toy demo. A real application with multi-process architecture, build pipelines, and comprehensive tests.

---

**Next:** [The Brainstorming Session](/part-2/brainstorming) — The conversation that prevents expensive mistakes.