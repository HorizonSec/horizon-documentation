# Security Policy

## Reporting Security Vulnerabilities

The HorizonSec team takes security vulnerabilities seriously. We appreciate your efforts to responsibly disclose your findings and will make every effort to acknowledge your contributions.

### How to Report a Security Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please report them via one of the following methods:

1. **Email**: Send a detailed report to [INSERT SECURITY EMAIL]
2. **GitHub Security Advisory**: Use the [GitHub Security Advisory](https://github.com/HorizonSec/horizon-template/security/advisories/new) feature (preferred)

### What to Include in Your Report

To help us better understand and resolve the issue, please include as much of the following information as possible:

- **Type of vulnerability** (e.g., SQL injection, XSS, authentication bypass, etc.)
- **Full paths of source file(s)** related to the vulnerability
- **Location of the affected source code** (tag/branch/commit or direct URL)
- **Step-by-step instructions** to reproduce the issue
- **Proof-of-concept or exploit code** (if possible)
- **Impact of the vulnerability** and how an attacker might exploit it
- **Any special configuration** required to reproduce the issue

### What to Expect

After you submit a report, you can expect:

1. **Acknowledgment**: We will acknowledge receipt of your vulnerability report within 48 hours
2. **Assessment**: We will investigate and assess the vulnerability within 5 business days
3. **Updates**: We will keep you informed of our progress throughout the process
4. **Resolution**: We will work to fix the vulnerability and coordinate disclosure timing with you

### Disclosure Policy

- We ask that you give us reasonable time to address the vulnerability before any public disclosure
- We will credit you for the discovery (if desired) when we publicly disclose the vulnerability
- We follow a coordinated disclosure process and aim to:
  - Acknowledge reports within 48 hours
  - Provide an initial assessment within 5 business days
  - Work towards a fix and coordinate public disclosure

### Supported Versions

We provide security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
| < Latest| :x:                |

We recommend always using the latest version of the template to ensure you have the most recent security updates.

## Security Best Practices

When using this template, consider the following security best practices:

### For Repository Maintainers

- **Keep dependencies updated**: Regularly update dependencies to patch known vulnerabilities
- **Enable security features**: Turn on GitHub's security features like Dependabot, code scanning, and secret scanning
- **Review code carefully**: Thoroughly review all pull requests before merging
- **Use branch protection**: Enable branch protection rules on your main branch
- **Limit access**: Grant repository access only to those who need it
- **Enable 2FA**: Require two-factor authentication for all contributors

### For Contributors

- **Never commit secrets**: Don't commit API keys, passwords, or other sensitive data
- **Review before pushing**: Double-check your changes before pushing commits
- **Use SSH keys**: Prefer SSH keys over HTTPS for Git operations
- **Keep your tools updated**: Use the latest versions of Git and development tools
- **Report suspicious activity**: If you notice anything unusual, report it immediately

## Security-Related Configuration

This template includes several security-related configurations:

- **`.gitignore`**: Configured to exclude common files that might contain secrets
- **GitHub Actions**: Workflows are configured with minimal necessary permissions
- **Dependabot**: Can be enabled to automatically check for vulnerable dependencies

## Additional Resources

- [GitHub Security Best Practices](https://docs.github.com/en/code-security/getting-started/github-security-features)
- [OWASP Top Ten](https://owasp.org/www-project-top-ten/)
- [CWE Top 25](https://cwe.mitre.org/top25/archive/2023/2023_top25_list.html)

## Questions?

If you have questions about this security policy, please open an issue (for non-sensitive questions) or contact the maintainers directly.

Thank you for helping keep HorizonSec and our community safe!
