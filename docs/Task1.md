# Code Blocks

Material for MkDocs renders beautiful, feature-rich code blocks out of the box.
With a few extensions enabled you get syntax highlighting, line numbers, annotations, and copy buttons.

## Configuration

```yaml
theme:
  features:
    - content.code.copy # adds a copy button to every block
    - content.code.annotate # enables inline annotations

markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.superfences
```

---

## Basic Fenced Code Block

Wrap code in triple backticks and add a language identifier for syntax highlighting.
[Pygments](https://pygments.org/languages/) supports 500+ languages.

````markdown
```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("world"))
```
````

**Result:**

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("world"))
```

---

## Adding a Title

Use the `title` attribute to label your code block — useful for showing a filename.

````markdown
```yaml title="mkdocs.yml"
site_name: Su and Ivy's docs
theme:
  name: material
```
````

**Result:**

```yaml title="mkdocs.yml"
site_name: Su and Ivy's docs
theme:
  name: material
```

---

## Line Numbers

Add `linenums="1"` to start numbering from line 1 (or any other number).

````markdown
```python linenums="1"
import httpx

response = httpx.get("https://api.example.com/v1/users")
print(response.json())
```
````

**Result:**

```python linenums="1"
import httpx

response = httpx.get("https://api.example.com/v1/users")
print(response.json())
```

---

## Highlighting Lines

Use `hl_lines` to draw attention to specific lines.

````markdown
```python linenums="1" hl_lines="2 3"
def connect(host: str, port: int):
    if port not in (80, 443):
        raise ValueError(f"Unsupported port: {port}")
    return f"Connected to {host}:{port}"
```
````

**Result:**

```python linenums="1" hl_lines="2 3"
def connect(host: str, port: int):
    if port not in (80, 443):
        raise ValueError(f"Unsupported port: {port}")
    return f"Connected to {host}:{port}"
```

---

## Inline Code Highlighting

With `pymdownx.inlinehilite` you can highlight inline snippets:

```markdown
Use `#!python print("hello")` to output text, or `#!bash export KEY=value` to set env vars.
```

**Result:** Use `#!python print("hello")` to output text, or `#!bash export KEY=value` to set env vars.

---

## Code Annotations

Annotations let you attach explanatory notes to specific lines. Add `# (1)` markers
in the code, then list the explanations below with `1.`.

````markdown
```yaml
theme:
  name: material
  features:
    - content.code.copy # (1)!
```

1. Adds a one-click copy button to every code block on the page.
````

**Result:**

```yaml
theme:
  name: material
  features:
    - content.code.copy # (1)!
```

1. Adds a one-click copy button to every code block on the page.
