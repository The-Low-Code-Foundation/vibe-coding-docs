---
title: Setup Guide
description: Getting your tools ready in 15 minutes
---

# Setup Guide

Everything you need to start, in 15 minutes.

---

## Required

### 1. Claude API Access

Get one of:
- **Claude Pro** ($20/month) — claude.ai with extended thinking
- **Claude API** — Pay per token, use with Cline

For this methodology, Pro is usually cheaper for moderate use.

### 2. Cline Extension

1. Open VS Code
2. Extensions → Search "Cline"
3. Install "Cline - AI Assistant"
4. Open Cline panel (View → Cline)
5. Configure:
   - API Provider: Anthropic
   - API Key: [your key]
   - Model: claude-sonnet-4-20250514
   - Auto-approve commands: **Off**

### 3. Git

If not installed:
- **Mac:** `xcode-select --install`
- **Windows:** [git-scm.com](https://git-scm.com)
- **Linux:** `sudo apt install git`

Verify: `git --version`

---

## Project Setup

**Create project structure:**

```bash
mkdir my-project
cd my-project
git init

# Create core docs
touch README.md ROADMAP.md CLAUDE_RULES.md TASK_TEMPLATE.md LEARNINGS.md

# Create source directory
mkdir src
```

**Populate docs:**

Copy templates from [Templates](/part-6/templates) into each file. Customize for your project.

---

## First Session Checklist

Before your first task:

- [ ] Cline installed and configured
- [ ] API key working (test with simple prompt)
- [ ] Project docs created from templates
- [ ] README has your MVP scope
- [ ] ROADMAP has your first few tasks
- [ ] CLAUDE_RULES customized for your tech stack

---

## Verify Setup

Open Cline and try:

```
Can you read my README.md and tell me what this project is about?
```

If Cline summarizes your project correctly, you're ready.

---

## Optional but Helpful

**GitHub account** — For phase audits and backup

**VS Code settings:**
```json
{
  "files.autoSave": "afterDelay",
  "editor.formatOnSave": true
}
```

**Project-specific .gitignore:**
```
node_modules/
.env
.DS_Store
```

---

## Quick Reference

| Tool | Purpose | Setup Time |
|------|---------|------------|
| Claude API | AI access | 5 min |
| Cline | VS Code integration | 5 min |
| Git | Version control | 2 min |
| Project docs | AI context | 30-60 min |

Total first-time setup: ~45 minutes
Subsequent projects: ~30 minutes (just docs)

---

## Troubleshooting

**Cline not responding:**
- Check API key is valid
- Check model name is correct
- Try restarting VS Code

**AI not reading docs:**
- Make sure docs are in project root
- Check file names are exact (README.md not Readme.md)
- Try explicit: "Please read README.md"

**Rate limits:**
- Wait a few minutes
- Check usage at console.anthropic.com
- Consider switching to claude-sonnet for cheaper tokens

---

**Ready?** Start with [The Brainstorming Session](/part-2/brainstorming).