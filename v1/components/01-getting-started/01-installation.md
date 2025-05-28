---
title: Installation
---

# Getting Started

Converge Components is a collection of specialized Blade components designed specifically for documentation management. These components integrate seamlessly with the Converge Framework to create consistent, professional technical documentation with advanced theming capabilities.

## Requirements


Converge Components are pure Laravel blade components enhanced with the Converge theming system. The package has the following dependencies:

- PHP >= 8.3
- Laravel >= 11.x
- [Converge]('https://convergephp.com/docs/intallation') Framework

## Installation

@blade
<x-converge::steps.vertical>

<!-- STEP 1 -->
<!-- <x-converge::steps.step number="1" title="Purchase a license">
<x-converge::card
    url="https://convergephp.com/toolkits/components"
    title="Purchase Converge Components"
    icon="iconsax-bul-card-pos"
    color="primary"
    description="Purchase a license for Converge Components"/>
</x-converge::steps.step> -->

<!-- STEP 2 -->
<!-- <x-converge::steps.step number="1" title="Add Converge Components repository to your composer.json file">
<x-slot:description>
You may install Converge Components as a Composer package via our private Satis repository. To get started, add the following repository to your application's composer.json file:
```json
{
    "repositories": [{
        "type": "composer",
    "url": "https://packagist.convergephp.com"
  }]
}
```
</x-slot:description>
</x-converge::steps.step> -->

<!-- STEP 3 -->
<x-converge::steps.step number="1" title="Install">
<x-slot:description>

```bash
composer require convergephp/blade-components
```
</x-slot:description>

</x-converge::steps.step>

<!-- STEP 4 -->
<x-converge::steps.step title="Publishing assets" last color="success">
<x-slot:description>
Run the command below at the root of your Laravel project. This will create a `public/vendor/converge` directory in your public directory.

```bash
php artisan vendor:publish --tag=converge-components-assets
```
</x-slot:description>
</x-converge::steps.step>

</x-converge::steps.vertical>
@endblade

**Now, you can use components within your markdown files.**

## Updating Converge Components

Running `composer update` at the root of your project will pull in the latest version of Converge Components.

```bash
composer update convergephp/blade-components
```

@blade
<x-converge::alert type="warning">
Always publish assets when you update to a new version of Converge Components
</x-converge::alert>
@endblade


To automate publishing of the Converge Components files every time you run `composer update`, you can add the following lines to your `composer.json` file under the `scripts` key.

```json
"scripts": {
"post-update-cmd": [
    {~ "@php artisan vendor:publish --tag=another-published-assest --force",~}
    "@php artisan vendor:publish --tag=converge-components-assets --force",
    {~"@php artisan vendor:publish --tag=any-other-assets --force",~}
],
}
```
