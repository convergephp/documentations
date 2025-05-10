---
title: Card Image
description: A versatile and responsive card component with advanced image handling and theme support
category: UI Components
---

# Card Image Component

The Card Image component offers a powerful and elegant solution for displaying image-based content in your application. It features comprehensive theme support for dark and light modes, multiple image source options, and customizable content areas—all designed to create visually appealing interfaces with minimal effort.

## Basic Usage

The component requires minimal setup to get started with an attractive image card:

@blade
    <x-converge::card.image title="Featured Content"
                            description="This is a description of the featured content."
                            src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            alt="Featured image" />
@endblade

```html
<x-converge::card.image title="Featured Content"
                        description="This is a description of the featured content."
                        {+src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                        alt="Featured image" />
```

## Image Source Options

One of the component's greatest strengths is its flexibility in handling various image sources. This allows you to organize your assets according to your project's needs while maintaining a consistent interface.

### External URL Source

Perfect for using images from CDNs, external services like Unsplash, or any publicly accessible URL:

@blade
    <x-converge::card.image title="External Image"
                            description="Image loaded from an unsplash via URL."
                            src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            alt="External image example" />
@endblade

```html
<x-converge::card.image title="External Image"
                        description="Image loaded from an unsplash via URL."
                        {+src="https://images.unsplash.com/photo-1465056836041-7f43ac27dcb5?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                        alt="External image example" />
```

### Laravel Storage Source

Seamlessly integrates with Laravel's storage system. This approach is ideal for user-uploaded content or dynamically generated images stored in your application's storage directory (`storage/app/public/images/exemple.webp`):

@blade
    <x-converge::card.image title="Storage Image"
                            description="Image loaded from Laravel storage directory."
                            srcStorage="images/exemple.webp"
                            alt="Storage image example" />
@endblade

```html
<x-converge::card.image title="Storage Image"
                        description="Image loaded from Laravel storage directory."
                        {+srcStorage="images/exemple.webp"+}
                        alt="Storage image example" />
```

> **Note:** Remember to create the symbolic link between your storage and public directories using `php artisan storage:link` for this feature to work correctly.

### Public Directory Source

For images stored directly in your application's public directory (`public/images/exemple.webp`), typically used for static assets:

@blade
    <x-converge::card.image title="Public Image"
                            description="Image loaded from public directory."
                            srcPublic="images/card.webp"
                            alt="Public directory image" />
@endblade

```html
<x-converge::card.image title="Public Image"
                        description="Image loaded from public directory."
                        {+srcPublic="images/card.webp"+}
                        alt="Public directory image" />
```

## Theme-Aware Images

The Card Image component takes user experience to the next level by supporting different images for dark and light themes. This ensures your visuals look perfect regardless of the user's preferred theme.

### External URL Theme Images

Use different external URLs for dark and light themes:

> Toggle your theme switcher to see the difference between dark and light mode images.

@blade
    <x-converge::card.image title="Theme-Aware External Images"
                            description="Different images for dark and light themes from external URLs."
                            src="https://images.unsplash.com/photo-1509023464722-18d996393ca8?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                            alt="Theme-aware external image" />
@endblade

```html
<x-converge::card.image title="Theme-Aware External Images"
                        description="Different images for dark and light themes from external URLs."
                        {+src="https://images.unsplash.com/photo-1509023464722-18d996393ca8?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                        {+srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                        alt="Theme-aware external image" />
```

### Storage Theme Images

Different images from your Laravel storage for each theme:

@blade
    <x-converge::card.image title="Theme-Aware Storage Images"
                            description="Different images for dark and light themes from storage."
                            srcStorage="images/hero-dark.webp"
                            srcStorageLight="images/hero-light.webp"
                            alt="Theme-aware storage image" />
@endblade

```html
<x-converge::card.image title="Theme-Aware Storage Images"
                        description="Different images for dark and light themes from storage."
                        {+srcStorage="images/hero-dark.webp"+}
                        {+srcStorageLight="images/hero-light.webp"+}
                        alt="Theme-aware storage image" />
```

### Public Directory Theme Images

Apply theme awareness to images in your public directory:

@blade
    <x-converge::card.image title="Theme-Aware Public Images"
                            description="Different images for dark and light themes from public directory."
                            srcPublic="images/hero-dark.webp"
                            srcPublicLight="images/hero-light.webp"
                            alt="Theme-aware public image" />
@endblade

```html
<x-converge::card.image title="Theme-Aware Public Images"
                        description="Different images for dark and light themes from public directory."
                        {+srcPublic="images/hero-dark.webp"+}
                        {+srcPublicLight="images/hero-light.webp"+}
                        alt="Theme-aware public image" />
```

### Mixed Source Theme Images

For maximum flexibility, you can even mix different source types between dark and light modes:

@blade
<x-converge::alert title="Mixed Sources">
You can combine different source types between dark and light modes to best suit your needs.
</x-converge::alert>
@endblade

@blade
    <x-converge::card.image title="Mixed Source Theme Images"
                            description="Storage image for dark mode, external URL for light mode."
                            {+srcStorage="images/hero-dark.webp"+}
                            {+srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                            alt="Mixed source theme image" />
@endblade

```html
<x-converge::card.image title="Mixed Source Theme Images"
                        description="Storage image for dark mode, external URL for light mode."
                        {+srcStorage="images/hero-dark.webp"+}
                        {+srcLight="https://images.unsplash.com/photo-1628171937573-a46e95b81d16?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"+}
                        alt="Mixed source theme image" />
```

## Advanced Usage Tips

### Image Optimization

For the best performance, consider the following best practices:

- Use WebP format when possible for better compression and quality
- Apply appropriate image dimensions to avoid unnecessary large downloads

### Accessibility Considerations

Always provide descriptive `alt` text for all images to ensure your content remains accessible to users with screen readers or when images fail to load.

## Component Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `title` | string | `''` | No | Title text displayed below the image |
| `description` | string | `''` | No | Description text displayed below the title |
| `src` | string | `''` | No | Primary external URL for the image (default/dark mode) |
| `srcLight` | string | `''` | No | External URL for light mode image |
| `srcStorage` | string | `''` | No | Path to image in Laravel storage (default/dark mode) |
| `srcStorageLight` | string | `''` | No | Path to light mode image in Laravel storage |
| `srcPublic` | string | `''` | No | Path to image in public directory (default/dark mode) |
| `srcPublicLight` | string | `''` | No | Path to light mode image in public directory |
| `alt` | string | `''` | No | Alt text for the image (important for accessibility) |

> **Priority Note:** If multiple source types are provided, the component follows this priority order: external URL (`src`/`srcLight`), storage (`srcStorage`/`srcStorageLight`), and then public directory (`srcPublic`/`srcPublicLight`).
