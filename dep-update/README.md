# Dependency Auto-Update

Weekly automated dependency update checks with PR creation.

## What it does

1. Runs every Monday at 9:00 UTC (configurable)
2. Checks `npm outdated` for all dependencies
3. Categorizes updates into major/minor/patch
4. Creates a PR with a detailed table of changes
5. Skips if everything is up to date

## Setup

1. Copy `deps.yml` to `.github/workflows/deps.yml`
2. That's it — no secrets or configuration needed

## How updates are handled

- **Patch/minor updates**: Applied automatically via `npm update`
- **Major updates**: Listed in the PR but not auto-installed (may have breaking changes)

Review the PR, run your tests, and merge when ready.

## Customization

- **Schedule**: Change the cron expression (default: Monday 9am UTC)
- **Auto-merge patches**: Add a step to auto-merge if tests pass
- **Ignore packages**: Add an `.npmrc` with ignore patterns
