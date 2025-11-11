
# My Base Setup for Augmented Coding with AI 
Sunday, November 09, 2025

Repository: [eferro/augmentedcode-configuration](https://github.com/eferro/augmentedcode-configuration)

Over the last months I've been experimenting a lot with AI-augmented coding — using AI tools not as replacements for developers, but as collaborators that help us code faster, safer, and with more intention.

Most of the time I use Cursor IDE, and I complement it with command-line agents such as Claude Code, Codex CLI, or Gemini CLI.

To make all these environments consistent, I maintain a small open repository that serves as my base configuration for augmented coding setups:

👉 eferro/augmentedcode-configuration

## Purpose
This repository contains the initial configuration I usually apply whenever I start a new project where AI will assist me in writing or refactoring code.

It ensures that both Cursor and CLI agents share the same base rules and principles — how to write code, how to take small steps, how to structure the workflow, etc.

In short: it's a simple but powerful way to keep my augmented coding workflow coherent across tools and projects.

## Repository structure
augmentedcode-configuration/
├── .agents/
│   └── rules/
│       ├── base.md
│       └── ai-feedback-learning-loop.md
├── .cursor/
│   └── rules/
│       └── use-base-rules.mdc
├── AGENTS.md
├── CLAUDE.md
├── GEMINI.md
├── codex.md
└── LICENSE

.agents/rules/base.md
This is the core file — it defines the base rules I use when coding with AI.

These rules describe how I want the agent to behave:

Always work in small, safe steps
Follow a pseudo-TDD style (generate a test, make it fail, then implement)
Keep code clean and focused
Prefer clarity and maintainability over cleverness
Avoid generating huge chunks of code in one go
At the moment, these rules are slightly tuned for Python, since that's the language I use most often. When I start a new project in another language, I simply review and adapt this file.

🔗 View .agents/rules/base.md


.agents/rules/ai-feedback-learning-loop.md
This file defines a small feedback and learning loop that helps me improve the rule system over time.

It contains guidance for the AI on how to analyze the latest session, extract insights, and propose updates to the base rules.

In practice, I often tell the agent to "apply the ai-feedback-learning-loop.md" to distill the learnings from the working session, so it can generate suggestions or even draft changes to the rules based on what we learned together.

🔗 View .agents/rules/ai-feedback-learning-loop.md


.cursor/rules/use-base-rules.mdc
This small file tells Cursor IDE to use the same base rules defined above.

That way, Cursor doesn't have a separate or divergent configuration — it just inherits from .agents/rules/base.md.

🔗 View .cursor/rules/use-base-rules.mdc


AGENTS.md, CLAUDE.md, GEMINI.md, codex.md
Each of these files is simply a link (or reference) to the same base rules file.

This trick allows all my CLI agents — Claude Code, Codex, Gemini CLI, etc. — to automatically use the exact same configuration.

So regardless of whether I'm coding inside Cursor or launching commands in the terminal, all my AI tools follow the same guiding principles.

🔗 AGENTS.md
🔗 CLAUDE.md
🔗 GEMINI.md
🔗 codex.md


## How I use it
Whenever I start a new project that will involve AI assistance:

Clone or copy this configuration repository.
Ensure that .agents/rules/base.md fits the project's language (I tweak it if I'm not working in Python).
Connect Cursor IDE — it will automatically load the rules from .cursor/rules/use-base-rules.mdc.
When using Claude Code, Codex, or Gemini CLI, they all read the same base rules through their respective .md links.
During or after a session, I often run the AI Feedback Learning Loop by asking the agent to apply the ai-feedback-learning-loop.md so it can suggest improvements to the rules based on what we've learned.
Start coding interactively: I ask the AI to propose small, incremental changes, tests first when possible, and to verify correctness step by step.
This results in a workflow that feels very close to TDD, but much faster. I like to call it pseudo-TDD.

It's not about strict process purity; it's about keeping fast feedback loops, learning continuously, and making intentional progress.

## Why this matters
When working with multiple AI agents, it's surprisingly easy to drift into inconsistency — different styles, different assumptions, different "personalities."

By having one shared configuration:

All tools follow the same Lean/XP-style principles.
The workflow remains consistent across environments.
I can evolve the base rules once and have every agent benefit from it.
It encourages me (and the agents) to think in small steps, test early, and refactor often.
The feedback learning loop helps evolve the rule system organically through practice.
It's a small setup, but it supports a big idea:

"Augmented coding works best when both human and AI share the same working agreements — and continuously improve them together."

## Adapting it
If you want to use this configuration yourself:

Fork or clone eferro/augmentedcode-configuration.
Adjust .agents/rules/base.md for your preferred language or conventions.
Point your IDE or CLI agents to those files.
Use .agents/rules/ai-feedback-learning-loop.md to help your agents reflect on sessions and evolve the rules.
Experiment — see how it feels to work with a single, unified, and self-improving set of rules across AI tools.

## Next steps
In an upcoming post, I'll share more details about the pseudo-TDD workflow I've been refining with these agents — how it works, what kinds of tests are generated, and how it compares to traditional TDD.

For now, this repository is just a small foundation — but it's been incredibly useful for keeping all my AI coding environments consistent, adaptive, and fast.

## Related Content
Pseudo TDD with AI
Mutation Testing: When "Good Enough" Tests Weren't
When AI Makes Good Practices Almost Free
