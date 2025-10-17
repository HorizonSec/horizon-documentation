# Folder Structure

This document describes the organization and structure of the Horizon Template repository. Understanding this structure will help you navigate the codebase and know where to place new files.

## Repository Structure

```
horizon-template/
├── .github/                          # GitHub-specific configurations
│   ├── ISSUE_TEMPLATE/              # Issue templates for bug reports and feature requests
│   │   ├── bug_report.md           # Template for reporting bugs
│   │   └── feature_request.md      # Template for requesting features
│   ├── workflows/                   # GitHub Actions workflows
│   │   └── ci.yml                  # Continuous integration workflow
│   └── PULL_REQUEST_TEMPLATE.md    # Template for pull requests
├── CODE_OF_CONDUCT.md               # Community code of conduct
├── CONTRIBUTING.md                  # Contribution guidelines
├── FOLDER_STRUCTURE.md              # This file - describes repository structure
├── LICENSE                          # MIT License
├── README.md                        # Main project documentation
├── SECURITY.md                      # Security policy and vulnerability reporting
└── .gitignore                       # Git ignore patterns
```

## Directory Descriptions

### `.github/`

Contains all GitHub-specific configuration files:

- **`ISSUE_TEMPLATE/`**: Templates for creating structured issues
  - `bug_report.md`: Helps users report bugs with all necessary information
  - `feature_request.md`: Guides users in proposing new features

- **`workflows/`**: GitHub Actions workflow definitions
  - `ci.yml`: Continuous integration workflow that runs tests and checks

- **`PULL_REQUEST_TEMPLATE.md`**: Template that appears when creating pull requests

### Root Directory Files

#### Documentation Files

- **`README.md`**: The main entry point for the repository. Contains:
  - Project overview
  - Installation instructions
  - Usage guidelines
  - Links to other documentation

- **`CONTRIBUTING.md`**: Guidelines for contributors including:
  - How to report bugs
  - How to suggest features
  - Development workflow
  - Coding standards
  - Commit message guidelines

- **`CODE_OF_CONDUCT.md`**: Defines expected behavior for community members:
  - Standards of behavior
  - Enforcement policies
  - Reporting guidelines

- **`SECURITY.md`**: Security policy including:
  - How to report vulnerabilities
  - Supported versions
  - Security best practices

- **`FOLDER_STRUCTURE.md`**: This document explaining the repository organization

- **`LICENSE`**: MIT License for the project

#### Configuration Files

- **`.gitignore`**: Specifies files and directories that Git should ignore:
  - Operating system files
  - IDE configurations
  - Build artifacts
  - Dependencies
  - Temporary files
  - Environment variables

## File Naming Conventions

- **Markdown files**: Use `UPPERCASE.md` for root-level documentation (e.g., `README.md`, `CONTRIBUTING.md`)
- **Template files**: Use `lowercase_with_underscores.md` (e.g., `bug_report.md`, `feature_request.md`)
- **Configuration files**: Follow the convention of the tool (e.g., `.gitignore`, `ci.yml`)

## When Using This Template

When you use this template for a new project, you may want to add:

### Source Code Directory

```
src/                    # Source code directory
├── components/        # Reusable components
├── utils/            # Utility functions
├── services/         # Service layer
└── ...               # Other source code
```

### Tests Directory

```
tests/                 # Test files
├── unit/             # Unit tests
├── integration/      # Integration tests
└── e2e/              # End-to-end tests
```

### Documentation Directory

```
docs/                  # Additional documentation
├── api/              # API documentation
├── guides/           # User guides
└── architecture/     # Architecture documentation
```

### Build and Distribution

```
dist/                  # Built/compiled files (should be in .gitignore)
build/                 # Build output (should be in .gitignore)
public/               # Public assets
assets/               # Static assets
```

### Configuration

```
config/               # Configuration files
├── development/      # Development environment config
├── staging/         # Staging environment config
└── production/      # Production environment config
```

## Best Practices

1. **Keep root directory clean**: Only essential files should be in the root
2. **Organize by feature**: Group related files together
3. **Use meaningful names**: File and directory names should be self-explanatory
4. **Document structure**: Update this file when adding new directories
5. **Ignore generated files**: Add build artifacts and dependencies to `.gitignore`
6. **Follow conventions**: Maintain consistency with established patterns

## Adding New Directories

When adding new directories to your project:

1. Create the directory with a clear, descriptive name
2. Add a `README.md` in the directory explaining its purpose
3. Update this `FOLDER_STRUCTURE.md` file with the new directory
4. Update `.gitignore` if the directory contains generated files
5. Document any special conventions for files in that directory

## Project-Specific Customization

This is a template repository. When using it for a specific project:

- [ ] Customize the folder structure to match your project needs
- [ ] Update this document to reflect your actual structure
- [ ] Remove sections that don't apply to your project
- [ ] Add project-specific directories and documentation
- [ ] Update the README.md with project-specific information

## Questions?

If you have questions about where a file should go or how to organize your code, refer to:
- This document
- The `CONTRIBUTING.md` file for contribution guidelines
- Open an issue to discuss structural changes
