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


## Security Concerns

While this is a powerful feature in Converge, it can quickly become a security nightmare if not used with caution. It introduces serious security risks when rendering dynamic or user-controlled content.

For example, if you use the divide component like this:

```php
<x-converge::divide
    title="available methods in SidebarItem"
    color="success"
>
{{ file_get_contents(base_bath('.env'))}}
</x-converge::divide>
```
You’ve now exposed your entire .env file to the public. All environment variables are fully visible, including secrets and database credentials.

This feature should only be used when trusted administrators are managing the documentation content.


@blade
<x-converge::alert type="warning">
    Don't use this in user driven contents 
</x-converge::alert>
@endblade

## Upcoming Solution in Converge Core

We're actively working on a solution. Our current direction involves sandboxing these components or building a minimal Blade-like engine that supports only the Converge component syntax. The goal is to keep the developer experience identical to Blade while restricting access to dangerous PHP functions.

## Your assignment

- Ensure that all documentation content is managed exclusively by trusted administrators.

- Carefully review all pull requests to the documentation repository — especially those modifying markdown files or using dynamic components.

- Audit your entire documentation to confirm that no sensitive logic, data access, or insecure function calls (e.g., file_get_contents, exec, eval) are exposed through components.

- Always remember: when using these components, there is no security layer between your application logic and the markdown content. Any misuse directly compromises your environment.