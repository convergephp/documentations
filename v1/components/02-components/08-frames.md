---
title: Image
description: A versatile image component with advanced handling capabilities including theme support, multiple source options, and responsive behavior
category: UI Components
---

# Image Component

The Image component provides a powerful and flexible solution for displaying images in your application. With support for multiple source types, theme awareness, and responsive sizing options, this component simplifies the process of integrating images while ensuring optimal visual presentation across all devices and user preferences.

## Basic Usage

Getting started with the Image component requires minimal configuration:

@blade
    <x-converge::image class="mt-10" src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop"
                        alt="Beautiful landscape" />
@endblade

```html
@blade
<x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop"
                    alt="Beautiful landscape" />
@endblade
```

## Image Source Options

Please refer to [card image](https://convergephp.com/docs/components/components/card-image#content-image-source-options) to learn more about image source.

## Theme-Aware Images

The Image component enhances user experience by supporting different images for dark and light themes, ensuring optimal visual presentation regardless of user preference.

### External URL Theme Images

Use different source image for dark and light themes:

> Toggle your theme switcher to see the difference between dark and light mode images.

@blade
    <x-converge::image src="https://images.unsplash.com/photo-1509023464722-18d996393ca8"
                        srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16"
                        alt="Theme-aware nature image"/>
@endblade

```html
@blade
<x-converge::image src="https://images.unsplash.com/photo-1509023464722-18d996393ca8"
                    srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16"
                    alt="Theme-aware nature image" />
@endblade
```
> You can even mix the source e.g. `src` from external source and `srcStorageLight` from storage.

## Lazy Loading

Improve page performance by enabling lazy loading for images below the fold:

@blade
    <x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                        alt="Lazy loaded image"
                        loading="lazy"/>
@endblade

```html
@blade
<x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                    alt="Lazy loaded image"
                    loading="lazy"/>
@endblde
```

###  Images columns

Use `style`or `class`attribute to make a grid :

@blade
    <div class="grid grid-cols-2 gap-4">
        <x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                            alt="Cover fitting"/>
        <x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                            alt="Contain fitting" />
    </div>
@endblade

```html
@blade
<div class="grid grid-cols-2 gap-4">
        <x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                            alt="Cover fitting" />
        <x-converge::image src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5"
                            alt="Contain fitting" />
</div>
@endblade
```

## Advanced Usage Tips

### Image Optimization

For the best performance, consider the following best practices:

- Use WebP format when possible for better compression and quality
- Enable lazy loading for images below the fold
- Use appropriately sized images for their display dimensions

## Component Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `src` | string | `''` | No | Primary external URL for the image (default/dark mode) |
| `srcLight` | string | `''` | No | External URL for light mode image |
| `srcStorage` | string | `''` | No | Path to image in Laravel storage (default/dark mode) |
| `srcStorageLight` | string | `''` | No | Path to light mode image in Laravel storage |
| `srcPublic` | string | `''` | No | Path to image in public directory (default/dark mode) |
| `srcPublicLight` | string | `''` | No | Path to light mode image in public directory |
| `alt` | string | `''` | Yes | Alt text for the image (important for accessibility) |
