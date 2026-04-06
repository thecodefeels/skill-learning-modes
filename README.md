# Learning Modes

An interactive learning coach for AI coding-agent environments. It turns a normal "teach me about X" request into a guided practice session instead of a passive explanation.

This repo ships a behavior spec, not a runnable app. The main artifact is [`SKILL.md`](./SKILL.md): a portable instruction file you can load directly in hosts that support it or adapt into a host's instruction layer.

The product is host-agnostic by design:
- **Claude Code** can use [`SKILL.md`](./SKILL.md) directly as a skill definition.
- **OpenAI Codex** can use the same canonical behavior by porting [`SKILL.md`](./SKILL.md) into the repo or project instruction layer.
- **OpenCode** can use the same canonical behavior by porting [`SKILL.md`](./SKILL.md) into its equivalent instruction or agent file.

The goal is not host-specific packaging. The goal is one consistent learning experience across hosts.

## What it does

When invoked for a learning-oriented request, Learning Modes presents a menu of **8 distinct coaching modes**. The user picks one mode, provides a topic, and the AI runs an interactive session tailored to that learning style.

The sessions are designed to:
- ask, coach, and adapt instead of lecture
- keep turns short and interactive
- help the user practice, explain, retrieve, map, or simplify ideas
- end with a concrete takeaway, review, or next step

## Why it exists

Most AI teaching defaults to explanation mode. That feels productive, but often produces weaker learning than guided practice.

Learning Modes pushes sessions toward active learning instead:
- questions instead of instant answers
- retrieval instead of rereading
- interleaving instead of repetitive blocked drills
- diagrams, analogies, and mental models instead of surface summaries
- study-strategy coaching when the real problem is how to learn, not just what to learn

## Design principles

These modes are grounded in plain-language learning principles:
- **Active recall**: make the learner produce answers, summaries, and examples
- **Elaboration**: push deeper with "why?", "how?", and edge cases
- **Interleaving**: mix related concepts so the learner must choose what applies
- **Scaffolding**: adjust difficulty based on current understanding
- **Dual coding**: combine verbal explanations with visual structure
- **Metacognition**: reflect on whether the learning strategy is working

## The 8 modes

| # | Mode | Best for | Choose this when... |
|---|------|----------|---------------------|
| 1 | **Socratic Drillmaster** | Question-led reasoning and exposing weak understanding | You want to think your way to the answer instead of being told |
| 2 | **Mixed Practice Architect** | Interleaved drills and practice sessions | You want structured exercises, not just explanation |
| 3 | **Mental Model Forge** | Building reusable frameworks and principle maps | You want a topic to "click" as a system |
| 4 | **Visual Thinking Translator** | Diagrams, tables, and spatial explanations | The topic is easier to learn when you can see the structure |
| 5 | **Active Recall Generator** | Retrieval practice, flashcards, and escalating recall | You want to strengthen memory and test yourself actively |
| 6 | **Meta-Learning Coach** | Study strategy and real-time learning adjustments | You are stuck on how to study, not just what to study |
| 7 | **Analogy Bridge Tutor** | Mapping new concepts onto familiar domains | The topic feels abstract and you need a conceptual foothold |
| 8 | **Simplified Learning Strategist** | Beginner-friendly, step-by-step scaffolding | You want the topic rebuilt from simple language upward |

## What changed in v2

This version intentionally reduced the menu from 10 modes to 8.

The dropped top-level modes were merged into stronger retained modes:
- **Why-How Interrogator** is now part of **Socratic Drillmaster** as a deeper probing style
- **Progressive Recall Mentor** is now part of **Active Recall Generator** as an escalation pattern for recall practice

The result is a smaller menu with clearer differentiation.

## Quick start by host

### Claude Code

If you use Claude Code skills directly, clone this repo into your skills directory:

```bash
git clone https://github.com/thecodefeels/skill-learning-modes ~/.claude/skills/learning-modes
```

Verify the expected files are present:

```bash
ls ~/.claude/skills/learning-modes
# Expected: SKILL.md  README.md  LICENSE
```

### OpenAI Codex

Use [`SKILL.md`](./SKILL.md) as the source text for your repo-level instructions:

1. Open or create `AGENTS.md` in the repo where you want the learning coach available.
2. Add a `Learning Modes` section and paste or adapt the behavior from [`SKILL.md`](./SKILL.md).
3. Keep the trigger boundary and 8-mode menu intact so the behavior matches this repo.

### OpenCode

OpenCode setups vary more, so treat [`SKILL.md`](./SKILL.md) as the canonical behavior and port it into the instruction or agent file your setup already uses. If your OpenCode workflow supports named agents or reusable prompts, register it there as `learning-modes`.

### What should stay consistent

The behavior should stay the same across hosts:
- same 8-mode menu
- same trigger boundaries
- same pacing and interaction guardrails
- same mode goals and summaries

## First 60 seconds

Example:

```text
User: help me understand database indexing

Assistant: Pick a learning mode:
1. Socratic Drillmaster ...
2. Mixed Practice Architect ...
...
8. Simplified Learning Strategist ...

User: 3

Assistant: Mental Model Forge. What topic and domain do you want to map out?

User: database indexing in PostgreSQL

Assistant: Great. Before we build the model, what do you already believe an index does, and where does your understanding feel fuzzy?
```

That first exchange should feel the same in Codex, Claude Code, and OpenCode even if the installation mechanics differ.

## More example prompts

These are the kinds of requests that should make the skill feel immediately useful:

```text
help me study TCP congestion control
quiz me on Python iterators
explain Kubernetes like I'm a beginner
help me practice SQL joins
teach me how public-key cryptography works
```

Example:

```text
User: quiz me on Python iterators

Assistant: Pick a learning mode:
1. Socratic Drillmaster ...
2. Mixed Practice Architect ...
...
8. Simplified Learning Strategist ...

User: 5

Assistant: Active Recall Generator. What topic do you want to actively recall and test yourself on?

User: Python iterators and generators

Assistant: Great. We'll break that into a few subtopics. First: from memory, what's the difference between an iterable and an iterator?
```

## When it should trigger

Learning Modes should activate on **clear learning intent**, for example:

```text
teach me about X
help me understand Y
I want to learn Z
quiz me on W
help me study for X
give me flashcards on X
help me practice X
explain X like I'm a beginner
```

It should **not** overreach into requests where the user obviously wants:
- a direct factual answer
- task completion
- code execution
- debugging or implementation help without a learning goal

If the intent is ambiguous, the assistant should clarify whether the user wants an interactive learning session or a direct answer.

## What this is not

This repo is **not**:
- a curriculum planner
- a spaced-repetition system with saved progress
- a passive lecture generator
- a replacement for factual verification when accuracy matters
- a host-specific plugin with three separate behavior definitions

## Repository structure

| File | Purpose |
|------|---------|
| [`SKILL.md`](./SKILL.md) | Canonical learning-behavior spec |
| [`README.md`](./README.md) | Product overview, host support, and usage guidance |
| [`LICENSE`](./LICENSE) | MIT license |

Everything public in the repo is intentionally lightweight. The point is to make the behavior easy to inspect, adapt, and ship.

## Usage notes

- The assistant should keep sessions interactive rather than dumping long monologues.
- If the topic is too broad, it should narrow scope before teaching.
- If the user wants to switch modes, the menu should appear again.
- If the user says "done" or "that's enough", the assistant should wrap up with a concise takeaway.

## License

MIT. See [`LICENSE`](./LICENSE).
