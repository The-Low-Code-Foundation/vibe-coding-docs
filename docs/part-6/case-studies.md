---
title: Case Studies
description: Real projects built with this methodology
---

# Case Studies

Real examples showing the methodology in practice.

---

## RISE: Desktop Application

**Project:** Desktop app for low-code AI-assisted development
**Complexity:** High (Electron, multi-process, webpack)
**Result:** Production-ready in 4 weeks, ~$400 tokens

### What Made It Work

**1. MVP scoping saved weeks**

Full vision included: visual code editor, AI code generation, template marketplace, cloud sync, team collaboration.

MVP scope: Project scaffolding with AI assistance. One core feature.

The brainstorming session cut 80% of features. Those features are still documented for v1.0—but MVP shipped.

**2. Documentation handled Electron complexity**

Electron apps have:
- Main process
- Renderer process
- IPC between them
- Webpack configuration
- Native module compatibility

CLAUDE_RULES included Electron-specific standards. LEARNINGS captured IPC gotchas. Each new task session started with full context.

**3. Confidence scoring caught integration issues**

Task 5 (IPC communication) initially scored 7/10—"works but timing feels fragile."

Pushed for fixes. Found race condition where renderer sent messages before main handler registered. Fixed before it became a nightmare.

**4. Phase audit found security gap**

Audit after MVP revealed: preload script exposed too much to renderer. Security risk.

Added to annex tasks. Fixed before any release.

### Numbers

| Metric | Value |
|--------|-------|
| Timeline | 4 weeks |
| Token cost | ~$400 |
| Lines of code | ~15,000 |
| Tasks | 32 |
| Avg confidence | 8.2/10 |

