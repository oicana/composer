# Oicana Composer Repository

_https://composer.oicana.com/_

This repository hosts a [Satis](https://github.com/composer/satis)-based Composer repository for Oicana PHP packages.

## Available Packages

- **oicana/oicana** - PDF templating with Typst for PHP
- **oicana/installer** - Composer plugin for automatic native extension installation

## Usage

Add this repository to your `composer.json`:

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://composer.oicana.com/composer"
        }
    ],
    "require": {
        "oicana/oicana": "^0.1.0-alpha.1"
    }
}
```

Then install as usual:

```bash
composer install
```

## License

Packages are licensed under PolyForm Noncommercial License 1.0.0. See individual package licenses and the [oicana website][oicana-website] for details.


[oicana-website]: https://oicana.com
