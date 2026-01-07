# Maintaining the `.github` Repository

This guide explains how to keep the `.github` repository current and ensure governance documents remain effective.

## Overview

The `.github` repository requires regular maintenance to:
- Keep policies aligned with current practices
- Update links and references
- Fix issues reported by community
- Adapt templates based on feedback
- Maintain security and compliance

## Maintenance Schedule

### Daily (Automated)

- **Stale issue cleanup** — `workflows/stale.yml` runs at 2 AM UTC
  - Marks issues stale after 60 days
  - Closes after 67 days
  - Exempts pinned/blocker issues

- **Issue auto-labeling** — `workflows/issue-labeling.yml` on issue creation
  - Auto-labels by type (bug, enhancement, question)
  - Auto-labels by priority (critical, high, low)

### Weekly

- **Monitor issues** — Check for:
  - Reported problems with templates
  - Outdated links or information
  - Community feedback on contributing guidelines

- **Review comments** — Look for:
  - Questions about policies
  - Suggestions for improvement
  - Clarification requests

### Monthly

- **Template effectiveness** — Ask:
  - Are issue templates being used?
  - Do templates capture necessary info?
  - Are there consistent gaps?
  - Should we modify templates?

- **Link audit** — Verify:
  - All documentation links work
  - No 404 errors in governance docs
  - Service repository links current

- **Security review** — Check:
  - No accidental secrets in files
  - Security policy is still accurate
  - Contact emails monitored

### Quarterly (Full Review)

- **Policy review** — Complete re-read of:
  - `CONTRIBUTING.md` — Still aligned with workflow?
  - `CODE_OF_CONDUCT.md` — Still inclusive and fair?
  - `SECURITY.md` — Accurate disclosure timeline?
  - Issue templates — Capture right information?

- **Update check** — Look for:
  - New best practices in community
  - Changes in service architecture
  - Updated tool versions
  - New or deprecated services

- **Metrics review** — Analyze:
  - Template usage statistics
  - Issue resolution time
  - Community health metrics
  - Workflow success rate

### Annually

- **Full audit** — Complete assessment:
  - Compliance audit (SOC 2, GDPR, etc.)
  - Security assessment
  - Policy effectiveness review
  - Community satisfaction survey

## How to Update Files

### 1. Identify What Needs Updating

**Sources of feedback:**
- GitHub issues in `.github` repo
- Community discussions
- Email feedback (conduct@materi.dev, hello@materi.dev)
- Service team feedback
- Metrics and analytics

### 2. Create a Feature Branch

```bash
git checkout -b chore/update-contributing-guide
# OR
git checkout -b feat/add-new-issue-template
# OR
git checkout -b docs/clarify-security-policy
```

Branch naming convention:
- `docs/` — Documentation updates
- `feat/` — New templates or workflows
- `fix/` — Bug fixes
- `chore/` — Maintenance updates

### 3. Make Changes

#### Updating Governance Documents

Example: Update CONTRIBUTING.md

```bash
# Make changes to CONTRIBUTING.md
# Verify markdown syntax
# Verify all links still work
# Test relative paths

# Stage changes
git add CONTRIBUTING.md

# Commit with descriptive message
git commit -m "docs(contributing): clarify service-specific workflows

- Add explicit links to each service repository
- Update Go version requirement to 1.25
- Clarify test requirements per service
- Fix broken relative links"
```

#### Adding a New Issue Template

Example: Add security issue template

```bash
# Create new template
cat > ISSUE_TEMPLATE/security_issue.md << 'EOF'
---
name: "🔒 Security Issue"
about: "Report a security vulnerability"
title: "security: "
labels: ["security"]
---

[Your template here]
EOF

# Verify frontmatter is correct
# Verify labels exist or will be created

# Stage and commit
git add ISSUE_TEMPLATE/security_issue.md
git commit -m "feat: add security issue template

- Includes vulnerability description
- Requests steps to exploit
- Asks for impact assessment
- Provides responsible disclosure timeline"
```

#### Updating Workflows

Example: Update issue-labeling workflow

```bash
# Edit workflows/issue-labeling.yml
# Verify YAML syntax
# Test with workflow syntax validator

git add workflows/issue-labeling.yml
git commit -m "ci: improve issue labeling workflow

- Add detection for 'accessibility' keyword
- Improve priority detection logic
- Update to actions/github-script@v7"
```

