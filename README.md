# BlogMate

A human-in-the-loop blogging assistant that turns a rough topic into a researched, SEO-aware article and a ready-to-open HTML page.

> **Status:** Working prototype / content workspace. BlogMate is an agent-assisted writing workflow, not a hosted application. It has no backend, database, CMS integration, or automated publishing pipeline. The HTML page is authored by hand (by the agent) from the Markdown source.

---

## 1. Project Overview and Problem Statement

### Overview

BlogMate is a blogging assistant agent that collaborates with a human writer inside a Switch room. It helps with:

- Generating and choosing article angles
- Researching a topic and collecting verifiable sources
- Building outlines and SEO packages
- Drafting and revising the article
- Converting the finished Markdown into a responsive, self-contained HTML page
- Flagging claims that still need verification

The current repository contains one completed article:

**"How AI Is Changing College Life in India — and Why Tier-2 Students Have the Most to Gain"**

It exists in two forms:

| File | Purpose |
|---|---|
| `blogmate-output/ai-college-students-india.md` | Source article with YAML front matter, FAQs, sources and verification flags |
| `blogmate-output/index.html` | Self-contained, responsive webpage version with TOC, SEO metadata and structured data |

### Problem Statement

Individual bloggers face a repetitive, multi-step workload:

1. Finding a topic and a differentiated angle.
2. Researching facts and keeping track of sources.
3. Structuring the article for readability and search.
4. Writing, revising and checking consistency.
5. Converting the draft into a presentable web page.
6. Avoiding unsupported claims, especially when using AI assistance.

Most AI writing tools optimise for speed and produce generic, source-light content. BlogMate takes the opposite approach: it keeps a human in the loop, links claims to sources, labels illustrative examples, and explicitly marks anything that still needs verification.

---

## 2. Why BlogMate Is Useful for Individual Bloggers

- **One workspace, end to end.** Topic discussion, research, draft, revision, SEO metadata and HTML output live in the same conversation and the same folder.
- **Research with receipts.** Factual claims link directly to their sources, and the README-style verification section makes open questions visible instead of hiding them.
- **Human control at the decision points.** The writer approves the angle, the outline and the revisions. BlogMate does not publish on its own.
- **SEO without guesswork.** Titles, meta description, keywords, slug and structured data are produced alongside the article, not bolted on later.
- **Readable output.** The HTML uses semantic sections, a working table of contents, responsive CSS, accessible focus states and print styles.
- **No lock-in.** The deliverables are plain Markdown and plain HTML/CSS/JS. Nothing requires a proprietary platform to open or edit.
- **Honest about limits.** The workflow distinguishes measured employability from placement rates, global data from India-specific data, and leading-institution samples from the broader system.

---

## 3. Technologies and Tools Used

### Content and output

| Technology | Role |
|---|---|
| **Markdown** | Source format for the article, with YAML front matter for SEO fields |
| **HTML5** | Semantic page structure: `header`, `main`, `nav`, `article`, `section`, `aside`, `footer` |
| **CSS3** | Custom properties, Grid, Flexbox, media queries, print styles, `prefers-reduced-motion` |
| **Vanilla JavaScript** | Reading-progress bar and active-section highlighting in the TOC. No frameworks, no dependencies |
| **JSON-LD** | `Article` and `FAQPage` structured data embedded in `index.html` |

### Collaboration and research

| Tool | Role |
|---|---|
| **Switch** | Room-based collaboration layer between the workspace owner and the BlogMate agent |
| **BlogMate agent** | The writing/research agent that performs the work inside the room |
| **Web search and web fetch** | Used to locate and read primary and secondary sources |
| **Local file tools** | Used to write and verify the Markdown and HTML files in the agent workspace |

### Explicitly **not** used

- No frontend framework (React, Vue, etc.)
- No CSS framework (Tailwind, Bootstrap, etc.)
- No static-site generator (Hugo, Jekyll, Eleventy, etc.)
- No Node.js/npm build step
- No backend, database, API, or authentication layer
- No CMS or publishing integration
- No analytics, testing framework, or CI/CD pipeline
- No automated Markdown-to-HTML converter (the HTML was authored manually)
- No Git repository initialised in this folder

