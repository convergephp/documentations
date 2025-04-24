---
title: Blade Components overview
---
**Blade Components for Converge Documentation Generator**

Converge is a powerful documentation generator that helps you create high-quality documentation for your projects. To make it even more
effective, we've designed a set of Blade components specifically for use with Converge. These components are tailored to provide a
seamless integration experience and help you create stunning documentation with ease.

**Overview**

The Blade Components package is a collection of pre-built HTML templates that can be used to enhance the visual appeal and functionality
of your Converge-generated documentation. With this package, you'll have access to a range of standard components designed to make your
documentation more engaging, informative, and easy to navigate.

### Standard Components

Here's an overview of the standard Blade components included in this package:

#### Card Component
A versatile component that can be used to display information, code examples, or even entire sections of content. Cards are fully
customizable and can be styled to match your brand's design guidelines.

#### Code Blocks
Highlight important code snippets and make them easy to read with our Code Blocks component. This component supports multiple
programming languages and includes features like syntax highlighting, line numbers, and collapsible blocks.

#### Alert Component
Draw attention to important information or warnings with our Alert component. Alerts can be used to highlight key messages, provide
feedback, or indicate potential issues.

#### Table of Contents (TOC) Component
Easily create a table of contents for your documentation using this component. The TOC is fully customizable and can be styled to match
your brand's design guidelines.

#### Icon Component
Add visual interest to your documentation with our Icon component. This component includes a range of pre-designed icons that can be
used to illustrate key concepts, highlight important information, or add decorative flair.

#### Callout Component
Use our Callout component to draw attention to specific information or highlights within your documentation. Callsouts are fully
customizable and can be styled to match your brand's design guidelines.

#### Divider Component
Add visual separation between sections of content with our Divider component. This component includes a range of styles, from simple
lines to decorative separators.

### Benefits

By using the Blade Components package with Converge, you'll enjoy:

* **Consistent branding**: Use pre-designed components that match your brand's design guidelines to ensure consistency across all your
documentation.
* **Improved readability**: Enhance the readability of your code examples and content with customizable formatting options.
* **Better organization**: Create a clear and organized structure for your documentation using our Table of Contents component.

### How to Use

To use the Blade Components package with Converge, follow these simple steps:

1. Install the package by running the following command  in your project directory.
```php
composer require converge/converge-components
```
2. Publish the assets to be discovered by converge framwork :
```php
php artisan vendor:publish --tag="converge-components-assets"
```
this commande will generate a css and js files within your root public folder.

3. Now you can use components inside yout markdown fils, and converge will rendred it.

### Conclusion

The Blade Components package is designed to help you create high-quality documentation for your projects using Converge. With its range
of standard components, you'll be able to enhance the visual appeal and functionality of your documentation, making it easier for
readers to engage with and understand your content.
