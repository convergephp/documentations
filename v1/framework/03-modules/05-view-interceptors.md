---
title: view interceptors in converge
---
# View Interceptor

## Introduction

While Converge has a highly customizable UI through themes, it also allows you to inject views at specific points during the rendering process. View interceptors give you this flexibility—you can register views or hooks at predefined view locations. This is especially useful when adding UI elements like cards (e.g., Carbon Ads) or badges to specific items in the sidebar.

## Registering View Interceptors

To register a new view interceptor, call the `intercept()` method from the module provider. It accepts two arguments:

1. The name of the interception point (using the `Interceptor` enum).
2. A callback that returns the content to be rendered.

```php
use Converge\Module;
use Converge\Enums\Interceptor;
use Illuminate\Contracts\View\View;

public function module(Module $module): Module
{
return $module
    // ...
    ->intercept(Interceptor::BODY_START, function (): View {
        return view('banners.featured-sponsors');
    });
}
```

Converge makes view injection more powerful by providing context at most interception point (not all), allowing you to render views conditionally. For example, to inject content only when a sidebar item is active (e.g., the topic being viewed), you can do:

```php
use Converge\Module;
use Converge\Enums\Interceptor;
use Illuminate\Contracts\View\View;
use Converge\Sidebar\SidebarItem;

public function module(Module $module): Module
{
return $module
    // ...
    ->intercept(Interceptor::AFTER_SIDEBAR_ITEM, function (SidebarItem $item): View|string|null {
        if ($item->isActive()) {
            return '<span class="badge">Active</span>'; // or svg('icon-name') etc.
        }

        return null;
    });
}
```

This feature unlocks powerful UI customizations, such as adding badges, icons, or additional markup based on the current rendering context.


when injecting some views you may re build the assets again using:

```shell
php artisan converge:build
```

you may keep watching changes by using :
```shell
php artisan converge:build --watch
```

## Available Interception Points

### Sidebar Items



These interception points give you access to the `SidebarItem` instance:

<x-converge::divide
    title="interception points"
    color="success"
/>

* `Interceptor::BEFORE_SIDEBAR_LINK` — Before the sidebar link
* `Interceptor::AFTER_SIDEBAR_LINK` — After the sidebar link
* `Interceptor::BEFORE_SIDEBAR_LABEL` — Before the sidebar label
* `Interceptor::AFTER_SIDEBAR_LABEL` — After the sidebar label

You can use the methods provided by `SidebarItem` to tailor the output as needed.

<x-converge::divide
    title="available methods in SidebarItem"
    color="success"
/>

```php
use Illuminate\Contracts\View\View;
use Converge\Sidebar\SidebarItem;
    ->intercept(Interceptor::AFTER_SIDEBAR_ITEM, function (SidebarItem $item): View|string|null {
        $item->isActive(); // check if current sidebar is the active one 

        $item->getLabel(); // eg : view interceptors

        $item->getSort(); // eg: 4, (reset to 0 in every group)
        
        $item->getDepth(); // eg: 1
        
        $item->getUrl(); // eg: /docs/modules/view-interceptors
    });
```
### Sidebar Groups 

These interception points are related to sidebar groups and provide access to the `SidebarGroup` instance:

<x-converge::divide
    title="interception points"
    color="success"
/>

* `Interceptor::BEFORE_SIDEBAR_GROUP_LABEL` — Before the sidebar group label
* `Interceptor::AFTER_SIDEBAR_GROUP_LABEL` — After the sidebar group label
* `Interceptor::BEFORE_SIDEBAR_GROUP_ITEMS` — Before the sidebar group items
* `Interceptor::AFTER_SIDEBAR_GROUP_ITEMS` — After the sidebar group items

You can use the methods provided by `SidebarItem` to tailor the output as needed.
<x-converge::divide
    title="available methods in SidebarGroup"
    color="success"
/>

```php
use Illuminate\Contracts\View\View;
use Converge\Sidebar\SidebarItem;
    ->intercept(Interceptor::AFTER_SIDEBAR_ITEM, function (SidebarItem $item): View|string|null {
        
        $item->getLabel(); // eg : modules

        $item->getSort(); 
        
        $item->getDepth(); 

        $item->getUrl(); // eg: /docs/modules

        $item->hasActiveChild(); // @todo 
    });
```
### Clusters Points

<x-converge::divide
    title="interception points"
    color="success"
/>

* `Interceptor::BEFORE_SIDEBAR_CLUSTERS` 
* `Interceptor::AFTER_SIDEBAR_CLUSTERS`

### Sidebar Points

no context aware available
<x-converge::divide
    title="interception points"
    color="success"
/>

* `Interceptor::SIDEBAR_START` 
* `Interceptor::BEFORE_SIDEBAR_ITEMS`
* `Interceptor::AFTER_SIDEBAR_ITEMS`
* `Interceptor::SIDEBAR_END`

### Head Point 

no context aware available
<x-converge::divide
    title="interception points"
    color="success"
/>

* `Interceptor::HEAD_START` 
* `Interceptor::HEAD_END`

These are particularly useful for injecting scripts like analytics tools (e.g., Google Analytics).
You can place your analytics script in a Blade component for clean reuse. For example:``resources/views/components/analytics/gtags.blade.php`` : 

```blade
@production
 <!-- gtags -->
    @if (config('services.google.analytics_id'))
        <script async
                src="https://www.googletagmanager.com/gtag/js?id={{ config('services.google.analytics_id') }}"></script>
        <script>
            window.dataLayer = window.dataLayer || [];

            function gtag() {
                dataLayer.push(arguments);
            }
            gtag('js', new Date());
            gtag('config', '{{ config('services.google.analytics_id') }}');
        </script>
    @endif
@endproduction
```

You can register the component in a specific module or globally via a service provider:

```php
    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {

        app(ViewInterceptor::class)
            ->registerViewInterceptor(Interceptor::HEAD_END, fn() => view('components.analytics.gtags'));
    }
```

Other points coming soon... 



