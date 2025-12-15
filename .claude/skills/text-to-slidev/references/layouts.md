# Slidev Layouts Reference

Complete guide to all 19 layouts in `@alexop/slidev-theme-brand`.

## Full-Screen Layouts

### cover
Title slide with optional background image.

```yaml
---
layout: cover
background: https://images.unsplash.com/photo-xxx
---

# Presentation Title

Subtitle or author
```

Props: `background` (optional URL)

### section
Centered section divider for major topic breaks.

```yaml
---
layout: section
---

# New Section Title
```

### statement
Full-screen bold statement.

```yaml
---
layout: statement
---

# Key Takeaway Message
```

### fact
Prominent display for statistics or key facts.

```yaml
---
layout: fact
---

# 90%

of developers prefer TypeScript
```

### full
Maximum content area, no padding.

```yaml
---
layout: full
---

[Full-width content here]
```

### none
No styling - raw layout for custom HTML/components.

### intro
Centered introduction layout.

```yaml
---
layout: intro
---

# Introduction

Welcome message
```

### end
Closing slide with optional background.

```yaml
---
layout: end
---

# Thank You!
```

## Padded Content Layouts

### default
Standard slide with consistent padding. Use for most content.

```yaml
---

# Slide Title

- Bullet point
- Another point

```

### center
Content centered vertically and horizontally.

```yaml
---
layout: center
---

# Centered Content

This appears in the middle of the slide
```

### quote
Prominent quotation display.

```yaml
---
layout: quote
---

"Design is not just what it looks like. Design is how it works."

— Steve Jobs
```

## Two-Column Layouts

### two-cols
Equal two-column split.

```yaml
---
layout: two-cols
---

::left::

## Left Column

Content here

::right::

## Right Column

Content here
```

Grid: `grid-cols-2 gap-16`

### two-cols-header
Header row spanning full width, then two columns below.

```yaml
---
layout: two-cols-header
---

# Header Spans Full Width

::left::

Left column content

::right::

Right column content
```

## Image Layouts

### image
Full-slide background image.

```yaml
---
layout: image
image: /path/to/image.png
backgroundSize: cover
---
```

Props:
- `image` (required) - Image path or URL
- `backgroundSize` - CSS background-size (default: `cover`)

### image-left
Image on left, content on right.

```yaml
---
layout: image-left
image: /path/to/image.png
---

## Content Title

Text appears on the right side
```

### image-right
Content on left, image on right.

```yaml
---
layout: image-right
image: /path/to/image.png
---

## Content Title

Text appears on the left side
```

## Embed Layouts

### iframe
Full-screen embedded webpage.

```yaml
---
layout: iframe
url: https://example.com
---
```

Props: `url` (required)

### iframe-left
Iframe on left, content on right.

```yaml
---
layout: iframe-left
url: https://example.com
---

## Explanation

Content about the embedded page
```

### iframe-right
Content on left, iframe on right.

```yaml
---
layout: iframe-right
url: https://example.com
---

## Explanation

Content about the embedded page
```

## Slot Syntax Reference

### Named Slots (Markdown style)

```markdown
::left::
Left content

::right::
Right content

::bottom::
Bottom content (for two-cols-header)
```

### Vue Template Syntax (Alternative)

```vue
<template v-slot:default>
  Left/default content
</template>

<template v-slot:right>
  Right content
</template>
```

## Layout Selection Quick Reference

| Use Case | Layout |
|----------|--------|
| Opening slide | `cover` |
| Section break | `section` |
| Regular content | `default` |
| Comparison | `two-cols` |
| Comparison with title | `two-cols-header` |
| Quote | `quote` |
| Statistic | `fact` |
| Bold statement | `statement` |
| Image focus | `image` |
| Image + text | `image-left` or `image-right` |
| Web demo | `iframe` |
| Demo + explanation | `iframe-left` or `iframe-right` |
| Closing | `section` or `end` |
