---
name: exam-revision-plan
description: "Build a multi-day revision plan up to an exam or deadline, then start today's study blocks in PomoDial. Use when the user mentions an exam, test, finals, a thesis or assignment deadline, or asks \"how should I revise before Friday?\" or \"make me a study schedule\"."
---
# Exam revision plan

PomoDial times and saves individual sessions; it doesn't store multi-day schedules. So write the multi-day plan in the conversation, and use PomoDial to run each day's study blocks.

## Steps

1. **Ask for what's missing** (in one message): exam date, subjects/topics, roughly how many hours a day they can study, and any days off.
2. **Write the plan** as a compact table: day | topics | number of 25-minute Pomodoros. Rules of thumb:
   - Weakest topics earlier; spread each topic over at least two days (spaced repetition).
   - Mix new material with review of earlier topics.
   - The day before the exam: light review and a past paper, no new topics.
   - Keep it realistic: most students sustain 6–10 Pomodoros a day.
3. **Offer to start today's blocks.** If the user agrees, use the plan-focus-session skill for today: `plan_focus_session` for today's window, then `start_focus_session` (mode `pomodoro`) with the first topic as the intention.
4. **On later days**, if the user comes back ("what's today's plan?"), restate that day's row from the plan in the conversation and start the first block. To check progress so far, call `get_focus_history` with `start_date` = the plan's first day and compare the saved intentions with the plan.

Never claim the plan is saved in PomoDial; only sessions are saved.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
