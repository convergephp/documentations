---
title: YouTube Video
description: A responsive YouTube video component with thumbnail preview, automatic playback control, and privacy options
category: Media Components
---

# YouTube Video Component

The YouTube Video component provides an elegant way to embed YouTube videos with a performance-optimized approach. It displays a thumbnail preview initially and loads the actual video only when users click to play, improving page load times and user experience.

## Component Preview

@blade
<x-converge::youtube-player
    videoId="rZOGx3iCDkA"/>
@endblade

```html
<x-converge::youtube-player
    videoId="rZOGx3iCDkA"
/>
```

## Complete Example

This example shows all available properties:

@blade
<x-converge::youtube-player
    videoId="rZOGx3iCDkA"
    videoTitle="Laravel Cloud As Staging Environment"
    description="Learn how to use laravel cloud as staging envirenment"
    publishedDate="2009-10-25T00:00:00Z"
    duration="PT3M33S"
    :autoplay="true"
    :controls="true"
    :enhancedPrivacy="true"
/>
@endblade

```html
<x-converge::youtube-player
    videoId="rZOGx3iCDkA"
    videoTitle="Laravel Cloud As Staging Environment"
    description="Learn how to use laravel cloud as staging envirenment"
    publishedDate="2009-10-25T00:00:00Z"
    duration="PT3M33S"
    :autoplay="false"
    :controls="true"
    :enhancedPrivacy="true"
/>
```

## Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `videoId` | string | | Yes | The YouTube video ID (found in the URL after `v=`) |
| `videoTitle` | string | 'youtube video' | No | Title of the video, used for accessibility |
| `description` | string | `null` | No | Video description metadata |
| `publishedDate` | string | current date | No | ISO 8601 formatted date when the video was published |
| `duration` | string | `null` | No | Video duration in ISO 8601 duration format |
| `autoplay` | boolean | `true` | No | Whether the video should autoplay when loaded |
| `controls` | boolean | `true` | No | Whether to show YouTube player controls |
| `enhancedPrivacy` | boolean | `true` | No | Uses youtube-nocookie.com domain for better privacy |
| `class` | string | `''` | No | Additional CSS classes to apply to the component |
