---
title: Steps
description: A vertical timeline component for displaying sequential content with clear visual indicators
category: UI Components
---

# Steps Component

The Steps component provides an elegant vertical timeline for displaying sequential content with visual indicators. Each step can include an icon or number, title, and descriptive content, making it perfect for multi-stage processes, tutorials, and timelines.

## Overview

The Steps component is designed to visually represent sequential information in a clear, structured format. It's particularly useful for:

- Creating instructional workflows with clear progression
- Displaying process timelines or step-by-step guides
- Showing historical events or activity logs
- Building user onboarding experiences
- Visualizing multi-stage forms or wizards

## Component Preview

@blade
<x-converge::steps.vertical>
    <x-converge::steps.step title="Setup Project">
        <x-slot:description>
        Initialize your project and install required dependencies.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step title="Configure Settings">
        <x-slot:description>
        Update your configuration files with appropriate settings.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step title="Launch Application" last>
        <x-slot:description>
        Deploy and launch your application.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

```html
<x-converge::steps.vertical>
    <x-converge::steps.step title="Setup Project">
        <x-slot:description>
        Initialize your project and install required dependencies.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step title="Configure Settings">
        <x-slot:description>
        Update your configuration files with appropriate settings.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step title="Launch Application" last>
        <x-slot:description>
        Deploy and launch your application.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

## Numbered Steps

Use the `number` attribute to display sequential numbers instead of icons:

@blade
<x-converge::steps.vertical>
    <x-converge::steps.step number="1" title="Planning Phase">
        <x-slot:description>
        Define project scope and objectives.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step number="2" title="Design Phase">
        <x-slot:description>
        Create wireframes and design mockups.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step number="3" title="Implementation Phase">
        <x-slot:description>
        Build and integrate components.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step number="4" title="Deployment Phase" last>
        <x-slot:description>
        Deploy to production and monitor performance.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

```html
<x-converge::steps.vertical>
    <x-converge::steps.step number="1" title="Planning Phase">
        <x-slot:description>
        Define project scope and objectives.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step number="2" title="Design Phase">
        <x-slot:description>
        Create wireframes and design mockups.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step number="3" title="Implementation Phase">
        <x-slot:description>
        Build and integrate components.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step number="4" title="Deployment Phase" last>
        <x-slot:description>
        Deploy to production and monitor performance.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

### Custom Icons

You can use custom icons from any Blade icon package:

To use custom icons:

1. Install a Blade icon package, for example:

```bash
# Install Heroicons
composer require blade-ui-kit/blade-heroicons

# Install Iconsax
composer require saade/blade-iconsax

# Install Bootstrap Icons
composer require davidhsianturi/blade-bootstrap-icons
```

2. Reference the icon in your step component:

@blade
<x-converge::steps.vertical>
    <x-converge::steps.step icon="heroicon-o-cog" title="Configure Settings">
        <x-slot:description>
        Configure application settings.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step icon="heroicon-o-check-circle" title="Complete Setup" last>
        <x-slot:description>
        Finalize setup and begin using the application.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

```html
<x-converge::steps.vertical>
    <x-converge::steps.step icon="heroicon-o-cog" title="Configure Settings">
        <x-slot:description>
        Configure application settings.
        </x-slot:description>
    </x-converge::steps.step>

    <x-converge::steps.step icon="heroicon-o-check-circle" title="Complete Setup" last>
        <x-slot:description>
        Finalize setup and begin using the application.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

### Custom Colors

Customize step colors using the `color` attribute:

Valid colors: `primary`, `success`, `warning`, `error`, `info`, `accent`

@blade
<x-converge::steps.vertical>
    <x-converge::steps.step title="Warning step" color="warning">
        <x-slot:description>
        Set up your development environment.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step number="2" title="Error step" color="error">
        <x-slot:description>
        Implement core functionality.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step title="Info step" color="info" last>
        <x-slot:description>
        All tasks completed successfully.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

```php
<x-converge::steps.vertical>
    <x-converge::steps.step title="Warning step" color="warning">
        <x-slot:description>
        Set up your development environment.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step number="2" title="Error step" color="error">
        <x-slot:description>
        Implement core functionality.
        </x-slot:description>
    </x-converge::steps.step>
    <x-converge::steps.step title="Info step" color="info" last>
        <x-slot:description>
        All tasks completed successfully.
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

