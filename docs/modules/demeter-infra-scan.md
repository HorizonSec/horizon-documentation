# DEMETER Infrastructure Scan

DEMETER (Dynamic Environment Monitoring and Evaluation for Threat and Error Recognition) is the infrastructure security scanning module of the Horizon Security Framework.

## Overview

DEMETER provides comprehensive infrastructure security scanning capabilities, identifying vulnerabilities, misconfigurations, and compliance violations across cloud and on-premises environments.

## Key Features

### Infrastructure Scanning
- **Multi-cloud Support**: Scan AWS, Azure, GCP, and hybrid environments
- **Network Scanning**: Comprehensive network security assessment
- **Asset Discovery**: Automatic discovery and inventory of infrastructure assets
- **Vulnerability Detection**: Identify known vulnerabilities (CVEs)

### Configuration Assessment
- **CIS Benchmarks**: Validate against CIS security benchmarks
- **Custom Policies**: Define and enforce custom security policies
- **Drift Detection**: Identify configuration drift from baseline
- **Compliance Checking**: Ensure compliance with industry standards

### Reporting & Analytics
- **Executive Dashboards**: High-level security posture overview
- **Detailed Reports**: Comprehensive vulnerability and compliance reports
- **Trend Analysis**: Track security improvements over time
- **Risk Scoring**: Prioritize remediation based on risk assessment

## Architecture

```
┌─────────────────────────────────────────┐
│      DEMETER Scanning Engine            │
├─────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐            │
│  │ Cloud    │  │ Network  │            │
│  │ Scanner  │  │ Scanner  │            │
│  └──────────┘  └──────────┘            │
│                                         │
│  ┌──────────┐  ┌──────────┐            │
│  │ Config   │  │ Vuln     │            │
│  │ Analyzer │  │ Database │            │
│  └──────────┘  └──────────┘            │
└─────────────────────────────────────────┘
```

## Installation

### Prerequisites
- Python 3.8 or higher
- Network access to target infrastructure
- Cloud provider credentials (for cloud scanning)
- GAIA Framework (recommended for integration)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/HorizonSec/demeter-infra-scan.git
cd demeter-infra-scan

# Install using Hatch
hatch env create

# Configure credentials
cp credentials.example.yaml credentials.yaml
# Edit credentials.yaml with your cloud provider credentials

# Run a quick scan
hatch run scan --target local
```

## Configuration

### Cloud Credentials

```yaml
# credentials.yaml
aws:
  access_key_id: YOUR_ACCESS_KEY
  secret_access_key: YOUR_SECRET_KEY
  regions: [us-east-1, us-west-2]

azure:
  subscription_id: YOUR_SUBSCRIPTION_ID
  client_id: YOUR_CLIENT_ID
  client_secret: YOUR_CLIENT_SECRET

gcp:
  project_id: YOUR_PROJECT_ID
  credentials_file: /path/to/service-account.json
```

### Scan Configuration

```yaml
# scan_config.yaml
scan:
  # Scan scope
  scope:
    - cloud_resources
    - network_devices
    - containers

  # Scan depth
  depth: comprehensive  # quick, standard, comprehensive

  # Exclusions
  exclude:
    - "10.0.0.0/8"
    - "tag:environment=dev"
```

## Usage

### Running Scans

#### Cloud Infrastructure Scan
```bash
# Scan all AWS resources
hatch run scan --provider aws --region us-east-1

# Scan specific Azure resource group
hatch run scan --provider azure --resource-group production

# Scan GCP project
hatch run scan --provider gcp --project my-project
```

#### Network Scan
```bash
# Scan network range
hatch run scan --type network --target 10.0.0.0/24

# Port scan
hatch run scan --type port --target 192.168.1.100 --ports 1-65535
```

#### Compliance Scan
```bash
# CIS benchmark scan
hatch run scan --compliance cis --version 1.4.0

# PCI-DSS compliance
hatch run scan --compliance pci-dss

# Custom policy scan
hatch run scan --policy custom_policy.yaml
```

### Viewing Results

```bash
# View latest scan results
hatch run results --latest

# View specific scan
hatch run results --scan-id abc123

# Export results
hatch run results --scan-id abc123 --export json --output results.json
```

### Integration with GAIA

```python
from gaia import Client

client = Client(token='your_token')

# Schedule periodic scans
scan_job = client.demeter.schedule_scan(
    provider='aws',
    regions=['us-east-1'],
    frequency='daily'
)

# Get scan results
results = client.demeter.get_scan_results(scan_id='abc123')

# Create remediation workflow
if results.critical_findings:
    client.workflow.execute('infrastructure_remediation',
                           findings=results.critical_findings)
```

## Scan Types

### Asset Discovery
Automatically discover and inventory infrastructure assets:
- Cloud instances and services
- Network devices
- Containers and orchestration platforms
- Storage resources
- Database instances

### Vulnerability Assessment
Identify security vulnerabilities:
- Known CVEs in operating systems and software
- Outdated software versions
- Unpatched systems
- Exposed services

### Configuration Analysis
Assess security configuration:
- Weak authentication settings
- Overly permissive access controls
- Missing encryption
- Insecure network configurations

### Compliance Validation
Validate compliance with standards:
- CIS Benchmarks
- PCI-DSS
- HIPAA
- SOC 2
- Custom frameworks

## Best Practices

### Scan Scheduling
- Run comprehensive scans weekly
- Run quick scans daily
- Scan after infrastructure changes
- Schedule during low-traffic periods

### Result Management
- Review critical findings immediately
- Track remediation progress
- Archive historical results
- Set up alerting for new critical findings

### Performance Optimization
- Use incremental scans when possible
- Limit concurrent scans
- Configure appropriate scan depth
- Use filters to exclude known-good resources

## Reporting

### Generate Reports

```bash
# Executive summary
hatch run report --type executive --format pdf

# Technical report
hatch run report --type technical --format html

# Compliance report
hatch run report --type compliance --standard cis
```

### Sample Report Sections
- Executive Summary
- Risk Overview
- Critical Findings
- Vulnerability Details
- Compliance Status
- Remediation Recommendations
- Historical Trends

## Troubleshooting

### Common Issues

**Issue: Authentication failures**
- Verify cloud credentials are correct and not expired
- Check IAM permissions for scanning operations
- Ensure network connectivity to cloud APIs

**Issue: Slow scans**
- Reduce scan scope or depth
- Increase scanning resources
- Use incremental scanning
- Check network bandwidth

**Issue: False positives**
- Review and tune detection rules
- Update vulnerability database
- Configure exceptions for known-good findings
- Validate findings manually

## Resources

- [GitHub Repository](https://github.com/HorizonSec/demeter-infra-scan)
- [API Documentation](https://horizonsec.github.io/demeter-infra-scan/api)
- [Scan Templates](https://github.com/HorizonSec/demeter-infra-scan/tree/main/templates)
- [Issue Tracker](https://github.com/HorizonSec/demeter-infra-scan/issues)

## Roadmap

- [x] AWS support
- [x] Azure support
- [x] GCP support
- [ ] Kubernetes scanning
- [ ] Container image scanning
- [ ] Serverless function scanning
- [ ] Automated remediation
- [ ] AI-powered risk analysis
