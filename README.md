# Postman User Guide

A beginner‑friendly, step‑by‑step guide for new users who want to learn how to send API requests, manage environments, organize collections, and troubleshoot common errors in Postman.

---

## Overview

This guide walks through Postman's core features using four hands‑on tasks, followed by reference pages for quick lookup.

| Task | Topic |
|------|-------|
| Task 1 | Sending a Basic GET Request |
| Task 2 | Using Environment Variables |
| Task 3 | Grouping Requests with Collections |
| Task 4 | Managing Collections |

Additional reference pages: **Glossary** and **Troubleshooting**.

---

## How We Collaborated

Our team coordinated over Discord for day‑to‑day communication. We used Git and GitHub for version control — each member worked on a separate branch and submitted pull requests to merge into `main`.

---

## How We Built This Guide

Our guide draws on hands‑on experience using Postman for API testing during our coursework, supplemented by the official [Postman documentation](https://learning.postman.com/docs/). We reflected on the steps that were most confusing when we first learned the tool and used those as the basis for our task structure.

### Using MkDocs

We built this documentation site using [MkDocs](https://www.mkdocs.org/) with the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. Material provided a clean layout, built‑in search, light/dark mode toggle, and admonition blocks — all of which improved the readability of our step‑by‑step instructions.

### Using Markdown

All pages are written in Markdown. We used MkDocs' admonition syntax to visually distinguish different types of callouts:

- `!!! info` — Helpful tips, explanations, or additional context to support your understanding  
- `!!! warning` — Cautions to help prevent errors or unintended behavior

### Using a Style Guide

We loosely followed the [Google Developer Documentation Style Guide](https://developers.google.com/style) to keep our writing consistent. Key decisions include:

- UI element names are always wrapped in **bold quotes** (e.g., **"Send"**, **"Collections"**)
- Code, URLs, and variable names are written in `monospace`
- Every task page includes an **Overview** at the top and a **Conclusion** at the bottom
- Steps are written as numbered lists with one action per step

---

## Intended Audience

This guide is written for:

- Beginners who want to practice sending HTTP requests
- Developers who need a simple tool to test RESTful APIs
- Anyone using Postman for the first time who wants a structured, visual introduction

No programming experience is required.

---

## Conclusion

Writing this guide gave us the opportunity to practice clear, task‑oriented technical writing for a web audience. Structuring each page around a real workflow — from sending a first request to managing and sharing collections — helped us think carefully about how beginners approach a new tool.

We hope this guide serves as a useful starting point for anyone learning Postman.

---

Built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).