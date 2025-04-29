## Installation

Learn how to install Converge on your laravel application.

### Prerequisites

Converge  is written in PHP, JavaScript, and leverages several Laravel components. It is shipped as a Laravel package and requires the following:

- PHP 8.3+
- Laravel 11+


@blade
<x-converge::steps.vertical>
<!-- STEP 1 -->
<x-converge::steps.step 
        number="1" 
        title="Installation" 
        description="First you shoud install converge using composer"
    >
<x-converge::container.code>
```php
composer require convergephp/converge
```
</x-converge::container.code>
</x-converge::steps.step>

<x-converge::steps.step 
        number="2" 
        title="Generate new module provider" 
        description="To start building documentation for your package or software, you need to create a **Module Provider** that will handle the configurationConverge includes a dedicated command to scaffold this for you."
    >
<x-converge::container.code>
```bash
php artisan converge:make-module DocsModuleProvider
```
</x-converge::container.code>

<x-converge::alert 
    title="you can omit ModuleProvider suffix"
/>

</x-converge::steps.step>

<!-- STEP 3 -->
<x-converge::steps.step 
        number="3" 
        title="publish the starterkit" 
        description="This publishes a starter documentation structure with file conventions to help you get started quickly."
    >
<x-converge::container.code>
```php
php artisan vendor:publish --tag="converge-starterkit"
```
</x-converge::container.code>
</x-converge::steps.step>
<!-- STEP 4 -->
<x-converge::steps.step 
        number="4" 
        title="Visite your navigator" 
        description="Open your browser and navigate to the route you configured to view your documentation (/docs)"
    >
<x-converge::container.code>
```shell
www.example.test/docs
```
</x-converge::container.code>

</x-converge::steps.step>

<!-- STEP 5 -->
<x-converge::steps.step title="Keep coding" end color="primary" last/>

</x-converge::steps.vertical>
@endblade

### Configure things from the command
during module generation you can specify the path where your documentations resides by using the ``--path`` flag, you can use Laravel path helpers like ``base_path():``
<x-converge::container.code>
```shell
php artisan converge:make-module ConvergeDocs --path=../../../docs
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
is very minimal and act as starting yet but already production ready configurations 
### Further Configuration

For additional configuration options, refer to the [Module Provider](modules/module-provider) documentation.

