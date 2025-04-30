## Module Providers

### Explanation

**Module providers** are the core building blocks in Converge. They are the *only* place where you configure documentation containers, known as **modules**.

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

<x-converge::container.code>
```bash
php artisan converge:make-module DocsModuleProvider
```
</x-converge::container.code>

<x-converge::alert 
    title="you can omit ModuleProvider suffix"
/>


### Configure things from the command
during module generation you can specify the path where your documentations resides by using the ``--path`` flag, you can use Laravel path helpers like ``base_path():``
<x-converge::container.code>
```shell
php artisan converge:make-module ConvergeDocs --path="base_path('docs-path')""
```
</x-converge::container.code>


to configure the route where the documentation will be accessed, use the ``--route`` flag:

<x-converge::container.code>
```shell
php artisan converge:make-module ConvergeDocs --path="base_path('docs')" --route="/docs"
```
</x-converge::container.code>

At this point, if you have valid markdown files under the folder you specified in the ``--path`` flag (e.g., ``base_path('docs')``), you can test the endpoint you defined in the ``--route`` flag (e.g., ``/docs``, ``localhost:8000/docs``, ``convergephp.test/docs``).

actually this will generate a `ConvergeDocsModuleProvider` module provider and adding it to your service providers in `bootstrap\providers.php`, all of your module providers will be located under `App\Providers\Converge`, in our case the fresh generated module provider

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
is very minimal and act as starting yet but already production ready configurations:
- `->default()` : must hold the value of the default module across modules, it usefull when nteracting with converge internal class to work with the active module.
- `->id('convergedocs')`: a must method to seperate every module resources.
- `->routePath('/docs')`: when you consulte this documentation generated docs for this module,
- `->in(base_path('docs'))`: where you markdown's file resides.  
and other optional configurations.

<x-converge::alert 
    type="warning"
    title="when the folder's files is a symlink path is mandantory to wrap your path the `realpath()` function, `(eg: realpath(base_path('docs')))`"
/>