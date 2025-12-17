---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
image: images/slideTitle.png
layout: cover
---

# Context Engineering 101

Getting the Best Vue Code out of Claude Code

---
layout: image
image: images/pastAlex.png
backgroundSize: contain
---

---
layout: image
image: images/projects.png
backgroundSize: contain
---

---

# What I wanted to share today 

- Vue best practices
- Claude Code basics
- How to combine them

---
layout: image
image: images/writeGoodStuff.png
backgroundSize: contain
---

---
layout: image
image: images/ciExample.png
backgroundSize: contain
---

---
layout: image
image: images/claudeCodeSearch.png
backgroundSize: contain
---

---
layout: image
image: images/image.png
backgroundSize: contain
---

---

Now Claude code basics

---
layout: image
image: images/context.png
backgroundSize: contain
---

---
layout: image
image: images/claudeMd.png
backgroundSize: contain
---

---

```markdown
# CLAUDE.md

AI agent guidance for Vue 3 PWA workout tracker.

## Project

**Stack**: Vue 3.5+, TypeScript (strict), Vite, Pinia, Dexie (IndexedDB), Vitest, shadcn-vue, Tailwind

**Architecture**: Bulletproof feature-based. ESLint enforces `Views → Features → Shared` boundaries.

## Commands

pnpm dev          # Development server
pnpm test         # Run tests
pnpm lint         # Fix lint errors (enforces ALL code style rules)
pnpm type-check   # TypeScript checking
pnpm build        # Production build
pnpm knip         # Find unused exports

## Before Committing

pnpm type-check && pnpm lint && pnpm test

Conventional Commits with scope: `feat(workout): add rest timer`
```

---

```markdown
## Directory Map

- `src/features/` - [Feature modules](src/features/CLAUDE.md) (workout, exercises, templates, benchmarks, settings, timers)
- `src/__tests__/` - [Testing patterns](src/__tests__/CLAUDE.md)
- `src/db/` - [Database/repositories](src/db/CLAUDE.md)
- `src/composables/` - Shared reactive logic (timers, dialogs, search)
- `src/views/` - Route-level pages
- `src/components/ui/` - shadcn-vue primitives (**do not edit**)

## Vue Pattern (No ESLint Rule)

Use `defineModel` for two-way binding: `const open = defineModel<boolean>('open')`

## Available Tools

`gh` (GitHub CLI), `tree`, `rg` (ripgrep) are installed.

## Quick Find

rg -n "export (const|function) use" src/composables src/features  # Composables
rg -n "RouteNames\." src/router                                    # Routes
tree src/features -L 2                                             # Directory structure
```

---

```markdown
# Testing Guide

AI agent guidance for testing in this Vue 3 PWA.

## Stack

**Framework**: Vitest 4 with **Playwright browser mode** (NOT jsdom)

**Libraries**: vitest-browser-vue, Vitest Browser locators (`page.getBy*`), fake-indexeddb

## Test Directories

| Directory | Purpose |
|-----------|---------|
| `composables/` | Direct composable unit tests |
| `integration/` | Full user flows with router + Pinia |
| `factories/` | Test data builders |
| `helpers/` | `createTestApp`, `withSetup`, page objects |
```

---

```markdown
## Core Patterns

### Reset Database Between Tests

import { resetDatabase } from '@/__tests__/setup'

beforeEach(async () => {
  await resetDatabase()
})
```
---


```markdown
### Test Composables Directly (No Lifecycle)

import { useRestTimer } from '@/composables/timers/useRestTimer'

it('starts timer', () => {
  const { start, isRunning } = useRestTimer()
  start(60)
  expect(isRunning.value).toBe(true)
})

### Use `withSetup()` for Lifecycle Composables

import { withSetup } from '@/__tests__/helpers/withSetup'

it('runs onMounted', () => {
  const [result, app] = withSetup(() => useMyComposable())
  expect(result.initialized.value).toBe(true)
  app.unmount()
})
```

---
layout: image
image: images/goodMdBlog.png
backgroundSize: contain
---

---
layout: image
image: images/slashFu.png
backgroundSize: contain
---

---
layout: image
image: images/slashCommand.png
backgroundSize: contain
---

---

# Custom Slash Commands

| Command | Description |
|---------|-------------|
| `/lint` | Run ESLint and fix any issues found |
| `/type-check` | Run TypeScript type checking and fix errors |
| `/check` | Review current changes with parallel subagents (multi-agent code review) |
| `/pr` | Open a pull request from the current branch (with Gherkin test plans) |
| `/push` | Commit staged changes and push to remote |
| `/fix-pipeline` | Check GitHub pipeline status and plan fixes if failing |
| `/review-coderabbit` | Review CodeRabbit comments on current PR and implement valid fixes |
| `/review-components` | Review changed Vue components for readability using design patterns |
| `/refactor-component` | Automatically refactor large Vue components using design patterns |
| `/research` | Research a problem using web search, documentation, and codebase exploration |
| `/shade` | List all available shadcn UI components in the project |
| `/create-command` | Generate a new slash command from a natural language description |


---
layout: image
image: images/codeRabi.png
backgroundSize: contain
---

---
layout: image
image: images/codeRabbit.png
backgroundSize: contain
---

