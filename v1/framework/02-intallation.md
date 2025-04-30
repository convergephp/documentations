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




### Further Configuration




For additional configuration options, refer to the [Module Provider](modules/module-provider) documentation.

