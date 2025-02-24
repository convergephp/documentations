## Overview

The **Converge Framework** is designed to **streamline documentation management** for all types of projects. Whether you're managing:

- Open-source packages
- Private packages
- Commercial software
- Or any project requiring comprehensive documentation

Converge simplifies the process and allows you to focus on **writing actual content** in minutes, rather than spending time designing or building a documentation website from scratch.  
the [converge](https://convergephp.com) docs are managed by converge
With Converge, you can:

- Quickly set up a professional and structured documentation system.
- Avoid repetitive tasks by leveraging ready-made components and configurations.
- Benefit from a modular architecture tailored to developers.

By focusing on content creation rather than infrastructure, Converge empowers developers to deliver high-quality documentation with minimal effort.

### Multi-Module Support

Converge lets you write fully separate, styled logic documentation for multiple packages or software projects within the same Laravel application. This is achieved using the [module](/modules) system, allowing you to:

- Create distinct modules for different projects.
- Maintain a unified system while keeping each project isolated.
- Quickly navigate and manage your docs from a central dashboard.

### Versioning Built-In

Do you have multiple versions of your package or software?

Converge is built with versioning in mind. You can maintain multiple versions of your documentation, with each version having its own dedicated content. Converge handles the complexity for you with simple configurations in the [module provider](/modules/module-provider).

### Blade Component Support

Converge scans your markdown files and renders any Blade component. It also comes with a set of pre-styled components, ranging from tips to custom code blocks.

Here’s a sneak peek at some of the components:

```html
this is in you mardown file
<x-converge::tips
  label="this is a self closing one in the multiple line"
  class="text-purple-500"
  variant="good"
/>
```

this what it generate:

<x-converge::tips
label="this is a self closing one in the multiple line"
class="text-purple-500"
variant="good"
/>

Magic, right? We’ve built a full Markdown extension for the [commonmark package](https://commonmark.thephpleague.com/) to do that for ya.

We’ve included more than **12 pre-built components** for you, which are highly integrated with the design system. Plus, you can create any custom Blade component you want.

### dark/light mode

Converge comes with built-in Light/Dark Mode support, allowing you to provide a seamless experience for users regardless of their preferences. The theme automatically switches based on system settings or manual selection, ensuring readability and comfort in any environment.

### Why Converge?

With Converge, you’re not just documenting — you’re building a powerful, scalable, and developer-focused system that works for you.

- Write less boilerplate and focus on what matters most: your content.
- Manage multiple projects, versions, clusters, and themes with ease.
- Leverage a growing ecosystem of prebuilt components to reduce complexity.
- Ensure a smooth, user-friendly experience for your documentation readers.

### Who is Behind Converge

The **Converge Framework** was founded by:
- [Charrafi Mohamed](https://github.com/CharrafiMed).
- [Ayoub El Hajji](https://github.com/Ayoubhj866) 
