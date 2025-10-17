# ARTEMIS Static Code Analysis

ARTEMIS (Automated Review and Testing Engine for Maintaining Integrity and Security) is the static application security testing (SAST) module of the Horizon Security Framework.

## Overview

ARTEMIS provides comprehensive static code analysis to identify security vulnerabilities, code quality issues, and compliance violations in source code before deployment.

## Key Features

### Security Analysis
- **Vulnerability Detection**: Identify OWASP Top 10 and CWE vulnerabilities
- **Secret Scanning**: Detect hardcoded credentials and API keys
- **Dependency Analysis**: Identify vulnerable third-party dependencies
- **Data Flow Analysis**: Track sensitive data flows

### Multi-Language Support
- **Compiled Languages**: Java, C/C++, C#, Go, Rust
- **Interpreted Languages**: Python, JavaScript/TypeScript, Ruby, PHP
- **Web Technologies**: HTML, CSS, SQL
- **Configuration**: YAML, JSON, XML, Dockerfiles

### Code Quality
- **Code Smells**: Detect maintainability issues
- **Complexity Analysis**: Measure cyclomatic complexity
- **Duplicate Code**: Identify code duplication
- **Coding Standards**: Enforce coding standards

### CI/CD Integration
- **GitHub Actions**: Native integration
- **GitLab CI**: Pipeline integration
- **Jenkins**: Plugin support
- **Azure DevOps**: Extension available

## Architecture

```
┌─────────────────────────────────────────┐
│      ARTEMIS Analysis Engine            │
├─────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐            │
│  │ Code     │  │ Security │            │
│  │ Parser   │  │ Rules    │            │
│  └──────────┘  └──────────┘            │
│                                         │
│  ┌──────────┐  ┌──────────┐            │
│  │ Data     │  │ Report   │            │
│  │ Flow     │  │ Generator│            │
│  └──────────┘  └──────────┘            │
└─────────────────────────────────────────┘
```

## Installation

### Prerequisites
- Python 3.8 or higher
- Git access to source repositories
- GAIA Framework (optional, for integration)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/HorizonSec/artemis-static-code.git
cd artemis-static-code

# Install using Hatch
hatch env create

# Run a quick scan
hatch run scan --path /path/to/your/code
```

## Configuration

### Analysis Configuration

```yaml
# artemis.yaml
analysis:
  # Languages to analyze
  languages:
    - python
    - javascript
    - java
    
  # Security rules
  security:
    enabled_rules:
      - sql-injection
      - xss
      - path-traversal
      - hardcoded-secrets
      - weak-crypto
    
    severity_threshold: medium
    
  # Code quality
  quality:
    max_complexity: 10
    max_lines_per_function: 50
    min_code_coverage: 80
    
  # Exclusions
  exclude:
    - "*/tests/*"
    - "*/vendor/*"
    - "*/node_modules/*"
```

### CI/CD Configuration

#### GitHub Actions
```yaml
# .github/workflows/artemis.yml
name: ARTEMIS Security Scan

on: [push, pull_request]

jobs:
  security-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Run ARTEMIS Scan
        uses: horizonsec/artemis-action@v1
        with:
          config: artemis.yaml
          fail-on: critical
          
      - name: Upload Results
        uses: actions/upload-artifact@v3
        with:
          name: artemis-report
          path: artemis-report.html
```

#### GitLab CI
```yaml
# .gitlab-ci.yml
artemis-scan:
  stage: security
  image: horizonsec/artemis:latest
  script:
    - artemis scan --config artemis.yaml --output gitlab.json
  artifacts:
    reports:
      sast: gitlab.json
  allow_failure: false
```

## Usage

### Command Line Scanning

#### Basic Scan
```bash
# Scan current directory
hatch run scan

# Scan specific directory
hatch run scan --path /path/to/code

# Scan specific files
hatch run scan --files src/main.py src/utils.py
```

#### Advanced Scanning
```bash
# Scan with specific configuration
hatch run scan --config artemis.yaml

# Scan only for security issues
hatch run scan --mode security

# Scan with severity filter
hatch run scan --min-severity high

# Output to different formats
hatch run scan --output json --file results.json
hatch run scan --output html --file report.html
hatch run scan --output sarif --file results.sarif
```

### Programmatic Usage

```python
from artemis import Scanner

# Initialize scanner
scanner = Scanner(config='artemis.yaml')

# Scan repository
results = scanner.scan_directory('/path/to/code')

# Filter results
critical_issues = [
    issue for issue in results.issues 
    if issue.severity == 'critical'
]

# Generate report
scanner.generate_report(
    results=results,
    format='html',
    output='report.html'
)
```

### Integration with GAIA

```python
from gaia import Client

client = Client(token='your_token')

# Scan repository via GAIA
scan_result = client.artemis.scan_repository(
    repo_url='https://github.com/example/repo',
    branch='main',
    config='artemis.yaml'
)

# Get scan results
if scan_result.has_critical_issues():
    # Create security incident
    client.workflow.execute('code_security_incident',
                           scan_id=scan_result.id)
