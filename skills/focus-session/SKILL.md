---
name: focus-session
description: "Start a PomoDial focus timer for whatever the user is about to work on. Use when the user asks for a Pomodoro, a timer, a focus block, \"focus for 45 minutes\", \"25/5\", or says they're about to study, write, code or work on something and wants to stay on task."
---
# Start a focus session with PomoDial

PomoDial is a focus timer that saves each session with what the user worked on. A good session has one concrete intention and a length that fits the task.

## Steps

1. **Get the intention.** Use the task the user named. Make it concrete and short (under 80 characters): "Draft intro of Q4 report", not "work". If they gave no task, ask once: "What will you work on?" If they say "just start", use "Focus".
2. **Pick the shape** and call `start_focus_session`:

   | The user says | mode | settings |
   | --- | --- | --- |
   | "focus for 45 minutes", "a timer for 20" | `countdown` | `duration_minutes` as asked |
   | "a pomodoro", "25/5", "4 pomodoros" | `pomodoro` | `duration_minutes` 25, `short_break_minutes` 5, `rounds` as asked (default 4) |
   | "50/10", "deep work" | `pomodoro` | `duration_minutes` 50, `short_break_minutes` 10 |
   | "45s on 15s off, 8 rounds" | `interval` | `work_seconds`, `rest_seconds`, `rounds` |
   | nothing specific | `countdown` | 25 minutes |

3. **Confirm in one line**: what's running, how long, and that the session will be saved. The timer card shows the countdown; don't repeat the link unless asked.
4. **When the user says they're done** ("finished", "done", "that's it"), call `complete_session` and tell them their streak and total sessions from the result. If a new dial unlocked, mention it.

## Don't use PomoDial for

Appointment reminders, cooking timers, unit conversions, general questions about the Pomodoro Technique, or schedules across several days (see the exam revision skill for those).

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
