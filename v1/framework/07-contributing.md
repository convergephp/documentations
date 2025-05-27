---
title: Contributing
---

> Parts of this guide are taken from [filament's contribution guide](https://filamentphp.com/docs/3.x/support/contributing), and it served as very useful inspiration.

## Reporting bugs

If you find a bug in Converge, please report it by opening an issue on our [GitHub repository](https://github.com/convergephp/converge/issues/new/choose). Before opening an issue, please search the [existing issues](https://github.com/convergephp/converge/issues?q=is%3Aissue) to see if the bug has already been reported.

Please make sure to include as much information as possible, including the version of packages in your app. You can use this Artisan command in your app to open a new issue with all the correct versions pre-filled:

```bash
php artisan converge:make-issue
```

When creating an issue, we require a "reproduction repository". **Please do not link to your actual project**, what we need instead is a _minimal_ reproduction in a fresh project without any unnecessary code. This means it doesn't matter if your real project is private / confidential, since we want a link to a separate, isolated reproduction. This allows us to fix the problem much quicker. **Issues will be automatically closed and not reviewed if this is missing, to preserve maintainer time and to ensure the process is fair for those who put effort into reporting.** If you believe a reproduction repository is not suitable for the issue, which is a very rare case, you may still open regular issue but please explain it well. 

Remember, bug reports are created in the hope that others with the same problem will be able to collaborate with you on solving it. Do not expect that the bug report will automatically see any activity or that others will jump to fix it. Creating a bug report serves to help yourself and others start on the path of fixing the problem.

## Development of new features

If you would like to propose a new feature or improvement to Converge, you may use our [discussion form](https://github.com/convergephp/converge/discussions) hosted on GitHub. If you are intending on implementing the feature yourself in a pull request, we advise you to mention `@charrafimed` or `@Ayoubhj866` in your feature discussion beforehand and ask if it is suitable for the framework to prevent wasting your time.

## Developing with a local copy of Converge

If you want to contribute to the converge framework, then you may want to test it in a real Laravel project:

- Fork [the GitHub repository](https://github.com/convergephp/converge) to your GitHub account.
- Create a Laravel app locally.
- Clone your fork in your Laravel app's root directory.
- In the `/packages/converge` directory, create a branch for your fix, e.g. `fix/error`.

Install the packages in your app's `composer.json`:

```json
{
    // ...
    "require": {
        "convergephp/converge": "*",
    },
    "minimum-stability": "dev",
    "repositories": [
        {
            "type": "path",
            "url": "packages/*"
        }
    ],
    // ...
}
```

Now, run `composer update`.

Once you're finished making changes, you can commit them and submit a pull request to [the GitHub repository](https://github.com/convergephp/converge).



## Security vulnerabilities

If you discover a security vulnerability within Converge, please email converge team via [convergephp@gmail.com](mailto:convergephp@gmail.com). All security vulnerabilities will be promptly addressed.

## Code of Conduct

Please note that Converge is released with a [Contributor Code of Conduct](https://github.com/convergephp/converge/blob/master/CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.
