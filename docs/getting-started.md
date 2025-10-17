# Getting Started

Welcome to the Horizon Security Framework! Follow these steps to get started:

## Prerequisites

Before you begin, ensure you have:

- Python 3.8 or higher
- Git installed on your system
- Basic understanding of security concepts
- Access to the HorizonSec repositories

## Installation

### Using Hatch (Recommended)

The Horizon documentation is managed using [Hatch](https://hatch.pypa.io/), a modern Python project manager.

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

### Manual Installation

If you prefer not to use Hatch:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/HorizonSec/horizon-documentation.git
   cd horizon-documentation
   ```

2. **Install dependencies**:
   ```bash
   pip install mkdocs mkdocs-material
   ```

3. **Serve the documentation**:
   ```bash
   mkdocs serve
   ```

## Explore the Modules

The Horizon Security Framework consists of four main modules:

1. **[GAIA Framework](modules/gaia-framework.md)** - Start here for the core framework
2. **[DEMETER Infrastructure Scan](modules/demeter-infra-scan.md)** - Infrastructure security assessment
3. **[HADES Endpoint Security](modules/hades-endpoint.md)** - Endpoint protection and monitoring
4. **[ARTEMIS Static Code Analysis](modules/artemis-static-code.md)** - Application security testing

## Next Steps

- Read the [Modules Overview](modules/index.md) to understand the framework architecture
- Check the individual module documentation for detailed setup instructions
- Join our community and contribute to the project

## Build and Deploy

### Build the Documentation

```bash
hatch run build
```

or with MkDocs directly:

```bash
mkdocs build
```

### Deploy to GitHub Pages

```bash
hatch run deploy
```

or with MkDocs directly:

```bash
mkdocs gh-deploy
```

## Getting Help

If you encounter any issues:

- Check the [GitHub Issues](https://github.com/HorizonSec/horizon-documentation/issues)
- Review the module-specific documentation
- Reach out to the HorizonSec team
