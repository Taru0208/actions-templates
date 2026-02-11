# Node.js CI/CD Pipeline

A production-ready GitHub Actions workflow for Node.js projects.

## What it does

1. **Tests** your code across Node 18, 20, and 22 (matrix strategy)
2. **Builds** and uploads artifacts
3. **Publishes** to npm automatically when you push a version tag

## Setup

1. Copy `ci.yml` to `.github/workflows/ci.yml` in your repo
2. For npm publishing: add your `NPM_TOKEN` to repo secrets

## Triggering a release

```bash
npm version patch   # or minor, major
git push --follow-tags
```

The workflow detects the `v*` tag and publishes to npm with provenance.

## Customization

- **Change Node versions**: Edit the `matrix.node` array
- **Skip npm publish**: Remove the `publish` job entirely
- **Add linting**: Add `npm run lint` step after install
- **Change build output**: Update the `path` in upload-artifact
