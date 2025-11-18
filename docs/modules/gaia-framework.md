# GAIA Framework

The GAIA Framework is the core orchestration and management platform for the Horizon Security Framework. It provides the foundation for integrating and coordinating all security modules.

## Overview

GAIA (Global Automated Intelligence Architecture) serves as the central nervous system of the Horizon Security Framework, orchestrating security operations, managing policies, and providing a unified interface for all security modules.

## Key Features

### Security Orchestration
- **Automated Workflows**: Define and execute complex security workflows across modules
- **Event Correlation**: Correlate security events from multiple sources
- **Response Automation**: Automated incident response and remediation

### Policy Management
- **Centralized Policies**: Define security policies in one place
- **Policy Enforcement**: Ensure consistent policy application across all modules
- **Compliance Tracking**: Monitor and report on compliance status

### Integration Hub
- **Module Integration**: Seamless integration with DEMETER, HADES, and ARTEMIS
- **Third-party Integration**: Connect with external security tools and platforms
- **API Gateway**: RESTful API for programmatic access

### Monitoring & Analytics
- **Real-time Dashboard**: Comprehensive security posture visualization
- **Advanced Analytics**: Machine learning-powered threat detection
- **Custom Reports**: Generate detailed security reports

## Architecture

GAIA is built on a microservices architecture for scalability and resilience:

```
┌─────────────────────────────────────────┐
│         GAIA Core Services              │
├─────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐            │
│  │ API      │  │ Event    │            │
│  │ Gateway  │  │ Bus      │            │
│  └──────────┘  └──────────┘            │
│                                         │
│  ┌──────────┐  ┌──────────┐            │
│  │ Policy   │  │ Workflow │            │
│  │ Engine   │  │ Engine   │            │
│  └──────────┘  └──────────┘            │
└─────────────────────────────────────────┘
```

## Installation

### Prerequisites
- Python 3.8 or higher
- PostgreSQL 12 or higher
- Redis 6 or higher
- Kubernetes cluster (optional, for production deployment)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/HorizonSec/gaia-framework.git
cd gaia-framework

# Install dependencies using Hatch
hatch env create

# Configure the environment
cp config.example.yaml config.yaml
# Edit config.yaml with your settings

# Run the development server
hatch run serve
```

## Configuration

Create a `config.yaml` file with the following structure:

```yaml
database:
  host: localhost
  port: 5432
  name: gaia_db
  user: gaia_user
  password: your_password

redis:
  host: localhost
  port: 6379

api:
  host: 0.0.0.0
  port: 8000

security:
  secret_key: your_secret_key
  jwt_expiration: 3600
```

## Usage

### Starting GAIA

```bash
# Start all services
hatch run start

# Start specific service
hatch run start-api
hatch run start-worker
```

### API Access

GAIA provides a RESTful API for integration:

```python
import requests

# Authenticate
response = requests.post('http://localhost:8000/api/auth/login',
    json={'username': 'admin', 'password': 'password'})
token = response.json()['token']

# Get security events
headers = {'Authorization': f'Bearer {token}'}
events = requests.get('http://localhost:8000/api/events', headers=headers)
```

### Creating Workflows

Define security workflows in YAML:

```yaml
name: threat_response
trigger:
  type: event
  source: hades
  severity: critical

steps:
  - action: isolate_endpoint
    module: hades

  - action: scan_infrastructure
    module: demeter

  - action: notify
    type: email
    recipients: [security-team@example.com]
```

## Integration with Other Modules

### DEMETER Integration
```python
from gaia import Client

client = Client(token='your_token')
# Trigger infrastructure scan
scan_result = client.demeter.scan(targets=['10.0.0.0/24'])
```

### HADES Integration
```python
# Query endpoint status
endpoints = client.hades.get_endpoints(status='at_risk')
```

### ARTEMIS Integration
```python
# Initiate code scan
scan = client.artemis.scan_repository(
    repo_url='https://github.com/example/repo',
    branch='main'
)
```

## Development

### Running Tests
```bash
hatch run test
```

### Contributing
See [CONTRIBUTING.md](https://github.com/HorizonSec/gaia-framework/blob/main/CONTRIBUTING.md) for development guidelines.

## Troubleshooting

### Common Issues

**Issue: API not responding**
```bash
# Check if services are running
hatch run status

# View logs
hatch run logs
```

**Issue: Database connection failed**
- Verify PostgreSQL is running
- Check database credentials in config.yaml
- Ensure database exists and user has proper permissions

## Resources

- [GitHub Repository](https://github.com/HorizonSec/gaia-framework)
- [API Documentation](https://horizonsec.github.io/gaia-framework/api)
- [Issue Tracker](https://github.com/HorizonSec/gaia-framework/issues)

## Roadmap

- [x] Core orchestration engine
- [x] Basic module integration
- [ ] Advanced analytics dashboard
- [ ] Machine learning threat detection
- [ ] Multi-tenancy support
- [ ] Cloud-native deployment options
