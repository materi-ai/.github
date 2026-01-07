# Contributing to Materi

Thank you for your interest in contributing to Materi! We welcome contributions from everyone in the community. This document provides guidelines and instructions for contributing.

## Code of Conduct

Before contributing, please review our [Code of Conduct](CODE_OF_CONDUCT.md). We are committed to providing a welcoming and inclusive environment for all contributors.

## How to Contribute

### Reporting Bugs

Found a bug? We'd love to hear about it. Please:

1. Check the [existing issues](https://github.com/materi) to see if someone has already reported it
2. If not, open a new issue using the **Bug Report** template
3. Include:
   - Clear description of the bug
   - Steps to reproduce
   - Expected vs. actual behavior
   - Environment information (OS, version, etc.)
   - Screenshots (if applicable)

### Requesting Features

Have an idea for a new feature? We'd like to hear it:

1. Check the [existing issues](https://github.com/materi) for similar requests
2. Open a new issue using the **Feature Request** template
3. Explain:
   - The use case
   - Why this feature would be valuable
   - Proposed implementation (if you have ideas)

### Submitting Code Changes

#### For Service Maintainers

The Materi organization uses a **multi-repository architecture**. Each service is maintained in its own repository:

| Service | Language | Repository |
|---------|----------|-----------|
| Canvas Editor | TypeScript/React | [github.com/materi/products-canvas](https://github.com/materi/products-canvas) |
| API Gateway | Go | [github.com/materi/domain-api](https://github.com/materi/domain-api) |
| Manuscript Service | Go | [github.com/materi/domain-manuscript](https://github.com/materi/domain-manuscript) |
| Printery Service | Go | [github.com/materi/domain-printery](https://github.com/materi/domain-printery) |
| Relay Service | Rust | [github.com/materi/domain-relay](https://github.com/materi/domain-relay) |
| Shield Auth | Go | [github.com/materi/domain-shield](https://github.com/materi/domain-shield) |
| Intelligence Service | Python | [github.com/materi/platform-intelligence](https://github.com/materi/platform-intelligence) |

**Each service has its own CONTRIBUTING.md with language-specific guidelines.**

#### General Steps

1. **Fork** the service repository you want to contribute to
2. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/description-of-feature
   ```
3. **Make your changes** following the service's code style guidelines
4. **Test your changes** thoroughly (see service README for test commands)
5. **Commit with clear messages** following conventional commits:
   ```bash
   git commit -m "feat: add new feature"
   git commit -m "fix: resolve bug in module"
   git commit -m "docs: update API documentation"
   ```
6. **Push to your fork** and **create a pull request** to the service's `main` branch
7. **Address code review feedback** from maintainers
8. **Celebrate** when your PR is merged!

### Improving Documentation

Documentation improvements are always welcome! You can contribute by:

- Fixing typos or unclear wording
- Adding missing documentation
- Improving architecture diagrams
- Enhancing API documentation
- Translating documentation

Documentation lives in several places:
- Individual service READMEs
- [docs.getmateri.com](https://docs.getmateri.com)
- This `.github` repository

## Development Workflow

### Setting Up Your Environment

Each service has its own setup instructions. See the service's README:

```bash
# Example for Canvas service
cd products-canvas
make setup      # Install dependencies
make dev        # Start development server
```

### Running Tests

Tests must pass before submitting a PR. Each service uses different tooling:

```bash
# API (Go)
cd domain-api && make test

# Shield (Python/Django)
cd domain-shield && python manage.py test

# Relay (Rust)
cd domain-relay && cargo test

# Canvas (TypeScript)
cd products-canvas && npm test
```

### Code Style

- **Go**: Follow [Effective Go](https://golang.org/doc/effective_go)
- **TypeScript/JavaScript**: Follow [Airbnb JS Style Guide](https://github.com/airbnb/javascript)
- **Python**: Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/)
- **Rust**: Follow [Rust API Guidelines](https://rust-lang.github.io/api-guidelines/)

Most services have automated linting. Run before committing:

```bash
# API
cd domain-api && make lint

# Canvas
cd products-canvas && npm run lint
```

## Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/) for consistency:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation changes
- `style:` — Code style changes (no logic changes)
- `refactor:` — Code refactoring
- `perf:` — Performance improvements
- `test:` — Test changes
- `chore:` — Build, CI, dependencies

### Examples
```bash
git commit -m "feat(api): add user validation endpoint"
git commit -m "fix(relay): correct WebSocket disconnect handling"
git commit -m "docs(contributing): clarify commit message format"
```

## Pull Request Guidelines

### Before Submitting

- [ ] Tests pass locally (`make test` or language-equivalent)
- [ ] Code follows style guidelines (linting passes)
- [ ] New features include tests
- [ ] Documentation is updated if needed
- [ ] No breaking changes without discussion
- [ ] Commit messages are clear and follow conventions

### PR Title Format

Use the same format as commit messages:
```
feat(module): brief description
fix(module): brief description
docs: brief description
```

### PR Description Template

PRs use an auto-filled template that asks for:
- Summary of changes
- Motivation and context
- Type of change (feature, bugfix, docs, etc.)
- Testing done
- Breaking changes (if any)

### Review Process

1. At least one maintainer reviews your PR
2. Automated tests must pass (CI/CD)
3. Code review feedback is addressed
4. PR is merged when approved

## Recognition

All contributors are recognized in:
- Commit history
- Pull request credits
- Service-specific contributor lists
- [github.com/materi](https://github.com/materi) contributor graph

## Getting Help

### Questions?
- Open a discussion in the service repository
- Ask in a GitHub issue
- Email: hello@getmateri.com

### Want to Contribute but Not Sure Where?
- Browse [open issues labeled "good first issue"](https://github.com/materi)
- Check service READMEs for contribution opportunities
- Look for "[help wanted](https://github.com/materi)" labels

### Confused About the Architecture?
- Read the [Architecture Documentation](https://docs.getmateri.com/architecture)
- Review the [`.github` README](https://github.com/materi/.github)
- Ask in an issue or discussion

## Licensing

By contributing to Materi, you agree that:
- Code contributions are licensed under the same license as the service
- Documentation contributions are licensed under CC BY 4.0
- You have the right to grant these licenses

## Questions?

Don't hesitate to reach out:
- Open an issue with the **Question** template
- Ask in service-specific discussions
- Email: hello@getmateri.com

---

**Thank you for contributing to Materi!** Your efforts help make document collaboration better for everyone.
