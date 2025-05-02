---
title: Markdown
description: Text formatting guide for content creation with Markdown syntax
category: Documentation
status: Stable
author: Converge UI
---

# Markdown

In addition to the components offered by Converge, you can also use Markdown syntax to format your content. Converge pre-styles most Markdown elements to ensure a consistent and professional appearance throughout your documentation. Markdown is a lightweight markup language that allows you to format text for web content using simple syntax. This guide covers the most common Markdown elements supported in our documentation system.

## Headers and Text

Headers create section titles with different levels of importance. They automatically generate anchors for navigation.

### Titles

Best used for section headers.

```markdown
## Titles
```

### Subtitles

Best used for subsection headers.

```markdown
### Subtitles
```

Titles and subtitles appear in the table of contents for easy navigation.

## Text Formatting

Format your text with simple markers to enhance readability.

| Style | How to write it | Result |
|-------|----------------|--------|
| Bold | `**bold**` | **bold** |
| Italic | `*italic*` | *italic* |
| Strikethrough | `~strikethrough~` | ~strikethrough~ |

You can combine these styles. For example, write `**_bold and italic_**` to get **_bold and italic_** text.

For superscript and subscript, use HTML tags:

| Text Size | How to write it | Result |
|-----------|----------------|--------|
| Superscript | `<sup>superscript</sup>` | <sup>superscript</sup> |
| Subscript | `<sub>subscript</sub>` | <sub>subscript</sub> |

## Links

Create hyperlinks to connect your documentation to other pages or external resources.

```markdown
[link text](https://example.com)
```

For internal documentation links, use root-relative paths:

```markdown
[link to page](/content/page-name)
```

## Blockquotes

Blockquotes highlight important information or quotations.

### Single-line Blockquote

```markdown
> This is a single line blockquote.
```

Renders as:

> This is a single line blockquote.

### Multi-line Blockquote

```markdown
> First paragraph of the blockquote.
>
> Second paragraph of the blockquote.
```

Renders as:

> First paragraph of the blockquote.
>
> Second paragraph of the blockquote.

## Code

Share code examples with proper syntax highlighting.

### Inline Code

Use backticks for inline code: `` `code` ``

### Code Blocks

For multi-line code snippets, use triple backticks with an optional language identifier:

````markdown
```php
public function example() {
    return "Hello World";
}
```
````

Renders as:

```php
public function example() {
    return "Hello World";
}
```

## Tables

Create structured data with tables.

```markdown
| Header 1         | Header 2         | Header 3         |
|------------------|------------------|------------------|
| Cell 1  content  | Cell 2  content  | Cell 3  content  |
| Cell 4  content  | Cell 5  content  | Cell 6  content  |
```

Renders as:

| Header 1         | Header 2         | Header 3         |
|------------------|------------------|------------------|
| Cell 1  content  | Cell 2  content  | Cell 3  content  |
| Cell 4  content  | Cell 5  content  | Cell 6  content  |

## Line Breaks

Create line breaks between paragraphs by adding a blank line or using HTML:

```markdown
Paragraph 1

Paragraph 2
```

Or use the HTML break tag:

```markdown
Line 1<br />
Line 2
```

To learn more about Markdown, visit <a href="https://www.markdownguide.org/" target="_blank" rel="noopener noreferrer">Markdown Guide</a>.

For building beautiful and well-structured documentation, consider using the Blade components offered by **Converge**. These components are designed to help you quickly create elegant [accordions](accordions), [steps](steps), [Youtube player](youtube-player), and more. Perfect for clean and readable developer documentation.
