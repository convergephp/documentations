---
title: view interceptors in converge
---

# View Interceptor

## Introduction

While Converge has a highly customizable UI through themes, it also allows you to inject views at specific points during the rendering process. The view interceptor gives you this flexibility you can register views or hooks at predefined view locations. This is especially useful when adding UI elements like cards (e.g., Carbon Ads) or badges to specific items in the sidebar.

## Registering view interceptors

to regist a new view interceptor, you can call the `closure()` from the module provider, it accept the name of interception point as first argument, and the second argument is a callback that returns the content to be rendered  


```php
use Converge\Module;
use Converge\Enums\Interceptor;
use Illuminate\Contracts\View\View;

public function module(Module $module): Module
{
    return $module
            // ...
            ->intercept(Interceptor::BODY_START, function (): View {
                return view('banners.featured-sponsors')
            })
}
```

converge makes injecting view more robust by giving you the context you are in so you can 
