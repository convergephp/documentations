---
title: code blocks themes
---
# Code block themes
converge uses [tempest/highlight](https://github.com/tempestphp/highlight) package wich's excellent for highlight code block and extensive syntax highlighting support with over 40 carefully curated themes to enhance code readability in your documentation.

## Configuration

Configure syntax highlighting using the `highlighterTheme()` function:

```php
use Converge\Theme\Theme;
use Converge\Enums\HighlighterName;

private function theme(Theme $theme)
{
    return $theme
        ->highlighterTheme(
            darkmodeHighlighter: HighlighterName::Github_dark_default, // for dark mode
            lightmodeHighlighter: HighlighterName::Github_light_default //  for light mode
        )
        ->layout(Layout::Default);
}
```

## Default Configuration

By default, Converge uses:
- **Light Mode**: `Github_light_default`
- **Dark Mode**: `Github_dark_default`

## Available Themes

### Dark Themes

| Theme | Value | Description |
|-------|-------|-------------|
| **Andromeeda** | `HighlighterName::Andromeeda` | Deep space-inspired dark theme |
| **Aurora X** | `HighlighterName::Aurora_x` | Vibrant aurora-colored syntax |
| **Ayu Dark** | `HighlighterName::Ayu_dark` | Modern dark theme with warm accents |
| **Catppuccin Frappé** | `HighlighterName::Catppuccin_frappe` | Warm, cozy dark theme |
| **Catppuccin Macchiato** | `HighlighterName::Catppuccin_macchiato` | Rich, coffee-inspired dark theme |
| **Catppuccin Mocha** | `HighlighterName::Catppuccin_mocha` | Deep, elegant dark theme |
| **Dark Plus** | `HighlighterName::Dark_plus` | Enhanced VS Code dark theme |
| **Dracula** | `HighlighterName::Dracula` | Popular purple-based dark theme |
| **Dracula Soft** | `HighlighterName::Dracula_soft` | Softer variant of Dracula theme |
| **Ellison** | `HighlighterName::Ellison` | Sophisticated dark theme |
| **GitHub Dark** | `HighlighterName::Dithub_dark` | GitHub's standard dark theme |
| **GitHub Dark Default** | `HighlighterName::Github_dark_default` | GitHub's default dark theme |
| **GitHub Dark Dimmed** | `HighlighterName::Github_dark_dimmed` | Dimmed version of GitHub dark |
| **Highlight Dark Lite** | `HighlighterName::Highlight_dark_lite` | Lightweight dark highlighting |
| **Highlight Tempest** | `HighlighterName::Highlight_tempest` | Storm-inspired dark theme |
| **Houston** | `HighlighterName::Houston` | Space mission dark theme |
| **Material Theme** | `HighlighterName::Material_theme` | Google Material dark theme |
| **Material Theme Darker** | `HighlighterName::Material_theme_darker` | Darker Material variant |
| **Material Theme Ocean** | `HighlighterName::Material_theme_ocean` | Ocean-inspired Material theme |
| **Material Theme Palenight** | `HighlighterName::Material_theme_palenight` | Palenight Material variant |
| **Min Dark** | `HighlighterName::Min_dark` | Minimalist dark theme |
| **Monokai** | `HighlighterName::Monokai` | Classic Monokai dark theme |
| **Night Owl** | `HighlighterName::Night_owl` | Night-optimized dark theme |
| **Nord** | `HighlighterName::Nord` | Arctic-inspired color scheme |
| **One Dark Pro** | `HighlighterName::One_dark_pro` | Professional Atom dark theme |
| **Poimandres** | `HighlighterName::Poimandres` | Philosophical dark theme |
| **Red** | `HighlighterName::Red` | Red-accented dark theme |
| **Rose Pine** | `HighlighterName::Rose_pine` | Elegant rose-tinted theme |
| **Rose Pine Moon** | `HighlighterName::Rose_pine_moon` | Moonlit Rose Pine variant |
| **Slack Dark** | `HighlighterName::Slack_dark` | Slack's dark interface theme |
| **Slack Ocean** | `HighlighterName::Slack_ochin` | Ocean-themed Slack variant |
| **Solarized Dark** | `HighlighterName::Solarized_dark` | Classic Solarized dark theme |
| **Synthwave 84** | `HighlighterName::Synthwave_84` | Retro synthwave-inspired theme |
| **Tokyo Night** | `HighlighterName::Tokyo_night` | Tokyo cityscape-inspired theme |
| **Vesper** | `HighlighterName::Vesper` | Evening-inspired dark theme |
| **Vitesse Black** | `HighlighterName::Vitesse_black` | Pure black theme |
| **Vitesse Dark** | `HighlighterName::Vitesse_dark` | Modern dark theme |

### Light Themes

| Theme | Value | Description |
|-------|-------|-------------|
| **Catppuccin Latte** | `HighlighterName::Catppuccin_latte` | Warm, coffee-inspired light theme |
| **GitHub Light** | `HighlighterName::Github_light` | GitHub's standard light theme |
| **GitHub Light Default** | `HighlighterName::Github_light_default` | GitHub's default light theme |
| **Highlight Light Lite** | `HighlighterName::Highlight_light_lite` | Lightweight light highlighting |
| **Inspired GitHub** | `HighlighterName::Inspired_github` | GitHub-inspired light theme |
| **Light Plus** | `HighlighterName::Light_plus` | Enhanced VS Code light theme |
| **Material Theme Lighter** | `HighlighterName::Material_theme_lighter` | Light Material variant |
| **Min Light** | `HighlighterName::Min_light` | Minimalist light theme |
| **Rose Pine Dawn** | `HighlighterName::Rose_pine_dawn` | Dawn-inspired Rose Pine variant |
| **Solarized Light** | `HighlighterName::Solarized_light` | Classic Solarized light theme |
| **Vitesse Light** | `HighlighterName::Vitesse_light` | Modern light theme |

## Examples

```php
// Using default GitHub themes
->highlighterTheme(
    darkmodeHighlighter: HighlighterName::Github_dark_default,
    lightmodeHighlighter: HighlighterName::Github_light_default
)

// Using Monokai for dark mode and Solarized for light mode
->highlighterTheme(
    darkmodeHighlighter: HighlighterName::Monokai,
    lightmodeHighlighter: HighlighterName::Solarized_light
)

// Using Material Theme variants
->highlighterTheme(
    darkmodeHighlighter: HighlighterName::Material_theme_darker,
    lightmodeHighlighter: HighlighterName::Material_theme_lighter
)

// Using Catppuccin theme family
->highlighterTheme(
    darkmodeHighlighter: HighlighterName::Catppuccin_mocha,
    lightmodeHighlighter: HighlighterName::Catppuccin_latte
)

// Using Rose Pi theme family
->highlighterTheme(
    darkmodeHighlighter: HighlighterName::Rose_pine_moon,
    lightmodeHighlighter: HighlighterName::Rose_pine_dawn
)
```

The syntax highlighting automatically adapts to your selected theme mode and provides consistent, readable code formatting across all supported programming languages.
