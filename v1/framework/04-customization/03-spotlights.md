# Spotlight Backgrounds

Converge provides several grid background patterns to enhance your documentation's visual design.

## Configuration

Configure spotlight backgrounds using the `spotlight()` function:

```php
use Converge\Module;
use Converge\Theme\Theme;
use Converge\Enums\Spotlight;

public function module(Module $module): Module
{
    return $module
                ->theme( function(Theme $theme) {
                    return $theme->spotlight(Spotlight::Grid);
                }
}
```

Alternatively, you may extract your the configuration into a separate method for better organization:

```php
use Converge\Theme\Theme;
use Converge\Enums\Spotlight;
use Converge\Theme\Theme;


public function module(Module $module): Module
{
    return $module
                ->theme(fn(Theme $theme) => $this->theme($theme));
}

private function theme(Theme $theme)
{
    return $theme
                ->spotlight(Spotlight::Grid);
}
```

## Available Patterns

| Pattern | Value | Description |
|---------|-------|-------------|
| **Grid** | `Spotlight::Grid` | Regular grid pattern |
| **Hive** | `Spotlight::Hive` | Hexagonal honeycomb pattern |
| **Strock** | `Spotlight::Strock` | Stroke-based minimal lines |

## Examples

```php
// Grid background
->spotlight(Spotlight::Grid)

// Hexagonal pattern
->spotlight(Spotlight::Hive)

// Minimal strokes
->spotlight(Spotlight::Strock)
```

Spotlight backgrounds automatically adapt to your theme colors and work seamlessly in both light and dark modes.
