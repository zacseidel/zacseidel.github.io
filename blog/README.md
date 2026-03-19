# Zac S. — Personal Blog

A clean, minimal Jekyll blog with three photo-inspired color themes, hosted free on GitHub Pages.

---

## Quick Start

### First-time setup

1. Create a new repo on GitHub called `zacseidel.github.io` (for a root-level site) or `blog` (for `zacseidel.github.io/blog/`)
2. Untar this archive and push:

```bash
cd blog
git init
git add .
git commit -m "Initial blog setup"
git branch -M main
git remote add origin git@github.com:zacseidel/blog.git
git push -u origin main
```

3. Go to **Settings → Pages → Source: Deploy from a branch → main / root → Save**
4. Your site will be live within a couple minutes

> If using the repo name `zacseidel.github.io`, leave `baseurl: ""` in `_config.yml` (already set). If using a different repo name like `blog`, set `baseurl: "/blog"`.

### Local preview (optional)

```bash
gem install bundler
bundle install
bundle exec jekyll serve
# Open http://localhost:4000
```

---

## Adding Content

All content lives in two folders: `_essays/` and `_projects/`. Each file is a Markdown file with a front matter block at the top (the stuff between `---` lines) followed by your writing.

Push to `main` and GitHub rebuilds the site automatically — usually within 1-2 minutes.

### Adding a new essay

Create a new file in `_essays/`. The filename becomes the URL slug, so keep it lowercase with hyphens:

**`_essays/my-essay-title.md`**

```markdown
---
title: "My Essay Title"
date: 2026-03-18
category: "Ideas"
reading_time: 6
---

Your essay goes here. Write in plain Markdown.

You can use **bold**, *italics*, [links](https://example.com), and all the usual Markdown formatting.

## Subheadings work

So do block quotes:

> This is a block quote.

And code blocks, images, lists — everything you'd expect.
```

**Front matter fields for essays:**

| Field          | Required? | Description                                        |
|----------------|-----------|----------------------------------------------------|
| `title`        | Yes       | The essay title                                    |
| `date`         | Yes       | Publication date (`YYYY-MM-DD`)                    |
| `category`     | No        | Shown as a label — use whatever you want           |
| `reading_time` | No        | Estimated minutes to read                          |

**Categories you've used so far:** Happiness, Books, Parenting, Ideas — but you can use any string.

### Adding a new project

Create a new file in `_projects/`. Same idea — filename becomes the URL slug:

**`_projects/my-project.md`**

```markdown
---
title: "My Project Name"
description: "A one-line summary that shows on the card."
status: "Active"
tech: ["HTML", "CSS", "JS"]
url_live: "https://zacseidel.github.io/my-project/"
url_repo: "https://github.com/zacseidel/my-project"
order: 5
---

A longer write-up about the project goes here. What it does, why you built it, how it works, what you learned — whatever feels right.

## How it works

Technical details, screenshots, etc.
```

**Front matter fields for projects:**

| Field         | Required? | Description                                               |
|---------------|-----------|-----------------------------------------------------------|
| `title`       | Yes       | Project name                                              |
| `description` | Yes       | One-line summary (shows on the card on the Projects page) |
| `status`      | No        | e.g. "Active", "Complete", "Experiment", "Archived"       |
| `tech`        | No        | List of technologies (shown as tags)                      |
| `url_live`    | No        | Link to live demo                                         |
| `url_repo`    | No        | Link to source code                                       |
| `order`       | No        | Controls sort order on the Projects page (lower = first)  |

---

## Copy-Paste Templates

### Essay template

Copy this into a new file in `_essays/`:

```markdown
---
title: ""
date: 2026-01-01
category: ""
reading_time: 5
---

Write here.
```

### Project template

Copy this into a new file in `_projects/`:

```markdown
---
title: ""
description: ""
status: "Active"
tech: []
url_live: ""
url_repo: ""
order: 10
---

Write here.
```

---

## Editing Existing Content

### On GitHub.com

1. Navigate to the file (e.g. `_essays/my-essay.md`)
2. Click the pencil icon (edit)
3. Make your changes
4. Click **Commit changes** at the bottom

### In VS Code locally

1. Edit the file
2. `git add . && git commit -m "Update essay" && git push`

---

## Color Themes

The site ships with three themes inspired by personal photos:

| Theme        | Accent  | Vibe                                      |
|--------------|---------|-------------------------------------------|
| **Canopy**       | `#3a5a2a` (forest green)  | Lush, earthy, grounded        |
| **Shoreline**    | `#e84825` (sunset coral)  | Vivid, warm, ocean energy     |
| **Golden Hour**  | `#8b5e2a` (warm amber)    | Rich, inviting, golden light  |

Visitors can switch themes using the three colored dots in the top-right nav. Their choice is saved in their browser.

### Changing the default theme

The default is Canopy. To change it, edit `_layouts/default.html` and find this line in the `<script>` near the top:

```javascript
var t = localStorage.getItem('theme') || 'canopy';
```

Change `'canopy'` to `'shoreline'` or `'golden-hour'`.

### Editing theme colors

All theme colors live at the top of `assets/css/style.css` as CSS variables. Each theme block looks like:

```css
[data-theme="shoreline"] {
  --color-bg: #faf8f5;
  --color-surface: #ffffff;
  --color-text: #2a2430;
  --color-text-secondary: #7a7280;
  --color-accent: #e84825;
  --color-accent-light: #fde8e1;
  --color-border: #e2ddd6;
  --color-border-light: #f0ece6;
}
```

Change any hex value and push — the whole site updates.

---

## Site Structure

```
├── _config.yml            # Site title, URL, collections config
├── _layouts/              # Page templates
│   ├── default.html       #   Base layout (header + footer + theme JS)
│   ├── essay.html         #   Essay page (title, date, category, body)
│   ├── project.html       #   Project page (title, tags, links, body)
│   ├── page.html          #   Generic page (About, Now)
│   └── post.html          #   Blog post (if needed)
├── _includes/
│   ├── header.html        #   Nav bar + theme switcher dots
│   └── footer.html        #   Footer
├── _essays/               #   ← Your essays go here
├── _projects/             #   ← Your projects go here
├── assets/css/style.css   #   All styles + theme definitions
├── index.html             #   Homepage
├── projects/index.html    #   Projects listing page
├── essays/index.html      #   Essays listing page
├── about/index.md         #   About page
└── now/index.md           #   Now page
```

### Pages you'll want to update

- **`about/index.md`** — Your bio. Written in Markdown.
- **`now/index.md`** — What you're working on right now. Update whenever things change.
- **`index.html`** — Homepage intro text (the "Hey, I'm Zac" section). Edit the HTML directly.

---

## Markdown Cheat Sheet

Since you'll be writing in Markdown, here's a quick reference:

```markdown
# Heading 1
## Heading 2
### Heading 3

**bold** and *italic*

[Link text](https://url.com)

![Alt text](image-url.jpg)

> Block quote

- Bullet list
- Another item

1. Numbered list
2. Second item

`inline code`

---   (horizontal rule)
```

---

## Troubleshooting

**Site not updating after push?** GitHub Pages can take 1-3 minutes. Check the build status at Settings → Pages, or the Actions tab.

**Broken layout?** Usually a front matter issue — make sure the `---` blocks are correct YAML. Common mistakes: missing quotes around titles with colons, or incorrect indentation in the `tech` list.

**Want to add an image to a post?** Drop the image in `assets/images/`, then reference it:

```markdown
![Description](/assets/images/my-photo.jpg)
```
