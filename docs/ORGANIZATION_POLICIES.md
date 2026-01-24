# 📋 Organization Policies

> **Comprehensive governance documentation for Violet Site Systems**

This document outlines the organization-wide policies, rules, and standards that govern all repositories within Violet Site Systems. These policies ensure consistency, security, and quality across our entire technology ecosystem.

---

## 🔒 Repository Protection Rules

Violet Site Systems maintains organization-level branch protection rules to ensure code quality, security, and collaborative development practices.

### Protected Branches

The following branch patterns are protected across all repositories:

- `main` - Primary production branch
- `master` - Legacy primary branch
- `production` - Production deployment branch
- `release/*` - All release branches

### Branch Protection Requirements

All protected branches enforce the following requirements:

| Requirement | Status | Description |
|------------|--------|-------------|
| **Pull Request Required** | ✅ Enabled | Direct pushes are prohibited; all changes must go through PR review |
| **Approvals Required** | ✅ 1+ Approvals | At least one approval from a team member or maintainer |
| **Status Checks** | ✅ Required | All automated checks must pass before merging |
| **Up-to-Date Branch** | ✅ Required | Branch must be current with base branch before merging |
| **Conversation Resolution** | ✅ Required | All review comments must be resolved |
| **Signed Commits** | 🔐 Recommended | Commit signing strongly encouraged for security |

### Bypass Access List

Certain automated systems and roles have bypass privileges to facilitate critical operations:

| Entity | Role | Bypass Permissions | Purpose |
|--------|------|-------------------|----------|
| **GitHub Copilot** | Automation | PR creation, branch push | Automated code contributions and fixes |
| **Dependabot** | Security Bot | Automated PRs, security updates | Dependency updates and vulnerability patches |
| **Organization Admins** | Admin | Full bypass (emergency only) | Critical fixes and emergency interventions |
| **Executive Team** | Leadership | Policy exceptions | Strategic decisions and policy adjustments |

> 📌 **Note**: Even with bypass access, following standard PR processes is encouraged. Bypass should only be used when absolutely necessary.

### Accessing Protection Rules

