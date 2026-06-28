# Security Policy

## Scope

SwiftSynapse is a framework for building AI agents on Apple platforms. Security concerns include:

- **Tool execution safety** — validated inputs, no injection vulnerabilities in tool dispatch
- **Hook system integrity** — hooks intercept agent events and must not leak data or alter agent behavior unexpectedly
- **Permission policy correctness** — access control rules must accurately reflect intended policy
- **Session persistence security** — session history written to disk must use secure file paths and access controls
- **Dependency vulnerabilities** — issues in transitive dependencies that could affect the framework

## Supported Versions

Only the **main branch** of each repository is currently supported.

## Reporting a Vulnerability

**Do not open a public GitHub Issue for security vulnerabilities.**

Instead, use one of these channels:

- **GitHub private vulnerability reporting** on the affected repository
- **Email** the maintainer directly

Please include a description of the vulnerability, steps to reproduce, and potential impact.

## Response Timeline

- **Acknowledgment**: within 48 hours
- **Assessment**: within 1 week
- **Fix**: prioritized by severity — critical issues are addressed immediately
