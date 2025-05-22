---
title: Timeline
description: A vertical timeline component for displaying chronological events and milestones with version tracking and detailed descriptions.
category: Components
author: Converge UI
---

# Timeline

The Timeline component provides a visually appealing way to display chronological events, version releases, or project milestones in a vertical layout with detailed information panels.

## Overview

Perfect for showcasing:
- Version history or release notes
- Project milestones and progress
- Chronological events or company history
- Development phases and roadmaps

## Basic Usage

<x-converge::timeline>
    <x-converge::timeline.step
        version="1.0.0.beta"
        date="May 2025"
        title="Converge Beta Release">

        <x-slot:description>
            First beta release with **core features** and basic functionality.
        </x-slot:description>

        Any additional content goes here.
    </x-converge::timeline.step>
</x-converge::timeline>

```php
@blade
<x-converge::timeline>
    <x-converge::timeline.step
        version="1.0.0.beta"
        date="Mai 2025"
        title="Converge Beta Release">

        <x-slot:description>
            First beta release with **core features** and basic functionality.
        </x-slot:description>

        Any additional content goes here.
    </x-converge::timeline.step>
</x-converge::timeline>
@endblade
```

## Advanced Usage

@blade
<x-converge::timeline>
<x-converge::timeline.step version="1.0.0" date="June 01, 2025" title="Major Feature Release of converge">
<x-slot:description>
**Key Features**
- Integrated Search engine
- Support for multiple themes
- Documentation mirrors filesystem structure
- Use Blade components directly within Markdown
- [And more](https://convergephp.com/roadmap)

```php
return $module
    ->id('converge-docs')
    ->default()
    ->routePath('docs')
    ->latestVersionLabel('v1.0.0-beta.3')
    ->brandLogo('Converge')
    ->intercept(Interceptor::FIXED_CARBON_ADS, fn () => view('components.carbon-ads'))
    ->defineClusters(fn(Clusters $clusters) => $this->defineClusters($clusters))
    ->defineMenuItems(fn(MenuItems $menuItems) => $this->defineMenuItems($menuItems))
    ->theme(fn(Theme $theme) => $this->theme($theme))
    ->in(realpath(base_path('docs/v1/framework')));
}
```
</x-slot:description>
Additional content can go here outside the description slot.
</x-converge::timeline.step>

<x-converge::timeline.step version="2.0.0" date="TBD" title="Converge version 2" >
<x-slot:description>
**Key Features**
- Single Page Application (SPA) mode
- Lazy-load sub-items for better performance
- Feedback and Ratings system
- [And more](https://convergephp.com/roadmap)
</x-slot:description>
</x-converge::timeline.step>
</x-converge::timeline>
@endblade


```html
@blade
<x-converge::timeline>
<x-converge::timeline.step version="1.0.0" date="June 01, 2025" title="Major Feature Release of converge">
    <x-slot:description>
    **Key Features**
    - Integrated Search engine
    - Support for multiple themes
    - Documentation mirrors filesystem structure
    - Use Blade components directly within Markdown
    - [And more](https://convergephp.com/roadmap)

    ```php
    return $module
        ->id('converge-docs')
        ->default()
        ->routePath('docs')
        ->latestVersionLabel('v1.0.0-beta.3')
        ->brandLogo('Converge')
        ->intercept(Interceptor::FIXED_CARBON_ADS, fn () => view('components.carbon-ads'))
        ->defineClusters(fn(Clusters $clusters) => $this->defineClusters($clusters))
        ->defineMenuItems(fn(MenuItems $menuItems) => $this->defineMenuItems($menuItems))
        ->theme(fn(Theme $theme) => $this->theme($theme))
        ->in(realpath(base_path('docs/v1/framework')));
    }
    ```
    </x-slot:description>
    Additional content can go here outside the description slot.
</x-converge::timeline.step>

<x-converge::timeline.step version="2.0.0" date="TBD" title="Converge version 2" >
    <x-slot:description>
    **Key Features**
    - Single Page Application (SPA) mode
    - Lazy-load sub-items for better performance
    - Feedback and Ratings system
    - [And more](https://convergephp.com/roadmap)
    </x-slot:description>
</x-converge::timeline.step>
</x-converge::timeline>
@endblade
```

## Props

### Timeline Container
| Name | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| `id` | `string` | `null` | No | Custom identifier for the timeline |

### Timeline Step
| Name | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| `version` | `string` | `null` | No | Version badge (e.g., "2.1.0") |
| `date` | `string` | `null` | No | Date with calendar icon |
| `title` | `string` | `''` | No | Main heading |

## Slots

### Description Slot
Use `<x-slot:description>` for Markdown-formatted content that appears in the left panel. This slot supports full Markdown syntax including code highlighting.

### Default Slot
The main content area accepts any HTML or Blade components for additional information.

## Features

- **Responsive Design**: Adapts to mobile and desktop layouts
- **Markdown Support**: Full Markdown in description slot with syntax highlighting
- **Anchor Links**: Auto-generated links when version is provided
- **Flexible Content**: Mix Markdown descriptions with rich HTML content
