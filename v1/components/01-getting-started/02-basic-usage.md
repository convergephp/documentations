---
title: Basic Usage
---

# Basic Usage

Once you have installed Converge Components, you can begin using them in your documentation. This guide will show you how to use the core components for creating professional documentation.

## Using Components in Markdown Files

Converge Components can be used directly within your markdown files using the `@blade` directive. This allows you to combine the simplicity of markdown with the power of Blade components.

### Basic Structure

A typical documentation page using Converge Components looks like:



```markdown
---
title: API Authentication
---

# API Authentication

Regular markdown content here...


{+@blade
<x-converge::alert title="Alert title">
    <!-- Component content here -->
</x-converge::alert>
@endblade+}

More markdown content...
```
