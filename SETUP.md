# Setup Instructions

## Initial Setup

### 1. Push to GitHub

Create a repository and push to it.

### 2. Enable GitHub Pages

1. Go to repository Settings → Pages
2. Source: "GitHub Actions"
3. Save

### 3. Configure Repository Dispatch Permission

The workflow needs permission to be triggered from the oicana/oicana repository.

**Option A: Use GitHub App or PAT (Recommended)**
1. Create a Personal Access Token with `repo` scope
2. Add it as a secret in the oicana/oicana repository:
   - Go to oicana/oicana Settings → Secrets and variables → Actions
   - Create new secret: `COMPOSER_REPO_TOKEN`
   - Use this token in the trigger workflow

**Option B: Use GITHUB_TOKEN (Simpler but limited)**
The default `GITHUB_TOKEN` can only trigger workflows in the same repository. You'll need to manually trigger rebuilds or use the scheduled daily build.

### 4. Update the Trigger Workflow (if using PAT)

In `/home/niklas/code/oicana/.github/workflows/trigger-composer-repo-update.yml`, replace:
```yaml
-H "Authorization: token ${{ secrets.GITHUB_TOKEN }}" \
```

with:
```yaml
-H "Authorization: token ${{ secrets.COMPOSER_REPO_TOKEN }}" \
```

### 5. Initial Build

Manually trigger the first build:
1. Go to https://github.com/oicana/composer/actions
2. Click on "Build and Deploy Satis Repository"
3. Click "Run workflow"
4. Wait 2-3 minutes for completion

### 6. Verify

After the workflow completes:
1. Check that GitHub Pages deployed successfully
2. Visit https://<org>.github.io/composer
3. You should see a Composer repository page with your packages

### 7. Test Installation

Create a test project:
```bash
mkdir test-oicana-php
cd test-oicana-php
composer init --no-interaction
```

Add to `composer.json`:
```json
{
    "repositories": [
        {
            "type": "composer",
            "url": "https://<org>.github.io/composer"
        }
    ],
    "require": {
        "oicana/oicana": "^0.1.0-alpha.1"
    }
}
```

Then:
```bash
composer install
```

## Future Releases

When you release a new PHP version in oicana/oicana:

1. Tag: `git tag oicana_php-v0.1.0-alpha.2`
2. Push: `git push --tags`
3. The Satis repository will automatically rebuild (via repository_dispatch trigger)
4. Users can `composer update` to get the new version

## Manual Rebuild

If automatic triggers aren't working:
1. Go to https://github.com/oicana/composer/actions
2. Run workflow manually
