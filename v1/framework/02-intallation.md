## Installation

Learn how to install Converge on your laravel application.

### Prerequisites

Converge  is written in PHP, JavaScript, and leverages several Laravel components. It is shipped as a Laravel package and requires the following:

- PHP 8.3+
- Laravel 11+


@blade
<x-converge::steps.vertical>
<x-converge::alert>
since converge still in beta, make sure your Composer minimum stability is set to `beta`
</x-converge::alert>
<!-- STEP 1 -->
<x-converge::steps.step
        number="1"
        title="Installation">

<x-slot:description>
First you shoud install converge using composer 


```php
composer require convergephp/converge
```
</x-slot:description>

</x-converge::steps.step>

<!-- STEP 2 -->
<x-converge::steps.step
        number="2"
        title="Generate new module provider">

<x-slot:description>
To start building documentation for your package or software, you need to create a **Module Provider** that will handle the configurationConverge includes a dedicated command to scaffold this for you.
```bash
php artisan converge:make-module DocsModuleProvider
```
</x-slot:description>

<x-converge::alert>
you can omit ModuleProvider suffix
</x-converge::alert>

</x-converge::steps.step>


<!-- STEP 3 -->
<x-converge::steps.step
        number="3"
        title="publish the starterkit">

<x-slot:description>
**This publishes a starter documentation structure with file conventions to help you get started quickly.**

```php
php artisan vendor:publish --tag="converge-starterkit"
```
</x-slot:description>

</x-converge::steps.step>


<!-- STEP 4 -->
<x-converge::steps.step
        number="4"
        title="Visite your navigator">

<x-slot:description>
**Open your browser and navigate to the route you configured to view your documentation (/docs).**
```shell
www.example.test/docs
```
</x-slot:description>

</x-converge::steps.step>

<!-- STEP 5 -->
<x-converge::steps.step title="Keep coding" end color="primary" last/>

</x-converge::steps.vertical>
@endblade




### Further Configuration


For additional configuration options, refer to the [Module Provider](modules/module-provider) documentation.
