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
composer require converge/converge
```
</x-converge::container.code>
</x-converge::steps.step>

<x-converge::steps.step 
        number="2" 
        title="Generate new module provider" 
        description="To start building documentation for your package or software, you need to create a **Module Provider** that will handle the configuration."
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
        description="this will show the file structure and naming convention of docs to get up and running to starts documentating right away "
    >
<x-converge::container.code>
```shell
www.example.test/docs
```
</x-converge::container.code>
</x-converge::steps.step>
<!-- STEP 4 -->
<x-converge::steps.step 
        number="4" 
        title="Visite your navigator" 
        description="Go to navigator and visite the magic"
    >
<x-converge::container.code>
```shell
www.example.test/docs
```
</x-converge::container.code>
</x-converge::steps.step>

<!-- STEP 5 -->
<x-converge::steps.step title="Keep coding" end color="primary" last>
</x-converge::steps.step>
</x-converge::steps.vertical>
@endblade





Converge comes with a pre-built command to generate the Module Provider:

```shell
php artisan converge:make-module ConvergeDocs
```

you can specify the path where your documentations resides by using the ``--path`` flag:

```shell
    php artisan converge:make-module ConvergeDocs --path=../../../docs
```

Alternatively, you can use Laravel path helpers like ``base_path():``

```shell
    php artisan converge:make-module ConvergeDocs --path="base_path('docs')"
```

to configure the route where the documentation will be accessed, use the ``--route`` flag:

```shell
    php artisan converge:make-module ConvergeDocs --path="base_path('docs')" --route="/docs"
```

At this point, if you have valid markdown files under the folder you specified in the ``--path`` flag (e.g., ``base_path('docs')``), you can test the endpoint you defined in the ``--route`` flag (e.g., ``/docs``, ``localhost:8000/docs``, ``convergephp.test/docs``).

### Further Configuration

For additional configuration options, refer to the [Module Provider](modules/module-provider) documentation.
