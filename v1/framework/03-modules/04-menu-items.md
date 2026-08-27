---
title: menu items
toc: [2,5]
---

# Menu Items

## Introduction
Menu items define navigational links or buttons that appear in your application’s UI. They can be configured per module and support customization such as icons, styles, target behavior, and grouping. This section covers how to define, style, and organize menu items using **Converge**.


### Adding Menu Items
Menu items can be configured per module. To add a menu item:

```php
use Converge\Module;
use Converge\MenuItems\MenuItem;
use Converge\MenuItems\MenuItems;

public function module(Module $module): Module
{
    return $module
            // ...
             ->defineMenuItems(function (MenuItems $menuItems) {
                $menuItems->add(
                    fn(MenuItem $menuItem) =>
                    $menuItem->url('https://github.com/convergephp/converge')
                        ->label('converge')
                );

                $menuItems->add(
                    fn(MenuItem $menuItem) =>
                    $menuItem->url('/')
                        ->label('home')
                );
            })
}
```
Every menu item has two essentiel configurations: `label` and `url`

<x-converge::alert>
`url` can be relative or absolute, as shown above
</x-converge::alert>

#### Menu Item Icon
To add a icon to a menu item:

```php
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->icon(fn() => svg('icon-name', 'h-5 w-5'))+}
    );
```

#### Menu Item Icon Position
To add a icon to a menu item:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->iconPosition(IconPosition::After)+}
    );
```

#### Open URL in New Tab
To make a menu item open in a new tab:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->openUrlInNewTab()+}
    );
```

#### additinal Menu Item styles 
To apply raw inline styles to a menu item:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->styles('color:red;margin-right:2px;')+}
        // or as an associative array
        {+->styles([
            'color' => 'red',
            'margin-right' => '2px'
        ])+}
    );
```

#### additinal Menu Item Classes 
Although Tailwind classes are purged during the build process, you can use the following pre-defined utility classes in your links, or injecting other css links using view interceptors:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->classes('btn btn-sm btn-outline btn-primary')+}
    );
```

<x-converge::alert>
You can use the following **button utility classes** for menu items or actions:
</x-converge::alert>
- `btn`, `btn-primary`, `btn-secondary`, `btn-accent`, `btn-neutral`
- `btn-info`, `btn-success`, `btn-warning`, `btn-error`
- `btn-outline`, `btn-ghost`, `btn-link`, `btn-active`, `btn-disabled`
- `btn-sm`, `btn-md`, `btn-lg`, `btn-block`, `btn-square`, `btn-circle`

These classes follow the [DaisyUI](https://daisyui.com/components/button/) naming convention and inherit your current theme's design system.

#### Menu Item Sort 
To define the sort order of a menu item:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->sort(2)+}
    );
```


### Adding Menu Items Groups

You can create a dropdown of menu items using the **MenuItemGroup** feature:
```php
use Converge\MenuItems\MenuItemGroup;
$menuItems->add(
    function (MenuItemGroup $group): void {
        // Setup the group button
        $group->label('Social Links');

        // Push items into the group
        $group->push(
            fn(MenuItem $item): MenuItem => $item
                ->label('Components')
                ->url('components')
                // Plus anything applicable to a solo menu item
        );

        $group->push(
            // Another regular menu item
        );
    }
);
```
<x-converge::alert>
you must hint `Converge\MenuItems\MenuItemGroup` for menu groups to work properly 
</x-converge::alert>


This allows you to group related links under a common label with full support for icons, styles, sorting, and more.

Since everything about single menu item links are documented above now let's focus on tweacking the dropdown button looks.

<x-converge::alert>
The only required configuration for menu item group is the **label** using `$group->label('social links')`
</x-converge::alert>
 
#### Open and Close Icons

You can changes the icon when the dropdown is open or close:  
```php
use Converge\MenuItems\MenuItemGroup;
$menuItems->add(
    function (MenuItemGroup $group): void {
        $group->label('Social Links')
              ->openIcon(fn() => svg('heroicon-c-arrow-top-right-on-square'))
              ->closeIcon(fn() => svg('heroicon-m-rocket-launch'))
              ->iconPosition(IconPosition::After); // or Before
              // changes the sort order    
              ->sort(4)
        // ... 
    }
);
```

