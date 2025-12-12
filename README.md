# Vibe Coding Guide

A methodology for building production-ready apps with AI assistance.

## What This Is

A structured approach to AI-assisted development that prevents the common failure pattern: spending thousands on tokens and ending up with broken code.

**Core ideas:**
- Scope an MVP before building everything
- Document first (AI has no memory—your docs are its memory)
- Work in focused tasks, one per session
- Check quality as you go (confidence scoring)
- Audit between phases

## Quick Start

1. Read the [Introduction](/docs/introduction.md)
2. Set up [your tools](/docs/part-1/tool-selection.md)
3. Have the [brainstorming session](/docs/part-2/brainstorming.md)
4. Create your [five docs](/docs/part-2/documentation-architecture.md)
5. Start building with the [Cline workflow](/docs/part-3/cline-workflow.md)

## Project Structure

```
docs/
├── introduction.md          # What and why
├── part-1/                  # Foundation
│   ├── philosophy.md        # The mindset
│   └── tool-selection.md    # Cline vs Claude Code
├── part-2/                  # Pre-Development
│   ├── brainstorming.md     # Scoping your MVP
│   └── documentation-architecture.md
├── part-3/                  # Execution
│   ├── cline-workflow.md    # Plan → Act → Verify
│   ├── task-patterns.md     # Documenting tasks
│   └── confidence-scoring.md
├── part-4/                  # Quality
├── part-5/                  # Advanced
└── part-6/                  # Resources & templates
```

## Writing Guide

See [WRITING_GUIDE.md](WRITING_GUIDE.md) for documentation standards. Key rules:
- 1,500 word max per chapter
- Templates under 30 lines
- Say it once, don't repeat
- Write like you're talking to a smart friend

## Proof It Works

This methodology built [RISE](https://github.com/The-Low-Code-Foundation/rise) — an Electron desktop app — in 4 weeks for ~$400 in tokens. Production-ready, documented, maintainable.

## Status

Documentation rewrite in progress. Core chapters complete, advanced topics coming.