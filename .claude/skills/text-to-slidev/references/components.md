# Components Reference

Complete API for components in `@alexop/slidev-addon-utils` and `@alexop/slidev-theme-brand`.

## Addon Components

### Callout

Alert box with type variants for highlighting important information.

```vue
<Callout type="info">
Content with **markdown** support
</Callout>
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `type` | `'info' \| 'warn' \| 'error'` | `'info'` | Visual style |

**Styles:**
- `info` - Blue border and background (tips, notes)
- `warn` - Yellow border and background (warnings, cautions)
- `error` - Red border and background (errors, dangers)

**Examples:**

```markdown
<Callout type="info">

### Pro Tip
Use `VClicks` for progressive reveals!

</Callout>

<Callout type="warn">
This API is deprecated in v2.0
</Callout>

<Callout type="error">
Breaking change: `oldMethod()` has been removed
</Callout>
```

### VuePlayground

Interactive Vue.js playground iframe.

```vue
<VuePlayground
  height="450px"
  url="https://play.vuejs.org/#eNp9k..."
/>
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `height` | `string` | `'600px'` | Container height |
| `width` | `string` | `'100%'` | Container width |
| `defaultTab` | `'script' \| 'template' \| 'style' \| 'preview'` | `'preview'` | Initial tab |
| `url` | `string` | - | Full Vue Playground URL (overrides defaultTab) |

**Usage:** Get URL from [play.vuejs.org](https://play.vuejs.org) Share button.

## Theme Components

### FolderTree

Interactive file/folder tree visualization.

```vue
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
package.json
`"
/>
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `root` | `boolean` | `false` | Enable root container with title |
| `title` | `string` | `'Project Files'` | Header title (requires `root`) |
| `structure` | `string` | - | Indentation-based tree structure |
| `nodes` | `TreeNode[]` | - | Alternative: array of node objects |
| `openAll` | `boolean` | `true` | Expand all folders initially |
| `openOnClicks` | `string[]` | `[]` | Paths to open on each click |

**Structure Syntax:**
- Indentation (2 spaces) defines hierarchy
- Trailing `/` forces folder type
- File types auto-detected by extension

**Click-based Reveal:**
```vue
<FolderTree
  root
  :openOnClicks="['/src/components', '/src/utils', '/src/App.vue']"
  :structure="`
src
  components
    Button.vue
  utils
    helpers.ts
  App.vue
`"
/>
```

### FeatureCard

Feature showcase card with hover effects.

```vue
<FeatureCard
  icon="i-carbon-code"
  title="Type Safety"
  description="Full TypeScript support"
/>
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `icon` | `string` | - | UnoCSS icon class |
| `title` | `string` | - | Card title |
| `description` | `string` | - | Card description |
| `bgColor` | `string` | - | Background color |
| `borderColor` | `string` | - | Border color |
| `titleColor` | `string` | - | Title text color |

**Grid Layout:**
```markdown
<div class="grid grid-cols-2 gap-4">

<FeatureCard icon="i-carbon-code" title="TypeScript" description="Full type safety" />
<FeatureCard icon="i-carbon-rocket" title="Fast" description="Optimized builds" />

</div>
```

### QuoteCard

Formatted quote with attribution.

```vue
<QuoteCard author="Steve Jobs">
Design is not just what it looks like. Design is how it works.
</QuoteCard>
```

**Props:**
| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `author` | `string` | Yes | Quote attribution |

## Slidev Built-in Components

### VClicks

Progressive reveal wrapper - children appear one per click.

```markdown
<VClicks>

- First item (click 1)
- Second item (click 2)
- Third item (click 3)

</VClicks>
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `depth` | `number` | `1` | Apply to nested list levels |
| `every` | `number` | `1` | Items to show per click |

**Note:** Blank lines around list items are required for proper markdown parsing.

### VClick

Single element reveal.

```markdown
<VClick>

This appears on click

</VClick>
```

**Advanced positioning:**
```html
<!-- Appear at specific click -->
<div v-click="3">Appears on click 3</div>

<!-- Appear with previous element -->
<div v-click>First</div>
<div v-after>Same time as First</div>

<!-- Hide after click -->
<div v-click.hide>Disappears on click</div>
```

### VSwitch

Switch between content on clicks:

```markdown
<VSwitch>
  <template #1>Content for click 1</template>
  <template #2>Content for click 2</template>
  <template #3>Content for click 3</template>
</VSwitch>
```

### Arrow

Draw arrows on slides.

```vue
<Arrow x1="100" y1="100" x2="200" y2="200" />
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `x1`, `y1` | `number` | - | Start position |
| `x2`, `y2` | `number` | - | End position |
| `width` | `number` | `2` | Line width |
| `color` | `string` | `'currentColor'` | Arrow color |

### Link

Navigate to specific slide.

```vue
<Link to="5">Go to slide 5</Link>
```

### SlidesTotal / SlideCurrentNo

Display slide numbers:

```markdown
Slide <SlideCurrentNo /> of <SlidesTotal />
```

### Toc (Table of Contents)

Auto-generate table of contents:

```markdown
<Toc />
```

**Props:**
| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `columns` | `number` | `1` | Number of columns |
| `maxDepth` | `number` | `Infinity` | Max heading depth |
| `minDepth` | `number` | `1` | Min heading depth |
| `mode` | `'all' \| 'onlyCurrentTree'` | `'all'` | Filter mode |

### Tweet

Embed a tweet:

```markdown
<Tweet id="1390115482657726468" />
```

### Youtube

Embed YouTube video:

```markdown
<Youtube id="dQw4w9WgXcQ" />
```

### SlidevVideo

Video with presentation controls:

```markdown
<SlidevVideo autoplay controls>
  <source src="/video.mp4" type="video/mp4" />
</SlidevVideo>
```

### Transform

Apply CSS transforms:

```markdown
<Transform scale="0.8" rotate="10">
  Transformed content
</Transform>
```

### LightOrDark

Show different content based on theme:

```markdown
<LightOrDark>
  <template #light>Light mode content</template>
  <template #dark>Dark mode content</template>
</LightOrDark>
```

## Component Selection Guide

| Need | Component |
|------|-----------|
| Highlight tip/warning | `Callout` |
| Show file structure | `FolderTree` |
| Interactive Vue demo | `VuePlayground` |
| Feature showcase | `FeatureCard` (in grid) |
| Quote with author | `QuoteCard` |
| Progressive list | `VClicks` |
| Single reveal | `VClick` |
| Swap content on clicks | `VSwitch` |
| Point to elements | `Arrow` |
| Table of contents | `Toc` |
| Embed YouTube | `Youtube` |
| Embed tweet | `Tweet` |
| Video playback | `SlidevVideo` |
| Scale/rotate content | `Transform` |
| Theme-aware content | `LightOrDark` |
| Slide navigation link | `Link` |
| Show slide numbers | `SlideCurrentNo` / `SlidesTotal` |