### Advanced Markdown Support

The Steps component supports rich markdown content within descriptions:

@blade
<x-converge::steps.vertical>
<x-converge::steps.step title="Markdown Example">
<x-slot:description>
This is **bold text** and *italic text*.

#### Code Example

```php
public function example()
{
    return "This is a code block with syntax highlighting";
}
```

> This is a blockquote that can be used for important notes.

- List item 1
- List item 2
</x-slot:description>
</x-converge::steps.step>
</x-converge::steps.vertical>
@endblade


```php
<x-converge::steps.vertical>
    <x-converge::steps.step title="Markdown Example">
        <x-slot:description>
            This is **bold text** and *italic text*.

            #### Code Example

            ```php
            public function example()
            {
                return "This is a code block with syntax highlighting";
            }
            ```

            > This is a blockquote that can be used for important notes.

            - List item 1
            - List item 2
        </x-slot:description>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

### Embedding Other Components

You can nest other Converge components inside steps:

@blade
<x-converge::steps.vertical>
    <x-converge::steps.step title="Step with Alert" description="Basic description here.">
        <x-converge::alert type="info" title="test">
            This is an embedded alert component inside a step.
        </x-converge::alert>
    </x-converge::steps.step>
    <x-converge::steps.step title="Step with Card" description="Another description.">
        <x-converge::card title="Purchase Converge blade components"
                    description="Purchase a license for Converge blade components"
                    url="/purchase"
                    icon="phosphor-lock-simple-open-fill"
                    class="group mt-4"></x-converge::card>
    </x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

```php
<x-converge::steps.vertical>
    // step 1
    <x-converge::steps.step title="Step with Alert" description="Basic description here.">
        // alert component
        <x-converge::alert type="info" title="test">
            This is an embedded alert component inside a step.
        </x-converge::alert>
    </x-converge::steps.step>

    // step 2
    <x-converge::steps.step title="Step with Card" description="Another description.">
        // card component
        <x-converge::card title="Purchase Converge blade components"
                    description="Purchase a license for Converge blade components"
                    url="/purchase"
                    icon="phosphor-lock-simple-open-fill"
                    class="group mt-4"></x-converge::card>
    </x-converge::steps.step>
</x-converge::steps.vertical>
```

## Props

| Prop Name | Type | Default | Required | Description |
|-----------|------|---------|----------|-------------|
| `title` | string | `'Step'` | No | The title text displayed for the step |
| `color` | string | `null` | No | The color for this specific step (overrides parent color) |
| `last` | boolean | `false` | No | When `true`, removes the connecting line below this step |
| `number` | string | `null` | No | When specified, displays a number instead of an icon |
| `icon` | string | `null` | No | The name of a Blade icon to display (requires appropriate Blade icon package) |

## Best Practices

For optimal use of the Steps component:

1. **Mark the Final Step**: Always use the `last` attribute on the final step to properly terminate the timeline.

2. **Use Descriptive Titles**: Keep step titles concise yet descriptive to clearly communicate each stage.


3. **Choose Appropriate Colors**: Use semantic colors to convey meaning:
   - `primary` for neutral steps
   - `success` for completed steps
   - `warning` for in-progress or attention-needed steps
   - `error` for critical steps or issues
   - `info` for informational steps

4. **Use Markdown for Rich Content**: Leverage the <`x-slot:description`> tag with markdown for formatted content.

5. **Consider Your Use Case**:
   - Use numbers for sequential processes with a defined number of steps
   - Use icons for more visual representation when numbers aren't needed

6. **Maintain Consistent Styling**: When using icons or numbers, maintain consistency throughout your steps.

7. **Nest Components Thoughtfully**: When embedding other components inside steps, ensure they complement rather than overwhelm the step content.

8. **Responsive Considerations**: The Steps component is responsive by default, but be mindful of content length on mobile devices.

## Troubleshooting

### Common Issues

1. **Icons Not Displaying**:
   - Ensure you've installed the appropriate Blade icon package
   - Verify the icon name is correct and follows the package's naming convention

2. **Markdown Not Rendering**:
   - Make sure content is within <`x-slot:description>`> tags
   - Check markdown syntax for errors

3. **Connecting Lines Misaligned**:
   - Ensure the `last` attribute is set on the final step
   - Check for proper closing of component tags
