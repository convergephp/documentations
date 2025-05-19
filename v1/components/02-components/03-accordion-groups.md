---
title: Accordion
description: A collapsible content component for displaying information in a space-efficient manner.
category: Components
---

# Accordion Group

The Accordion Group component allows you to create a set of related accordions where only one can be open at a time.

### Preview

@blade
<x-converge::accordion.group>
    <x-converge::accordion.item title="First Item" index="0">
        Content for first accordion item.
    </x-converge::accordion.item>
    <x-converge::accordion.item title="Second Item" index="1">
        *Content for second accordion item.*
    </x-converge::accordion.item>
    <x-converge::accordion.item title="Third Item" index="2">
        **Content for third accordion item.**
    </x-converge::accordion.item>
</x-converge::accordion.group>
@endblade

here is the code of this example
```php
<x-converge::accordion.group>
  // item 1
  <x-converge::accordion.item title="First Item" index="0">
     Content for first accordion item.
  </x-converge::accordion.item>

  // item 2
  <x-converge::accordion.item title="Second Item" index="1">
    *Content for second accordion item.*
  </x-converge::accordion.item>

  // item 3
  <x-converge::accordion.item title="Third Item" index="2">
     **Content for third accordion item.**
  </x-converge::accordion.item>
</x-converge::accordion.group>
```

### Accordion Group Props

| Name          | Type      | Default | Required | Description                                |
|---------------|-----------|---------|----------|--------------------------------------------|
| `activeItem`  | `integer` | `0`     | No       | Index of initially active accordion item   |

### Accordion Item Props

| Name      | Type      | Default           | Required | Description                           |
|-----------|-----------|-------------------|----------|---------------------------------------|
| `title`   | `string`  | `Accordion Item`  | No       | The heading text for the item         |
| `index`   | `integer` | `0`               | No       | Position index in the accordion group |
