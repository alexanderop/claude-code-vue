---
name: text-to-slidev
description: Convert technical notes, documentation, and text into Slidev presentations using @alexop/slidev-theme-brand. Use when asked to create slides, presentations, convert notes to slides, turn documentation into a talk, or generate a slidev deck. Triggers: "create presentation", "make slides", "convert to slidev", "slides from", "turn into a talk", "presentation from".
---

# Text to Slidev Converter

Convert technical text into polished Slidev presentations optimized for `@alexop/slidev-theme-brand`.

## Required Frontmatter

Every presentation must start with:

```yaml
---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: [Generated Title]
layout: cover
---
```

## Workflow

1. **Analyze** - Identify content type (code-heavy, narrative, comparison)
2. **Structure** - Break into intro/body/conclusion with logical sections
3. **Layout** - Select appropriate layout for each slide
4. **Components** - Apply Callout, FolderTree, VClicks where beneficial
5. **Output** - Generate complete slides.md

## Content Analysis

### Code-Heavy Content (>30% code blocks)
- Use `default` layout predominantly
- Split code blocks at logical breaks (max 20 lines)
- Use `two-cols` for code + explanation
- Add line highlighting for step-by-step teaching

### Narrative Content
- Vary layouts for visual interest
- Use `section` slides between major topics
- Convert dense paragraphs to bullet lists (max 5-6 items)
- Apply VClicks for progressive reveals

## Layout Selection

| Content Pattern | Layout | Notes |
|----------------|--------|-------|
| Title/opening | `cover` | First slide always |
| New major topic | `section` | Centered, full-screen |
| Regular content | `default` | Bullets, paragraphs, code |
| Side-by-side | `two-cols` | Comparisons, code+notes |
| With header row | `two-cols-header` | Title spanning columns |
| Single quote | `quote` | Prominent quotation |
| Key statistic | `fact` | Single impactful number |
| Full image | `image` | Background visual |
| Image + text | `image-left` / `image-right` | Split layout |
| Closing | `section` or `end` | Thank you, questions |

For complete layout documentation: [references/layouts.md](references/layouts.md)

## Slide Decomposition Rules

- **One idea per slide** - Keep focused
- **Max 5-6 bullet points** - Split longer lists across slides
- **Max 20 lines of code** - Break at logical points
- **Use section breaks** - Insert `layout: section` for topic transitions
- **Always end properly** - Include closing slide (questions/thank you)

## Component Usage

### Callout - Highlight important information

```markdown
<Callout type="info">
Pro tip or helpful note
</Callout>

<Callout type="warn">
Warning or caution
</Callout>

<Callout type="error">
Critical error or danger
</Callout>
```

**When to use:**
- `info` → Tips, notes, helpful information
- `warn` → Warnings, deprecations, cautions
- `error` → Breaking changes, critical errors, dangers

### VClicks - Progressive reveal

```markdown
<VClicks>

- First point (revealed on click 1)
- Second point (revealed on click 2)
- Third point (revealed on click 3)

</VClicks>
```

**When to use:** Bullet lists, step-by-step content, feature lists

### FolderTree - Project structure

```markdown
<FolderTree
  root
  title="Project Structure"
  :structure="`
src
  components
    Button.vue
    Card.vue
  utils
    helpers.ts
  App.vue
`"
/>
```

**When to use:** Explaining project organization, file structures, directory layouts

### VuePlayground - Interactive demos

```markdown
<VuePlayground
  height="450px"
  url="https://play.vuejs.org/#eNp9k..."
/>
```

**When to use:** Interactive Vue code demonstrations (requires play.vuejs.org URL)

For complete component API: [references/components.md](references/components.md)

## Code Block Handling

### Syntax Highlighting

Use language identifiers: `vue`, `ts`, `js`, `html`, `css`, `bash`, `json`, `yaml`

```markdown
```ts
const example = "highlighted TypeScript"
```
```

### Line Highlighting

```markdown
```ts {2,4-6}
// Line 1
const highlighted = true  // Line 2 highlighted
// Line 3
const also = "highlighted" // Lines 4-6 highlighted
const these = "too"
const lines = "yes"
```
```

### Progressive Line Highlighting (Click-based)

Use `|` to separate highlight stages for code walkthroughs:

```markdown
```ts {1|3-4|all}
// Click 1: line 1 highlighted
function add(a: number, b: number) {
  // Click 2: lines 3-4 highlighted
  return a + b
}
// Click 3: all lines highlighted
```
```

**When to use:** Teaching code step-by-step, explaining complex functions

### Code in Two Columns

```markdown
---
layout: two-cols
---

::left::

## The Code

```vue
<script setup>
const count = ref(0)
</script>
```

::right::

## Explanation

- `ref(0)` creates reactive state
- Initial value is 0
- Updates trigger re-renders
```

## Slot Syntax

For two-column layouts, use named slots:

```markdown
---
layout: two-cols
---

::left::

Content for left column

::right::

Content for right column
```

Or for `two-cols-header`:

```markdown
---
layout: two-cols-header
---

# Header spans full width

::left::

Left column content

::right::

Right column content
```

## Output Format

Generate a complete `slides.md` file:

```markdown
---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: Presentation Title
layout: cover
---

# Presentation Title

Subtitle or author

---
layout: section
---

# First Section

---

# Content Slide

<VClicks>

- Point one
- Point two
- Point three

</VClicks>

---
layout: section
---

# Questions?
```

## Advanced Features

For technical presentations, consider:

- **Magic Move** - Animated code transitions between states
- **Mermaid diagrams** - Flowcharts, sequence diagrams from text
- **LaTeX math** - Inline `$E=mc^2$` or block `$$...$$`
- **Monaco Editor** - Interactive editable code blocks
- **Motion animations** - Element movement with `v-motion`

See [references/advanced.md](references/advanced.md) for syntax and examples.

## References

- [references/layouts.md](references/layouts.md) - Complete layout guide with all 19 layouts
- [references/components.md](references/components.md) - Full component API documentation
- [references/advanced.md](references/advanced.md) - Animations, diagrams, code features, LaTeX
- [references/examples.md](references/examples.md) - Complete input→output transformation examples
