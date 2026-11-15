---
name: writing-sprint
description: "Run focused writing sprints for a thesis, dissertation, essay, paper, report, proposal, blog post or any long document. Use when the user says they need to write, draft or edit something long, is stuck on a writing task, or asks for deep work time."
---
# Writing sprints

Long writing goes faster as a few timed sprints with a concrete output per sprint, separating drafting from editing.

## Steps

1. **Define the output** of the first sprint with the user: a word count or a section ("Draft 400 words of the methods section", "Outline chapter 2"). Avoid vague intentions like "work on thesis".
2. **Choose the length**: 50 minutes with a 10-minute break for deep work (`pomodoro`, `duration_minutes` 50, `short_break_minutes` 10); 25/5 if the user is struggling to start. Default to 2–4 `rounds`.
3. **Start it** with `start_focus_session`, the output as the intention.
4. **Give one rule for the sprint**: draft only, no editing, no research tabs; leave "[TODO: check source]" notes instead of stopping.
5. **When they finish**, call `complete_session`, ask what they produced, and suggest the next sprint's output (e.g. "edit the 400 words" or "draft the next 400").
6. **For a review of writing progress**, call `get_focus_history` and summarise sessions whose intentions mention the document.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
