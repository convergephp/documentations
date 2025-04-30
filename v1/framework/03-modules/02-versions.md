### Converge versions

converge is designed with versionned systems in mind from day one, even the path given to fresh modules are consider as default version path and can be considered as latest version,

in simplest form you can mark the version the module is using by invoking `->latestVersionLabel('label')` or `versionAs('label')` label can be any string, eg: `v1.0.0-beta.2`, ...

<x-converge::container.code>
```php
use Converge\Module;

public function module(Module $module): Module
{
    return $module
            // ...
            ->latestVersionLabel('v1.0.0-beta.2')
            // or 
            ->versionAs('v1.0.0-beta.2')
}  
```
</x-converge::container.code>

the default version URI is implicitly token from the route path you give the module in the `routePath('/docs')`, to explicitly give the latest version an suffix like `docs/v1.x`, so you can so by: 

<x-converge::container.code>
```php
use Converge\Module;

public function module(Module $module): Module
{
    return $module
            // ...
            ->versionAs('v1.0.0-beta.2') // the label is must when giving the label
            ->quietedVersionUrl('v1.x')
            // or
            ->latestVersionLabel('v1.0.0-beta.2')
            ->latestVersionUrl('v1.x')
}  
```
</x-converge::container.code>

<x-converge::alert 
    type="warning"
    title="giving url explicitly to the default version in your docs, must have a label "
/>

all of the docs above are about tunnin the default verson that came implicitly for fresh or basic modules 