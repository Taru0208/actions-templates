# Auto-Versioning + Changelog

Automatically bumps your package version and generates a changelog based on conventional commits.

## How it works

1. Parses commit messages since the last tag
2. Determines the version bump type:
   - `feat:` → minor bump (0.1.0 → 0.2.0)
   - `fix:` → patch bump (0.1.0 → 0.1.1)
   - `feat!:` or `fix!:` → major bump (0.1.0 → 1.0.0)
3. Updates `package.json` version
4. Generates/prepends to `CHANGELOG.md`
5. Commits, tags, and pushes
6. Creates a GitHub Release with notes

## Setup

1. Copy `release.yml` to `.github/workflows/release.yml`
2. Use conventional commit messages in your project

## Usage

### Automatic (based on commits)

Go to Actions → Release → Run workflow

The workflow analyzes commits since the last tag and determines the bump type automatically.

### Manual override

When running the workflow, you can select a specific bump type (patch/minor/major) to override auto-detection.

## Commit convention

```
feat: add new export format        → minor bump
fix: handle empty directories      → patch bump
feat!: change CLI flag names       → major bump
docs: update README                → no bump (included in "Other" changelog section)
refactor: simplify parser logic    → no bump
```

## No dependencies

This workflow uses only shell scripting and built-in Node.js — no third-party actions for versioning or changelog generation.