---
layout: image
image: images/subagents.png
backgroundSize: contain
---

---
layout: image
image: images/research.png
backgroundSize: contain
---

---
layout: image
image: images/check.png
backgroundSize: contain
---

---
layout: image
image: images/report.png
backgroundSize: contain
---

---
layout: image
image: images/ultrahink.png
backgroundSize: contain
---

---

We can stack Slash commands that can use subagents

AGENTIC ENGINEERING !!!!

---
layout: image
image: images/notCorrect.png
backgroundSize: contain
---

---
layout: image
image: images/hooks.png
backgroundSize: contain
---

---
layout: image
image: images/stop.png
backgroundSize: contain
---

---
layout: image
image: images/skills.png
backgroundSize: contain
---

---
layout: image
image: images/searchDocs.png
backgroundSize: contain
---

---

```markdown
# null

# Claude Code Documentation Map

This is a comprehensive map of all Claude Code documentation pages with their headings, designed for easy navigation by LLMs.

> **Note:** This file is auto-generated by GitHub Actions. Do not edit manually.
> Last updated: 2025-11-06 00:10:13 UTC

## Document Structure

This map uses a hierarchical structure:

* **##** marks documentation groups (e.g., 'Getting started')
* **###** marks individual documentation pages
* **Nested bullets** show the heading structure within each page
* Each page title links to the full documentation

## Getting started

### [overview](https://code.claude.com/docs/en/overview.md)

* Get started in 30 seconds
* What Claude Code does for you
* Why developers love Claude Code
* Next steps
* Additional resources

### [quickstart](https://code.claude.com/docs/en/quickstart.md)
```

---
layout: image
image: images/vitestSkill.png
backgroundSize: contain
---

---

Most vue sites have a llms.txt

```markdown
# Vitest

> Next Generation Testing Framework

A Vite-native testing framework. It's fast!

## Table of Contents

### Config Reference

- [Configuring Vitest](/config.md)
- [include | Config](/config/include.md)
- [exclude | Config](/config/exclude.md)
- [includeSource | Config](/config/include-source.md)
- [name | Config](/config/name.md)
- [server | Config](/config/server.md)
- [deps | Config](/config/deps.md)
- [runner | Config](/config/runner.md)
- [benchmark | Config](/config/benchmark.md)
- [alias | Config](/config/alias.md)
- [globals | Config](/config/globals.md)
- [environment | Config](/config/environment.md)
- [environmentOptions | Config](/config/environmentoptions.md)
- [watch | Config](/config/watch.md)
- [watchTriggerPatterns | Config](/config/watchtriggerpatterns.md)
- [root | Config](/config/root.md)
- [dir | Config](/config/dir.md)
- [reporters | Config](/config/reporters.md)
```

---

```markdown
---
name: shadcn-vue-docs
description: Fetch and answer questions about shadcn-vue components and documentation. Use when asked about shadcn-vue usage, component APIs, installation, theming, or any Vue shadcn question. Triggers include "how do I use shadcn", "shadcn component", "shadcn-vue docs", "what shadcn components are available", or any question about vue-shadcn library usage and configuration.
---

# shadcn-vue Documentation Skill

Fetch official shadcn-vue documentation to answer user questions accurately.

## Workflow

1. **Fetch the documentation index** from `https://www.shadcn-vue.com/llms.txt`
2. **Identify relevant pages** based on the user's question
3. **Fetch specific documentation pages** to get detailed information
4. **Provide accurate answers** with code examples from the official docs
```

---

This is much better than MCPs. MCPs blow up your context and you can't customize them.

Instead of using the GitHub MCP server, just install `gh` and tell Claude Code to use it.

---
layout: image
image: images/brainStorm.png
backgroundSize: contain
---

---
layout: image
image: images/askQuestions.png
backgroundSize: contain
---

---
layout: image
image: images/details.png
backgroundSize: contain
---

---
layout: image
image: images/design.png
backgroundSize: contain
---

---

Here is Claude's plan:
╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌
 Weekly Workout Goal Feature

 Summary

 Add a weekly goal card to the home view where users can set a target (number of workouts OR total duration) and see their
 progress via a circular ring with contextual motivational messages.

 User Decisions

 - Goal metric: User chooses between workout count OR duration (hours/minutes)
 - Motivation: Progress visual + contextual text messages
 - Visual style: Circular progress ring (minimal/subtle, matches existing UI)
 - Configuration: Inline on home view (tap card to edit)
 - Data storage: Single user setting (not separate table)

---

Tips to Get Started

<v-clicks>

1. Write a good claude.md file
2. Automate what you can with slash commands (refactoring, git)
3. Think if subagents can make sense (code reviews)
4. Add hooks (files Claude should not read, e.g., .env)
5. Customize your own workflow with skills (brainstorm, git-worktree, frontend-skill)
6. Work together as a team—share what works and try to force yourself to use these tools
7. Automate tasks—ship faster and better code

</v-clicks>

---
layout: image
image: images/qaEngenier.png
backgroundSize: contain
---

---
layout: image
image: images/qaReport.png
backgroundSize: contain
---

---
layout: image
image: images/aiTags.png
backgroundSize: contain
---







