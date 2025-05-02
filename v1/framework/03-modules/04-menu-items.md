---
title: view interceptors
---

## View Interceptors

While Converge has a highly customizable UI through themes, it also allows you to inject views at specific points during the rendering process. The view interceptor gives you this flexibility you can register views or hooks at predefined view locations. This is especially useful when adding UI elements like cards (e.g., Carbon Ads) or badges to specific items in the sidebar.

### Adding Menu Items
menu items can be configured per module. To add a menu item:

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
every menu item has two essentiel configurations: `label` and `url`

<x-converge::alert>
`url` can be relative or absolute, as shown above
</x-converge::alert>

#### Menu Item Icon
to add a icon to a menu item :

```php
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->icon(fn() => svg('icon-name', 'h-5 w-5'))+}
    );
```

#### Menu Item Icon Position
to add a icon to a menu item :

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->iconPosition(IconPosition::After)+}
    );
```

#### Menu Item Icon Position
to open url in new tab:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->openUrlInNewTab()+}
    );
```

#### additinal Menu Item styles 
to add raw styles to that menu item:

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
while you have a very liimited access to sepcific classes since tailwind get purged in the build process, but you can pass you assets class then use them:

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
to change the order of a menu item:

```php
use Converge\Enums\IconPosition;
$menuItems->add(
        fn(MenuItem $menuItem) => $menuItem
        // ...
        {+->sort(2)+}
    );
```


### Adding Menu Items Groups

you can create a dropdown of menu items by using menu item group feature in converge 