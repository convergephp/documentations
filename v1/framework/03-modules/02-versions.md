## Converge versions
Converge is built with versioned documentation systems in mind from the start. Even if you don't explicitly define a version, every module path (e.g., `/docs`),  is internally treated as a default or effectively representing the latest version of that module.

### Tunning The Default Version

#### Defining a Version Label
You can assign a version label to your module using either `->latestVersionLabel('label')` or `versionAs('label')`, The label can be any valid version string (e.g., ``v1.0.0``,`` v2.1``, ``v1.0.0-beta.2``, etc.).

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
#### Customizing the Version URL

By default, Converge extracts the version from the module’s route path (e.g., `/docs` is treated as the latest version).
If you want to explicitly define a friendly suffix (like `/docs/v1.x`) for the latest version, you must also set a version label.

You can use either `->quietedVersionUrl()` or `->latestVersionUrl()`:

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
    title="Explicit version URLs must include a version label. it may used for versions dropdown in top navbar"
/>

>The examples above focus on customizing the default version — which is automatically inferred for basic or newly registered modules.

### Adding More Versions
before adding new versions instance you need the default version a [label placeholder](#content-defining-a-version-label)

to effectively add new more version you need to invoke the `defineVersions()` method:

<x-converge::container.code>
```php
use Converge\Module;

public function module(Module $module): Module
{
    return $module
            // ...
            ->versionAs('v4.0.0-beta.2') // the label is must when giving the label
            ->quietedVersionUrl('v4.x') // optional
            // or
            ->latestVersionLabel('v4.0.0-beta.2')
            ->latestVersionUrl('v4.x') // optional
            // ..
            ->defineVersions(function (Versions $versions) {
                
                $versions->add(
                    fn(Version $version) => $version
                        ->label('V3.0.0')
                        ->route('v3.x')
                        ->in(base_path('docs/V3'))
                );

                $versions->add(
                    fn(Version $version): Version => $version
                        ->label('v2.0.0')
                        ->route('v2.x') 
                        ->asAbsolute()
                        ->in(base_path('docs/v2'))
                );
                
                $versions->addLink(
                    fn(VersionLink $version) => $version
                        ->label('V0.0.0')
                        ->url('www.legacy-docs.com/docs')
                );
            });
}  
```
</x-converge::container.code>

the closure inside `->defineVersions()` is used to setup the versions system 
- you can add local versions that will consumed by the treated module  by using `->add()` 
- pointing to legacy documentation versions or any external links by using `->addLink()` 