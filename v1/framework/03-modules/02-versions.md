## Converge versions
Converge is built with versioned documentation systems in mind from the start. Even if you don't explicitly define a version, every module path (e.g., `/docs`),  is internally treated as a default or effectively representing the latest version of that module.

### Tunning The Default Version

#### Defining a Version Label
You can assign a version label to your module using either `->latestVersionLabel('label')` or `versionAs('label')`, The label can be any valid version string (e.g., ``v1.0.0``,`` v2.1``, ``v1.0.0-beta.2``, etc.).

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

#### Customizing the Version URL

By default, Converge extracts the version from the module’s route path (e.g., `/docs` is treated as the latest version).
If you want to explicitly define a friendly suffix (like `/docs/v1.x`) for the latest version, you must also set a version label.

You can use either `->quietedVersionUrl()` or `->latestVersionUrl()`:

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

@blade
<x-converge::alert type="warning">
Explicit version URLs must include a version label. it may used for versions dropdown in top navbar
</x-converge::alert>
@endblade

>The examples above focus on customizing the default version — which is automatically inferred for basic or newly registered modules.

### Adding More Versions
Before you can define additional versions, you must first assign a version label to the default version. see [Defining a Version Label](#content-defining-a-version-label)

To declare multiple versions, use the `defineVersions()` method:

```php
use Converge\Module;

public function module(Module $module): Module
{
    return $module
            // ...
            ->versionAs('v4.0.0-beta.2') // required
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
                        ->asAbsolute() // optional
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

Inside the ``defineVersions()`` callback, you have access to two core methods:

#### Local Versions

- `->add()` : Registers a local version stored and rendered by Converge.
this function accept a closure as well and you need to setup the three buidling blocks needed by each version *label*,*route*,*contents*:

```php
use Converge\Versions\Version;
$versions->add(
    fn(Version $version): Version => $version
        ->label('v2.0.0') // the label of the version (used in the dropdown)
        ->route('v2.x')  // Used in URL: /docs/v2.x
        ->in(base_path('docs/v2')) // Path to the content
    );
```

The route given to each version is going to be suffixed friendly to the routepath given in the module eg: `docs/v2.x`, unless you invoke the `->asAbsolute()` method, so the version will accessed on `/v2.x`:

```php
use Converge\Versions\Version;
$versions->add(
    fn(Version $version): Version => $version
         // previous 3 methods...
         {+->asAbsolute()+}
    );
```

> each versions may have it's own clusters you may refer to [clusters docs](clusters)

#### External Versions

You may using converge to documente only latest versions of your software, and older versions may still in external places, converge also handle that easily for you, so to add an legacy, or external links version you may need to use `->addLink()` this function need 2 required building blocks `url()`, and `label()` :

```php
use Converge\Versions\VersionLink;

$versions->addLink(
    fn(VersionLink $version) => $version
        ->label('V1.0.0') // required
        ->url('https://legacy-docs.com/docs') // required
    );
```

### Version Dropdown Sorting

Converge will reverse the order you use during adding versions and build the dropdown, you may changes the sort of the versions by using the `->sort()`: method.

```php
use Converge\Versions\VersionLink;
use Converge\Versions\Version;

$versions->add(
fn(Version $version): Version => $version
        // ...
        {+ ->sort(2) +} // any int
        // ...
);

$versions->addLink(
    fn(VersionLink $version) => $version
        // ...
        {+ ->sort(3) +} // any int
        // ...
);

```
