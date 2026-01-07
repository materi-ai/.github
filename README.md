# Materi Organization `.github` Repository

This is the **single source of truth** for Materi organization governance, community standards, and contribution guidelines across all repositories.

## What is this repository?

This repository (`github.com/materi/.github`) contains the foundational governance and community files that apply organization-wide to all Materi repositories. GitHub automatically reads specific files from this repository to:

- Display the organization profile
- Show contribution guidelines
- Display code of conduct
- Provide security vulnerability disclosure policy
- Auto-populate issue and pull request templates
- Run organization-level automation

## Repository Structure

```
.github/
├── README.md                         # This file
├── LICENSE                           # MIT license for content
├── CODEOWNERS                        # Code ownership and review requirements
│
├── profile/
│   └── README.md                     # Organization profile (displayed on org page)
│
├── CONTRIBUTING.md                   # How to contribute to Materi services
├── CODE_OF_CONDUCT.md                # Community behavioral standards
├── SECURITY.md                       # Security vulnerability disclosure policy
├── FUNDING.yml                       # Sponsorship and support options
│
├── ISSUE_TEMPLATE/
│   ├── bug_report.md                 # Template for bug reports
│   ├── feature_request.md            # Template for feature requests
│   ├── question.md                   # Template for questions
│   └── config.yml                    # Issue template configuration
│
├── pull_request_template.md          # Standard pull request checklist
│
├── workflows/
│   ├── issue-labeling.yml            # Automatically label issues
│   ├── stale.yml                     # Close stale issues and PRs
│   └── community-health.yml          # Track community metrics (future)
│
└── docs/
    ├── SETUP.md                      # How to initialize .github in new orgs
    ├── MAINTENANCE.md                # Keeping governance docs current
    └── FAQ.md                        # Frequently asked questions
```

## Key Files and Their Purpose

### Governance and Community

- **[profile/README.md](profile/README.md)** — Displays on the organization's GitHub profile page
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — Guidelines for contributing to Materi services
- **[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)** — Community standards and expectations
- **[SECURITY.md](SECURITY.md)** — How to responsibly disclose security vulnerabilities

### Contributor Experience

- **[ISSUE_TEMPLATE/](ISSUE_TEMPLATE/)** — Auto-filled templates when contributors open issues
- **[pull_request_template.md](pull_request_template.md)** — Auto-filled template for pull requests
- **[FUNDING.yml](FUNDING.yml)** — Sponsorship options and support links

### Automation

- **[workflows/](workflows/)** — GitHub Actions that run organization-wide automation
  - Issue auto-labeling
  - Stale issue management
  - Community health monitoring

## How Files are Applied

### To This Organization

When you visit the Materi organization on GitHub:

```
github.com/materi
    ↓
    GitHub reads .github repository:
    ├─ /profile/README.md → displays on org profile
    ├─ /CONTRIBUTING.md → shown in community guidelines
    ├─ /CODE_OF_CONDUCT.md → shown in community profile
    ├─ /SECURITY.md → shown in security policy tab
    └─ /FUNDING.yml → enables sponsor button
```

### To Service Repositories

Templates and workflows apply automatically to all service repositories:

```
github.com/materi/products-canvas
    ↓
    GitHub discovers .github org repo and:
    ├─ Shows /ISSUE_TEMPLATE/* when creating issues
    ├─ Shows /pull_request_template.md when creating PRs
    ├─ Runs /workflows/* as applicable
    └─ Uses CODEOWNERS for review requests
```

## Making Changes

### Governance File Updates

1. **Create a branch** from `main`
2. **Make changes** to the governance file
3. **Submit a pull request** with clear justification
4. **Required reviewers** (from CODEOWNERS) review
5. **Merge** to `main` when approved

### Review Process

- Security policy changes → reviewed by @materi/security-team
- Code of conduct changes → reviewed by @materi/community-leads
- Contribution guidelines → reviewed by @materi/tech-leads
- Templates → reviewed by @materi/platform-team
- All changes → reviewed by @materi/admins

Changes become effective immediately after merging to `main`.

## Maintenance

### Regular Tasks

- **Monthly**: Review open discussions and feedback on governance docs
- **Quarterly**: Audit for outdated links or policies
- **Annually**: Full review and update cycle

See [docs/MAINTENANCE.md](docs/MAINTENANCE.md) for detailed maintenance procedures.

## Understanding GitHub's Special Files

GitHub has special handling for certain files in `.github` repositories:

| File | Discovered By | Displayed At | Updates |
|------|---------------|--------------|---------|
| `profile/README.md` | GitHub | Org profile page | Auto (main branch) |
| `CONTRIBUTING.md` | GitHub | Community profile | Auto (main branch) |
| `CODE_OF_CONDUCT.md` | GitHub | Community profile | Auto (main branch) |
| `SECURITY.md` | GitHub | Security policy tab | Auto (main branch) |
| `FUNDING.yml` | GitHub | Sponsor button | Auto (main branch) |
| `ISSUE_TEMPLATE/*.md` | GitHub | Issue creation form | Auto (main branch) |
| `pull_request_template.md` | GitHub | PR creation form | Auto (main branch) |
| `workflows/*.yml` | GitHub Actions | Triggered by events | Auto (main branch) |

**Important**: GitHub only reads from the **default branch** (usually `main`). Changes on feature branches won't be discovered until merged.

## Getting Help

### For Contributors
- Read [CONTRIBUTING.md](CONTRIBUTING.md)
- Ask questions in service-specific repositories
- Review [docs/FAQ.md](docs/FAQ.md)

### For Maintainers
- See [docs/SETUP.md](docs/SETUP.md) for initial setup
- See [docs/MAINTENANCE.md](docs/MAINTENANCE.md) for ongoing maintenance
- Review [CODEOWNERS](CODEOWNERS) for ownership structure

## Related Documentation

- [Materi Organization Profile](profile/README.md)
- [Contributing to Materi](CONTRIBUTING.md)
- [Community Code of Conduct](CODE_OF_CONDUCT.md)
- [Security Disclosure Policy](SECURITY.md)
- [Setup Guide](docs/SETUP.md)
- [Maintenance Guide](docs/MAINTENANCE.md)
- [Frequently Asked Questions](docs/FAQ.md)

## Repository Metadata

- **Visibility**: Public
- **License**: Dual licensed (MIT for templates, CC BY 4.0 for governance content)
- **Maintainers**: @materi/admins
- **Default Branch**: main

---

**Last Updated**: 2026-01-07
**Maintained By**: Materi Governance Team
