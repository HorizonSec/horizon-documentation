# Horizon Security Documentation

[![CI](https://github.com/HorizonSec/horizon-documentation/workflows/CI/badge.svg)](https://github.com/HorizonSec/horizon-documentation/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

Welcome to the **Horizon Security Documentation** repository! This is the centralized documentation hub for the Horizon Security Framework, providing comprehensive documentation for all modules and components.

The Horizon Security Framework consists of four core modules:
- **GAIA Framework** - Security orchestration and management
- **DEMETER Infrastructure Scan** - Infrastructure security assessment
- **HADES Endpoint Security** - Endpoint detection and response
- **ARTEMIS Static Code Analysis** - Application security testing

## Documentation Site

The documentation is built with [MkDocs](https://www.mkdocs.org/) and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).

Visit the live documentation at: **https://horizonsec.github.io/horizon-documentation**

## Getting Started

### Using Hatch (Recommended)

This project uses [Hatch](https://hatch.pypa.io/) for project management.

1. **Install Hatch**:
   ```bash
   pip install hatch
   ```

2. **Clone the repository**:
   ```bash
   git clone https://github.com/HorizonSec/horizon-documentation.git
   cd horizon-documentation
   ```

3. **Serve the documentation locally**:
   ```bash
   hatch run serve
   ```
   
   The documentation will be available at `http://127.0.0.1:8000`

### Manual Setup

If you prefer not to use Hatch:

1. **Install dependencies**:
   ```bash
   pip install mkdocs mkdocs-material
   ```

2. **Serve locally**:
   ```bash
   mkdocs serve
   ```

## Available Commands

### Using Hatch

```bash
# Serve documentation locally (with live reload)
hatch run serve

# Build documentation
hatch run build

# Deploy to GitHub Pages
hatch run deploy

# Clean build artifacts
hatch run clean
```

### Using MkDocs directly

```bash
# Serve documentation locally
mkdocs serve

# Build documentation
mkdocs build

# Deploy to GitHub Pages
mkdocs gh-deploy
```

## Documentation Structure

```
docs/
├── index.md                    # Home page
├── getting-started.md          # Getting started guide
└── modules/                    # Module documentation
    ├── index.md                # Modules overview
    ├── gaia-framework.md       # GAIA Framework
    ├── demeter-infra-scan.md   # DEMETER Infrastructure Scan
    ├── hades-endpoint.md       # HADES Endpoint Security
    └── artemis-static-code.md  # ARTEMIS Static Code Analysis
```

## Contributing

We welcome contributions from the community! Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for details on:
- How to submit issues
- How to create pull requests
- Documentation standards and best practices
- Development workflow

## Code of Conduct

This project adheres to a Code of Conduct that all contributors are expected to follow. Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) to understand the expected behavior when participating in this project.

## Security

If you discover a security vulnerability, please follow the guidelines in [SECURITY.md](SECURITY.md) to report it responsibly.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For questions, issues, or feature requests:
- Open an issue using the appropriate template
- Contact the HorizonSec team
- Check existing documentation and issues

## Acknowledgments

- Thanks to all contributors who help improve this template
- Built with ❤️ by the HorizonSec team