### 4. Submit Pull Request

Create a PR to `main`:

```bash
git push origin chore/update-contributing-guide
# Then go to GitHub and create PR
```

PR should include:
- **Title:** Clear, follows convention (`docs:`, `feat:`, etc.)
- **Description:** Why the change is needed
- **Testing:** How you tested the changes
- **Review:** Who should review (check CODEOWNERS)

Example PR description:

```markdown
## Description

Updated CONTRIBUTING.md to clarify service-specific development workflows
and add missing links to service repositories.

## Why

Community members reported confusion about different setup processes for
each service. Clarifying the hierarchy helps new contributors.

## Changes

- Link to each service's CONTRIBUTING.md
- Add per-language setup commands
- Clarify test requirements
- Fix broken links to documentation

## Testing

- Verified all links in updated document
- Tested markdown rendering
- Checked relative paths work correctly

## Related Issues

Closes #5
Related to #12
```

### 5. Address Review Feedback

1. Review comments will come from CODEOWNERS
2. Make requested changes
3. Commit with clear message:
   ```bash
   git commit -m "docs(contributing): address review feedback

   - Clarify security policy link location
   - Add example for PR submission
   - Improve prose clarity"
   ```
4. Push updated branch
5. PR auto-updates with new commits

### 6. Merge to Main

Once approved:
1. Squash and merge (preferred for single change)
2. Or regular merge (for multi-commit changes)
3. Delete feature branch

Changes are **live immediately** after merge to `main`.

## Common Maintenance Tasks

### Task: Update Service Repository Links

When a service repo changes name or location:

1. Find all references:
   ```bash
   grep -r "github.com/materi/old-repo-name" .
   ```

2. Update in files:
   - `profile/README.md` (Key Projects table)
   - `CONTRIBUTING.md` (Service table)
   - Any workflow files
   - Issue template contact links

3. Commit with clear message:
   ```bash
   git commit -m "docs: update service repository URL

   - Rename products-canvas repo reference
   - Update all links from old to new URL
   - Verify all links working"
   ```

### Task: Add New Security Contact

When security team structure changes:

1. Update `SECURITY.md`:
   - Add/remove team member names
   - Update email addresses
   - Update PGP key if applicable

2. Test contact email:
   ```bash
   # Send test email to new contact
   echo "Test of security@materi.dev" | mail -s "Test" security@materi.dev
   ```

3. Commit with message:
   ```bash
   git commit -m "docs(security): update security team contacts

   - Add new security lead contact info
   - Update response time expectations
   - Verify email monitored"
   ```

### Task: Update Code of Conduct

When policy changes or issues arise:

1. Review current CODE_OF_CONDUCT.md
2. Discuss changes with leadership team
3. Update with new policy
4. Submit PR with clear justification
5. Allow time for community feedback

Example:

```bash
git commit -m "docs: update code of conduct

- Clarify remote event guidelines
- Add pronoun usage expectations
- Strengthen enforcement procedures
- Include appeals process"
```

### Task: Improve Issue Templates

When templates aren't capturing needed info:

1. Analyze issues reported recently
2. Identify missing fields
3. Test template in preview
4. Update template
5. Document why change was made

Example:

```bash
git commit -m "feat: improve bug report template

- Add environment variable section
- Add previous version info
- Remove rarely-used fields
- Clarify reproducibility requirements"
```

### Task: Update Workflows

When GitHub Actions updates or workflow needs improvement:

1. Test workflow locally or in test repo
2. Verify new syntax
3. Check Actions marketplace for updates
4. Update workflow file
5. Monitor execution after merge

Example:

```bash
git commit -m "ci: update GitHub Actions versions

- actions/github-script: v6 → v7
- actions/stale: v8 → v9
- Add new permissions structure"
```

## Validation Before Committing

### Markdown Validation

```bash
# Check markdown syntax (if you have a validator)
npm install -g markdownlint-cli
markdownlint *.md ISSUE_TEMPLATE/*.md
```

### YAML Validation

```bash
# Check workflow YAML syntax
python3 -m yaml workflows/*.yml
```

### Link Validation

