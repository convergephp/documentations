## Module Providers

### Explanation

**Module providers** are the core building blocks in Converge. They are the *only* place where you configure documentation containers, known as **modules**.


> the [Official Converge documentation](/docs)  is powered by its own module provider. You can view the full configuration on [Github](https://github.com/convergephp/convergephp.com/blob/master/app/Providers/Converge/DocsModuleProvider.php) 

The official Converge documentation is powered by its own module provider. You can view the full configuration on GitHub.
Each module acts as a fully isolated documentation instance, with its own:

- file path (content source),

- browser route (endpoint),

- theme settings,

- view interceptors,

- sidebar configuration,

- and more.

This architecture enables complete separation and customization of documentation experiences.

Imagine your Laravel application needs to document three different software products. You would create three distinct modules, each with its own ``ModuleProvider``, allowing you to:

- Serve each documentation set from a different URL (``/product-a/docs``, ``/product-b/docs``, ...),

- Apply custom ``themes`` per product,

- Use different markdown ``paths`` and ``clusters``,

- Add product-specific ``menus items``, ``logos``, and ``settings``.

- This modular design makes your docs ``scalable``, ``reusable``, and ``cleanly isolated``.

### Creating Module Providers 
You can scaffold a new module provider using the following Artisan command:
<x-converge::container.code>
```bash
php artisan converge:make-module DocsModuleProvider
```
</x-converge::container.code>

<x-converge::alert 
    title="you can omit ModuleProvider suffix"
/>


### Configuration Options During Generation
You can configure your module directly from the CLI.
<x-converge::container.code>
```shell
php artisan converge:make-module ConvergeDocs --path="base_path('docs-path')""
```
</x-converge::container.code>

Set the browser route:
<x-converge::container.code>
```shell
php artisan converge:make-module ConvergeDocs --path="base_path('docs')" --route="/docs"
```
</x-converge::container.code>

Once created, if your folder contains valid Markdown files, you can access your documentation at the route you specified (e.g., ``/docs``, ``localhost:8000/docs``, ``convergephp.test/docs``).

This will generate a `ConvergeDocsModuleProvider` and automatically register it in `bootstrap/providers.php`.

All module providers are placed under ``App\Providers\Converge``.

@blade
<x-converge::code.frame filename="ConvergeDocsModuleProvider.php">
```php
namespace App\Providers\Converge;

use Converge\Enums\Spotlight;
use Converge\MenuItems\MenuItem;
use Converge\MenuItems\MenuItems;
use Converge\Module;
use Converge\Providers\ModuleProvider;
use Converge\Theme\Theme;

class ConvergeDocsModuleProvider extends ModuleProvider
{
    /**
     * Register New Module Service Provider.
     */
    public function module(Module $module): Module
    {
        return $module
            ->default()
            ->id('convergedocs')
            ->routePath('/docs')
            ->in(base_path('docs'))
            ->brandLogo("Converge")
            ->theme(function (Theme $theme) {
                return $theme
                    ->spotlight(Spotlight::Strock);
            })
            ->defineMenuItems(function (MenuItems $menuItems) {
                $menuItems->add(
                    fn (MenuItem $menuItem) =>
                        $menuItem->url('https://github.com/convergephp')
                            ->openUrlInNewTab()
                            ->label('Github')
                    );

                $menuItems->add(
                    fn (MenuItem $menuItem) =>
                        $menuItem->url('https://github.com/convergephp?sponsor=1')
                            ->label('Sponsor')
                    );
            });
    }
}
```
</x-converge::code.frame>
@endblade

### Key Methods Breakdown
- `->default()` : Marks this as the default module. Used internally when no specific module is selected.
- `->id('convergedocs')`: Required. Must be unique across modules. Used to differentiate resources and cache keys.
- `->routePath('/docs')`: URL route for serving the module.
- `->in(base_path('docs'))`: Filesystem path to your documentation.  
<x-converge::alert 
    type="warning"
    title="If your docs folder is a symlink, wrap it in realpath() to resolve correctly. `(eg: realpath(base_path('docs')))`"
/>
- `->brandLogo('converge')` (optional): Optional branding logo see [branding section](/themes/branding) for more.
- `->theme(fn(Converge\Theme\Theme $theme) => ...)`: Configure colors, spotlight behavior, and visual identity see [themes docs](../customization/themes) for more.

- `->defineMenuItems(fn( Converge\MenuItems\MenuItems $menuItems) => ...)`: Easily define navigation links see [menu items docs](menu-items) for more. 

