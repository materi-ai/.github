# Frequently Asked Questions About `.github`

Common questions from contributors, maintainers, and team members about the `.github` repository.

## General Questions

### Q: What is the `.github` repository?

**A:** It's a special repository in the Materi organization that contains organization-wide governance documents, community guidelines, and contribution standards. GitHub automatically reads specific files from this repository to display on your organization profile and in all member repositories.

### Q: Why is it important?

**A:** Because it:
- Ensures consistent contributor experience across all services
- Centralizes governance (no duplicated policies)
- Makes onboarding faster for new team members
- Establishes clear community standards
- Demonstrates professionalism and inclusivity

### Q: Where is the `.github` repository?

**A:** [github.com/materi/.github](https://github.com/materi/.github)

### Q: How do I access it?

**A:** Like any other repository. But remember:
- Only organization members can access it
- Some files are read-only (through CODEOWNERS)
- Changes require pull requests (on default branch `main`)

### Q: What if I notice something wrong?

**A:**
1. For docs/typos: Open an issue or submit a PR
2. For governance problems: Email conduct@materi.dev
3. For security policy issues: Email security@materi.dev
4. For process feedback: Open an issue with "question" label

---

## Organization Profile

### Q: Why is my organization profile different?

**A:** The `.github` repository controls how your organization appears on GitHub. Specifically, `profile/README.md` is displayed instead of the default organization landing page.

### Q: How do I change what appears on the organization profile?

**A:** Edit `profile/README.md` in the `.github` repository:
1. Create a branch
2. Make changes to `profile/README.md`
3. Submit PR
4. Get it merged to `main`
5. Changes appear immediately on github.com/materi

### Q: Why isn't the profile updating after I merged a PR?

**A:**
- GitHub only reads from the **default branch** (usually `main`)
- Wait 5-10 minutes for cache refresh
- Do a hard refresh: `Ctrl+Shift+R` in browser
- Verify the changes are actually on the `main` branch

### Q: Can I have a different profile for each team?

**A:** No, the `.github` repository controls the organization-wide profile. Individual teams cannot override it. However, individual repositories can have their own README files.

---

## Governance and Policies

### Q: How were these policies created?

**A:** The policies in this repository were created to:
- Foster an inclusive community
- Establish clear contribution guidelines
- Ensure security and safety
- Align with industry best practices
- Follow GitHub's recommendations

### Q: Can I suggest changes to the Code of Conduct?

**A:** Yes!
1. Open an issue with your suggestion
2. Lead discussions with the community
3. Once consensus is reached, create a PR
4. Community lead reviews and merges

### Q: What if someone violates the Code of Conduct?

**A:**
1. Report to conduct@materi.dev with details
2. The community leadership team investigates
3. They follow the enforcement process in CODE_OF_CONDUCT.md
4. Actions are taken confidentially

### Q: Is the Code of Conduct enforced?

**A:** Yes. See the "Enforcement" section in CODE_OF_CONDUCT.md for:
- How violations are reported
- How they're investigated
- What consequences apply
- How to appeal

### Q: What's the difference between governance and service-specific policies?

**A:**
- **Governance (.github):** Organization-wide rules, everyone follows
- **Service-specific:** Individual service repos can add their own rules
- **Example:** Contributing guidelines say "follow service's code style" - each service defines its own

---

## Contributing Guidelines

### Q: Why do I need to follow the contributing guidelines?

**A:** To ensure:
- Consistent code quality
- Clear communication
- Smooth collaboration
- Fair review process
- Successful merges

### Q: Can I skip the contributing guidelines?

**A:** Not recommended. Guidelines exist because they:
- Help PR get approved faster
- Prevent rework and delays
- Show respect for maintainers' time
- Lead to better code

Maintainers may request you follow guidelines before merging.

### Q: Which guidelines apply to me?

**A:**
- **Everyone:** CODE_OF_CONDUCT, SECURITY policies
- **Contributors:** CONTRIBUTING guidelines
- **Maintainers:** Additional responsibilities (see CODEOWNERS)
- **Service-specific:** Each service may have additional requirements

### Q: Where are service-specific guidelines?

**A:** Each service repository has its own README with setup and contribution instructions. Links are in CONTRIBUTING.md.

### Q: Can I contribute to the `.github` repository itself?

**A:** Yes, but:
- Changes require appropriate reviewers (see CODEOWNERS)
- Governance documents need leadership review
- Templates need testing
- Workflows need validation

---

## Issue Templates

### Q: Why should I use issue templates?

**A:** Because:
- They capture necessary information
- They help triage issues faster
- They reduce back-and-forth questions
- They provide consistent format

### Q: What if the template doesn't fit my issue?

**A:**
1. Use the closest matching template
2. Adjust sections as needed
3. Describe why you diverged
4. Maintainers appreciate clarity

### Q: Can I suggest a new issue template?

**A:** Yes! Open an issue in `.github` repo:
1. Describe what's missing
2. Explain why it's needed
3. Provide example content
4. Discuss with team
5. PR to add new template

### Q: Will my issue be rejected if I don't use the template?

**A:** Not automatically, but:
- Maintainers may ask you to provide missing information
- Using templates makes approval faster
- Templates exist to help both you and maintainers

---

## Pull Request Template

### Q: Do I have to follow the PR template?

**A:** Mostly yes, because it ensures:
- Clear description of changes
- References to related issues
- Evidence of testing
- Documentation updates

### Q: What if I don't test my changes?

**A:** Mark the checkbox as unchecked and explain why:
```markdown
- [ ] Unit tests added/updated - (not applicable for docs)
```

Maintainers may block merge if testing is necessary.

### Q: Can I commit directly without PR?

**A:** Depends on your role:
- **Contributors:** No, always use PR
- **Maintainers:** Rarely, only for urgent hotfixes
- **Bots:** Yes, with special approval

Most work should go through PR for review.

---

## Workflows and Automation

### Q: What are the workflows doing?

**A:** Two main workflows:

1. **Issue Labeling** (`issue-labeling.yml`)
   - Runs: When issue created
   - Does: Auto-labels bugs, features, questions, priority
   - Benefit: Organizes issues without manual labeling

2. **Stale Management** (`stale.yml`)
   - Runs: Daily at 2 AM UTC
   - Does: Marks old issues, closes very old ones
   - Benefit: Keeps issue list clean, shows what's active

### Q: Why was my issue labeled as "bug" when it's a question?

**A:** The workflow detected keywords. You can:
1. Remove the label manually
2. Adjust the issue title
3. Add a comment correcting the label
4. Report to team if workflow needs improvement

### Q: Why did my issue get closed?

**A:** The stale workflow closes issues inactive for 67+ days:
- Issues marked stale after 60 days
- Closed 7 days later if still inactive
- Pinned/blocker issues are exempted

To keep it open:
1. Add a comment updating status
2. Reopen if closed
3. Use pinned/blocker labels for critical issues

### Q: Can I turn off the stale workflow?

**A:** Organization admins can, but it's not recommended because:
- Issue list becomes cluttered
- Old issues stay visible
- It's hard to tell what's still relevant

Instead, if issue is still relevant:
- Add a comment
- Update with progress
- Reopen if closed

### Q: How do I test a workflow?

**A:**
1. Go to **Actions** tab in `.github` repo
2. Find the workflow you want to test
3. Click **Run workflow** (if available)
4. Select branch (usually `main`)
5. Click **Run workflow**
6. Watch execution logs

---

## Security

### Q: What is the security policy?

**A:** See [SECURITY.md](../SECURITY.md). It explains:
- How to report vulnerabilities responsibly
- Contact information (security@materi.dev)
- Disclosure timeline (90 days)
- Responsible disclosure expectations

### Q: Should I open a public GitHub issue for security bugs?

**A:** **NO.** Always report privately:
1. Email security@materi.dev with details
2. Include: description, reproduction steps, impact
3. Wait for acknowledgment (within 24 hours)
4. Coordinate disclosure timeline
5. We'll announce publicly only when patch is ready

Opening public issue can help attackers before fix exists.

### Q: What if I find a vulnerability in the `.github` repository itself?

**A:** Same process:
1. Email security@materi.dev
2. Describe the issue
3. Wait for response
4. Coordinate responsible disclosure

### Q: Will I get credited for finding a vulnerability?

**A:** Yes, in the security advisory (unless you prefer anonymity):
- Your name/handle in release notes
- Special recognition on governance pages
- Our gratitude!

---

## Maintenance and Updates

### Q: How often are documents updated?

**A:** Maintenance schedule:
- **Daily:** Automated workflows
- **Weekly:** Manual review of issues
- **Monthly:** Template effectiveness check
- **Quarterly:** Full policy review
- **Annually:** Compliance audit

### Q: Can I propose major policy changes?

**A:** Yes, but follow the process:
1. Open issue for discussion
2. Allow 2+ weeks for community feedback
3. Reach consensus with leadership
4. Create PR with final policy
5. Merge after approval

### Q: What if a new law requires policy change?

**A:** Urgent process:
1. Notify @materi/admins immediately
2. Create emergency PR if time-sensitive
3. Expedited review (same day)
4. Merge and communicate to all

### Q: Who maintains this repository?

**A:** See CODEOWNERS:
- **Security policies:** @materi/security-team
- **Code of Conduct:** @materi/community-leads
- **Contributing guides:** @materi/tech-leads
- **Templates/workflows:** @materi/platform-team
- **Overall:** @materi/admins

---

## Technical Questions

### Q: Why do some files end with `.yml` and others `.yaml`?

**A:** Both are valid YAML extensions. We use `.yml` for brevity, but `.yaml` also works. GitHub recognizes both.

### Q: Can I modify CONTRIBUTING.md for my service?

**A:** Sort of. You have two options:

1. **Add to existing:** Create service-specific section
   ```markdown
   ## Canvas Service (Next.js)

   [Canvas-specific setup...]
   ```

2. **Create service-specific file:** In your service repo
   ```
   [your-service]/CONTRIBUTING.md
   ```

   GitHub will show both the org-wide and service-specific version.

### Q: Why is the branch named `main` not `master`?

**A:** Industry standard since 2020:
- More inclusive language
- Better reflects purpose
- GitHub's new default
- Aligns with Linux kernel, etc.

### Q: Can I use this `.github` repo in my own projects?

**A:** Yes! The governance content is licensed under CC BY 4.0, so you can:
- Copy templates to your projects
- Adapt policies for your community
- Use as reference
- Credit Materi if you want

Just adjust organization names and contact info.

---

## Troubleshooting

### Q: Templates aren't showing in my repo's issues

**A:** Check:
1. Is your repo in the materi organization? (Not a fork)
2. Is `.github` the organization's main repo?
3. Is the default branch `main`?
4. Wait 5 minutes and refresh browser
5. Hard refresh: `Ctrl+Shift+R`

### Q: PR template isn't auto-filling

**A:** Check:
1. File is at `.github/pull_request_template.md`
2. Syntax is correct (--- delimiters optional)
3. You're using GitHub's PR creation UI (not CLI)
4. Default branch is `main`

### Q: Workflow is failing

**A:** Check:
1. Go to **Actions** tab
2. Click the failed workflow
3. Read the error message
4. Common issues:
   - YAML syntax error (check indentation)
   - Outdated action version
   - Missing permissions
   - Token not available

### Q: I think something is broken

**A:** Open an issue in `.github` repo:
1. Use "Bug Report" template
2. Include: what's broken, expected behavior, how to reproduce
3. Team will investigate and fix

---

## More Questions?

- **Search existing issues:** [github.com/materi/.github/issues](https://github.com/materi/.github/issues)
- **Ask on discussions:** If no issue exists, create one
- **Email for non-public questions:** hello@materi.dev
- **Security questions:** security@materi.dev
- **Governance questions:** conduct@materi.dev

---

**Last Updated:** 2026-01-07
**Maintained By:** Materi Governance Team
