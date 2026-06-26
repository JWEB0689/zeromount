# Security Policy

## Supported Versions

We release security patches for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| latest   | ✅ Yes |
| previous | ✅ Security fixes only |
| < N/A | ❌ No longer supported |

## Reporting a Vulnerability

**Please do NOT report security vulnerabilities via public GitHub issues.**

Instead, please report them via:

- **Email**: security@github.com
- **GitHub Security Advisory**: [Report a vulnerability](https://github.com/JWEB0689/zeromount/security/advisories/new)

We will acknowledge receipt within 48 hours and provide a more detailed response within 7 days.

## Disclosure Policy

- We follow [Coordinated Vulnerability Disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure)
- We aim to patch critical vulnerabilities within 7 days
- We will credit reporters in the security advisory (unless anonymity requested)
- Public disclosure coordinated after fix is available

## Security Best Practices

### For Users

- Always use the latest stable release
- Verify signatures/checksums of downloads
- Keep dependencies updated
- Report suspicious behavior

### For Contributors

- Never commit secrets, keys, or tokens
- Run security scans before PR: `{{SECURITY_CMD}}`
- Follow secure coding practices for {{LANGUAGE}}
- Review dependencies for known vulnerabilities

## Security Features

Mountless module loading for rooted Android
Kernel-level VFS path redirection without mount table pollution
SUSFS integration for enhanced root hiding
WebUI with real-time module management
Bootloop guard with automatic fallback strategies
Strategy-based fallback (direct, kprobe, ftrace, sysfs)
Zero persistent mount table modifications

## Audit History

| Date | Version | Type | Description |
|------|---------|------|-------------|
| 2026-06-26 | current | Initial security audit | Repository reviewed for kernel module security and root hiding mechanisms |

---

*Template based on rtk/odysseus security policies*