# Setting up Emojis

Material for MkDocs supports the full set of [Twemoji](https://twemoji.twitter.com/) and [Material Design Icons](https://pictogrammers.com/library/mdi/) via a simple shortcode syntax. Once configured, you can drop emojis and icons anywhere in your Markdown.

## Configuration

Add the following to your `mkdocs.yml`:

```yaml
markdown_extensions:
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

## Basic Usage

Use `:name:` shortcodes inline with your text:

```markdown
:smile: :rocket: :warning: :white_check_mark: :tada:
```

**Result:** :smile: :rocket: :warning: :white_check_mark: :tada:

---

## Common Emoji Shortcodes

| Shortcode            | Emoji | Use case                |
| -------------------- | ----- | ----------------------- |
| `:rocket:`           | 🚀    | Launches, deploys       |
| `:white_check_mark:` | ✅    | Success, completed      |
| `:warning:`          | ⚠️    | Caution, deprecation    |
| `:x:`                | ❌    | Errors, unsupported     |
| `:bulb:`             | 💡    | Tips, ideas             |
| `:book:`             | 📖    | Documentation, reading  |
| `:lock:`             | 🔒    | Security, auth          |
| `:gear:`             | ⚙️    | Configuration, settings |

---

## Emoji in Headings and Lists

Emojis work inside headings, list items, and tables — anywhere Markdown is rendered.

```markdown
## :rocket: Deployment

- :white_check_mark: Step one complete
- :gear: Configuring environment
- :lock: Securing credentials
```

**Result:**

### :rocket: Deployment

- :white_check_mark: Step one complete
- :gear: Configuring environment
- :lock: Securing credentials

---

## Finding Emojis

Browse the full list at [emojipedia.org](https://emojipedia.org) or search the
[Twemoji cheat sheet](https://twemoji-cheatsheet.vercel.app/). Most standard
emoji names work as-is with underscores replacing spaces.
