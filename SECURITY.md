# Security Policy

## Reporting Security Vulnerabilities

Materi takes security seriously. If you discover a security vulnerability, please report it **responsibly and confidentially**. Do not open a public GitHub issue.

### How to Report

**Email**: security@materi.dev

Please include:

1. **Vulnerability Description** — What is the security issue?
2. **Affected Component** — Which service/feature is affected?
3. **Severity** — How critical is this vulnerability?
   - **Critical**: Immediate threat, RCE, authentication bypass, data breach
   - **High**: Significant impact, privilege escalation, sensitive data exposure
   - **Medium**: Moderate impact, requires specific conditions
   - **Low**: Minor impact, defense in depth issue
4. **Steps to Reproduce** — Clear instructions to demonstrate the issue
5. **Potential Impact** — What could an attacker do?
6. **Suggested Fix** — If you have a fix in mind (optional)
7. **Your Contact Info** — Email and/or phone for follow-up

### What to Expect

- **Acknowledgment**: We'll confirm receipt within 24 hours
- **Assessment**: We'll evaluate severity and impact (3-5 days)
- **Timeline**: We'll discuss timeline with you before public disclosure
- **Updates**: Regular status updates every 5 business days
- **Credit**: You'll be credited when the fix is published (unless you prefer anonymity)

### Disclosure Timeline

We follow a **90-day responsible disclosure policy**:

| Phase | Duration | Action |
|-------|----------|--------|
| **Report** | Day 1 | You report vulnerability |
| **Acknowledgment** | Day 1 | We confirm receipt |
| **Assessment** | Days 2-5 | We evaluate severity |
| **Fix Development** | Days 6-60 | We develop and test patch |
| **Release** | Day 61+ | We release patch |
| **Public Disclosure** | Day 90 | We publish security advisory |

If a patch is ready before 90 days, we'll coordinate disclosure earlier. If more time is needed, we'll communicate with you.

## Security Best Practices

### For Users

- **Keep software updated** — Apply security patches promptly
- **Use strong passwords** — Minimum 12 characters, mixed case, numbers, symbols
- **Enable 2FA** — Two-factor authentication where available
- **Monitor activity** — Review login history and connected devices
- **Report suspicious activity** — Contact us immediately if you notice issues

### For Contributors

- **Never commit secrets** — No API keys, passwords, tokens in code
- **Use `.env.example`** — Show required vars without actual values
- **Run security scans** — Use `make security` before pushing
- **Review PRs carefully** — Look for security issues in code review
- **Keep dependencies updated** — Run `make security` to check for vulnerabilities

### For Maintainers

- **Security scanning** — All CI/CD pipelines include security checks
- **Dependency updates** — Review and apply patches promptly
- **Code review** — All changes reviewed before merge
- **Secrets rotation** — Rotate credentials periodically
- **Incident response** — Follow incident response procedures

## Supported Versions

We provide security patches for:

| Version | Support Level | End of Life |
|---------|---------------|------------|
| Latest | Full support | Current + 1 year |
| Previous | Security patches only | Current release + 6 months |
| Older | Unsupported | Not patched |

### Version Schedule

- **New releases**: Monthly or as needed
- **Security patches**: Within 7 days of fix approval
- **Breaking changes**: Announced 30 days before release

## Known Security Considerations

### Authentication

- All API endpoints require JWT authentication
- Tokens expire after 1 hour
- Refresh tokens valid for 30 days
- Passwords hashed with bcrypt (minimum 12 rounds)

### Data Protection

- All data encrypted in transit (TLS 1.3)
- Sensitive data encrypted at rest (AES-256)
- Database connections use SSL/TLS
- File uploads scanned for malware

### Infrastructure

- Infrastructure as Code reviewed and audited
- Network segmentation between services
- Web Application Firewall (WAF) enabled
- DDoS protection enabled
- Regular penetration testing (quarterly)

## Security Testing

### Automated Scanning

- **SAST** (Static Application Security Testing)
  - Go: gosec
  - Python: bandit
  - Rust: cargo-audit
  - JavaScript: eslint-plugin-security

- **Dependency Scanning**
  - npm audit (JavaScript)
  - pip-audit (Python)
  - cargo-audit (Rust)
  - Dependabot (all languages)

- **Container Scanning**
  - Trivy for container images
  - Signed images with cosign
  - Registry scanning enabled

### Penetration Testing

- Quarterly external penetration tests
- Annual red team exercise
- Bug bounty program (coming soon)

### Compliance

- SOC 2 Type II audit (annual)
- GDPR compliance verified
- HIPAA ready (not yet certified)
- Secure SDLC (SDL) practices

## Incident Response

### Response Steps

1. **Report** received and triaged
2. **Assess** impact and severity
3. **Contain** — Stop active exploitation
4. **Fix** — Develop and test patch
5. **Release** — Deploy patch to production
6. **Notify** — Inform affected users
7. **Document** — Post-incident review

### Incident Communication

- **Critical**: Notification within 2 hours
- **High**: Notification within 24 hours
- **Medium**: Notification within 7 days
- **Low**: Published in release notes

## Responsible Disclosure Hall of Fame

We recognize security researchers who responsibly disclose vulnerabilities. If you find a vulnerability and follow our disclosure process, we'll credit you publicly (with permission).

**[Researchers who have reported vulnerabilities]** *(To be updated)*

## Security Resources

- **Security Best Practices**: [docs.getmateri.com/security](https://docs.getmateri.com/security)
- **Incident Response Plan**: [Internal only - email security@materi.dev]
- **Privacy Policy**: [getmateri.com/privacy](https://getmateri.com/privacy)
- **Terms of Service**: [getmateri.com/terms](https://getmateri.com/terms)

## Questions?

- **Security Issues**: security@materi.dev
- **General Questions**: hello@materi.dev
- **Bug Bounty Info**: bounty@materi.dev (coming soon)

---

**Last Updated**: 2026-01-07
**Next Review**: 2026-04-07
**Policy Version**: 1.0