```bash
# Check links with custom script
python3 << 'EOF'
import re, os

for root, dirs, files in os.walk('.'):
    dirs[:] = [d for d in dirs if d != '.git']
    for f in files:
        if f.endswith('.md'):
            path = os.path.join(root, f)
            with open(path) as file:
                for match in re.finditer(r'\[(.*?)\]\((.*?)\)', file.read()):
                    url = match.group(2)
                    if url.startswith('../') or url.startswith('./'):
                        if not os.path.exists(url):
                            print(f"Broken: {url} in {path}")
EOF
```

## Handling Issues and PRs

### When Issues are Opened

1. **Label appropriately** — Tag with type (question, bug, enhancement)
2. **Respond promptly** — Within 24 hours
3. **Clarify if needed** — Ask for specific information
4. **Fix or discuss** — Determine if action needed

### When PRs are Opened

1. **Review promptly** — Within 48 hours
2. **Check CODEOWNERS** — Ensure right people review
3. **Test changes** — Verify markdown, links, syntax
4. **Provide feedback** — Clear, actionable suggestions
5. **Merge when ready** — Delete branch after merge

### When Issues Report Errors

**Example:** "The link to API docs is broken"

1. Verify the issue
2. Identify root cause
3. Fix and test
4. Create PR with fix
5. Close issue with commit reference

## Escalation Procedures

### Urgent Changes (Security, Critical Docs)

**Timeline:** Same day response

Examples:
- Security disclosure timeline changed
- Critical governance issue
- Compliance requirement update

**Process:**
1. Immediately notify team leads
2. Create PR with clear justification
3. Expedited review (within 4 hours)
4. Merge and deploy immediately

### Policy Changes

**Timeline:** 2-4 week discussion period

Examples:
- Update Code of Conduct
- Change contributing process
- New governance requirement

**Process:**
1. Open issue for discussion
2. Allow community feedback (1-2 weeks)
3. Reach consensus with leadership
4. Create PR with changes
5. Merge after approval

### Experimental Changes

**Timeline:** Test in feature branch

Examples:
- New issue template
- Workflow improvements
- Process changes

**Process:**
1. Create feature branch
2. PR with clear testing plan
3. Test in non-critical context
4. Gather feedback
5. Refine and merge

## Monitoring and Metrics

### Metrics to Track

```bash
# Count issues using each template
gh issue list --label "bug" --json title --jq 'length'
gh issue list --label "enhancement" --json title --jq 'length'
gh issue list --label "question" --json title --jq 'length'

# Average issue resolution time
# (requires custom script or GitHub API analysis)

# Template usage effectiveness
# (survey contributors)
```

### Health Checks

Monthly review:
- [ ] All links working
- [ ] No 404 errors in docs
- [ ] Security contact email monitored
- [ ] Stale workflow running successfully
- [ ] Issue templates being used
- [ ] No secrets in repository

## Review Checklist

Before merging any change:

- [ ] Syntax is valid (markdown, YAML)
- [ ] All links verified and working
- [ ] No hardcoded secrets or credentials
- [ ] Proper commit message format
- [ ] Appropriate reviewers assigned
- [ ] All tests passing (if applicable)
- [ ] Documentation updated if needed
- [ ] Related issues linked in PR

## Maintenance Contacts

| Role | Contact | Responsibility |
|------|---------|-----------------|
| **Governance Lead** | @materi/tech-leads | CONTRIBUTING.md, policies |
| **Community Lead** | @materi/community-leads | CODE_OF_CONDUCT enforcement |
| **Security Lead** | @materi/security-team | SECURITY.md, vulnerability policy |
| **Platform Lead** | @materi/platform-team | Workflows, templates, automation |

## Escalation Path

```
Issue/Feedback
    ↓
Review by relevant maintainer (see CODEOWNERS)
    ↓
Decision: Minor fix / Discussion needed / Urgent action
    ↓
For Minor: PR → Review → Merge
For Discussion: Issue → Feedback period → Consensus → PR
For Urgent: Direct PR → Expedited review → Merge
```

## Related Documentation

- [README.md](../README.md) — Repository overview
- [SETUP.md](SETUP.md) — Initial organization setup
- [FAQ.md](FAQ.md) — Common maintenance questions

## Support

- **Questions:** Open an issue in this repository
- **Governance Discussions:** conduct@materi.dev
- **Maintenance Help:** @materi/platform-team

---

**Last Updated:** 2026-01-07
**Maintained By:** Materi Governance Team
**Next Review:** 2026-04-07
