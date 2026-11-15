# PomoDial

PomoDial is a focus timer built around one habit: say what you're working on before the clock starts. This plugin brings it into ChatGPT and Claude, with skills that turn study, revision, writing and client work into timed, saved focus sessions.

![PomoDial](assets/logo.png)

## Use it

Connect your PomoDial account (free), then just ask:

- "Start a 25-minute focus session on my report"
- "Plan Pomodoros to revise for my biology exam from 2 to 6pm"
- "My exam is on Friday. Make me a revision plan"
- "Start a 20-minute Anki review, I have 150 cards due"
- "Help me write my thesis introduction in focused sprints"
- "I'm done" (completes the session and updates your streak)
- "What did I get done this week?"
- "How many hours did I spend on Acme this month?"

A live timer card shows the countdown with Start, Pause, Skip and Reset buttons. Every session is saved to your PomoDial history at [pomodial.com](https://www.pomodial.com).

## Skills

| Skill | What it does |
| --- | --- |
| `focus-session` | Starts a countdown, Pomodoro or interval timer with a clear intention |
| `plan-focus-session` | Fits study or work blocks into a time window, around breaks and meetings |
| `exam-revision-plan` | Turns an exam date into a day-by-day revision plan, then starts today's blocks |
| `flashcard-review` | Short timed sprints for Anki, flashcards and language practice |
| `writing-sprint` | Timed deep-work sprints for theses, essays and reports |
| `session-wrap-up` | Completes a session, updates the streak and sets up the next one |
| `weekly-focus-review` | Summarises what you studied or worked on, your streak and patterns |
| `client-time-log` | Logs focused time per client and totals hours for a period |

## Data

The plugin connects to the PomoDial server at `https://www.pomodial.com/mcp`, after you sign in to your PomoDial account. When you use it, it sends the session details you give (what you're working on, durations, start and finish) to your PomoDial account and reads your saved sessions to answer questions about your history. The plugin itself stores nothing and runs no code; its skills are written instructions. See the [privacy policy](https://www.pomodial.com/privacy) and [terms](https://www.pomodial.com/terms). Support: [pomodial.com/support](https://www.pomodial.com/support).

## License

MIT
