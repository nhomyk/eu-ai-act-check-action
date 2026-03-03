# Contributing to EU AI Act Compliance Check

Thanks for your interest in contributing! This action checks AI systems for EU AI Act conformity, and contributions that improve article detection accuracy or reduce false positives are especially valuable.

## How to Contribute

### Reporting Issues

- **Security vulnerabilities**: See [SECURITY.md](SECURITY.md)
- **Bugs**: Open an issue with steps to reproduce, expected vs. actual behavior, and your environment
- **False positives/negatives**: Include the code snippet that was incorrectly flagged (or missed) and the scan output

### Pull Requests

1. Fork the repo and create a branch from `main`
2. Make your changes in `scan.py` or `action.yml`
3. Test locally: `python scan.py` from the repo root
4. Ensure the self-test workflow passes: the action runs against itself on every PR
5. Open a PR with a clear description of what changed and why

### Adding New Compliance Checks

The `AIActComplianceChecker` class in `scan.py` checks for specific article requirements. To add or improve a check:

1. Identify the EU AI Act article and specific requirement
2. Define detection patterns (keywords, code structures, file patterns)
3. Assign appropriate severity (error for missing requirements, warning for partial compliance)
4. Test against repos that are known-compliant and known-noncompliant to calibrate
5. Reference the article number in the finding message

### Code Style

- Python 3.11+, no external dependencies (stdlib only)
- Keep `scan.py` self-contained — the action must run without pip install for the scanner itself
- SARIF output must validate against the SARIF 2.1.0 schema

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
