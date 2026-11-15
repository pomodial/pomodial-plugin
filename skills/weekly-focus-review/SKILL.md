---
name: weekly-focus-review
description: "Use when the user asks what they got done or studied, how much they studied or worked this week or month, how their focus or streak is going, when they focus best, wants to compare periods, or wants to pick up where they left off, using their saved PomoDial sessions."
---

# Review focus history

Give the user a short, honest review of their saved PomoDial sessions.

## Steps

1. Work out the period. Default to this week (Monday to today). Use the user's period if they give one ("last week", "October", "yesterday").
2. Call `get_focus_history` with `start_date` and `end_date` for that period and `status` "all".
3. Call `get_productivity_summary` for the current streak and all-time totals.
4. From the returned sessions only, write the review:
   - **What they worked on**: group completed sessions by intention, with time spent on each.
   - **Totals**: completed sessions and total focus time for the period, plus the current streak.
   - **Patterns** (only if there are at least 5 sessions): the time of day and weekday with the most completed focus.
   - **Unfinished**: intentions from abandoned or in-progress sessions that never got a completed session.
5. Keep it to a short paragraph plus a few bullets. End by offering one next step, such as "Want to pick up '<unfinished intention>' with a 25-minute session?" If they say yes, call `start_focus_session` with that intention.

## Rules

- Use only the data the tools return. Don't guess at sessions, times or reasons.
- If there are no sessions in the period, say so plainly and offer to start one.
- Don't judge or lecture the user about their focus.

If the user's own instructions conflict with this skill, follow the user.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.