---

## 4. How Switch Enables Human-Agent Collaboration

Switch provides a shared room where the writer and BlogMate exchange messages and files. In practice, this project used Switch as follows:

1. **The owner addresses the agent in a room.** Messages arrive with the room, sender and message context, so the agent knows who is asking and where to reply.
2. **The agent replies in the same room.** Updates, drafts, questions and final paths are posted back to the room rather than hidden in a private session.
3. **Work is discussed before it is produced.** BlogMate proposed three angles and an outline; the owner chose one and gave revision notes.
4. **Revisions are explicit.** The owner supplied six improvement points; the agent applied them and reported what changed.
5. **The agent works on the owner's machine.** Files are written to the agent's workspace and the exact path is reported back for the owner to open.
6. **The human stays in control.** Nothing is published. The owner reviews the Markdown and HTML locally.

Switch handles the conversation and message delivery. It does **not** host the blog, publish the page, or provide analytics in this project.

---

## 5. Complete Workflow: Topic Submission to HTML Generation

```text
Owner posts a topic in the Switch room
        |
        v
BlogMate clarifies scope and proposes angles
        |
        v
Owner selects an angle  (e.g. "Beyond the Metro" — tier-2/tier-3 students)
        |
        v
BlogMate researches the topic and collects sources
        |
        v
BlogMate posts an outline + SEO package for approval
        |
        v
Owner reviews and requests revisions
        |
        v
BlogMate drafts the article with inline source links and verification flags
        |
        v
BlogMate saves the Markdown to blogmate-output/
        |
        v
BlogMate authors index.html from the Markdown
  (semantic sections, anchors, responsive CSS, SEO meta, JSON-LD)
        |
        v
BlogMate verifies the output
  (file exists, byte size, tag balance, anchor targets, encoding)
        |
        v
BlogMate reports the exact file path in the room
        |
        v
Owner opens index.html in a browser and reviews it
```

### Step-by-step

1. **Topic submission.** The owner describes the subject in the Switch room.
2. **Angle selection.** BlogMate proposes multiple angles. The chosen angle for this article was *"Beyond the Metro: How AI Is Levelling the Field for Tier-2 and Tier-3 Students."*
3. **Research.** Sources were gathered for enrolment data, institutional AI adoption, graduate employability, internet access, language technology, public learning platforms and the IndiaAI Mission. Figures that could be misread were annotated.
4. **Outline and SEO.** The structure, primary keyword, secondary keywords, meta title, meta description and slug were agreed before drafting.
5. **Drafting.** The article was written with inline links, labelled everyday examples and explicit verification flags.
6. **Revision.** The owner's feedback was applied: a stronger opening, more Indian college examples, less repetition, a conversational-but-professional tone, preserved source links, a memorable takeaway and no fabricated data.
7. **Markdown output.** The final article, FAQs, 13 sources and verification flags were saved to `blogmate-output/ai-college-students-india.md`.
8. **HTML output.** `blogmate-output/index.html` was authored from the Markdown with:
   - 12 anchored sections and a working table of contents
   - Responsive layout (sticky sidebar on desktop, stacked on mobile)
   - Example and caveat callouts
   - Highlighted verification flags
   - SEO metadata, Open Graph, Twitter card and JSON-LD
   - Accessibility features (skip link, focus styles, reduced-motion support)
   - Print styles
9. **Verification.** The agent checked the file on disk and validated that every TOC anchor resolves, HTML tags are balanced and no encoding corruption is present.
10. **Handoff.** The exact path was posted back to the room.

---

## 6. Project Folder Structure

```text
blogmate/
├── README.md                          <- this file
└── blogmate-output/
    ├── ai-college-students-india.md   <- Markdown source (article + FAQs + sources + flags)
    └── index.html                     <- responsive HTML webpage
```

