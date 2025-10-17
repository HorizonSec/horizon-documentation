# Folder Structure

This document describes the organization and structure of the Horizon Documentation repository. Understanding this structure will help you navigate the documentation and know where to add new content.

## Repository Structure

```
horizon-documentation/
├── .github/                          # GitHub-specific configurations
│   ├── ISSUE_TEMPLATE/              # Issue templates
│   │   ├── bug_report.md           # Template for reporting documentation issues
│   │   └── feature_request.md      # Template for requesting new documentation
│   ├── workflows/                   # GitHub Actions workflows
│   │   └── ci.yml                  # Documentation validation workflow
│   └── PULL_REQUEST_TEMPLATE.md    # Template for documentation PRs
├── docs/                            # Main documentation directory
│   ├── modules/                     # Module-specific documentation
│   │   └── example-module/         # Example module documentation
│   │       └── README.md           # Module documentation template
│   ├── guides/                      # User guides and tutorials
│   │   └── STYLE_GUIDE.md          # Documentation style guide
│   ├── api/                         # API documentation
│   └── architecture/                # Architecture and design documents
├── CODE_OF_CONDUCT.md               # Community code of conduct
├── CONTRIBUTING.md                  # Contribution guidelines for documentation
├── FOLDER_STRUCTURE.md              # This file - describes repository structure
├── LICENSE                          # MIT License
├── MODULE_INDEX.md                  # Central index of all documented modules
├── README.md                        # Main repository documentation
├── SECURITY.md                      # Security policy and vulnerability reporting
└── .gitignore                       # Git ignore patterns
```

## Directory Descriptions

### `.github/`

Contains all GitHub-specific configuration files:

- **`ISSUE_TEMPLATE/`**: Templates for creating structured issues
  - `bug_report.md`: Helps users report documentation issues
  - `feature_request.md`: Guides users in requesting new documentation

- **`workflows/`**: GitHub Actions workflow definitions
  - `ci.yml`: Automated checks for documentation quality and structure

- **`PULL_REQUEST_TEMPLATE.md`**: Template for documentation pull requests

### `docs/`

The main documentation directory containing all module and guide documentation:

- **`modules/`**: Module-specific documentation
  - Each module has its own subdirectory
  - Contains README.md with complete module documentation
  - May include additional files for API docs, examples, etc.
  - Example: `docs/modules/example-module/`

- **`guides/`**: User guides, tutorials, and best practices
  - `STYLE_GUIDE.md`: Documentation writing standards
  - Getting started guides
  - Integration tutorials
  - Best practices documentation

- **`api/`**: API documentation and references
  - API endpoint documentation
  - API usage guides
  - Authentication guides

- **`architecture/`**: Architecture and design documentation
  - System architecture diagrams
  - Design decisions
  - Technical specifications

### Root Directory Files

#### Documentation Files

- **`README.md`**: The main entry point for the repository. Contains:
  - Repository overview and purpose
  - Quick start guide
  - Navigation help
  - Links to key documentation

- **`MODULE_INDEX.md`**: Central catalog of all documented modules:
  - Complete list of modules with descriptions
  - Direct links to module documentation
  - Module categories and organization
  - Instructions for adding new modules

- **`CONTRIBUTING.md`**: Guidelines for documentation contributors:
  - How to add new documentation
  - Documentation standards
  - Pull request process
  - Review guidelines

- **`CODE_OF_CONDUCT.md`**: Expected behavior for contributors:
  - Community standards
  - Enforcement policies
  - Reporting guidelines

- **`SECURITY.md`**: Security policy including:
  - How to report vulnerabilities
  - Supported versions
  - Security best practices

- **`FOLDER_STRUCTURE.md`**: This document explaining the repository organization

- **`LICENSE`**: MIT License for the documentation

#### Configuration Files

- **`.gitignore`**: Specifies files and directories that Git should ignore:
  - Operating system files
  - IDE configurations
  - Build artifacts
  - Dependencies
  - Temporary files
  - Environment variables

## File Naming Conventions

- **Markdown files**: Use `UPPERCASE.md` for root-level documentation (e.g., `README.md`, `MODULE_INDEX.md`)
- **Module directories**: Use `lowercase-with-hyphens` (e.g., `example-module`, `api-gateway`)
- **Guide files**: Use `UPPERCASE.md` for main guides (e.g., `STYLE_GUIDE.md`)
- **Configuration files**: Follow the convention of the tool (e.g., `.gitignore`, `ci.yml`)

## Documentation Organization

### Module Documentation Structure

Each module follows this standard structure:

```
docs/modules/module-name/
├── README.md              # Main module documentation
├── QUICKSTART.md          # Quick start guide (optional)
├── API.md                 # API reference (optional)
├── CONFIGURATION.md       # Configuration guide (optional)
├── EXAMPLES.md            # Usage examples (optional)
├── TROUBLESHOOTING.md     # Common issues (optional)
└── assets/               # Images, diagrams, etc. (optional)
```

### Required Content in Module README

Every module's README.md must include:

1. **Overview**: What the module does
2. **Installation**: How to install
3. **Quick Start**: Simple example
4. **Configuration**: Configuration options
5. **Usage**: How to use the module
6. **API Reference**: Key APIs (or link to API.md)
7. **Troubleshooting**: Common issues

### Guide Documentation

Guides in `docs/guides/` should:
- Be focused on a specific topic
- Include practical examples
- Link to related modules
- Follow the style guide

## Best Practices

1. **Keep structure consistent**: Follow the established module documentation pattern
2. **Organize by module**: Each module gets its own directory
3. **Use meaningful names**: Directory and file names should be self-explanatory
4. **Update the index**: Always update MODULE_INDEX.md when adding modules
5. **Follow the style guide**: Maintain consistency with docs/guides/STYLE_GUIDE.md
6. **Include examples**: Add practical code examples in all documentation
7. **Link between docs**: Create cross-references to related documentation

## Adding New Content

### Adding a New Module

1. Create module directory: `docs/modules/module-name/`
2. Copy the example template from `docs/modules/example-module/README.md`
3. Fill in all required sections
4. Add any additional documentation files as needed
5. Update `MODULE_INDEX.md` with the new module
6. Submit a pull request

### Adding a New Guide

1. Create the guide in `docs/guides/`
2. Follow the style guide for formatting
3. Include practical examples
4. Link from README.md or MODULE_INDEX.md as appropriate
5. Submit a pull request

### Adding API Documentation

1. Create or update files in `docs/api/`
2. Follow REST API documentation standards
3. Include request/response examples
4. Document authentication requirements
5. Link from relevant module documentation

## Repository-Specific Conventions

This documentation repository follows these conventions:

### Documentation Status

Each module in MODULE_INDEX.md has a status:
- **Active**: Module is actively maintained and documented
- **Deprecated**: Module is deprecated, docs kept for reference
- **In Development**: Documentation is being written
- **Archived**: Module is no longer maintained

### Version Information

- Document version-specific features in module docs
- Keep a CHANGELOG.md for significant documentation updates
- Note breaking changes clearly

### Cross-References

- Use relative links between documents
- Link to specific sections using anchors
- Keep links up-to-date when moving files

## Questions?

If you have questions about where documentation should go:
- Check the [Style Guide](docs/guides/STYLE_GUIDE.md)
- Review the [example module](docs/modules/example-module/)
- Refer to [CONTRIBUTING.md](CONTRIBUTING.md)
- Open an issue to discuss structural changes
