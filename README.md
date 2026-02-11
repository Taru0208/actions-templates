# GitHub Actions Template Suite

5 production-ready GitHub Actions workflows for Node.js projects. Copy, paste, customize — no third-party marketplace actions for core logic.

## Templates

| Template | What it does | File |
|----------|-------------|------|
| [Node.js CI/CD](nodejs-ci/) | Matrix testing, build artifacts, npm publish on tag | `ci.yml` |
| [Auto-Versioning](auto-version/) | Conventional commit parsing, version bump, changelog generation | `release.yml` |
| [Dependency Updates](dep-update/) | Weekly outdated checks, categorized PR creation | `deps.yml` |
| [Code Quality](code-quality/) | ESLint + Prettier + test coverage with PR comments | `quality.yml` |
| [Deploy to VPS](deploy-vps/) | SSH deployment with zero-downtime + automatic rollback | `deploy.yml` |

## Philosophy

- **No unnecessary dependencies**: Workflows use shell scripting and built-in Node.js where possible
- **Copy-paste ready**: Each template works standalone — no shared libraries needed
- **Well-documented**: Every template includes a README with setup instructions and customization tips
- **Opinionated defaults**: Sensible settings out of the box, easy to change

## Quick start

1. Pick the templates you need
2. Copy the `.yml` files to `.github/workflows/` in your repo
3. Add any required secrets (see each template's README)
4. Push to trigger

## Who is this for?

- Solo developers who want CI/CD without configuring everything from scratch
- Teams standardizing on a workflow pattern across multiple repos
- Anyone tired of searching Stack Overflow for "github actions node.js deploy"

## License

MIT

---

Built by [Taru](https://github.com/Taru0208)
