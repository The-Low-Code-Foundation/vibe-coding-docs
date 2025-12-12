---
title: Common Pitfalls
description: What goes wrong and how to recover
---

# Common Pitfalls

## TLDR

Even with a solid methodology, things go wrong. Recognizing problems early and knowing how to recover keeps projects on track.

---

## Pitfall 1: Scope Creep

**What happens:**
You're building login. AI suggests "while we're here, let's add password reset, OAuth, 2FA..."

Three days later you're still on "authentication" and nothing is done.

**Signs:**
- Tasks keep expanding
- "Quick additions" pile up
- Original timeline is blown
- MVP features keep growing

**Recovery:**
Stop. Return to your ROADMAP. Is this task done as originally scoped? If yes, close it. New ideas go to backlog, not current task.

**Prevention:**
When AI suggests additions, say: "Good idea. Add it to ROADMAP for later. For now, let's finish the original scope."

---

## Pitfall 2: Confidence Inflation

**What happens:**
AI rates everything 8/10 or 9/10. You don't verify. Later, you discover the code has significant issues.

**Signs:**
- Every task is 8/10+ with minimal justification
- You're not manually testing
- "Tests pass" but tests are superficial
- Bugs appear when integrating tasks

**Recovery:**
Slow down. For the next few tasks, verify everything yourself:
- Run the code manually
- Try edge cases
- Read the tests—are they actually testing important things?
- Question the confidence score

**Prevention:**
Treat AI's confidence score as a starting point. Trust but verify. If you haven't tested it yourself, you don't know it works.

---

## Pitfall 3: Documentation Rot

**What happens:**
You update code but not docs. ROADMAP says one thing, code does another. LEARNINGS hasn't been updated in weeks.

**Signs:**
- AI suggests things that contradict existing code
- You're confused about what's been built
- New chats start with outdated context
- Technical decisions don't match docs

**Recovery:**
Dedicate a session to doc cleanup:
- Update ROADMAP with actual status
- Review README for accuracy
- Add missing LEARNINGS entries
- Check CLAUDE_RULES still reflects reality

**Prevention:**
End-of-task habit: "Before closing, are docs updated?" Takes 2 minutes. Saves hours of confusion.

---

## Pitfall 4: The Endless Debug Loop

**What happens:**
You hit a bug. AI suggests a fix. It doesn't work. AI suggests another. Still broken. You've been on the same issue for 2 hours.

**Signs:**
- Same error keeps appearing
- Fixes create new bugs
- AI is guessing rather than reasoning
- You're frustrated and stuck

**Recovery:**
Stop. Take a break. Then:
1. Start a fresh chat
2. Clearly describe the problem from scratch
3. Ask AI to reason through it step-by-step
4. If still stuck after 30 minutes, ask a human or step away

**Prevention:**
Set a time limit. If a bug isn't solved in 30 minutes, something is wrong with the approach, not just the code. Step back and reconsider.

---

## Pitfall 5: Ignoring AI's Questions

**What happens:**
AI asks clarifying questions. You say "just do whatever." AI makes assumptions. Assumptions are wrong.

**Signs:**
- AI's output doesn't match your expectations
- You're surprised by implementation choices
- Rework is common
- "That's not what I wanted" happens frequently

**Recovery:**
For the next task, engage with every question. If AI asks "should I use approach A or B?", think about it and answer.

**Prevention:**
AI's questions are usually good. They surface ambiguity you hadn't considered. Answer them thoughtfully—it takes less time than rework.

---

## Pitfall 6: Skipping the Brainstorm

**What happens:**
You jump straight to coding without scoping. Three weeks later, you realize you built the wrong thing or too much.

**Signs:**
- No clear MVP definition
- Features keep getting added
- You're not sure when "done" is
- Budget is blown

**Recovery:**
Stop building. Have the brainstorming conversation now. Define MVP. Cut scope. Resume with focus.

**Prevention:**
Always start with: "Help me scope an MVP for this." 30 minutes of conversation prevents weeks of wasted work.

---

## Pitfall 7: Perfectionism

**What happens:**
Every task needs to be 10/10. You refactor endlessly. MVP takes 3 months instead of 3 weeks.

**Signs:**
- Tasks reopen for "polish"
- You're optimizing before validating
- "Good enough" feels wrong
- Ship date keeps slipping

**Recovery:**
Set a hard deadline. Whatever is 8/10 by that date ships. Note improvements for v1.0, don't block MVP.

**Prevention:**
Remember: MVP validates the concept. It doesn't need to be perfect. You'll improve it after you know it's worth improving.

---

## Pitfall 8: Solo Hero Mode

**What happens:**
You stop using the methodology. "I'll just quickly..." becomes "I've been hacking for a week and everything is broken."

**Signs:**
- Tasks aren't documented
- Confidence scores skipped
- Chat history is a mess
- You feel lost in your own project

**Recovery:**
Pause. Document current state. Create proper tasks for what's next. Return to the workflow.

**Prevention:**
The methodology feels slow until you experience the alternative. Trust the process, especially when you're tempted to skip it.

---

## Quick Recovery Checklist

When a project feels off-track:

1. [ ] Is scope still reasonable? (Check ROADMAP)
2. [ ] Are docs current? (Quick review)
3. [ ] Am I actually testing? (Be honest)
4. [ ] Am I in an endless loop? (Time-check)
5. [ ] Should I just start fresh? (New chat, clear head)

Most problems resolve with: stop, document current state, start a fresh chat with clear scope.

---

**Next:** [Team Workflows](/part-5/team-workflows) — Adapting this for multiple people.