# Horizon Documentation

[![CI](https://github.com/HorizonSec/horizon-documentation/workflows/CI/badge.svg)](https://github.com/HorizonSec/horizon-documentation/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

Welcome to the **Horizon Documentation** repository! This is the centralized documentation hub for all modules and projects within the HorizonSec organization. This repository ensures easy access, collaboration, and maintenance of documentation across the entire Horizon ecosystem.

### Key Features

- **Centralized Access**: All module documentation in one place
- **Easy Discovery**: Comprehensive module index for quick navigation
- **Standardized Structure**: Consistent documentation format across all modules
- **Version Control**: Git-based documentation management with full history
- **Collaboration**: Simple contribution workflow for documentation updates
- **Quality Assurance**: Automated CI checks for documentation standards

## Getting Started

### For Documentation Users

If you're looking for documentation on a specific Horizon module:

1. **Check the [Module Index](MODULE_INDEX.md)** - Central catalog of all documented modules
2. **Browse by category** - Navigate to `docs/modules/` to explore all modules
3. **Use search** - Use GitHub's search feature to find specific topics
4. **Read guides** - Check `docs/guides/` for tutorials and best practices

### For Documentation Contributors

If you want to add or update documentation:

1. **Read the [Contributing Guidelines](CONTRIBUTING.md)** - Learn our contribution process
2. **Follow the [Style Guide](docs/guides/STYLE_GUIDE.md)** - Ensure consistency
3. **Use the template** - See `docs/modules/example-module/` for structure
4. **Submit a pull request** - Follow our PR template

## Repository Structure

See [FOLDER_STRUCTURE.md](FOLDER_STRUCTURE.md) for a detailed explanation of the repository structure.

### Quick Overview

```
horizon-documentation/
├── docs/
│   ├── modules/          # Module-specific documentation
│   ├── guides/           # User guides and tutorials
│   ├── api/              # API documentation
│   └── architecture/     # Architecture documents
├── MODULE_INDEX.md       # Central index of all modules
├── README.md            # This file
├── CONTRIBUTING.md      # Contribution guidelines
└── .github/             # GitHub configuration
```

## Documentation Structure

### Module Documentation

Each module has its own directory under `docs/modules/` with:
- README.md - Main module documentation
- Configuration guides
- API reference
- Examples and tutorials
- Troubleshooting guides

### Guides and Tutorials

The `docs/guides/` directory contains:
- Getting started guides
- Best practices
- Style guides
- Integration tutorials

## Adding Module Documentation

To add documentation for a new module:

1. **Create module directory**:
   ```bash
   mkdir -p docs/modules/your-module-name
   ```

2. **Create README.md** using the [example template](docs/modules/example-module/README.md)

3. **Update the [Module Index](MODULE_INDEX.md)** with your module information

4. **Submit a pull request** following the [contribution guidelines](CONTRIBUTING.md)

See the [Style Guide](docs/guides/STYLE_GUIDE.md) for documentation standards.

## Finding Documentation

### Browse by Module

- Visit the [Module Index](MODULE_INDEX.md) for a complete list
- Navigate to `docs/modules/` directory
- Check module categories (core, integration, utility)

### Search

Use GitHub's search functionality:
- Search by module name
- Search by feature or keyword
- Filter by file type or path

## Contributing

We welcome contributions to improve documentation! Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for details on:
- How to add or update module documentation
- Documentation standards and style guide
- Pull request process
- Best practices for documentation

### Documentation Guidelines

- Follow the [Style Guide](docs/guides/STYLE_GUIDE.md)
- Use the [example module template](docs/modules/example-module/README.md)
- Keep documentation up-to-date with code changes
- Include practical examples and use cases
- Test all code examples before submitting

## Code of Conduct

This project adheres to a Code of Conduct that all contributors are expected to follow. Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) to understand the expected behavior when participating in this project.

## Security

If you discover a security vulnerability, please follow the guidelines in [SECURITY.md](SECURITY.md) to report it responsibly.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For documentation-related questions:
- Check the [Module Index](MODULE_INDEX.md) for module documentation
- Review the [Style Guide](docs/guides/STYLE_GUIDE.md) for documentation standards
- Open an issue using the appropriate template
- Contact the HorizonSec documentation team

## Acknowledgments

- Thanks to all contributors who help maintain and improve Horizon documentation
- Built with ❤️ by the HorizonSec team