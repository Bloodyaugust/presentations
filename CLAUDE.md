# Claude Instructions — Presentations Project

This repo contains RevealJS presentations. Each deck lives in its own subfolder at the project root.

## Project Structure

```
presentations/
├── README.md
├── CLAUDE.md
├── .claude/skills/create-deck/SKILL.md
├── my-first-talk/
│   └── index.html
└── another-deck/
    └── index.html
```

Each deck folder contains at minimum an `index.html`. Additional assets (images, custom CSS) go in the same folder.

## RevealJS CDN Base

```
https://cdn.jsdelivr.net/npm/reveal.js@5
```

## Standard HTML Template

Use this template when creating a new deck:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>PRESENTATION_TITLE</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reset.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/THEME.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/highlight/monokai.css">
</head>
<body>
  <div class="reveal">
    <div class="slides">

      <section>
        <h1>PRESENTATION_TITLE</h1>
        <p>SUBTITLE</p>
      </section>

      <!-- Add slides here -->

    </div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/notes/notes.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/markdown/markdown.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/highlight/highlight.js"></script>
  <script>
    Reveal.initialize({
      hash: true,
      plugins: [ RevealMarkdown, RevealHighlight, RevealNotes ]
    });
  </script>
</body>
</html>
```

## Slide Patterns

### Plain HTML slide
```html
<section>
  <h2>Slide Title</h2>
  <ul>
    <li>Point one</li>
    <li>Point two</li>
  </ul>
</section>
```

### Markdown slide
```html
<section data-markdown>
  <textarea data-template>
## Slide Title

- Point one
- Point two
  </textarea>
</section>
```

### Vertical slides (sub-sections)
```html
<section>
  <section><h2>Chapter One</h2></section>
  <section><h2>Deep Dive</h2></section>
</section>
```

### Code with syntax highlighting
```html
<section>
  <pre><code data-trim data-noescape class="language-javascript">
function hello() {
  console.log("Hello, world!");
}
  </code></pre>
</section>
```

### Speaker notes
```html
<section>
  <h2>My Slide</h2>
  <aside class="notes">
    These are speaker notes. Press S to view them.
  </aside>
</section>
```

### Slide with background
```html
<section data-background-color="#1a1a2e">
  <h2>Dark Background</h2>
</section>

<section data-background-image="image.jpg">
  <h2>Image Background</h2>
</section>
```

## Available Themes

`black` · `white` · `league` · `beige` · `sky` · `night` · `serif` · `simple` · `solarized` · `moon` · `dracula`

## Naming Conventions

- Deck folder names: `kebab-case` (e.g., `intro-to-react`, `q3-roadmap`)
- One `index.html` per deck (self-contained, loads from CDN)
- Additional assets alongside `index.html` (e.g., `images/`, `custom.css`)

## When Creating a Deck

1. Use `AskUserQuestion` to interview the user (see `/create-deck` skill)
2. Create `<deck-name>/index.html` from the standard template above
3. Replace `PRESENTATION_TITLE`, `SUBTITLE`, and `THEME` placeholders
4. Populate slides based on the user's outline
5. Confirm the file was created and tell the user to open it in a browser