**Code:** [github.com/The-Low-Code-Foundation/rise](https://github.com/The-Low-Code-Foundation/rise)

---

## Simple Dashboard: Quick Win

**Project:** Internal metrics dashboard
**Complexity:** Low (React, Express, PostgreSQL)
**Result:** Working MVP in 1.5 weeks, ~$150 tokens

### What Happened

**Brainstorm output:**
- Core need: See key metrics in one place
- MVP: 5 charts, one database, manual refresh
- Deferred: Real-time updates, drill-downs, alerts

**Development:**
- Task 1: Project setup, database schema (Day 1)
- Task 2: API endpoints for each metric (Day 2-3)
- Task 3: React dashboard with charts (Day 4-5)
- Task 4: Polish and deploy (Day 6-7)

**Smooth because:**
- Small scope clearly defined
- Standard tech stack, no surprises
- Each task genuinely independent
- No complex state management

### Lessons

Simple projects don't need heavy process. But they still benefit from:
- Clear scope (prevents feature creep)
- Task structure (maintains focus)
- Confidence scoring (catches issues)

Overhead: Maybe 2 hours of documentation. Time saved: Unknown bugs not shipped.

---

## Complex Refactor: Large Codebase

**Project:** Modernize legacy Node.js backend
**Complexity:** High (existing 50k lines, many dependencies)
**Result:** Clean migration in 8 weeks, ~$600 tokens

### The Challenge

Existing codebase:
- 50,000 lines of JavaScript
- Callbacks everywhere (pre-async/await)
- No tests
- Minimal documentation
- Multiple undocumented integrations

### How Methodology Helped

**1. Brainstorming defined scope**

Not "rewrite everything." Instead: "Modernize auth module first. If that works, continue. If not, reconsider."

**2. Documentation became discovery**

Creating CLAUDE_RULES forced documenting existing patterns. Creating ROADMAP required understanding dependencies. Documentation phase revealed hidden complexity.

**3. Task structure made it manageable**

```
Phase 1: Auth module (8 tasks)
Phase 2: User module (6 tasks)
Phase 3: API routes (10 tasks)
Phase 4: Integration (4 tasks)
```

Each task: Touch one module. Keep everything else working.

**4. Phase audits verified compatibility**

After each module, audit checked:
- Old tests still pass (compatibility)
- New code meets standards
- No regressions introduced

### Numbers

| Metric | Value |
|--------|-------|
| Timeline | 8 weeks |
| Token cost | ~$600 |
| Lines modernized | ~30,000 |
| Tasks | 28 |
| Regressions caught | 12 (all in audit) |

---

## Failed Project: Learning Experience

**Project:** Real-time collaboration tool
**What happened:** Abandoned after 3 weeks and $500
**Why it failed:** Methodology was skipped

### The Mistakes

**1. No brainstorming**

Jumped straight to: "Build real-time collaborative editor."

Should have asked: "What's the MVP? Can we validate with something simpler?"

**2. No documentation**

"I'll add docs later." Later never came. Each session started confused.

**3. No confidence scoring**

"It works... mostly." Kept building on shaky foundation. Issues compounded.

**4. No phase audit**

By week 3, problems were everywhere. No clear path to fix them. Abandoned.

### What Would Have Helped

MVP scope: "Single-user editor first. Real-time sync after that works."

Documentation: Decisions captured, context preserved.

Confidence scoring: Stopped when foundation was shaky.

Phase audit: Issues caught before they multiplied.

### The Real Lesson

The methodology feels like overhead—until you skip it and watch a project fall apart.

---

## OpsNest Conference Sync: Desktop Integration Tool

**Project:** Electron app syncing Monday.com, Google Sheets, and Outlook with AI analysis
**Complexity:** High (4 API integrations, OAuth, bi-directional sync, AI classification)
**User:** Non-technical conference operations manager
**Result:** All 4 phases delivered — auth, data layer, bi-directional sync, AI email analysis

### The Problem

Conference operations managers juggle three disconnected tools:
- Monday.com for task tracking
- Google Sheets as the equipment source of truth
- Outlook for vendor communications

Every change requires manually updating all three systems. Multiply one chair order by hundreds of equipment items across dozens of event areas and you get the picture.

### What Made It Work

**1. "Download and double-click" drove every architecture decision**

The user has no technical skills and no IT department. This ruled out hosted solutions, terminal commands, and any setup requiring developer consoles. Electron was the only choice that delivers a true double-click experience with OAuth handled internally.

**2. Service Account eliminated the hardest UX problem**

Google OAuth requires users to visit Google Cloud Console — a non-starter. Instead, the app bundles a Service Account. The user just shares their Google Sheet with an email address, exactly like sharing with a colleague. Zero technical setup.

**3. AI-in-the-loop, not AI-in-charge**

Claude classifies vendor emails and drafts replies, but the user always reviews before sending. Escalations flag issues without taking action. This builds trust with non-technical users who are wary of automation making decisions for them.

**4. Source-of-truth rules prevent sync chaos**

Instead of "last write wins" (confusing), clear rules: Google Sheets wins for quantities, Monday wins for task status. Everything else escalates to the user. Simple, predictable, no surprises.

### The Phases

Each phase was a separate focused session, keeping AI context tight and diffs reviewable:

1. **Scaffold** — Electron shell, Express OAuth server, IPC bridge, 4-step onboarding wizard with all auth flows working
2. **Data layer** — SQLite schema (8 tables), Google Sheets + Monday.com imports with column mapping, live dashboard with area grid
3. **Sync engine** — Per-field change tracking via sync journal, bi-directional push to Sheets + Monday, conflict detection with auto-resolve and user escalation
4. **Email + AI** — Outlook email fetch, Claude classification (auto-response / non-answer / substantive / needs-attention), AI draft composition with equipment context, periodic escalation review

### Numbers

| Metric | Value |
|--------|-------|
| Integrations | 4 (Monday, Sheets, Outlook, Claude) |
| Auth flows | API keys (2) + Service Account + OAuth PKCE |
| Sync model | Poll-and-reconcile (2-minute interval) |
| Data model | 8 SQLite tables + sync journal |
| Phases delivered | 4 (scaffold, data, sync, email+AI) |
| Total | ~38 files, ~2,400 lines |

---

## Patterns Across Projects

**What consistently works:**
- Brainstorming cuts scope dramatically
- Documentation prevents context loss
- Confidence scoring catches issues early
- Phase audits find accumulated problems
- New chat per task keeps AI focused

**What varies by project:**
- Documentation depth (simple vs complex projects)
- Task granularity (small vs large codebase)
- Audit frequency (stable vs risky changes)

**Universal truth:**
30 minutes of planning saves days of rework. Every time.

---

**Next:** [Getting Started](/introduction) — Ready to try it yourself?