View and manage organization-level rules at:  
🔗 [Repository Rules Settings](https://github.com/organizations/Violet-Site-Systems/settings/rules)

---

## 🤖 Automation Configuration

### GitHub Copilot

**Status**: ✅ Enabled Organization-Wide

GitHub Copilot is configured as our AI-powered development assistant, providing:

- **Code Generation**: Intelligent code suggestions and completions
- **Automated PR Creation**: Automated pull requests for improvements and fixes
- **Code Review Assistance**: AI-powered code review comments and suggestions
- **Documentation Generation**: Automated documentation updates
- **Security Scanning**: AI-assisted vulnerability detection

**Configuration Details**:
- Models: GPT-4 and specialized code models
- Access: Available to all organization members
- Branch Pattern: `copilot/*` for automated branches
- Review Process: All Copilot PRs require human review before merge

See [Copilot Configuration](./COPILOT_CONFIGURATION.md) for detailed setup and best practices.

### Dependabot

**Status**: ✅ Enabled Organization-Wide

Dependabot automatically monitors and updates dependencies:

- **Security Updates**: Automatic PRs for security vulnerabilities
- **Version Updates**: Scheduled dependency version updates
- **Package Ecosystems**: npm, pip, Maven, Docker, GitHub Actions, and more
- **Update Schedule**: Weekly for minor versions, immediate for security patches
- **Auto-Merge**: Enabled for patch-level security updates after CI passes

**Branch Pattern**: `dependabot/*`

---

## 🌿 Branch Naming Conventions

Consistent branch naming improves organization and automation integration.

### Standard Branch Prefixes

| Prefix | Purpose | Example | Auto-Merge Eligible |
|--------|---------|---------|-------------------|
| `feature/` | New features and enhancements | `feature/user-authentication` | ❌ No |
| `fix/` | Bug fixes and corrections | `fix/login-validation-bug` | ❌ No |
| `copilot/` | GitHub Copilot automated changes | `copilot/update-readme` | ✅ After review |
| `dependabot/` | Dependency updates | `dependabot/npm/react-19.0.0` | ✅ Auto (security) |
| `hotfix/` | Critical production fixes | `hotfix/payment-gateway-issue` | ❌ No |
| `release/` | Release preparation branches | `release/v2.1.0` | ❌ No |
| `docs/` | Documentation updates | `docs/api-reference` | ✅ After review |
| `refactor/` | Code refactoring | `refactor/auth-module` | ❌ No |
| `test/` | Test additions or fixes | `test/integration-suite` | ❌ No |

### Branch Naming Best Practices

- Use lowercase with hyphens (kebab-case)
- Keep names descriptive but concise
- Include issue/ticket numbers when applicable: `feature/123-add-oauth`
- Avoid special characters except hyphens and forward slashes

---

## 🔄 Pull Request Guidelines

### Required PR Checks

All pull requests must pass the following before merging:

✅ **Code Quality Checks**
- Linting (ESLint, Prettier, language-specific linters)
- Code formatting standards
- Build compilation success
- No merge conflicts

✅ **Testing Requirements**
- All existing tests pass
- New tests for new features
- Minimum code coverage maintained
- Integration tests (where applicable)

✅ **Security Checks**
- CodeQL security scanning
- Dependency vulnerability scans
- Secret detection (no leaked credentials)
- License compliance

✅ **Review Requirements**
- At least 1 approval from maintainer or team member
- All conversations resolved
- No requested changes pending

### PR Best Practices

**Creating Pull Requests**:
1. **Clear Title**: Use descriptive titles (e.g., "Add OAuth2 authentication")
2. **Detailed Description**: Include:
   - What changes were made and why
   - Issue/ticket references
   - Testing performed
   - Breaking changes (if any)
3. **Small, Focused Changes**: Keep PRs manageable and focused on single concerns
4. **Screenshots**: Include for UI changes
5. **Documentation**: Update relevant docs with your changes

**Reviewing Pull Requests**:
1. **Timely Reviews**: Respond to review requests within 24-48 hours
2. **Constructive Feedback**: Be specific, kind, and helpful
3. **Test Locally**: Pull and test changes when possible
4. **Security Focus**: Look for potential security issues
5. **Approve or Request Changes**: Use GitHub's review options explicitly

**Merging Pull Requests**:
- Use **Squash and Merge** for cleaner history (default)
- Use **Rebase and Merge** for preserving commit history (when requested)
- Use **Merge Commit** for release branches only
- Delete branch after merge (automatic)

---

## 🔐 Security Policies

### Vulnerability Reporting

**Security Contact**: [security@accessvexel.com](mailto:security@accessvexel.com)

**Reporting Process**:
1. **Do NOT** open public issues for security vulnerabilities
2. Email security@accessvexel.com with:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact assessment
   - Suggested fix (if available)
3. Expect initial response within 24-48 hours
4. Work with our team on coordinated disclosure

**Bug Bounty**: We operate a private bug bounty program for qualifying vulnerabilities. Contact security team for details.

### Secret Scanning

**Status**: ✅ Enabled Organization-Wide

- Automatic detection of leaked credentials and secrets
- Real-time scanning of commits and PRs
- Immediate alerts to repository admins
- Integration with secret management systems
- Automated secret revocation workflows

**Supported Secret Types**:
- API keys and tokens
- Database credentials
- Private keys and certificates
- OAuth tokens
- Cloud provider credentials
- Third-party service tokens

### Code Scanning

**Status**: ✅ Enabled Organization-Wide

**Tools in Use**:
- **CodeQL**: GitHub's semantic code analysis engine
- **Dependabot Security**: Dependency vulnerability detection
- **Custom Scanners**: Language-specific security tools

**Scanning Frequency**:
- Every push to protected branches
- Every pull request
- Weekly scheduled scans
- On-demand scans available

**Vulnerability Response**:
- **Critical**: Immediate action required (within 24 hours)
- **High**: Fix within 7 days
- **Medium**: Fix within 30 days
- **Low**: Fix in next major release or within 90 days

---

## ⚖️ Compliance & Standards

### Code Quality Requirements

All code must meet the following standards:

**General Standards**:
- Follow language-specific style guides (e.g., PEP 8 for Python, Airbnb for JavaScript)
- Include appropriate comments and documentation
- Write self-documenting code with clear naming
- Maintain consistent formatting (automated via Prettier/formatters)
- Keep functions and methods focused and concise

**Testing Standards**:
- Unit test coverage: minimum 70% for new code
- Integration tests for all API endpoints
- End-to-end tests for critical user flows
- Performance tests for computationally intensive operations

**Documentation Standards**:
- README.md in every repository
- API documentation for all public interfaces
- Inline code comments for complex logic
- Architecture decision records (ADRs) for significant choices
- Changelog maintenance for all releases

### Licensing Standards

**Default License**: MIT License

All Violet Site Systems projects are released under OSI-approved open-source licenses:

**Approved Licenses**:
- ✅ **MIT License** (default, maximum permissiveness)
- ✅ **Apache License 2.0** (patent protection)
- ✅ **GPL v3** (copyleft when required)
- ✅ **BSD 3-Clause** (permissive with attribution)

**Sustainability Licenses**:

In addition to traditional open-source licenses, we support and use [BGINexus.io Sustainability Licenses](./SUSTAINABILITY_LICENSES.md) to embed environmental, social, and ethical commitments:

- **SUL-1.0**: Sustainable Use License
- **EIL-1.0**: Environmental Impact License
- **SBL-1.0**: Social Benefit License
- **CGL-1.0**: Community Governance License
- **EAL-1.0**: Ethical AI License
- **CAL-1.0**: Climate Accountability License

See [Sustainability Licenses Documentation](./SUSTAINABILITY_LICENSES.md) and [License Library](../licenses/) for full details.

**License Compliance**:
- All dependencies must use OSI-approved licenses
- No GPL dependencies in MIT/Apache projects (license compatibility)
- License files must be included in all distributions
- Third-party code must retain original attribution and licenses

### Accessibility Standards

**Requirement**: WCAG 2.1 Level AA (minimum)

All user-facing applications must:
- Support keyboard navigation
- Provide screen reader compatibility
- Maintain sufficient color contrast ratios
- Include alt text for images
- Support text resizing and zoom
- Provide closed captions for video content

### Data Privacy & Protection

**Compliance Frameworks**:
- ✅ GDPR (General Data Protection Regulation)
- ✅ CCPA (California Consumer Privacy Act)
- ✅ SOC 2 Type II principles

**Requirements**:
- Privacy by design and default
- Data minimization principles
- User consent management
- Right to access, correct, and delete data
- Data breach notification procedures
- Regular privacy impact assessments

---

## 📞 Contact & Exceptions

### Policy Questions

For questions about these policies, contact:

- **General Inquiries**: [hello@violet-site-systems.dev](mailto:hello@violet-site-systems.dev)
- **Technical Questions**: [tech@violet-site-systems.dev](mailto:tech@violet-site-systems.dev)
- **Policy Clarifications**: [governance@violet-site-systems.dev](mailto:governance@violet-site-systems.dev)

### Requesting Policy Exceptions

In exceptional circumstances, policy exceptions may be granted:

1. **Submit Request**: Email governance@violet-site-systems.dev with:
   - Specific policy requiring exception
   - Detailed justification
   - Proposed alternative approach
   - Time frame needed
   - Risk assessment

2. **Review Process**: Requests are reviewed by the governance team

3. **Decision Timeline**: Response within 5-7 business days

4. **Documentation**: Approved exceptions are documented with rationale

### Policy Updates

These policies are reviewed and updated quarterly. Significant changes are communicated to all organization members via:

- GitHub Discussions
- Organization announcements
- Email notifications
- Team meetings

**Last Updated**: December 2025  
**Version**: 1.0  
**Next Review**: March 2026

---

## 📚 Related Documentation

- [Copilot Configuration Guide](./COPILOT_CONFIGURATION.md)
- [Sustainability Licenses](./SUSTAINABILITY_LICENSES.md)
- [License Library](../licenses/)

---

<div align="center">

**Questions or Feedback?**  
We welcome input on our policies. Open a [Discussion](https://github.com/orgs/Violet-Site-Systems/discussions) or contact the governance team.

---

**© 2024 Violet Site Systems • Building the Future with AI**

</div>
