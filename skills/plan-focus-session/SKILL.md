---
name: plan-focus-session
description: "Use when the user wants to plan focus, study, revision or work time into a time window today, such as \"I have 3 hours until 5pm\", \"plan my revision from 2 to 6\", \"help me study for my exam tonight\", \"plan pomodoros from 9 to 12:30 with lunch at 12\", \"fit focus blocks between my meetings\" or \"plan my afternoon\"."
---

# Plan a focus session

Turn a time window into whole focus blocks with clock times, each with an intention, and show the live PomoDial timer card.

## Inputs to collect

- **Window**: a start time, an end time, or minutes available. If the user says "now", use the current time as the start.
- **Time zone**: PomoDial takes it from the app. Only ask if the plan comes back without clock times.
- **Fixed breaks**: lunch, meetings or other times to skip. If the user mentions a break without a clock time, ask one short question for the time before planning.
- **Block length**: default 25 minutes work, 5 minutes short break. Use what the user says ("50/10" means 50 work, 10 break). Leave the long break unset unless the user asks for a specific one.
- **Intentions**: what the user will work on. If they list several tasks or topics, pass them in order as `intentions`, one per block. If they give one goal, use it for every block. Don't invent tasks they didn't mention.

## Studying and workdays

- **Students**: turn each topic into a block that names an output ("Ch. 4 notes into 10 flashcards", "Past paper Q1-3 timed"), hardest topic first. For an exam several days away, use the exam revision skill for the multi-day plan, then this skill for today.
- **Workdays**: pass each meeting and lunch as a fixed break with a label, and put the most important task in the first block.

## Steps

1. Call `plan_focus_session` with the window, date (if not today), breaks, block lengths and intentions.
2. The result includes a live timer card. Nothing is started or saved until the user presses Start on the card or asks you to start.
3. Reply in two or three lines: number of focus blocks, total focus time, the planned end time, and any note the plan returned (for example, a shortened long break or a daylight-saving change). Mention that they can press Start on the card and add the blocks to their calendar. Don't list every block unless asked.
4. If the user asks to start straight away, call `start_focus_session` for the first block with its intention.

## Don't use this skill for

- Reminders about future appointments, or schedules spread over several days.
- Questions about how long something takes (cooking, travel) or unit conversions.

If the user's own instructions conflict with this skill, follow the user.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.
