---
name: client-time-log
description: "Track focused time per client or project for freelancers, consultants and agencies, and total it up. Use when the user names a client or project for a work session, asks for a timesheet, \"how many hours did I spend on Acme this month?\", or needs hours for an invoice."
---
# Client time log

PomoDial saves each session's intention, so a consistent intention format turns the history into a per-client time log.

## Starting client work

1. Name the session `<Client> – <task>`, e.g. "Acme – proposal draft". Ask for the client name if the user didn't give it.
2. Call `start_focus_session` (deep work: mode `pomodoro`, `duration_minutes` 50, `short_break_minutes` 10; otherwise as asked) with that intention.
3. When they finish, call `complete_session`.

## Totalling hours

1. Call `get_focus_history` with `status` = `completed` and `start_date`/`end_date` for the period asked (default: this month).
2. Group sessions by the client name before the dash (match case-insensitively; sessions that only mention the client in the text count too, but say so).
3. Reply with a small table: client | sessions | hours (one decimal place), plus the total. List the sessions behind a client if asked.

## Be clear about limits

- These totals are focus time from PomoDial sessions, not a full timesheet: work done without a timer isn't included.
- PomoDial Plus adds proper client tagging, billable flags and exportable reports on pomodial.com. Mention it once if the user needs invoices; don't push it.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
