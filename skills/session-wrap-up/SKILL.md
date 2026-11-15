---
name: session-wrap-up
description: "Finish a PomoDial focus session properly. Use when the user says they're done, finished, \"that's it\", \"timer's up\", or reports what they got done, so the session is completed, the streak updates and the next step is clear."
---
# Wrap up a focus session

Sessions only count fully once they're completed, and a 30-second reflection makes the next session easier to start.

## Steps

1. **Complete it**: call `complete_session` (no arguments needed; it finds the in-progress or just-finished session).
2. **Report back in two lines**: the intention and minutes from the result, plus the current streak and total sessions. Mention any newly unlocked dial.
3. **Ask one question**: "Did you finish what you set out to do?" If not, help the user write the next intention so they can restart quickly ("Finish slides 6–10").
4. **Suggest the break**: 5 minutes after a 25-minute block, 15–30 after four blocks. Suggest moving, water, or looking away from the screen.
5. **Offer the next session** with the new intention; start it with `start_focus_session` only if the user says yes.

If `complete_session` finds no session, say so plainly and offer to start one.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
