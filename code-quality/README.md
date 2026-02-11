# Code Quality Check

Automated linting, formatting, and test coverage checks on every pull request.

## What it does

1. **Lint check**: Runs ESLint (if configured)
2. **Format check**: Runs Prettier to verify formatting
3. **Test coverage**: Runs tests with coverage and comments the results on the PR

## Setup

1. Copy `quality.yml` to `.github/workflows/quality.yml`
2. Ensure your `package.json` has a `lint` script (optional)
3. Ensure ESLint and/or Prettier are in devDependencies (optional)

The workflow gracefully skips checks when tools aren't configured — you can adopt linting and formatting incrementally.

## Coverage reporting

The workflow tries multiple approaches to generate coverage:
1. `npm run test:coverage` (custom script)
2. `npm test -- --coverage` (Jest/Vitest flag)
3. `npx c8 npm test` (c8 coverage tool)

If coverage data is found, it posts a comment on the PR with a coverage table.

## Customization

- **Coverage threshold**: Add a step that fails if coverage is below a target
- **File patterns**: Change the Prettier glob to match your project structure
- **Auto-fix**: Add a step that runs `eslint --fix` and commits
