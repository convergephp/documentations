---
title: Accordion
description: A collapsible content component for displaying information in a space-efficient manner.
category: Components
status: Stable
author: Converge UI
---

# Accordion

The Accordion component offers an elegant way to toggle the visibility of content sections, helping to manage information density in your UI. When space is at a premium, accordions allow users to selectively reveal only the content they're interested in.

## Overview

Accordions are particularly useful when you need to:
- Present a large amount of information in a limited space
- Group related content into collapsible sections
- Create a cleaner and more focused user interface

## Preview

@blade
<x-converge::accordion title="Introduction to Accordions" open="true">
  Accordions provide a way to organize content into collapsible sections.

  ```php
  public function toggleVisibility() {
      return $this->isVisible ? 'Hide content' : 'Show content';
  }
  ```
</x-converge::accordion>
@endblade

here is the code of this example
```php
<x-converge::accordion title="Introduction to Accordions" open="true">
  Accordions provide a way to organize content into collapsible sections.
  // any content
</x-converge::accordion>
```

## Props

| Name      | Type      | Default    | Required | Description                           |
|-----------|-----------|------------|----------|---------------------------------------|
| `title`   | `string`  | -          | Yes      | The heading text shown in the accordion header |
| `open`    | `boolean` | `false`    | No       | Whether the accordion is initially expanded |
| `id`      | `string`  | Auto-generated | No   | Custom identifier for the accordion element |
