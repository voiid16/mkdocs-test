# Content Tabs

Content tabs let you group related content under selectable labels — ideal for showing
the same instructions in multiple languages, or comparing alternative approaches side by side.

## Configuration

```yaml
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true # required for the modern tab style
  - pymdownx.superfences # needed for code blocks inside tabs
```

---

## Basic Tabs

Wrap tab content with `=== "Label"` blocks. Indentation must be consistent (4 spaces).

```markdown
=== "Python"
`python
    import httpx
    response = httpx.get("https://api.example.com/v1/users")
    `

=== "JavaScript"
`js
    const res = await fetch("https://api.example.com/v1/users");
    const data = await res.json();
    `

=== "cURL"
`bash
    curl https://api.example.com/v1/users \
      -H "Authorization: Bearer $TOKEN"
    `
```

**Result:**

=== "Python"
`python
    import httpx
    response = httpx.get("https://api.example.com/v1/users")
    `

=== "JavaScript"
`js
    const res = await fetch("https://api.example.com/v1/users");
    const data = await res.json();
    `

=== "cURL"
`bash
    curl https://api.example.com/v1/users \
      -H "Authorization: Bearer $TOKEN"
    `

---

## Tabs with Text and Lists

Tab content isn't limited to code — you can include any Markdown inside a tab.

```markdown
=== ":material-apple: macOS"
Install via Homebrew:

    1. Open Terminal
    2. Run `brew install mkdocs`
    3. Verify with `mkdocs --version`

=== ":material-linux: Linux"
Install via pip:

    1. Ensure Python 3.8+ is installed
    2. Run `pip install mkdocs-material`
    3. Verify with `mkdocs --version`

=== ":material-microsoft-windows: Windows"
Install via pip in PowerShell:

    1. Ensure Python 3.8+ is installed
    2. Run `pip install mkdocs-material`
    3. Verify with `mkdocs --version`
```

**Result:**

=== ":material-apple: macOS"
Install via Homebrew:

    1. Open Terminal
    2. Run `brew install mkdocs`
    3. Verify with `mkdocs --version`

=== ":material-linux: Linux"
Install via pip:

    1. Ensure Python 3.8+ is installed
    2. Run `pip install mkdocs-material`
    3. Verify with `mkdocs --version`

=== ":material-microsoft-windows: Windows"
Install via pip in PowerShell:

    1. Ensure Python 3.8+ is installed
    2. Run `pip install mkdocs-material`
    3. Verify with `mkdocs --version`

---

## Linked Tabs

By default, all tab groups on a page switch independently. To sync tabs with the same
label across the whole page, add `slugify` to your config:

```yaml
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
      slugify: !!python/object/apply:pymdownx.slugs.slugify
        kwds:
          case: lower
```

When a reader selects "Python" in one group, every other tab group on the page
that has a "Python" tab will switch to it automatically.
