# Oicana Composer Repository

This repository hosts a [Satis](https://github.com/composer/satis)-based Composer repository for Oicana PHP packages.

## 🎯 Purpose

The main [oicana/oicana](https://github.com/oicana/oicana) repository is a monorepo containing integrations for multiple languages. Since Packagist.org doesn't support packages in subdirectories, this repository provides a custom Composer repository to make PHP packages easily installable.

## 📦 Available Packages

- **oicana/oicana** - PDF templating with Typst for PHP
- **oicana/installer** - Composer plugin for automatic native extension installation

## 🚀 Usage

Add this repository to your `composer.json`:

```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://oicana.github.io/composer"
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

## 🔄 How It Works

1. **Automated Builds**: GitHub Actions automatically builds the Satis repository
2. **Git Subtree Split**: PHP packages from subdirectories are split into separate branches
3. **Static Repository**: Satis generates a static Composer repository
4. **GitHub Pages**: The static files are hosted for free on GitHub Pages
5. **Auto-updates**: Runs daily to pick up new releases

## 🛠️ Manual Build Trigger

To manually trigger a rebuild:

1. Go to [Actions](../../actions/workflows/build-and-deploy.yml)
2. Click "Run workflow"
3. Wait for the build to complete (~2-3 minutes)

## 📚 Documentation

- [Satis Documentation](https://github.com/composer/satis)
- [Oicana Documentation](https://docs.oicana.com/)
- [Composer Repositories](https://getcomposer.org/doc/05-repositories.md)

## 🤝 Contributing

This repository is automatically maintained. Package updates come from the main [oicana/oicana](https://github.com/oicana/oicana) repository.

For issues with the packages themselves, please open an issue in the main repository.

## 📄 License

Packages are licensed under PolyForm Noncommercial License 1.0.0. See individual package licenses for details.
