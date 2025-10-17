# HADES Endpoint Security

HADES (Host-based Advanced Detection and Enforcement System) is the endpoint detection and response (EDR) module of the Horizon Security Framework.

## Overview

HADES provides comprehensive endpoint protection, detecting and responding to advanced threats on workstations, servers, and IoT devices in real-time.

## Key Features

### Threat Detection
- **Behavioral Analysis**: Machine learning-based behavior monitoring
- **Signature Detection**: Pattern matching for known threats
- **Anomaly Detection**: Identify unusual system behavior
- **Real-time Monitoring**: Continuous endpoint surveillance

### Incident Response
- **Automated Response**: Immediate threat containment
- **Endpoint Isolation**: Quarantine compromised systems
- **Threat Remediation**: Automated malware removal
- **Forensic Collection**: Preserve evidence for investigation

### Endpoint Management
- **Agent Deployment**: Lightweight agent for all platforms
- **Centralized Management**: Single pane of glass for all endpoints
- **Policy Enforcement**: Ensure security policy compliance
- **Update Management**: Automatic agent and signature updates

### Advanced Features
- **Memory Analysis**: Detect fileless malware
- **Process Monitoring**: Track process execution chains
- **Network Monitoring**: Monitor network connections
- **File Integrity Monitoring**: Detect unauthorized file changes

## Architecture

```
┌─────────────────────────────────────────┐
│      HADES Control Plane                │
├─────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐            │
│  │ Threat   │  │ Response │            │
│  │ Engine   │  │ Engine   │            │
│  └──────────┘  └──────────┘            │
│                                         │
│  ┌──────────┐  ┌──────────┐            │
│  │ Agent    │  │ Forensic │            │
│  │ Manager  │  │ Storage  │            │
│  └──────────┘  └──────────┘            │
└────────┬────────────────────────────────┘
         │
    ┌────┴────┬────────┬────────┐
    │         │        │        │
┌───▼────┐ ┌─▼───┐ ┌──▼───┐ ┌──▼─────┐
│Endpoint│ │End- │ │End-  │ │ ...    │
│Agent 1 │ │pt 2 │ │pt 3  │ │        │
└────────┘ └─────┘ └──────┘ └────────┘
```

## Installation

### Prerequisites
- GAIA Framework (recommended)
- Supported operating systems for endpoints:
  - Windows 10/11, Server 2016+
  - Linux (Ubuntu, RHEL, CentOS, Debian)
  - macOS 11+

### Control Plane Setup

```bash
# Clone the repository
git clone https://github.com/HorizonSec/hades-endpoint.git
cd hades-endpoint

# Install using Hatch
hatch env create

# Initialize the database
hatch run init-db

# Start the control plane
hatch run start-server
```

### Agent Deployment

#### Windows
```powershell
# Download and install agent
Invoke-WebRequest -Uri "https://releases.horizonsec.io/hades/agent-windows.msi" -OutFile "hades-agent.msi"
msiexec /i hades-agent.msi SERVER_URL=https://hades.example.com TOKEN=your_token

# Verify installation
Get-Service HADESAgent
```

#### Linux
```bash
# Download and install agent
curl -O https://releases.horizonsec.io/hades/agent-linux.deb
sudo dpkg -i agent-linux.deb

# Configure
sudo hades-agent configure --server https://hades.example.com --token your_token

# Start agent
sudo systemctl start hades-agent
sudo systemctl enable hades-agent
```

#### macOS
```bash
# Download and install agent
curl -O https://releases.horizonsec.io/hades/agent-macos.pkg
sudo installer -pkg agent-macos.pkg -target /

# Configure and start
sudo hades-agent configure --server https://hades.example.com --token your_token
sudo launchctl load /Library/LaunchDaemons/com.horizonsec.hades.plist
```

## Configuration

### Control Plane Configuration

```yaml
# config.yaml
server:
  host: 0.0.0.0
  port: 8443
  ssl:
    enabled: true
    cert: /path/to/cert.pem
    key: /path/to/key.pem

database:
  host: localhost
  port: 5432
  name: hades_db

threat_detection:
  ml_model: /path/to/model.pkl
  signature_db: /path/to/signatures.db
  update_interval: 3600  # seconds

response:
  auto_isolate: true
  isolation_threshold: critical
  auto_remediate: true
```

### Agent Policy

```yaml
# agent_policy.yaml
monitoring:
  processes: true
  network: true
  files: true
  registry: true  # Windows only
  
detection:
  behavioral: true
  signature: true
  anomaly: true
  
response:
  allow_isolation: true
  allow_remediation: true
  allow_quarantine: true

exclusions:
  paths:
    - /opt/safe_application
  processes:
    - safe_process.exe
```

## Usage

### Monitoring Endpoints

