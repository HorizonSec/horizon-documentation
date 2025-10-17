# Modules Overview

The Horizon Security Framework is composed of four integrated modules that work together to provide comprehensive security coverage for your infrastructure and applications.

## Core Modules

### GAIA Framework
The foundational module that provides core security orchestration and management capabilities. GAIA serves as the central hub for coordinating security operations across all modules.

**Key Features:**
- Security orchestration and automation
- Centralized policy management
- Cross-module integration
- Real-time security monitoring

[Learn more about GAIA Framework →](gaia-framework.md)

### DEMETER Infrastructure Scan
Infrastructure security scanning and assessment module that identifies vulnerabilities and misconfigurations in your cloud and on-premises infrastructure.

**Key Features:**
- Automated infrastructure scanning
- Cloud security posture management
- Configuration compliance checking
- Vulnerability assessment

[Learn more about DEMETER →](demeter-infra-scan.md)

### HADES Endpoint Security
Comprehensive endpoint detection and response (EDR) solution that protects workstations and servers from advanced threats.

**Key Features:**
- Real-time threat detection
- Behavioral analysis
- Incident response automation
- Forensic capabilities

[Learn more about HADES →](hades-endpoint.md)

### ARTEMIS Static Code Analysis
Static application security testing (SAST) module that analyzes source code to identify security vulnerabilities before deployment.

**Key Features:**
- Multi-language support
- Security vulnerability detection
- Code quality analysis
- Integration with CI/CD pipelines

[Learn more about ARTEMIS →](artemis-static-code.md)

## Module Status

| Module | Status | Latest Version |
|--------|--------|----------------|
| GAIA Framework | Active | In Development |
| DEMETER Infrastructure Scan | Active | In Development |
| HADES Endpoint Security | Active | In Development |
| ARTEMIS Static Code Analysis | Active | In Development |

## Architecture

The Horizon Security Framework modules are designed to work together seamlessly:

```
┌─────────────────────────────────────────────┐
│          GAIA Framework (Core)              │
│  Security Orchestration & Management        │
└──────────┬──────────────────────────────────┘
           │
    ┌──────┴──────┬──────────┬──────────┐
    │             │          │          │
┌───▼────┐  ┌────▼───┐  ┌──▼────┐  ┌──▼────────┐
│DEMETER │  │ HADES  │  │ARTEMIS│  │  Future   │
│ Infra  │  │Endpoint│  │ Code  │  │  Modules  │
│ Scan   │  │Security│  │Analysis│  │           │
└────────┘  └────────┘  └───────┘  └───────────┘
```

## Getting Started

1. Start with the [GAIA Framework](gaia-framework.md) to set up the core infrastructure
2. Deploy module-specific components based on your security needs
3. Configure integrations between modules for comprehensive coverage

## Contributing

Each module has its own repository and contribution guidelines. Visit the individual module documentation for details on how to contribute.
