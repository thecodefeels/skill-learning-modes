# Claude Skill Learning Modes

A Claude Code skill that turns any AI session into an interactive learning coach. It provides 10 evidence-based learning modes grounded in cognitive science, each one a distinct coaching style the user picks before a session begins.

This repo is meant to be dropped into a Claude Code skills directory and used immediately. There is no build step, no setup script, and no hidden configuration.

The only file Claude Code needs is `SKILL.md`.

This repository targets Claude Code's skill system. Claude Desktop can connect to Claude Code through MCP, but that is a separate integration and does not load this `SKILL.md` file as a native desktop skill.

## What it does

When triggered, the skill presents a menu of 10 learning modes and runs a fully interactive session in the chosen mode. Sessions are conversational: the AI waits for responses, adapts to the user's level, and ends with a concrete takeaway or summary.

## Why it exists

Most AI teaching experiences default to explanation mode. This skill pushes the session into deliberate practice instead:

- Socratic questioning instead of direct answers
- active recall instead of passive reading
- interleaving instead of blocked drills
- mental models, analogies, and visuals instead of surface summaries

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
git clone https://github.com/thecodefeels/skill-learning-modes ~/.claude/skills/learning-modes
```

That's it. Claude Code discovers skills by directory presence — no config file changes needed.

## What's in the repo

| File | Purpose |
|------|---------|
| `SKILL.md` | Main skill definition Claude Code loads |
| `README.md` | Project overview, install, and usage |
| `LICENSE` | MIT license for public use and redistribution |

## Verify installation

```bash
ls ~/.claude/skills/learning-modes
# Expected: SKILL.md  README.md  LICENSE
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
[`SKILL.md`](./SKILL.md) is the source of truth for the skill. The rest of the repository is supporting documentation and licensing.

## License

MIT. See [`LICENSE`](./LICENSE).
