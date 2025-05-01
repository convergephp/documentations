## Converge Clusters

### Default Cluster

Clusters are logical groupings of documentation files within a version of a module. Each version can have multiple clusters, and clusters typically represent major content areas like:

- 📘 Documentation
- 📦 Components
- 📂 Tutorials
- 📑 API References
- ...and more

> Each version in Converge can contain multiple clusters, and even the silent or "quiet" default version may includes its own clusters.

When a module is freshly initialized and no versions or clusters are explicitly defined, Converge will automatically:

- Provide a quiet version, based on the module’s root path

- Attach a default cluster to that version, ensuring structure is always in place

You can make the default cluster visible in the sidebar by simply assigning to it the label .

Let’s see how easy it is to define clusters in Converge:

<x-converge::container.code>

```php
use Converge\Module;

public function module(Module $module): Module
{
    return $module
            // ...
             ->defineClusters(function (Clusters $clusters) {
                // Required: complete the setup of default cluster first
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->label('Documentation')  // This Displayed in sidebar
                )->default(); // Uses routePath() and in() defined in module() level as configurations.

                 // Add an additional cluster
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->route('components') // Maps to docs/components/*
                        ->label('Components') //  Displayed in the sidebar
                        ->in(realpath(base_path('docs/components')))
                );

                // Add a link-type cluster
                $clusters->addLink(
                    fn(ClusterLink $cluster) => $cluster
                        ->url('www.convergephp.com/blog')
                        ->label('Blog')
                );
            })
}
```

</x-converge::container.code>

#### Why default Clusters setup needed ?

Whenever you need to add a cluster for a specific version, you must set up a default cluster by marking it with  `->default()`, A default cluster behaves like a regular cluster but, by default, uses the path provided to the version itself to serve its contents.

<x-converge::alert title="in fresh module it will use the path provided to the `in()` to serve contents "/>

<x-converge::container.code>

```php
 $clusters->add(
        fn(Cluster $cluster) => $cluster
            ->label('Documentation')
    )->default();
```

</x-converge::container.code>

#### Adding More clusters

After setting up your default cluster and assigning it a label, it's time to add more clusters. Each cluster consists of three essential building blocks:
-  _URL_
-  _Label_
- _Path Contents_

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            ->route('components') // Defines the cluster route (docs/components)
            ->label('Components') // The label used in the sidebar
            ->in(base_path('docs/components'))  // Path to the contents
    );
```

</x-converge::container.code>


you may need to changes the icon ([see how to add icons in converge](../04-customization/icons)) of that cluster using `icon()` method:
<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            // ...
            {+->icon(fn() => svg('iconsax-bul-3dcube', 'h-5 w-5'))+}
    );
```
</x-converge::container.code>

you may need to changes the order of the cluster by using `->sort()` method as accept any `int/Closure`:

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            //  ...
            {+->sort(0)+}
    );
```
</x-converge::container.code>

### Tunning Cluser Url
by default the default cluster of each version (including the quieted version) will be accessed in the URL defined for that version, and for additional clusters they will suffix the URL defined on the `route()` method eg: `docs/components`, `docs/v3.x/guide`..., you how ever converge let's you define how your cluster's URL will relative to:

<x-converge::alert title="this configurations works for explicit defained versions"/>
#### Absolute Url 
- to make you cluster URL absolute to `/` URL you may use `absoluteUrl()` method:

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            //  ...
            {+->absoluteUrl()+}
    );
```
</x-converge::container.code>
so now the URL given to the `route()` eg: `route('guide')` method will accessible in absolute manner`/guide` ...

#### Absolute Url With Module Url

- to make you cluster Url relative to your module Url (escape the version Url) eg: `docs/v4.x/guide` to `/docs/quide` Url you may use `absoluteUrlWithModuleUrl()` method:

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            //  ...
            {+->absoluteUrlWithModuleUrl()+}
    );
```
</x-converge::container.code>

#### Absolute Url With Module Url

- to make you cluster URL absolute to your module Url (escape the version Url) eg: `docs/v4.x/guide` to `/V4.x/quide` Url you may use `absoluteUrlWithModuleUrl()` method:

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            //  ...
            {+->absoluteUrlWithVersionUrl()+}
    );
```
</x-converge::container.code>