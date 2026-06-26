# Contributing to zeromount

Thank you for your interest in contributing! This document outlines the process and standards for contributing to this project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Code Standards](#code-standards)
- [Testing](#testing)
- [Documentation](#documentation)
- [Pull Request Process](#pull-request-process)
- [Release Process](#release-process)

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). By participating, you are expected to uphold this code.

## Getting Started

### Prerequisites

- Rust 1.70+, Linux kernel headers, cargo, clang, bindgen, just

### Setup

```bash
# Clone the repository
git clone https://github.com/JWEB0689/zeromount.git
cd zeromount

# Install dependencies
cargo build --release

# Run tests to verify setup
cargo test --all {{TEST_CMD}}{{TEST_CMD}} cargo clippy --all-targets --all-features -- -D warnings
```

## Development Workflow

1. **Fork** the repository
2. **Create a branch** from `main`/`master`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the code standards below
4. **Run tests and linting** locally:
   ```bash
   cargo clippy --all-targets --all-features -- -D warnings {{LINT_CMD}}{{LINT_CMD}} cargo fmt --all -- --check
   cargo test --all {{TEST_CMD}}{{TEST_CMD}} cargo clippy --all-targets --all-features -- -D warnings
   ```
5. **Commit** with conventional commits:
   ```bash
   git commit -m "feat(scope): description of change"
   ```
6. **Push** to your fork and **open a Pull Request**

## Code Standards

### Conventional Commits

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Formatting, missing semicolons, etc.
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `perf`: Performance improvement
- `test`: Adding missing tests
- `chore`: Maintenance tasks
- `ci`: CI/CD changes

### Language-Specific Standards

### Rust
- Follow Rust API guidelines
- Use cargo clippy --all-targets --all-features -- -D warnings
- Format with cargo fmt --all
- No unwrap() in production code - use proper error handling

### C/Kernel Module
- Follow Linux kernel coding style
- Use clang-format
- No kernel panics - handle all error paths
- Use proper locking primitives

### WebUI (Svelte + Rust)
- Type-safe IPC between frontend and backend
- All API endpoints documented

### Formatting

- Run the formatter before committing: `cargo fmt --all`
- CI will fail if code is not properly formatted

### Linting

- Run linter before committing: `cargo clippy --all-targets --all-features -- -D warnings {{LINT_CMD}}{{LINT_CMD}} cargo fmt --all -- --check`
- No new lint warnings allowed

## Testing

### Running Tests

```bash
cargo test --all {{TEST_CMD}}{{TEST_CMD}} cargo clippy --all-targets --all-features -- -D warnings
```

### Test Requirements

- All new features must include tests
- Bug fixes must include a regression test
- Aim for >80% code coverage
- Tests must pass on all supported platforms

### Test Organization

- Unit tests: `tests/unit/` or `*_test.*` alongside source
- Integration tests: `tests/integration/`
- E2E tests: `tests/e2e/`

## Documentation

### Required Documentation Updates

- **README.md**: Update if user-facing behavior changes
- **CHANGELOG.md**: Add entry under "Unreleased" section
- **API docs**: Update docstrings/comments for public APIs
- **Architecture docs**: Update if structural changes

### Documentation Style

- Clear, concise, and example-driven
- Keep it up to date with code changes
- Use markdown for all documentation

## Pull Request Process

### Before Submitting

- [ ] Tests pass locally (`cargo test --all {{TEST_CMD}}{{TEST_CMD}} cargo clippy --all-targets --all-features -- -D warnings`)
- [ ] Linting passes (`cargo clippy --all-targets --all-features -- -D warnings {{LINT_CMD}}{{LINT_CMD}} cargo fmt --all -- --check`)
- [ ] Formatting correct (`cargo fmt --all`)
- [ ] Documentation updated
- [ ] CHANGELOG.md updated (under "Unreleased")
- [ ] Conventional commit messages

### PR Requirements

- **Title**: Follows conventional commits (e.g., `feat: add new feature`)
- **Description**: Explains *what* and *why*, not *how*
- **Linked Issues**: Reference related issues (`Fixes #123`)
- **Screenshots**: For UI changes
- **Breaking Changes**: Clearly marked in description

### Review Process

1. Automated CI must pass
2. At least 1 maintainer approval required
3. No unresolved review comments
4. Branch must be up to date with base branch

### Merge Strategy

- **Squash and merge** for feature branches
- **Rebase and merge** for small fixes
- **Merge commit** for major releases

## Release Process

Releases are automated via GitHub Actions:

1. Tag a release: `git tag v1.2.3 && git push origin v1.2.3`
2. CI builds artifacts for all platforms
3. GitHub Release created with artifacts
4. CHANGELOG.md updated automatically
5. Package published to registry (if configured)

### Versioning

Follows [Semantic Versioning](https://semver.org/):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes (backward compatible)

## Getting Help

- Open a [Discussion](../../discussions) for questions
- Check existing [Issues](../../issues) before creating new ones
- For security issues, see [SECURITY.md](SECURITY.md)

---

*Template based on rtk/odysseus contributing guidelines*