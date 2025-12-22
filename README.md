# core-cloud-workflow-node-npm-test

A GitHub Actions workflow for running npm test on Node.js projects to identify and report code quality issues.

## Overview

This workflow automates code testing of Node.js projects within the core-cloud ecosystem, ensuring code quality standards are met.

## Features

- Automated npm testing

## Requirements

- Valid `package.json`, `package-lock.json` and valid `npm run test` command

## Usage

Reference this workflow in your GitHub Actions pipeline:

```yaml
jobs:
    test:
        uses: UKHomeOffice/core-cloud-workflow-node-npm-test
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `working_directory` | Directory to run npm test in | No | `.` |
| `node_version` | Node version | No | `24` |
| `post_install_script` | Optional script to run after npm install  | No | `` |



## Outputs

| Output | Description |
|--------|-------------|
| `npm_test_exit_code` | Exit code from npm test (0 = success) |

## Support

For issues or questions:
- Create an issue in this repository
- Contact the Sauron Team on Slack: #core-cloud-team-sauron
- For tag enforcement questions, contact the Checkov workflow maintainers: #core-cloud-team-sauron

---

## Updated Repository Structure
```
core-cloud-workflow-node-npm-test/
.github
├── workflows
|    └── self-test.yaml
|
├── action.yaml
├── CODEOWNERS
├── README.md
└── tests
    ├── test-test-invalid/
    └── test-test-valid/
```

### 📘 SonarQube Configuration 
– `sonar-project.properties`

```
sonar.exclusions=tests/**

```

This removes all test fixtures and example IaC from SonarQube analysis, ensuring the Quality Gate only evaluates the actual workflow, action code, and scripts.

| Directory           | Purpose                                               | Excluded From SAST? |
| ------------------- | ----------------------------------------------------- | ------------------- |
| `tests/**`          | Local npm test test harness (intentionally invalid code) | ✅ Yes               |
| `action.yaml`       | Composite action logic                                | ❌ No                |

This setup ensures clean SAST results without blocking PRs due to intentionally invalid IaC.

## Contributing

Please read [CONTRIBUTING.md](./CONTRIBUTING.md)

## Security

Please read [SECURITY.md](./SECURITY.md)