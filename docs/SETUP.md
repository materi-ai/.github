# Setting Up `.github` Repository for Materi Organization

This guide explains how to initialize and configure the `.github` repository for the Materi organization on GitHub.

## Overview

The `.github` repository is a special repository that serves as the single source of truth for organization-wide governance, community standards, and contribution guidelines. GitHub automatically reads specific files from this repository to display on your organization profile and in all member repositories.

## Prerequisites

- Admin access to the Materi GitHub organization
- Git installed locally (`git --version`)
- Basic understanding of GitHub organization management

## Step-by-Step Setup

### Step 1: Create the `.github` Repository

1. Go to [github.com/materi](https://github.com/materi)
2. Click **New Repository** or go to **Settings → Repositories → New**
3. Configure the repository:
   - **Repository Name:** `.github` (exactly)
   - **Description:** "Organization governance, community guidelines, and contribution standards for Materi"
   - **Visibility:** Public (recommended for transparency)
   - **Initialize this repository with:**
     - ✅ Add a README file (optional, we'll replace it)
     - ✅ Add .gitignore (optional, we'll replace it)
   - Do NOT initialize with license (we'll add our own)

4. Click **Create Repository**

### Step 2: Clone and Push Existing Content

If you already have a local `.github` repository prepared:

```bash
# Navigate to your local .github directory
cd /path/to/local/.github

# Add remote to GitHub
git remote add origin https://github.com/materi/.github.git

# Verify remote
git remote -v

# Set main as default branch (optional but recommended)
git branch -M main

# Push to GitHub
git push -u origin main
```

If GitHub created a README/LICENSE, you may need to pull first:

```bash
# Pull existing content
git pull origin main --allow-unrelated-histories

# Resolve any conflicts (keep our versions)
git checkout --ours .

# Complete the merge
git add . && git commit -m "Merge GitHub-created files"

# Push
git push origin main
```

### Step 3: Configure Organization Settings

#### Enable Code of Conduct

1. Go to **Settings → Community**
2. Under "Code of Conduct," click **Add**
3. Select "Contributor Covenant"
4. Our `.github/CODE_OF_CONDUCT.md` will be detected automatically

#### Enable Contributing Guidelines

1. Go to **Settings → Community**
2. Contributing guidelines are auto-detected from `.github/CONTRIBUTING.md`
3. Should show: ✅ "Contributing guidelines"

#### Enable Security Policy

1. Go to **Settings → Code security and analysis → Security policy**
2. Our `.github/SECURITY.md` will be detected
3. Contributors will see this when reporting vulnerabilities

#### Configure Sponsorship (Optional)

1. Go to **Settings → Sponsorships**
2. Enable if you want the sponsor button on your profile
3. Our `.github/FUNDING.yml` will populate sponsor options

#### Set Default Branch

1. Go to **Settings → Default branch**
2. Change from `master` to `main` (if not already done)
3. Note: GitHub may have defaulted to `main`

### Step 4: Verify GitHub Discovery

After pushing, verify that GitHub has discovered your special files:

| File | Location to Check | Expected Result |
|------|-------------------|-----------------|
| `profile/README.md` | Organization profile page | Custom profile displays |
| `CONTRIBUTING.md` | Settings → Community | Shows "Contributing guidelines" ✅ |
| `CODE_OF_CONDUCT.md` | Settings → Community | Shows "Code of conduct" ✅ |
| `SECURITY.md` | Settings → Code security | Shows security policy ✅ |
| `FUNDING.yml` | Organization profile | Sponsor button appears (if enabled) |
| Issue templates | Click **New Issue** → See dropdown | 3 templates available |
| PR template | Create new PR | Template auto-fills |

**Note:** GitHub discovers files from the **default branch only**. Changes on feature branches won't be visible until merged.

### Step 5: Test Issue/PR Templates

1. Go to any service repository (e.g., [github.com/materi/products-canvas](https://github.com/materi/products-canvas))
2. Click **Issues → New Issue**
3. Verify you see three options:
   - 🐛 Bug Report
   - ✨ Feature Request
   - ❓ Question
4. Create a test issue to verify template auto-fills
5. Go to **Pull Requests → New Pull Request**
6. Verify PR template auto-fills in the description

### Step 6: Test Workflows

#### Test Issue Labeling Workflow

1. In any service repo, create a new issue with title: `bug: something broken`
2. Wait a few seconds for the workflow to run
3. Verify the `bug` label was added automatically

#### Test Stale Issues Workflow

1. The stale workflow runs daily at 2 AM UTC
2. To test manually:
   - Go to [github.com/materi/.github/actions](https://github.com/materi/.github/actions)
   - Find the "Close Stale Issues and PRs" workflow
   - Click **Run workflow** → **Run workflow** (main branch)
   - Watch the execution in **Actions** tab

### Step 7: Configure Branch Protection (Optional)

For `.github` repository (important because it affects org-wide policies):

1. Go to **Settings → Branches**
2. Add branch protection rule for `main`:
   - ✅ Require pull request reviews before merging (min 1 reviewer)
   - ✅ Dismiss stale pull request approvals when new commits are pushed
   - ✅ Require status checks to pass (if any CI configured)
   - ✅ Require branches to be up to date before merging
   - ✅ Restrict who can push to matching branches (admins only)

This ensures governance changes are reviewed before deployment.

### Step 8: Set Up CODEOWNERS (Optional)

Our `.github/CODEOWNERS` file is already configured. Verify GitHub is using it:

1. Go to **Settings → Code owners**
2. Should show "CODEOWNERS file found in main" ✅
3. File will auto-update reviews based on CODEOWNERS rules

### Step 9: Onboard Team Members

Create an initial wiki page or documentation for team:

```markdown
# .github Repository Onboarding

Welcome! This repository controls organization-wide policies.

## Key Points

1. **This affects all services** — Changes here apply org-wide
2. **All changes require PR** — No direct commits to main
3. **Review required** — See CODEOWNERS for who reviews what
4. **Default branch only** — GitHub reads from main branch
5. **CI/CD changes** — Add/update workflows carefully

## Common Tasks

### Update Contribution Guidelines
- Edit `/CONTRIBUTING.md`
- Submit PR with clear justification
- At least one tech lead must review

### Add New Issue Template
- Create file in `/ISSUE_TEMPLATE/`
- Add frontmatter (name, about, labels)
- PR required
- Becomes available after merge

### Report Governance Issues
- Email: conduct@materi.dev (Code of Conduct)
- Email: security@materi.dev (Security Policy)
- GitHub issue: Process/documentation problems

## Questions?

See [../docs/FAQ.md](../docs/FAQ.md) for common questions.
```

## Troubleshooting

### "Templates not showing up in Issues"

**Cause:** GitHub only reads from default branch

**Fix:**
1. Verify `main` is the default branch
2. Verify `.github` repo is in the organization (not a user repo)
3. Wait 5 minutes and refresh
4. Check `.github/ISSUE_TEMPLATE/` folder exists and is not empty

### "Workflows not running"

**Cause:** Workflows must be on default branch

**Fix:**
1. Ensure workflows are committed and pushed to `main`
2. Verify workflow syntax in [GitHub Actions Syntax](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions)
3. Check the **Actions** tab for execution logs
4. Look for validation errors in the workflow YAML

### "SECURITY.md not showing in security tab"

**Cause:** Security policy not enabled

**Fix:**
1. Go to **Settings → Code security and analysis**
2. Scroll to "Security policy"
3. Click **Set up a security policy**
4. GitHub will detect `.github/SECURITY.md`
5. Click **Publish**

### "Contributing guidelines not discoverable"

**Cause:** File location or naming wrong

**Fix:**
1. Verify file is at `.github/CONTRIBUTING.md` (exact path)
2. Verify it's on the default branch
3. Go to **Settings → Community** to manually check
4. Wait 5-10 minutes for cache refresh

### "Code of Conduct not showing"

**Cause:** File missing or wrong location

**Fix:**
1. Verify file is at `.github/CODE_OF_CONDUCT.md`
2. Verify content exists (not empty)
3. Try removing and re-adding from Settings → Community
4. Force refresh: `Ctrl+Shift+R` on browser

## Verification Checklist

After setup, verify:

- [ ] `.github` repository created as public
- [ ] All files pushed to `main` branch
- [ ] `main` is the default branch
- [ ] Organization profile shows custom README
- [ ] Settings → Community shows all governance docs
- [ ] Settings → Code security shows security policy
- [ ] Issue templates appear in "New Issue" dropdown
- [ ] PR template auto-fills on new PR
- [ ] CODEOWNERS file recognized
- [ ] Branch protection rules configured (optional)
- [ ] Team members notified of changes

## Next Steps

1. **Share this repo with team** — Announce to contributors
2. **Review CONTRIBUTING.md** — Ensure service links are current
3. **Schedule review** — Quarterly review of all governance docs
4. **Monitor issues** — Watch for template effectiveness
5. **Iterate** — Improve based on contributor feedback

## Related Documentation

- [README.md](../README.md) — Repository overview
- [MAINTENANCE.md](MAINTENANCE.md) — How to update governance docs
- [FAQ.md](FAQ.md) — Common questions

## Support

- **Questions:** Open an issue in this repository
- **Governance Issues:** Email conduct@materi.dev
- **Security Issues:** Email security@materi.dev

---

**Last Updated:** 2026-01-07
**Maintained By:** Materi Governance Team
**Status:** Ready for GitHub organization deployment
