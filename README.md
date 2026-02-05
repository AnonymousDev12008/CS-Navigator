
# CS Navigator – Interactive Learning Map

CS Navigator is a single‑page **interactive map** of computer science topics and free learning resources.  
It’s meant for students and self‑taught learners who want to see “the whole CS world” at a glance and then dive into high‑quality materials for each topic.

---

## Live app

https://cs-navigator-xi.vercel.app

---

## Why this exists

When you’re starting out, CS can feel like a messy list of buzzwords: OS, networking, DevOps, ML, web, security… and a thousand random tutorials.  
This project tries to answer a simple question:

> “What are the main areas of CS, and what’s a good **first free resource** for each of them?”

There are already great self‑study roadmaps like OSSU and TeachYourselfCS. 
CS Navigator sits at a slightly higher level: a visual overview + curated links that you can actually click through and explore.

---

## What it does

- Shows a **horizontal tree map** of major CS domains:
  - Programming & CS fundamentals
  - Web development (frontend, backend, full‑stack)
  - Data science & AI
  - Systems, OS & networking
  - Cybersecurity & ethical hacking
  - DevOps & cloud
  - Mobile, game dev, UX/UI, HCI, databases, and more.
- Each leaf node links to at least one **free** resource (courses, docs, tutorials) so you can start learning immediately.
- A small footer explains how to use the map so new users aren’t confused on first load.
- Built as a **single static HTML file**, so it’s easy to host anywhere (GitHub Pages, Netlify, any static server).

---

## How to use the map

- **Expand a topic**  
  Click a **blue filled** node to expand or collapse its branch (e.g., “Web Development” → “Frontend Basics”).

- **Open a resource**  
  Click a **blue outlined** node (or its label) to open the external resource in a new tab.

- **Explore the space**  
  Scroll horizontally and vertically to move around the tree, and follow branches that match what you want to learn first (e.g., “Data Science & AI” → “Math for DS” → “Linear Algebra”).

- **Use it with your degree / self‑study plan**  
  Treat it as a **compass**: a quick way to discover what to learn next and which free resource to try, alongside your university courses or a longer roadmap like OSSU or TeachYourselfCS.

---

## How it was built

This project is intentionally minimal: no framework, no build step, no backend.

- **Data first**  
  - All topics and resources live in a single JavaScript object called `data`.  
  - Each node has a `name`, and some have a `url`; children form the tree structure.

- **Layout with D3.js**  
  - We use `d3.hierarchy` and `d3.tree()` to compute node positions for a tidy **left‑to‑right tree**.[web:262]  
  - Links are rendered as SVG paths with `d3.linkHorizontal`.

- **Interaction model**  
  - Internal nodes (branches) toggle between `children` and `_children` to expand/collapse on click.  
  - Leaf nodes with a `url` open that link in a new tab instead of toggling.

- **Styling & theming**  
  - Colors and spacing are handled with **CSS variables**.  
  - A small header explains what the map is; a footer explains how to use it.  
  - A tiny JavaScript snippet toggles `data-theme="dark" | "light"` on the `<html>` element and stores the preference in `localStorage` so the site remembers your theme choice.

The whole thing lives in `index.html`, which makes it easy to read through the source and tweak it for your own purposes.

---

## Running locally

You don’t need anything special to run this.

```bash
git clone https://github.com/YOUR-USERNAME/cs-navigator.git
cd cs-navigator
# Then open index.html in your browser (double-click or File → Open)

