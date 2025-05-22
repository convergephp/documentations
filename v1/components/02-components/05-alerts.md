---
title: Alerts
description: A versatile notification component for displaying contextual messages, warnings, or feedback to users
category: UI Components
---

# Alerts Component

The Alerts component provides a flexible and visually distinctive way to display important messages to users. Each alert can include an optional icon and customized content, making it perfect for notifications, warnings, success messages, and informational feedback.

## Component Preview

@blade
<x-converge::alert type="primary">
    This is a standard primary alert with important information.
</x-converge::alert>
@endblade

```html
@blade
<x-converge::alert type="primary">
    This is a standard primary alert with important information.
</x-converge::alert>
@endblade
```

## Alert Types

The component supports multiple alert types to convey different contexts:

@blade
<x-converge::alert type="primary">
    This is a primary alert with that render a word or phrase as `code`.
</x-converge::alert>

<x-converge::alert type="info">
    This is an info alert for helpful tips and notes.
</x-converge::alert>

<x-converge::alert type="success">
    This is a success alert to confirm completed actions.
</x-converge::alert>

<x-converge::alert type="warning">
    This is a warning alert for potential issues.
</x-converge::alert>

<x-converge::alert type="error">
    This is an error alert for critical problems.
</x-converge::alert>

<x-converge::alert type="ghost">
    This is a ghost alert with minimal styling.
</x-converge::alert>
@endblade

```html
@blade
<x-converge::alert type="primary">
     This is a primary alert with that render a word or phrase as `code`.
</x-converge::alert>

<x-converge::alert type="info">
    This is an info alert for helpful tips and notes.
</x-converge::alert>

<x-converge::alert type="success">
    This is a success alert to confirm completed actions.
</x-converge::alert>

<x-converge::alert type="warning">
    This is a warning alert for potential issues.
</x-converge::alert>

<x-converge::alert type="error">
    This is an error alert for critical problems.
</x-converge::alert>

<x-converge::alert type="ghost">
    This is a ghost alert with minimal styling.
</x-converge::alert>
@endblade
```

### Without Icons

You can disable the icon display by setting the `icon` attribute to `false`:

@blade
<x-converge::alert type="warning" :icon="false">
    This warning alert appears without an icon.
</x-converge::alert>
@endblade

```html
@blade
<x-converge::alert type="warning" :icon="false">
    This warning alert appears without an icon.
</x-converge::alert>
@endblade
```

### Code Example in Alerts

You can include code snippets within your alerts:

@blade
<x-converge::alert type="primary">
To denote a word or phrase as code, enclose it in backticks `code`
</x-converge::alert>
@endblade

```html
@blade
<x-converge::alert type="primary">
To denote a word or phrase as code, enclose it in backticks `code`
</x-converge::alert>
@endblade
```


### Markdown Support

The alert component supports rich markdown content within descriptions:

@blade
<x-converge::alert>
**Bold text**

*italic text*

- list item
- list item 2
</x-converge::alert>
@endblade

```html
@blade
<x-converge::alert>
**Bold text**

*italic text*

- list item
- list item 2
</x-converge::alert>
@endblade
```


## Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `type` | string | `'primary'` | No | The style variant for the alert (`primary`, `info`, `success`, `warning`, `error`, `ghost`) |
| `icon` | boolean | `true` | No | Whether to display the default icon for the alert type |
