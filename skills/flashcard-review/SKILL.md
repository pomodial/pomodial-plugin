---
name: flashcard-review
description: "Run focused flashcard or language-learning review sprints with PomoDial. Use when the user mentions Anki, Quizlet, flashcards, cards due, vocabulary, verbs, grammar drills or language practice (e.g. German verbs, Spanish vocab) and wants to get through them."
---
# Flashcard and language review sprints

Flashcard review works best in short, intense sprints with a clear target, because attention drops quickly on repetitive cards.

## Steps

1. **Find the target**: how many cards are due, or which deck/topic ("German verbs: Genitiv"). If unknown, ask once.
2. **Choose the sprint**:
   - Up to ~100 cards: one 20-minute `countdown`.
   - More: `pomodoro` mode, `duration_minutes` 20, `short_break_minutes` 5, enough `rounds` to cover the cards at roughly 5–8 cards a minute.
   - Speaking/drill practice: `interval` mode, e.g. 45 s speak / 15 s rest, 10 rounds.
3. **Start it** with `start_focus_session`. Put the deck and target in the intention, in the user's language: "Anki: 150 cards (German verbs)".
4. **When they finish**, call `complete_session`, then ask how many cards are left. If some remain, offer one more short sprint.

## Tips (offer once)

- Don't add new cards during a review sprint; note them for later.
- Say answers out loud for language cards.
- Leech cards (failed 4+ times) are worth rewriting, not repeating.

## If PomoDial isn't connected

If the PomoDial tools aren't available, tell the user to connect PomoDial first (in ChatGPT: Apps; in Claude: the plugin's Connectors tab or Customize > Connectors), then continue. Never pretend a session was started or saved.

## Always

- Reply in the user's language, including the intention you save.
- Never call `timer_card_action`; only the timer card's buttons use it.
- Don't show an empty timer. If `render_focus_timer` would have nothing to show, offer to start a session instead.
