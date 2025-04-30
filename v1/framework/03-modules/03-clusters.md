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
                // required and must be the first  
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->label('Documentation')
                )->default(); // required, it will use the routePath(), and in() configurations.

                // adding new cluster
                $clusters->add(
                    fn(Cluster $cluster) => $cluster
                        ->route('components') // where it lives docs/components/*
                        ->label('Components') // used on the sidebar 
                        ->in(realpath(base_path('docs/v1/components')))
                );
                // you may add cluster link as well 
                $clusters->addLink(
                    fn(ClusterLink $cluster) => $cluster
                        ->url('www.convergephp.com/blog')
                        ->label('Blog')
                );
            })
}  
```
</x-converge::container.code>