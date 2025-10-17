# Contributing to Horizon Template

First off, thank you for considering contributing to the Horizon Template! It's people like you that make this template better for everyone in the HorizonSec organization.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Features](#suggesting-features)
  - [Submitting Pull Requests](#submitting-pull-requests)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Message Guidelines](#commit-message-guidelines)

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

## How Can I Contribute?

### Reporting Bugs

Bugs are tracked as GitHub issues. When creating a bug report, please use the bug report template and include:

- **Clear and descriptive title** for the issue
- **Detailed description** of the problem
- **Steps to reproduce** the behavior
- **Expected behavior** vs actual behavior
- **Screenshots** if applicable
- **Environment details** (OS, browser, versions, etc.)
- **Additional context** that might be helpful

**Before submitting a bug report:**
- Check the existing issues to avoid duplicates
- Verify the bug in the latest version
- Collect relevant information about your environment

### Suggesting Features

Feature requests are also tracked as GitHub issues. When creating a feature request, please use the feature request template and include:

- **Clear and descriptive title** for the suggestion
- **Detailed description** of the proposed feature
- **Use cases** explaining why this feature would be useful
- **Alternatives** you've considered
- **Additional context** like mockups or examples

**Before submitting a feature request:**
- Check if the feature already exists
- Review existing feature requests
- Consider if the feature aligns with the project's goals

### Submitting Pull Requests

We actively welcome your pull requests! Here's how to contribute code:

1. **Fork the repository** and create your branch from `main`
2. **Make your changes** following our coding standards
3. **Test your changes** thoroughly
4. **Update documentation** as needed
5. **Write clear commit messages** following our guidelines
6. **Submit a pull request** using the PR template

**Pull Request Process:**
- Fill out the PR template completely
- Link related issues using keywords (e.g., "Fixes #123")
- Ensure all tests pass
- Request review from maintainers
- Address review feedback promptly
- Keep your PR focused on a single concern

**Pull Request Requirements:**
- [ ] Code follows the project's coding standards
- [ ] Self-review of code completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests added/updated and passing
- [ ] Dependent changes merged and published

## Development Workflow

### Setting Up Development Environment

1. Clone your fork:
   ```bash
   git clone https://github.com/your-username/horizon-template.git
   cd horizon-template
   ```

2. Add upstream remote:
   ```bash
   git remote add upstream https://github.com/HorizonSec/horizon-template.git
   ```

3. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Making Changes

1. Make your changes in your feature branch
2. Test your changes locally
3. Commit your changes with clear messages
4. Push to your fork

### Syncing with Upstream

Keep your fork synchronized with the upstream repository:

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

## Coding Standards

### General Guidelines

- **Write clear, readable code** - Code is read more often than written
- **Keep it simple** - Avoid unnecessary complexity
- **Follow existing patterns** - Maintain consistency with the codebase
- **Comment wisely** - Explain why, not what
- **Test your code** - Write tests for new functionality

### Style Guide

- Use consistent indentation (spaces vs tabs should match existing code)
- Follow language-specific conventions and best practices
- Keep line length reasonable (typically 80-120 characters)
- Use meaningful variable and function names
- Organize imports/includes logically

### Documentation

- Update README.md for user-facing changes
- Update inline documentation for code changes
- Add comments for complex logic
- Keep documentation concise and clear

## Commit Message Guidelines

Write clear, concise commit messages that explain the changes:

### Format

```
<type>: <subject>

<body>

<footer>
```

### Type

- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Code style changes (formatting, etc.)
- **refactor**: Code refactoring
- **test**: Adding or updating tests
- **chore**: Maintenance tasks

### Examples

```
feat: add bug report template

Added a comprehensive bug report template to improve issue quality
and make it easier for contributors to report issues effectively.

Closes #123
```

```
fix: correct typo in README

Fixed spelling error in installation instructions.
```

### Best Practices

- Use imperative mood ("add feature" not "added feature")
- Keep subject line under 50 characters
- Capitalize the subject line
- Don't end subject line with a period
- Separate subject from body with a blank line
- Wrap body at 72 characters
- Use body to explain what and why, not how

## Questions?

If you have questions about contributing, feel free to:
- Open an issue with your question
- Reach out to the maintainers
- Check existing documentation

Thank you for contributing to Horizon Template! 🎉
