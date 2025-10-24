# Contributing to KIND-ID

Welcome, and thank you for helping build the future of human-centric authentication.

---

## 🧭 Table of Contents
1. [Purpose](#purpose)
2. [Code of Conduct](#code-of-conduct)
3. [Repository Structure](#repository-structure)
4. [Development Environment](#development-environment)
5. [Branching Model](#branching-model)
6. [Commit Conventions](#commit-conventions)
7. [Testing & Linting](#testing--linting)
8. [Documentation Standards](#documentation-standards)
9. [Security Disclosure Policy](#security-disclosure-policy)
10. [Contributor Recognition](#contributor-recognition)

---

## Purpose
This document explains how to contribute to the KIND-ID project in a way that keeps the codebase clean, transparent, and auditable.

---

## Code of Conduct
Participation in this project requires adherence to the [Code of Conduct](CODE_OF_CONDUCT.md).  
Disrespectful or exclusionary behavior will result in removal from the contributor program.

---

## Repository Structure
```

kindid/             # Core SDK (Python)
server/             # FastAPI microservice
extension/          # Chrome/Edge extension
docs/               # Documentation suite
tests/              # Unit/integration tests
installers/         # Platform installers
.github/workflows/  # CI/CD pipelines

````

---

## Development Environment
* Use **Python 3.11+** and **Node 18+**.
* Create a virtual environment:
  ```bash
  python -m venv venv
  source venv/bin/activate
````

* Install dependencies:

  ```bash
  pip install -r requirements.txt
  npm install --prefix extension
  ```
* Pre-commit hooks (optional but recommended):

  ```bash
  pre-commit install
  ```

---

## Branching Model

We use a simplified **GitHub Flow**:

| Branch           | Purpose                           |
| :--------------- | :-------------------------------- |
| `main`           | Stable, production-ready releases |
| `dev`            | Active development                |
| `feature/<name>` | Specific feature work             |
| `fix/<name>`     | Bug fixes                         |
| `docs/<topic>`   | Documentation updates             |

Merge only through pull requests. Each PR requires:

* Passing CI tests
* Reviewer approval
* Signed commits

---

## Commit Conventions

Follow the [Conventional Commits](https://www.conventionalcommits.org) format:

```
type(scope): short description
```

Types include:
`feat`, `fix`, `docs`, `test`, `build`, `ci`, `refactor`, `perf`, `chore`.

Example:

```
feat(auth): add Argon2id salt rotation
```

---

## Testing & Linting

Run tests:

```bash
pytest -v
```

Run linter and type checker:

```bash
flake8 kindid
mypy kindid
```

JavaScript linting for the extension:

```bash
npm run lint --prefix extension
```

All tests must pass before merging.

---

## Documentation Standards

* Every public function/class must have a docstring following Google style.
* Markdown files should start with a level-1 heading and end with a horizontal rule.
* All docs live in `/docs` and are cross-linked from the root [README](README.md).

---

## Security Disclosure Policy

If you discover a vulnerability:

1. **Do not open a public issue.**
2. Email `security@kind-id.org` with:

   * Description
   * Reproduction steps
   * Impact assessment
   * Suggested mitigation
3. You’ll receive acknowledgment within 72 hours.

Responsible reporters will be credited in release notes.

---

## Contributor Recognition

Each merged PR automatically adds your name to the CONTRIBUTORS.md ledger.
Outstanding contributors may be invited to the **KIND-ID Governance Council** (see [Governance Charter](docs/GOVERNANCE_CHARTER.md)).

---

Thank you for strengthening the world’s most transparent authentication protocol.
