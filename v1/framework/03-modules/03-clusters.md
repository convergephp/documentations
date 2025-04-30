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
                // Required: Define the default cluster first
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->label('Documentation')  // This label makes it visible in the sidebar
                )->default(); // Uses routePath() and in() defined in module() level as configurations.

                 // Add an additional cluster
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->route('components') // Maps to docs/components/*
                        ->label('Components') //  Displayed in the sidebar
                        ->in(realpath(base_path('docs/v1/components')))
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

every time you need to add a cluster for a specific version you need to setup the default cluster by marking it with `->default()`, it's a regular cluster but as default it will use the `path` provided to the version itself to serve contents

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

after you setup you default cluster, and giving it a label now it's time for you add more clusters, each cluster had 3 essentiel building blocks: _URL_, _Label_,_Path Contents_.

<x-converge::container.code>

```php
   $clusters->add(
        fn(Cluster $cluster) => $cluster
            ->route('components')
            ->label('Components')
            ->in(base_path('docs/v1/components'))
    );
```

</x-converge::container.code>
