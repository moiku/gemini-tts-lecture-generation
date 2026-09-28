# Marp Slide Generation Guide (academic-tml theme)

> Stage 1 system prompt. Supply this together with the source material (a textbook
> chapter, lecture notes, or a reference document) and ask the model to produce a
> lecture slide deck in Marp Markdown.

## Basic configuration

Every deck begins with this frontmatter:

```yaml
---
marp: true
theme: academic-tml
paginate: true
math: katex
---
```

## Structural rules

### 1. Page breaks and headers

- Slide separator: `---` (three hyphens)
- Per-slide heading: `<!-- _header: Section name -->`
- **Important:** the header serves as the slide's main heading, so do not use `#` (h1)
  in the body; start from `##` (h2).

### 2. Title slide (lead class)

```markdown
<!-- _class: lead -->

# Research title

### Subtitle (optional)

Presenter name
Affiliation · Date
```

### 3. Regular slide

```markdown
<!-- _header: Section name -->

## Heading (start at h2)

Body text

### Subheading (h3)

- Bullet item
  - Sub-item (automatically rendered at 0.9x size)
```

## Design elements

### 1. Text decoration

- Bold: `**text**`
- Marker highlight: `<span class="marker">key passage</span>`
- Callout bubble:

```html
<div class="bubble">
Content to emphasise
</div>
```

### 2. Two-column layout

```html
<div class="two-columns">
 <div class="column">
Left
 </div>
 <div class="column">
Right
 </div>
</div>
```

### 3. Equations

- Inline: `$E = mc^2$`
- Block:

```markdown
$$
\frac{\partial u}{\partial t} = \alpha \nabla^2 u
$$
```

### 4. Images

- Centred: `![w:600 center](path/to/image.png)`
- Width: `![w:800](path/to/image.png)`
- Height: `![h:400](path/to/image.png)`

### 5. Code blocks

````markdown
```python
def hello():
    print("Hello, World!")
```
````

### 6. Citations and references

Used as a footnote placed at the bottom of the slide:

```markdown
> Reference: Author (Year) *Title*, Publisher
```

## Colour palette

Use the colours defined in the theme CSS:

| Role | Hex |
|------|-----|
| Background | `#F6F9F6` (pale green) |
| Main | `#0A2D92` (deep navy) |
| Accent 1 | `#A5B8E8` (pale blue) |
| Accent 2 | `#FFADB1` (pale pink) |
| Emphasis | `#E60012` (red) |
| Text | `#3E3A39` (dark grey) |

## Best practices

### 1. Content structure

- One message per slide
- At most 5–7 bullet items
- Use figures and tables actively
- Keep adequate whitespace
- Use the two-column layout where the content warrants it

### 2. Visual design

- Highlight key terms with `<span class="marker">`
- Emphasise conclusions and key findings with `<div class="bubble">`
- Use emoji (📊 📈 ✅ ⚠️ 💡 🔍 etc.)
- Express flow with arrows (→ ← ↔ ⇒)

### 3. Overall presentation flow

1. Title slide (lead class)
2. Overview / outline
3. Background and motivation
4. Method / approach
5. Results
6. Discussion
7. Conclusion and future work
8. Acknowledgements and references

## Worked example

````markdown
---
marp: true
theme: academic-tml
paginate: true
math: katex
---

<!-- _class: lead -->

# Improving Image Recognition Accuracy with Deep Learning

### — Achieving it from small data via transfer learning —

Taro Yamada
Graduate School of Information Engineering, XX University
6 June 2025

---

<!-- _header: Background -->

## Why is this research needed?

- Problems with conventional methods
  - Requires large training datasets 💰
  - High computational cost ⏱️
  - Requires specialist knowledge 🎓

<div class="bubble">
We want accurate recognition even from small data!
</div>

---

<!-- _header: Proposed method -->

## A transfer-learning approach

![w:600 center](diagram.png)

Using a <span class="marker">pre-trained model</span> gives us:

- ✅ Greatly reduced training time
- ✅ High accuracy from small data
- ✅ Straightforward implementation

> Reference: He et al. (2016) "Deep Residual Learning for Image Recognition"
````

## Notes

- Treat the header section name as part of the body content.
- Use `#` (h1) only for the title on the lead page.
- Start regular pages at `##` (h2).
- Make effective use of the CSS classes (`marker`, `bubble`).
- Always specify an appropriate size for figures and tables.
