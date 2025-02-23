## Installation

Learn how to install Converge on your laravel application.

### Prerequisites

Converge v1.x is written in PHP, JavaScript, and leverages several Laravel components. It is shipped as a Laravel package and requires the following:

- PHP 8.3+
- Laravel 11+

```shell
    composer require convergephp/converge
```
### Generate the Module Provider

To start building documentation for your package or software, you need to create a **Module Provider** that will handle the configuration.

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

