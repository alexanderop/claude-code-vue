# Transformation Examples

Complete input→output examples showing how to convert text to Slidev slides.

## Example 1: Code Tutorial

### Input

```
Vue 3 Composables Tutorial

Composables are functions that encapsulate reactive state and logic. They're the recommended way to share stateful logic in Vue 3.

Creating a composable:
1. Create a function starting with "use"
2. Use reactive APIs inside (ref, computed, watch)
3. Return the state and methods
4. Import and call in components

Example - useCounter:

import { ref } from 'vue'

export function useCounter(initial = 0) {
  const count = ref(initial)
  const increment = () => count.value++
  const decrement = () => count.value--
  return { count, increment, decrement }
}

Warning: Always return refs, not .value - this preserves reactivity.

Best practices:
- Name with "use" prefix
- Keep focused on single concern
- Document parameters and return types
- Handle cleanup in onUnmounted
```

### Output

```markdown
---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: Vue 3 Composables Tutorial
layout: cover
---

# Vue 3 Composables Tutorial

Building reusable stateful logic

---
layout: section
---

# What are Composables?

---

# Composables Overview

Functions that encapsulate reactive state and logic.

**The recommended way to share stateful logic in Vue 3.**

<VClicks>

- Replaces mixins from Vue 2
- Better TypeScript support
- Explicit dependencies
- Easy to test

</VClicks>

---
layout: section
---

# Creating a Composable

---

# The Pattern

<VClicks>

1. Create a function starting with `use`
2. Use reactive APIs inside (`ref`, `computed`, `watch`)
3. Return the state and methods
4. Import and call in components

</VClicks>

---
layout: two-cols
---

::left::

## useCounter Example

```ts
import { ref } from 'vue'

export function useCounter(initial = 0) {
  const count = ref(initial)

  const increment = () => count.value++
  const decrement = () => count.value--

  return { count, increment, decrement }
}
```

::right::

## Key Points

<VClicks>

- Function name starts with `use`
- `ref()` creates reactive state
- Methods modify the ref's `.value`
- Returns object with state + methods

</VClicks>

<Callout type="warn">

Always return refs, not `.value` - this preserves reactivity!

</Callout>

---

# Best Practices

<VClicks>

- **Name with "use" prefix** - Convention for composables
- **Keep focused** - Single concern per composable
- **Document types** - Parameters and return values
- **Handle cleanup** - Use `onUnmounted` for side effects

</VClicks>

---
layout: section
---

# Questions?
```

---

## Example 2: Architecture Overview

### Input

```
Monorepo Structure for Slidev

This project uses pnpm workspaces with three packages:

Theme package (@alexop/slidev-theme-brand):
- Custom dark theme with pink accent
- 19 layouts (cover, section, two-cols, etc.)
- Components like FolderTree, FeatureCard
- Geist Sans and Geist Mono fonts

Addon package (@alexop/slidev-addon-utils):
- Reusable components: Callout, VuePlayground
- TwoCols layout
- Shared across presentations

Starter template:
- Example presentation
- Uses both packages via workspace:*
- Run with pnpm dev

The packages are linked via pnpm workspace protocol.
```

### Output

```markdown
---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: Monorepo Structure for Slidev
layout: cover
---

# Monorepo Structure for Slidev

pnpm workspaces architecture

---
layout: section
---

# Project Structure

---
layout: two-cols
---

::left::

<FolderTree
  root
  title="Monorepo"
  :structure="`
packages
  slidev-theme-brand
    layouts/
    components/
    styles/
  slidev-addon-utils
    components/
    layouts/
starter
  slides.md
  public/
pnpm-workspace.yaml
`"
/>

::right::

## Three Packages

<VClicks>

- **Theme** - Visual styling & layouts
- **Addon** - Reusable components
- **Starter** - Example presentation

</VClicks>

<Callout type="info">

Linked via `workspace:*` protocol

</Callout>

---

# Theme Package

`@alexop/slidev-theme-brand`

<div class="grid grid-cols-2 gap-4 mt-4">

<div>

### Features

<VClicks>

- Dark theme with pink accent (#ff6bed)
- 19 layouts available
- Geist Sans & Mono fonts
- Custom components

</VClicks>

</div>

<div>

### Components

<VClicks>

- FolderTree
- FeatureCard
- QuoteCard
- ContactItem

</VClicks>

</div>

</div>

---

# Addon Package

`@alexop/slidev-addon-utils`

<VClicks>

- **Callout** - Info/warn/error alerts
- **VuePlayground** - Interactive Vue demos
- **TwoCols** - Simple two-column layout

</VClicks>

<Callout type="info">

Shared across all presentations using this theme

</Callout>

---

# Getting Started

```bash
# Install dependencies
pnpm install

# Start development
pnpm dev

# Build for production
pnpm build
```

---
layout: section
---

# Questions?
```

---

## Example 3: Comparison Content

### Input

```
Options API vs Composition API

Options API:
Pros:
- Familiar to Vue 2 developers
- Organized by option type (data, methods, computed)
- Less boilerplate for simple components

Cons:
- Logic scattered across options
- Difficult to extract and reuse logic
- Poor TypeScript inference

Composition API:
Pros:
- Logic organized by feature/concern
- Easy to extract into composables
- Excellent TypeScript support
- Better code reuse

Cons:
- Learning curve for Options API users
- More flexibility can lead to inconsistency
- Requires understanding of reactivity

Recommendation: Use Composition API for new projects, especially with TypeScript.
```

### Output

```markdown
---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: Options API vs Composition API
layout: cover
---

# Options API vs Composition API

Choosing the right approach for Vue 3

---
layout: section
---

# The Comparison

---
layout: two-cols-header
---

# Options API

::left::

## Pros

<VClicks>

- Familiar to Vue 2 developers
- Organized by option type
- Less boilerplate for simple components

</VClicks>

::right::

## Cons

<VClicks>

- Logic scattered across options
- Difficult to extract and reuse
- Poor TypeScript inference

</VClicks>

---
layout: two-cols-header
---

# Composition API

::left::

## Pros

<VClicks>

- Logic organized by feature
- Easy to extract into composables
- Excellent TypeScript support
- Better code reuse

</VClicks>

::right::

## Cons

<VClicks>

- Learning curve
- More flexibility → inconsistency risk
- Requires reactivity understanding

</VClicks>

---
layout: fact
---

# Recommendation

Use **Composition API** for new projects

<p class="text-xl mt-4 opacity-80">Especially with TypeScript</p>

---
layout: section
---

# Questions?
```

---

## Pattern Summary

| Input Pattern | Transformation |
|--------------|----------------|
| Title at top | `cover` layout with title |
| Section headers | `section` layout breaks |
| Bullet lists | `<VClicks>` wrapper |
| Code blocks | Fenced code with language |
| Warnings/tips | `<Callout type="...">` |
| File structures | `<FolderTree>` component |
| Pros/cons lists | `two-cols-header` layout |
| Key statistics | `fact` layout |
| Step-by-step | Numbered `<VClicks>` |
| Comparisons | `two-cols` layout |
