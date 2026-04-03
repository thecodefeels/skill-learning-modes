# skill-learning-modes

A Claude Code skill that turns any AI session into an interactive learning coach. It implements 10 evidence-based learning modes grounded in cognitive science — each one a distinct coaching style the user picks before a session begins.

## What it does

When triggered, the skill presents a menu of 10 learning modes and runs a fully interactive session in the chosen mode. Sessions are conversational: the AI waits for responses, adapts to the user's level, and ends with a concrete takeaway or summary.

## The 10 modes

| # | Mode | Best for |
|---|------|----------|
| 1 | **Socratic Drillmaster** | Building reasoning skills by never giving answers directly — only questions |
| 2 | **Mixed Practice Architect** | 30–45 min interleaved drills that mix related concepts to strengthen recall |
| 3 | **Why-How Interrogator** | Stress-testing knowledge by demanding mechanistic, edge-case-aware explanations |
| 4 | **Mental Model Forge** | Building reusable principle maps you can apply to new situations |
| 5 | **Visual Thinking Translator** | Dual-coding every concept with a verbal explanation + ASCII diagram or table |
| 6 | **Active Recall Generator** | Forcing production (summaries, analogies, flashcards) instead of passive reading |
| 7 | **Meta-Learning Coach** | Coaching the study strategy itself, not just the content |
| 8 | **Analogy Bridge Tutor** | Mapping new concepts onto domains the user already knows well |
| 9 | **Simplified Learning Strategist** | Building from a 12-year-old explanation up to full complexity, step by step |
| 10 | **Progressive Recall Mentor** | Escalating questions through Bloom's taxonomy from recall to synthesis |

## Requirements

- [Claude Code](https://claude.ai/code) CLI installed and authenticated

## Install

Clone this repo directly into the Claude Code skills directory:

```bash
git clone https://github.com/mrvn/skill-learning-modes ~/.claude/skills/learning-modes
```

That's it. Claude Code discovers skills by directory presence — no config file changes needed.

## Verify installation

```bash
ls ~/.claude/skills/learning-modes
# Expected: SKILL.md  README.md  learning-modes.skill
```

Start a Claude Code session and say any of the trigger phrases below. The skill menu should appear immediately.

## Usage — trigger phrases

The skill activates on intent, not exact wording. Any of these will trigger it:

```
teach me about X
help me understand Y
I want to learn Z
quiz me on W
explain X like I'm a beginner
help me study for X
I want to practice X
give me flashcards on X
```

After the menu appears, pick a mode by number or name, then provide a topic.

## Switching modes mid-session

Say "switch modes" or "show menu" at any point. The skill will re-present the menu and start fresh with the new mode.

## File reference

| File | Purpose |
|------|---------|
| `SKILL.md` | The skill definition loaded by Claude Code — full mode instructions and session logic |
| `learning-modes.skill` | Original packaged distribution artifact |
| `README.md` | This file |
