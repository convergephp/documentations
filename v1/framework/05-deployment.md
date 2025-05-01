---
title: 'Using Converge in Production'
---

# Deployment
Converge is a lightweight framework designed to manage documentation and shipped as a laravel package. It works by leveraging flat files, typically Markdown files, to structure and display documentation content. Its simplicity and modularity make it an excellent tool for organizing and serving documentation within Laravel applications.

## Built In Docs
If your documentation is part of a Laravel application, there is no need for additional setup when deploying Converge. Converge integrates seamlessly with your app and will serve the documentation directly from the defined file paths. However, whenever you update the documentation structure (e.g., adding/removing files) or modify the content itself (e.g., editing a Markdown file), you need to ensure that the search index is rebuilt, and the cache is cleared to reflect the changes.

<x-converge::alert title="This use case is ideal for simpler documentation scenarios, such as API documentation or catalog-based docs, where content and structure don't change frequently."/>

**rebuild the search index for new changes to take effect:**

<x-converge::container.code>
```bash
php artisan converge:index-search
```
</x-converge::container.code>

**clear the cache to destroy the files tree cache**
<x-converge::container.code>
```bash
php artisan converge:index-search
```
</x-converge::container.code>

## When Docs in sperate docs
In many real-world use cases, larger frameworks or packages maintain separate repositories specifically for their documentation. 

This is typically done to have more granular control over the content, especially in cases where documentation changes frequently such as fixing typos, improving the material etc. 

### Using Git Submodule


you may make the docs available in your laravel app by leveraging [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) feature in git so you will have repository of your docs inside the repositories of your actuall app without any history dependecy and already it's a production setup. 

<x-converge::alert title="this approach introduce a big mess in zero downtime architecture since you can't update the docs repository only, so you need a new deployment for every docs changes and since it get rid of git when building the artifact"/>

but you can use it in local dev, and in production leverage the symlinks approach this is actually how we manage documentations on converge 

### Using Symlinks (Recomended)
this is the cleanest and most scalable approach in production and even can be used in local. This method allows you to manage your documentation repository independently, without directly integrating it into your Laravel app's codebase. Symlinks provide a dynamic link between the app and documentation, which makes it much easier to manage and update the documentation content without affecting the application itself.
To set up symlinks, follow this example structure:

```
        laravel-app/
            app/*
            bootstrap/*
            config/*
            docs/ --> symlink to the external docs repository
            database/*
            storage/*
            ...
         docs/ (separate documentation repository)
```

#### Steps to Set Up Symlinks:

@blade
<x-converge::steps.vertical>

<!-- STEP 1 -->
<x-converge::steps.step number="1" title="Clone the Documentation Repository">
    First, clone the documentation repository into a separate directory outside your main application. This ensures that the documentation is managed independently from the app's codebase.
</x-converge::steps.step>

<!-- STEP 2 -->
<x-converge::steps.step number="2" title="Create the Symlink" description="Create a symlink within your Laravel app that points to the cloned documentation repository. You can do this using the following command:">
<x-converge::container.code>
```shell
ln -s /path/to/docs /path/to/your/laravel-app/docs
```
</x-converge::container.code>
</x-converge::steps.step>

<!-- STEP 3 -->
<x-converge::steps.step number="3" title="Update the Documentation">
You can now update the docs repository independently, and any changes will be reflected immediately in the Laravel app as the symlink points to the external documentation directory.
</x-converge::steps.step>
</x-converge::steps.vertical>
@endblade