# IofI Project Internal Coding Standards & Data Sharing
**Version 0.1 - Draft for Comment**

*Internal standards for the Industries of Ideas project*

---

## Overview

This document outlines coding standards and data sharing practices for **internal use** within the Industries of Ideas (IofI) project. These standards are designed to reduce friction, improve onboarding, and ensure reproducible results across all project teams.

**This is a living document.** We welcome feedback, suggestions, and contributions from all project participants to refine these standards based on usage and team needs.

## How to Contribute to These Standards

- **Feedback**: Submit issues or suggestions via GitHub Issues
- **Updates**: Propose changes through Pull Requests
- **Examples**: Add code examples or use cases to existing sections
- **Discussion**: Use GitHub Discussions for broader conversations about standards

All changes will be reviewed by the technical standards team and approved through project governance processes.

---

## 1. Code Sharing Practices

### 1.1 Version Control
- Use **Git** with clear branch naming: `feature-...`, `fix-...`, `chore-...`
- Open PRs early; require review and status checks before merge to `main`/`develop`
- Write meaningful commit messages

### 1.2 Documentation
- Repository `README` with definition, setup, quick start, and examples
- Include `CONTRIBUTING.md`, `CHANGELOG.md`, and architecture notes
- Inline comments for non-obvious logic; keep them current

### 1.3 Licensing
- Add a `LICENSE` file (MIT, Apache-2.0, GPL, or org policy)
- Verify third-party license compatibility

### 1.4 Code Quality & Security
- Enforce style with linters/formatters (e.g., Ruff/Black; ESLint/Prettier)
- Write unit tests
- Never commit secrets or passwords

### 1.5 Reproducibility
- Maintain dependency lists (`requirements.txt`, `package.json`)
- Document OS/toolchain; consider Docker for environment parity
- Provide sample/synthetic data when real data can't be shared

---

## 2. Data Sharing Practices

### 2.1 Data Classification
- **Internal/Confidential** — limited share; agreements may apply
- **Restricted/Sensitive** — PII/PHI; approvals + controls required

### 2.2 Privacy & Security
- De-identify/anonymize data
- Comply with GDPR/HIPAA/IRB and org policies
- Secure transfer & storage (SFTP/HTTPS, encrypted buckets, least-privilege ACLs)

### 2.3 Metadata & Documentation
- Data dictionary (field names and data types)
- Document collection, cleaning, transformation, QA/QC processes
- **Provenance information**: Include who created the data, when, with what code, where, and for what purpose
- **Original sources**: Document what original data files were used, including vintage information

### 2.4 Formats & Accessibility
- Prefer open formats (CSV/JSON/Parquet)
- Document encodings (UTF-8 default)

### 2.5 Licensing & Attribution
- Attach data license (e.g., CC BY, CC BY-NC) and usage terms
- Credit sources and contributors; provide citation examples

**Future consideration**: Machine-readable metadata formats (DDI, Croissant) for public data releases.

---

## 3. Standard IofI Function Libraries

### 3.1 Contribution Process
- Submit functions through Pull Requests to designated library files (e.g., `iofi_standard_text_functions.py`)
- Include comprehensive docstrings with attribution
- Add unit tests for all contributed functions
- Follow project coding standards

### 3.2 Attribution & Credit
All functions must include attribution in docstring format:
```python
def example_function(data):
    """
    Brief description of function.
    
    Args:
        data: Description of input
        
    Returns:
        Description of output
        
    Author: Your Name (your.email@institution.edu)
    Contributors: Name1, Name2 (if applicable)
    Reviewers: Name1, Name2
    Created: YYYY-MM-DD
    """
```

### 3.3 Review Process
- Technical review for correctness and performance
- Code style review for consistency
- Documentation review for clarity
- Integration testing with existing library functions

### 3.4 Library Organization
- Group related functions by domain (text processing, data validation, visualization, etc.)
- Maintain backward compatibility when possible
- Version control shared libraries with semantic versioning

---

## 4. Coding Standards

### 4.1 Naming Conventions
- Variables/functions: `snake_case`
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Modules/files: `snake_case`
- Tests: mirror module name with `test_*.py` / `*.spec.ts`
- Avoid cryptic abbreviations; prefer clarity over brevity

### 4.2 Project Structure
- Keep clear `src/`, `tests/`, `docs/`, `scripts/` layout
- One responsibility per module; avoid "god" modules

### 4.3 Commenting & Docstrings
- Docstrings for public APIs (functions/classes/modules)
- Follow consistent style (e.g., Google format)
- Include params, returns, raises

### 4.4 Style Rules
- Consistent indentation
- Prefer pure functions; avoid side effects where possible
- Small functions (≤ 30–40 lines) and single responsibility
- Enable type checking

### 4.5 Testing & Coverage
- Minimum coverage targets per repo type
- Name tests clearly
- CI enforces tests

### 4.6 Error Handling & Logging
- Use typed exceptions and specific `catch`/`except` blocks
- Structured, leveled logs (`DEBUG`→`ERROR`); no secrets
- Return helpful error messages; preserve stack traces

### 4.7 Performance Guidelines
- Measure before optimizing; add benchmarks for hot paths
- Choose appropriate data structures; avoid N+1 queries
- Document complexity of critical functions

### 4.8 Security Practices
- Validate/sanitize inputs; avoid injection
- Store secrets in vaults; rotate keys; principle of least privilege
- Keep packages up-to-date
- Review potential risks for public-facing services

### 4.9 Code Review
- **Author**: small PRs; include tests; update docs; link issue
- **Reviewer**: check correctness, tests, style, security, and performance risks
- Require at least one approver

---

## 5. Sharing Platforms

### 5.1 Code Repositories
- GitHub for primary development
- Institutional archival where required
- Branch protection, CODEOWNERS, CI gates

### 5.2 Data Repositories
- Use appropriate platforms (e.g., Dataverse) for data sharing
- Follow institutional data management policies

---

## 6. Collaboration & Governance

- Define clear roles and SLAs (maintainers, reviewers, contributors)
- Use Architectural Decision Records (ADR) for major technical decisions
- Establish escalation paths for disputes
- Maintain governance that's strict on safety and reproducibility, lightweight on ceremony

---

## 7. Ethical & Legal Considerations

- Don't share proprietary/sensitive assets without written permission
- Comply with funder, publisher, and institutional mandates
- Retain DUA/DTA records
- Respect intellectual property and cultural data sovereignty
- Follow community norms

---

## Document History & Updates

- **v0.1**: Initial draft for project team review
- **Next**: Incorporate feedback from project stakeholder meetings

Submit feedback, suggestions, or proposed changes via GitHub Issues or Pull Requests.
