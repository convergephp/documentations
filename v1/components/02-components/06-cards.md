---
title: Card
description: A versatile card component for displaying content with customizable icons and colors
category: UI Components
---

# Card Component

The Card component provides a clean, versatile container for various content types, featuring customizable icons, colors, and optional link functionality.

- Use [image card]('https://convergephp.com/docs/card-image'), for images cards
- Use [grid]('https://convergephp.com/docs/card-grid'), for columns grid

## Basic Usage

### Linkable

Create clickable cards that link to a URL:

@blade
<x-converge::card
    title="Linkable Card"
    description="A concise description of this feature and its benefits."
    icon="heroicon-o-light-bulb"
/>
@endblade

```html
{+<x-converge::card+}
    title="Linkable"
    description="This is a card with link."
    icon="heroicon-o-light-bulb"
/>
```

### Without Link

@blade
<x-converge::card.horizontal
    title="Without link"
    color="warning"
    description="This is a card without link."
    icon="heroicon-o-camera"
/>
@endblade

```html
{+<x-converge::card.horizontal+}
    title="Without link card"
    description="A concise description of this feature and its benefits."
    icon="heroicon-o-camera"
/>
```

## Color Variants

Customize card appearance with different color schemes:

@blade
<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <x-converge::card
        title="Primary"
        description="Default color scheme."
        icon="heroicon-o-star"
        color="primary"
    />
    <x-converge::card
        title="Success"
        description="Indicates successful actions."
        icon="heroicon-o-check-circle"
        color="success"
    />
    <x-converge::card
        title="Warning"
        description="Indicates caution or pending status."
        icon="heroicon-o-exclamation"
        color="warning"
    />
    <x-converge::card
        title="Error"
        description="Indicates error states or alerts."
        icon="heroicon-o-x-circle"
        color="error"
    />
    <x-converge::card.horizontal
        title="Info"
        description="Used for informational content."
        icon="heroicon-o-information-circle"
        color="info"
    />
</div>
@endblade

```html
<x-converge::card
    title="Primary"
    description="Default color scheme."
    icon="heroicon-o-star"
    color="primary"
/>

<x-converge::card
    title="Success"
    description="Indicates successful actions."
    icon="heroicon-o-check-circle"
    color="success"
/>

<!-- Additional color variants: warning, error, info -->
```

## Custom Icons

Incorporate icons from any Blade icon package. In the example below we use `iconsax-bul-wallet-minus` icon from `iconsax`:

```bash
# Install Blade icon packages
composer require blade-ui-kit/blade-heroicons
composer require saade/blade-iconsax
composer require davidhsianturi/blade-bootstrap-icons
```

@blade
<x-converge::card
    title="Support Center"
    description="Get help and answers to common questions."
    icon="iconsax-bul-wallet-minus"
    color="error"
/>
@endblade

```html
<x-converge::card
    title="Support Center"
    description="Get help and answers to common questions."
    icon="iconsax-bul-wallet-minus"
    color="error"
/>
```

## Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `title` | string | - | Yes | The main heading for the card |
| `description` | string | - | Yes | The descriptive text displayed below the title |
| `icon` | string | `null` | No | The name of a Blade icon to display (requires appropriate Blade icon package) |
| `url` | string | `'#'` | No | URL to navigate to when card is clicked; use `'#'` for non-linking cards |
| `color` | string | `'primary'` | No | The color theme for the card; options: `primary`, `warning`, `error`, `success`, `info` |