```bash
# List all endpoints
hatch run endpoints list

# Get endpoint details
hatch run endpoints show --id endpoint-123

# Filter endpoints by status
hatch run endpoints list --status at_risk
```

### Threat Management

```bash
# View active threats
hatch run threats list --status active

# Get threat details
hatch run threats show --id threat-456

# Manually respond to threat
hatch run threats respond --id threat-456 --action isolate
```

### Forensic Investigation

```bash
# Collect forensic data from endpoint
hatch run forensics collect --endpoint endpoint-123

# Search forensic data
hatch run forensics search --query "process:suspicious.exe"

# Export forensic timeline
hatch run forensics timeline --endpoint endpoint-123 --export timeline.json
```

### Integration with GAIA

```python
from gaia import Client

client = Client(token='your_token')

# Get at-risk endpoints
endpoints = client.hades.get_endpoints(
    filters={'risk_level': ['high', 'critical']}
)

# Isolate endpoint
client.hades.isolate_endpoint(endpoint_id='endpoint-123')

# Create incident workflow
for endpoint in endpoints:
    client.workflow.execute('endpoint_incident_response', 
                           endpoint=endpoint.id)
```

## Threat Detection

### Behavioral Analysis
HADES uses machine learning to detect suspicious behavior:
- Unusual process execution patterns
- Abnormal network activity
- Unexpected file modifications
- Privilege escalation attempts

### Signature-based Detection
Detect known threats using signatures:
- Malware families
- Exploit kits
- Ransomware patterns
- APT indicators

### Indicators of Compromise (IOCs)
Monitor for IOCs:
- File hashes
- IP addresses
- Domain names
- Registry keys
- Mutex names

## Response Actions

### Automated Responses
- **Isolate**: Disconnect endpoint from network
- **Quarantine**: Move suspicious files to secure location
- **Terminate**: Kill malicious processes
- **Block**: Prevent execution of malicious binaries

### Manual Responses
```bash
# Isolate endpoint
hatch run response isolate --endpoint endpoint-123

# Restore from isolation
hatch run response restore --endpoint endpoint-123

# Quarantine file
hatch run response quarantine --file /path/to/suspicious.exe

# Block hash
hatch run response block --hash abc123def456
```

## Incident Investigation

### Timeline Analysis
```python
# Get endpoint activity timeline
timeline = client.hades.get_timeline(
    endpoint_id='endpoint-123',
    start_time='2024-01-01T00:00:00Z',
    end_time='2024-01-02T00:00:00Z'
)

# Filter for process events
process_events = [e for e in timeline if e.type == 'process']
```

### Memory Forensics
```bash
# Capture memory dump
hatch run forensics memory-dump --endpoint endpoint-123

# Analyze memory dump
hatch run forensics analyze-memory --dump memory-123.dmp
```

## Best Practices

### Deployment
- Deploy agents to all critical systems first
- Test policies in a staging environment
- Use phased rollout for large deployments
- Monitor agent health and connectivity

### Policy Management
- Start with detection-only mode
- Gradually enable automated responses
- Regularly review and update policies
- Document policy exceptions

### Incident Response
- Investigate all critical alerts within 1 hour
- Maintain forensic data for at least 90 days
- Document all incident response actions
- Conduct post-incident reviews

## Troubleshooting

### Agent Issues

**Agent not connecting**
```bash
# Check agent status
sudo systemctl status hades-agent

# View agent logs
sudo journalctl -u hades-agent -n 100

# Test connectivity
hades-agent test-connection
```

**High CPU usage**
- Adjust scanning frequency
- Add exclusions for known-good paths
- Update to latest agent version

**False positives**
- Review detection rules
- Add exclusions for legitimate software
- Tune behavioral analysis sensitivity

## Performance Optimization

### Agent Resource Usage
```yaml
# Optimize agent performance
performance:
  cpu_limit: 10  # percent
  memory_limit: 256  # MB
  scan_frequency: 3600  # seconds
  batch_events: true
```

### Control Plane Scaling
- Use load balancer for multiple control plane instances
- Scale database for large deployments
- Use caching for frequently accessed data
- Archive old forensic data

## Resources

- [GitHub Repository](https://github.com/HorizonSec/hades-endpoint)
- [Agent Documentation](https://horizonsec.github.io/hades-endpoint/agent)
- [API Reference](https://horizonsec.github.io/hades-endpoint/api)
- [Issue Tracker](https://github.com/HorizonSec/hades-endpoint/issues)

## Roadmap

- [x] Windows, Linux, macOS agent support
- [x] Behavioral detection engine
- [x] Automated response capabilities
- [ ] Mobile device support (iOS, Android)
- [ ] Container runtime protection
- [ ] Extended Detection and Response (XDR) integration
- [ ] Threat hunting queries
- [ ] Enhanced memory forensics