```

## Security Rules

### Injection Vulnerabilities
- SQL Injection
- Command Injection
- LDAP Injection
- XPath Injection
- Template Injection

### Cross-Site Scripting (XSS)
- Reflected XSS
- Stored XSS
- DOM-based XSS

### Authentication & Authorization
- Weak authentication
- Broken access control
- Insecure session management
- Missing authorization

### Cryptography
- Weak encryption algorithms
- Hardcoded secrets
- Insecure random number generation
- Weak hashing

### Data Protection
- Sensitive data exposure
- Insufficient data validation
- Missing input sanitization
- Information disclosure

## Dependency Scanning

### Vulnerability Detection
```bash
# Scan dependencies
hatch run scan-deps --path package.json

# Check for known vulnerabilities
hatch run scan-deps --check-cve

# Generate SBOM
hatch run scan-deps --sbom --output sbom.json
```

### Supported Package Managers
- npm/yarn (JavaScript)
- pip/poetry (Python)
- Maven/Gradle (Java)
- NuGet (.NET)
- Cargo (Rust)
- Go modules (Go)

## Reporting

### Report Formats

#### HTML Report
```bash
hatch run scan --output html --file report.html
```
Interactive HTML report with:
- Executive summary
- Vulnerability breakdown
- Code snippets
- Remediation guidance

#### JSON Report
```bash
hatch run scan --output json --file results.json
```
Machine-readable format for:
- CI/CD integration
- Custom tooling
- Data analysis

#### SARIF Report
```bash
hatch run scan --output sarif --file results.sarif
```
Standard format for:
- GitHub Code Scanning
- IDE integration
- Security tools

### Sample Report Structure
```json
{
  "summary": {
    "total_issues": 42,
    "critical": 5,
    "high": 12,
    "medium": 20,
    "low": 5
  },
  "issues": [
    {
      "id": "sql-injection-001",
      "severity": "critical",
      "title": "SQL Injection vulnerability",
      "description": "User input directly used in SQL query",
      "file": "src/database.py",
      "line": 45,
      "code_snippet": "query = f'SELECT * FROM users WHERE id = {user_id}'",
      "recommendation": "Use parameterized queries"
    }
  ]
}
```

## Custom Rules

### Creating Custom Rules

```yaml
# custom_rules.yaml
rules:
  - id: custom-logger-usage
    name: Insecure logging
    severity: medium
    languages: [python]
    pattern: |
      print($SENSITIVE_DATA)
    message: "Avoid using print() for sensitive data"
    recommendation: "Use proper logging framework"
    
  - id: custom-api-key-check
    name: Hardcoded API key
    severity: critical
    languages: [python, javascript]
    pattern: |
      api_key = "$VALUE"
    message: "Hardcoded API key detected"
    recommendation: "Use environment variables"
```

### Using Custom Rules
```bash
hatch run scan --rules custom_rules.yaml
```

## Best Practices

### Development Workflow
1. **Pre-commit Hooks**: Scan changed files before commit
2. **Pull Request Checks**: Automated scanning on PR creation
3. **Daily Scans**: Full repository scans
4. **Release Gates**: Block releases with critical issues

### Configuration
- Start with default rules, gradually add custom rules
- Set appropriate severity thresholds
- Configure exclusions for generated code
- Regularly update rule sets

### Remediation
- Address critical issues immediately
- Set SLAs for different severity levels
- Track remediation metrics
- Provide developer training

## Integration Examples

### Pre-commit Hook
```bash
# .git/hooks/pre-commit
#!/bin/bash
hatch run scan --files $(git diff --cached --name-only) --min-severity high
if [ $? -ne 0 ]; then
    echo "Security issues found. Commit aborted."
    exit 1
fi
```

### Jenkins Pipeline
```groovy
pipeline {
    agent any
    stages {
        stage('Security Scan') {
            steps {
                sh 'hatch run scan --output sarif --file results.sarif'
                recordIssues(tools: [sarif(pattern: 'results.sarif')])
            }
        }
    }
}
```

## Troubleshooting

### Common Issues

**Issue: High memory usage**
- Scan smaller code sections
- Increase available memory
- Exclude large generated files

**Issue: False positives**
- Review and tune rules
- Add suppressions for false positives
- Use custom rules for specific needs

**Issue: Slow scans**
- Enable incremental scanning
- Optimize exclusion patterns
- Use parallel processing

## Resources

- [GitHub Repository](https://github.com/HorizonSec/artemis-static-code)
- [Rule Documentation](https://horizonsec.github.io/artemis-static-code/rules)
- [API Reference](https://horizonsec.github.io/artemis-static-code/api)
- [Issue Tracker](https://github.com/HorizonSec/artemis-static-code/issues)

## Roadmap

- [x] Multi-language support
- [x] CI/CD integration
- [x] Dependency scanning
- [ ] AI-powered vulnerability detection
- [ ] Interactive remediation suggestions
- [ ] IDE plugins (VS Code, IntelliJ)
- [ ] Real-time scanning during development
- [ ] Advanced data flow analysis
