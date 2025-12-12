---
title: Introduction
description: What this guide is and who it's for
---

# Introduction

## TLDR

Most AI coding fails because people build everything at once, skip quality checks, and end up with expensive broken code.

This guide fixes that with a simple system: scope an MVP first, document before coding, check quality as you go, and audit between phases.

It's not magic. It's just structure that works.

---

## The Problem

You have a great idea. You prompt AI to build it. Three weeks and $2000 in tokens later, you have 50,000 lines of code that sort of works but breaks in weird ways. You can't fix the bugs. You can't hand it to another developer. Project abandoned.

This happens because:
- **No scoping** — You asked for everything at once
- **No quality gates** — Broken code kept building on broken code
- **No documentation** — AI "forgot" early decisions
- **No validation** — You never checked if the core concept even worked

## The Solution

Before building anything, have a conversation with AI:

> "I want to build X. Help me identify what I can realistically build in 2-3 weeks to prove the core concept works."

That conversation produces an MVP scope. Build that first. If it works, continue. If not, you learned for $200 instead of $2000.

Then apply structure during development:
- **Document first** — AI reads your docs for context every session
- **Task-based work** — One focused task per session
- **Confidence scoring** — Rate each task 1-10, fix anything below 8
- **Phase audits** — Fresh AI reviews your code between major milestones

---

## What You'll Learn

**Part I: Foundation**
- Why structure matters more than AI capability
- Choosing the right tools (Cline vs Claude Code)

**Part II: Pre-Development**
- The brainstorming session that scopes your MVP
- Setting up your documentation

**Part III: Execution**
- The Cline workflow (Plan → Act → Verify)
- Task documentation patterns
- Confidence scoring

**Part IV: Quality**
- Phase audits with fresh AI eyes
- When and how to comment code

**Part V: Advanced**
- Context window management
- Common pitfalls and recovery
- Team workflows

**Part VI: Resources**
- Templates (lean ones, not 80-line monsters)
- Prompt library
- Case studies

---

## Who This Is For

**Developers** — You want AI to accelerate your work without producing garbage code.

**Technical Founders** — You need to validate ideas quickly without burning your runway.

**Team Leads** — You want standards for how your team uses AI tools.

**Non-coders with technical sense** — You can read code and guide AI even if you don't write it fluently.

---

## What This Isn't

❌ A tutorial on using Claude or ChatGPT basics

❌ Magic that removes human judgment

❌ A way to build production apps with zero coding knowledge

❌ Guaranteed success (but much better odds)

---

## Prerequisites

- Basic understanding of software development
- Comfort with command line and Git
- Claude API access (Pro, Team, or API)
- Cline extension for VS Code (recommended)
- Willingness to document before coding

---

## Expected Results

| Project Type | Timeline | Token Cost | Output |
|--------------|----------|------------|--------|
| Simple MVP | 2-3 weeks | $150-300 | Working proof of concept |
| Complex MVP | 4-6 weeks | $300-600 | Production-ready core |
| Large refactor | 6-12 weeks | $500-1500 | Documented, tested codebase |

These assume following the methodology. Skip steps and costs balloon.

---

## How to Read This

**If you're eager:** Jump to [Part II: Brainstorming](/part-2/brainstorming). That's where the real work starts.

**If you're skeptical:** Read [Philosophy](/part-1/philosophy) to understand why this works.

**If you just want templates:** Go to [Part VI: Resources](/part-6/templates).

**If you're setting up a team:** Start with Philosophy, then skip to [Team Workflows](/part-5/team-workflows).

---

**Let's go:** [Philosophy & Approach](/part-1/philosophy)