Notes:

- `blogmate-output/` is the only generated-content folder.
- There are no build, config, dependency or source-code folders.
- Screenshots are not yet captured; see Section 8.

---

## 7. Setup and Usage Instructions

### Requirements

- A modern web browser (Chrome, Edge, Firefox or Safari)
- A text editor for editing Markdown/HTML (optional)
- No installation, package manager or build step

### View the article

1. Navigate to `blogmate-output/`.
2. Open `index.html` in a browser.

On Windows PowerShell:

```powershell
Start-Process ".\blogmate-output\index.html"
```

Or double-click the file in File Explorer.

### Edit the Markdown source

Open `blogmate-output/ai-college-students-india.md` in any Markdown editor. The YAML front matter contains:

```yaml
title:
meta_title:
meta_description:
primary_keyword:
secondary_keywords:
url_slug:
```

### Edit the HTML page

Open `blogmate-output/index.html` in a text editor. All styling and scripting are inline, so there are no external assets to manage. If you add or rename a section:

1. Give the `<section>` a unique `id`.
2. Add a matching `<a href="#your-id">` entry in the table of contents.
3. Re-check that every anchor resolves.

### Verify the files exist

```powershell
Get-Item -LiteralPath ".\blogmate-output\ai-college-students-india.md", ".\blogmate-output\index.html" |
  Select-Object FullName, Length, LastWriteTime
```

### Publish

There is no built-in publishing step. To publish, upload `index.html` (and optionally the Markdown) to any static host or paste the content into your CMS manually.

---

## 8. Screenshots

Placeholders only — screenshots have **not** been captured yet.

### Desktop view

```text
![BlogMate article — desktop view](docs/screenshots/desktop.png)
```

*Suggested capture: full page at 1440px width, showing the sticky TOC and article.*

### Mobile view

```text
![BlogMate article — mobile view](docs/screenshots/mobile.png)
```

*Suggested capture: 390px width, showing the stacked layout and TOC.*

### Table of contents and callouts

```text
![BlogMate TOC and example callout](docs/screenshots/toc-callouts.png)
```

*Suggested capture: the sidebar with an active section plus one example callout.*

### Switch room collaboration

```text
![Switch room conversation](docs/screenshots/switch-room.png)
```

*Suggested capture: the room thread showing the topic, revisions and final file path. Redact any private information before publishing.*

---

## 9. Future Enhancements

These are ideas only; none are implemented.

- **Automated Markdown → HTML pipeline.** Replace manual authoring with a documented converter and a reusable template.
- **Reusable article template.** Extract the current design into a template so new posts do not start from a copied file.
- **Multi-article index.** Generate a homepage listing all published articles.
- **Automated checks.** Add scripts for broken links, missing anchors, duplicate IDs, meta-length limits and HTML validation.
- **Image workflow.** Support diagrams and screenshots with responsive `srcset` and alt-text checks.
- **Dark mode.** Add a theme toggle that respects `prefers-color-scheme`.
- **Accessibility audit.** Run automated and manual checks (contrast, landmarks, keyboard order).
- **Fact-verification log.** Turn the inline flags into a structured checklist that must be cleared before publishing.
- **Deployment options.** Document one-click deployment to a static host.
- **Localisation.** Produce Hindi or other Indian-language versions of the same article.
- **Analytics.** Optional, privacy-friendly page-view tracking after publishing.
- **Version control.** Initialise Git and track article revisions.

---

## Accuracy Notes

This README describes only what exists in this folder today:

- Two output files, both plain text formats.
- A manual, agent-assisted workflow.
- No application code, server, database, tests, or integrations.

Article-level caveats are preserved inside the article itself and in its **"Still flagged for verification"** section. In particular:

- The EY-Parthenon–FICCI survey covers **30 leading institutions**, not tier-2/tier-3 colleges.
- The **86% student AI usage** figure is **global**, not India-specific.
- Mercer figures measure **assessed employability**, not placement rates.
