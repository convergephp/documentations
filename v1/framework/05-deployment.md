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
<x-converge::steps.step number="3" title="Update the Documentation" end last>
You can now update the docs repository independently, and any changes will be reflected immediately in the Laravel app as the symlink points to the external documentation directory.
</x-converge::steps.step>
</x-converge::steps.vertical>
@endblade

<x-converge::alert type="warning" title="whenever docs's contents changes, reindexing search and clearing the cache is required"/>

### Using github actions to apdate docs seperately

```yml
name: update docs on server

on:
  pull_request:
    types: [closed]
    branches:
      - master
  push:
    branches:
      - master

jobs:
  update-docs:
    name: Updating The Docs
    if: github.event.pull_request.merged == true || github.event_name == 'push'
    runs-on: ubuntu-22.04

    steps:
      - name: Setup SSH
        uses: appleboy/ssh-action@v1.2.2

        with:
            host: 89.117.36.52
            username: username ## user that have previliege to sshing and update docs repo
            key: ${{ secrets.SSH_PRIVATE_KEY }}
            passphrase: ${{ secrets.SSH_PASSPHRASE }}
            script: |
              set -e
              echo "Navigating to docs repo..."
              cd ~/path/docs

              echo "Pulling latest changes..."
              git pull origin master 

              echo "Re-indexing docs search..."
              cd ~/path/to/laravel-app
              php artisan converge:index-search

              echo "Reloading php fpm..."
              sudo service php8.3-fpm reload 

              echo "clearing the cache..."
              php artisan cache:clear

              echo "re-building the app cache..."
              php artisan optimize
```
<x-converge::alert type="warning" title="reloading php8.3-fpm required sudo previliges wich may not regular users have "/>

#### Securing SSH and Sudo Permissions

To keep your server secure, it’s recommended to use a single user for the Laravel app that has access to both the application and the documentation repository. The user should only be granted sudo privileges for running the following command: 

<x-converge::container.code>
```shell
    sudo service php8.3-fpm reload
```
</x-converge::container.code>

To achieve this, you need to edit the **/etc/sudoers**file. Be sure to edit it with caution, as manual changes without syntax checks can break user permissions and lock you out of your server. Instead, use the `visudo` command to edit the sudoers file safely:

<x-converge::container.code>
```shell
    sudo visudo 
```
</x-converge::container.code>

Then, add the following line at the appropriate place in the file:

<x-converge::container.code>
```shell
username ALL=NOPASSWD: usr/sbin/service php8.3-fpm reload
```
</x-converge::container.code>

This grants the `username` user permission to run the specified command without a password prompt, ensuring secure yet functional access.