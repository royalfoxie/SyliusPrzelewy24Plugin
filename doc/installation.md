# Installation

## Overview:
GENERAL
- [Requirements](#requirements)
- [Composer](#composer)
- [Basic configuration](#basic-configuration)
- [Application configuration](#application-configuration)
---
ADDITIONAL
- [Known Issues](#known-issues)
---

## Requirements:
We work on stable, supported and up-to-date versions of packages. We recommend you to do the same.

| Package       | Version   |
|---------------|-----------|
| PHP           | \>=8.2    |
| sylius/sylius | ^2.0      |
| MySQL         | \>= 5.7   |
| NodeJS        | \>= 18    |

> This branch (`master-after-changes`) adds Sylius 2.x support. The upstream
> `2.1.x` tags only support Sylius 1.12/1.13 and are **not** compatible with Sylius 2.x.

## Composer:

This branch is not published on Packagist, so add the repository and require the
development branch:

```json
// composer.json
{
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/royalfoxie/SyliusPrzelewy24Plugin"
        }
    ],
    "require": {
        "bitbag/przelewy24-plugin": "dev-master-after-changes"
    }
}
```

```bash
composer update bitbag/przelewy24-plugin
```

## Basic configuration:
Add plugin dependencies to your `config/bundles.php` file:

```php
# config/bundles.php

return [
    ...
    BitBag\SyliusPrzelewy24Plugin\BitBagSyliusPrzelewy24Plugin::class => ['all' => true],
];
```

## Application configuration:
Import the plugin twig hooks so the gateway configuration fields are rendered in
the admin payment method form:

```yaml
# config/packages/przelewy24.yaml
imports:
    - { resource: "@BitBagSyliusPrzelewy24Plugin/config/config.yaml" }
```

Then clear the cache:

```bash
bin/console cache:clear
```

## Known issues
### Translations not displaying correctly
For incorrectly displayed translations, execute the command:
```bash
bin/console cache:clear
```
