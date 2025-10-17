# Horizon Core

Horizon Core is the foundational template repository for the HorizonSec organization, providing a standardized starting point for all new projects and modules within the Horizon Security Framework.

## Overview

Horizon Core serves as the organizational template that ensures consistency, quality, and best practices across all HorizonSec projects. It provides the essential structure, documentation, and workflows that every project in the organization should have.

## Key Components

### Project Structure
Horizon Core includes:
- **Comprehensive Documentation**: README, CONTRIBUTING, CODE_OF_CONDUCT
- **Issue Templates**: Bug reports and feature request templates
- **Pull Request Templates**: Standardized PR submission format
- **GitHub Actions CI**: Automated testing and validation workflows
- **Security Policy**: Guidelines for responsible vulnerability disclosure
- **Standard .gitignore**: Comprehensive ignore patterns for multiple languages
- **MIT License**: Open-source licensing

### Documentation Standards

All projects derived from Horizon Core maintain consistent documentation:

```
project-root/
├── README.md               # Project overview and quick start
├── CONTRIBUTING.md         # Contribution guidelines
├── CODE_OF_CONDUCT.md     # Community standards
├── SECURITY.md            # Security policy
├── LICENSE                # MIT License
├── FOLDER_STRUCTURE.md    # Repository organization
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md
    │   └── feature_request.md
    └── PULL_REQUEST_TEMPLATE.md
```

### CI/CD Workflows

Horizon Core provides automated workflows for:
- **Linting**: Code style and formatting checks
- **Testing**: Automated test execution
- **Security**: Basic security scanning
- **Build Validation**: Ensure project builds successfully

## Using Horizon Core as a Template

### For New Projects

1. **Create from Template**
   - Navigate to [HorizonSec/horizon-core](https://github.com/HorizonSec/horizon-core)
   - Click "Use this template"
   - Name your new repository
   - Choose visibility settings

2. **Initial Setup**
   ```bash
   # Clone your new repository
   git clone https://github.com/HorizonSec/your-new-project.git
   cd your-new-project
   
   # Customize the template
   # Update README.md with project-specific information
   # Modify LICENSE if needed
   # Update SECURITY.md with your contact information
   ```

3. **Customize CI/CD**
   - Edit `.github/workflows/ci.yml` for project-specific tests
   - Add language-specific linting tools
   - Configure deployment workflows as needed

### Best Practices

#### Documentation
- Keep README.md up to date with current features
- Document all configuration options
- Include code examples and usage patterns
- Maintain a changelog for version tracking

#### Issue Management
- Use provided templates for consistency
- Label issues appropriately
- Link issues to pull requests
- Keep issue descriptions clear and actionable

#### Pull Requests
- Follow the PR template
- Include tests for new features
- Update documentation
- Ensure CI passes before requesting review

## Integration with Horizon Security Framework

Horizon Core is used as the foundation for all modules in the Horizon Security Framework:

### Framework Modules Built on Horizon Core

- **[GAIA Framework](../modules/gaia-framework.md)** - Security orchestration
- **[DEMETER Infrastructure Scan](../modules/demeter-infra-scan.md)** - Infrastructure scanning
- **[HADES Endpoint Security](../modules/hades-endpoint.md)** - Endpoint protection
- **[ARTEMIS Static Code Analysis](../modules/artemis-static-code.md)** - Code analysis

Each module starts with the Horizon Core template and extends it with module-specific functionality while maintaining the core structure and standards.

## Features

### Automated Quality Checks

The CI workflow includes:

```yaml
# Automated checks on every push and PR
- File formatting validation
- Trailing whitespace detection
- Markdown linting
- Large file detection
- Required file verification
- Content validation
- Basic security scanning
```

### Community Guidelines

Horizon Core enforces:
- **Code of Conduct**: Professional and inclusive community standards
- **Contributing Guide**: Clear process for contributions
- **Security Policy**: Responsible disclosure procedures
- **License Compliance**: MIT License for all projects

## Customization Guide

### Adding Project-Specific Files

```bash
# Example: Adding a Python project structure
your-project/
├── src/
│   └── your_module/
├── tests/
├── requirements.txt
├── setup.py
└── pyproject.toml
```

### Extending CI Workflows

```yaml
# .github/workflows/ci.yml
jobs:
  python-tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest
```

### Adding Language-Specific Configurations

#### Python Projects
```bash
# Add to .gitignore
__pycache__/
*.py[cod]
venv/
.pytest_cache/

# Add configuration files
pyproject.toml
setup.py
requirements.txt
```

#### Node.js Projects
```bash
# Add to .gitignore
node_modules/
dist/
*.log

# Add configuration files
package.json
tsconfig.json
.eslintrc.js
```

#### Go Projects
```bash
# Add to .gitignore
*.exe
*.test
vendor/

# Add configuration files
go.mod
go.sum
```

## Governance

### Repository Maintenance

Horizon Core is maintained by the HorizonSec team with:
- Regular updates to dependencies
- Security patches
- CI/CD improvements
- Documentation enhancements

### Version Updates

When Horizon Core is updated:
1. Changes are documented in the repository
2. Projects using the template are notified
3. Migration guides are provided when needed
4. Breaking changes follow semantic versioning

### Contributing to Horizon Core

Contributions to improve the template are welcome:

```bash
# Fork the repository
git clone https://github.com/YourUsername/horizon-core.git
cd horizon-core

# Create a feature branch
git checkout -b feature/improvement

# Make your changes
# Test thoroughly
# Submit a PR with clear description
```

## Support and Resources

### Getting Help

- **Documentation**: [HorizonSec Documentation](https://horizonsec.github.io/horizon-documentation)
- **Issues**: [GitHub Issues](https://github.com/HorizonSec/horizon-core/issues)
- **Discussions**: [GitHub Discussions](https://github.com/HorizonSec/horizon-core/discussions)
- **Team Contact**: security@horizonsec.org

### Additional Resources

- [GitHub Template Documentation](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Semantic Versioning](https://semver.org/)
- [Conventional Commits](https://www.conventionalcommits.org/)

## Examples

### Projects Using Horizon Core

All HorizonSec projects are built on Horizon Core:

| Project | Type | Status |
|---------|------|--------|
| horizon-documentation | Documentation | Active |
| gaia-framework | Security Framework | In Development |
| demeter-infra-scan | Infrastructure Scanner | In Development |
| hades-endpoint | Endpoint Security | In Development |
| artemis-static-code | Code Analysis | In Development |

### Success Stories

Horizon Core has enabled:
- ✅ Consistent project structure across the organization
- ✅ Faster project bootstrapping (minutes instead of hours)
- ✅ Improved code quality through automated checks
- ✅ Better community engagement with clear guidelines
- ✅ Reduced security issues through built-in scanning

## Roadmap

Future enhancements to Horizon Core:

- [ ] Multi-language templates (Python, Go, JavaScript, Rust)
- [ ] Enhanced security scanning with CodeQL
- [ ] Automated dependency updates with Dependabot
- [ ] Performance testing templates
- [ ] Container and Kubernetes configurations
- [ ] Advanced GitHub Actions workflows
- [ ] Integration testing templates
- [ ] Documentation site generation

## License

Horizon Core is licensed under the MIT License. See the [LICENSE](https://github.com/HorizonSec/horizon-core/blob/main/LICENSE) file for details.

## Acknowledgments

Horizon Core is built with inspiration from:
- GitHub's recommended repository templates
- Industry best practices for open-source projects
- Community feedback and contributions
- Lessons learned from HorizonSec project development

---

**Next Steps**: Check out the [Getting Started Guide](../getting-started.md) to begin using Horizon Core for your next project.
