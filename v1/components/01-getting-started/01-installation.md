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

## Install

@blade
<x-converge::steps.vertical>

<!-- STEP 1 -->
<x-converge::steps.step number="1" title="Purchase a license">
<x-converge::card
    url="https://convergephp.com/toolkits/components"
    title="Purchase Converge Components"
    icon="iconsax-bul-card-pos"
    color="primary"
    description="Purchase a license for Converge Components"/>
</x-converge::steps.step>

<!-- STEP 2 -->
<x-converge::steps.step number="2" title="Add Converge Components repository to your composer.json file" description="You may install Converge Components as a Composer package via our private Satis repository. To get started, add the following repository to your application's composer.json file:">
<x-converge::container.code>
```json
{
  "repositories": [{
    "type": "composer",
    "url": "https://packagist.convergephp.com"
  }]
}
```
</x-converge::container.code>
</x-converge::steps.step>

<!-- STEP 3 -->
<x-converge::steps.step number="3" title="Install">
<x-slot:description>
<ul>
    <li style="line-height: 1.8rem">
    At the root of your Laravel project, run the following command in your console terminal to pull in the package.
    </li>
    <li style="line-height: 1.8rem">
    When running `composer require converge/converge-components`, you will be prompted to provide a username and password. Use the email address associated with your Converge account as the username and your <strong>license key</strong> as the password. These credentials will authenticate your Composer session and grant you permission to download the Converge Components source code.
    </li>
</ul>
</x-slot:description>

<x-converge::container.code>
```bash
composer require converge/converge-components
```
</x-converge::container.code>
</x-converge::steps.step>

<!-- STEP 4 -->
<x-converge::steps.step title="Publishing assets" last color="success">
<x-slot:description>
    <p style="line-height:1.8rem">Run the command below at the root of your Laravel project. This will create a <x-converge::code>public/vendor/converge</x-converge::code> directory in your public directory.</p>
</x-slot:description>
<x-converge::container.code>
```bash
php artisan vendor:publish --tag=converge-components-assets
```
</x-converge::container.code>
</x-converge::steps.step>

</x-converge::steps.vertical>
@endblade

**Now, you can use components within your markdown files.**

## Updating Converge Components

Running `composer update` at the root of your project will pull in the latest version of Converge Components.

<x-converge::container.code>
```bash
composer update converge/converge-components
```
</x-converge::container.code>


<x-converge::alert type="warning" title="Always publish assets when you update to a new version of Converge Components"/>

To automate publishing of the Converge Components files every time you run `composer update`, you can add the following lines to your `composer.json` file under the `scripts` key.

<!-- @blade -->
<x-converge::container.code>
```json
"scripts": {
"post-update-cmd": [
    {~ "@php artisan vendor:publish --tag=another-published-assest --force",~}
    "@php artisan vendor:publish --tag=converge-components-assets --force",
    {~"@php artisan vendor:publish --tag=any-other-assets --force",~}
],
```
</x-converge::container.code>
