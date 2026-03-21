# Security & Penetration Testing
> 76 skills | Secure your applications with audits, pen testing, and security best practices

> **WARNING:** All skills in this file are [SEC].
> Only use with explicit authorization: pentest engagements, CTFs, labs, or defensive security.

## Security General
| Skill | What it does | Level |
|-------|-------------|-------|
| `007` | Security auditing, hardening, and STRIDE threat analysis | [SEC] |
| `security` | General-purpose security guidance | [SEC] |
| `security-audit` | Run a comprehensive security audit | [SEC] |
| `security-auditor` | DevSecOps-focused security auditing | [SEC] |
| `vulnerability-scanner` | Scan for OWASP 2025 vulnerabilities | [SEC] |
| `security-bluebook-builder` | Generate Security Blue Books | [SEC] |
| `security-compliance-compliance-check` | Check compliance against security standards | [SEC] |
| `security-requirement-extraction` | Extract security requirements from specs | [SEC] |
| `security-scanning-security-dependencies` | Find vulnerabilities in dependencies | [SEC] |
| `security-scanning-security-hardening` | Apply multi-layer security hardening | [SEC] |
| `security-scanning-security-sast` | Run static application security testing | [SEC] |
| `sast-configuration` | Configure SAST tool settings | [SEC] |
| `api-security-best-practices` | Apply API security best practices | [SEC] |
| `api-security-testing` | Test APIs for security weaknesses | [SEC] |
| `pci-compliance` | Ensure PCI DSS compliance | [SEC] |
| `gdpr-data-handling` | Handle data in line with GDPR rules | [SEC] |
| `secrets-management` | Manage secrets in CI/CD pipelines | [SEC] |
| `cc-skill-security-review` | Review authentication and security logic | [SEC] |
| `privacy-by-design` | Build apps with privacy as a core principle | [SEC] |
| `constant-time-analysis` | Detect timing side-channel vulnerabilities | [SEC] |
| `differential-review` | Review code diffs for security issues | [SEC] |
| `audit-context-building` | Build granular context for code audits | [SEC] |
| `audit-skills` | Audit AI skill definitions for safety | [SEC] |
| `cred-omega` | Secure API keys and credential management | [SEC] |
| `supply-chain-risk-auditor` | Audit dependency supply chain risks | [SEC] |
| `agentic-actions-auditor` | Audit GitHub Actions for security risks | [SEC] |
| `gha-security-review` | Review GitHub Actions security configuration | [SEC] |
| `zeroize-audit` | Find missing memory zeroization | [SEC] |
| `variant-analysis` | Find similar vulnerabilities across a codebase | [SEC] |

## Penetration Testing
| Skill | What it does | Level |
|-------|-------------|-------|
| `pentest-checklist` | Plan and organize penetration tests | [SEC] |
| `pentest-commands` | Reference common pentest commands | [SEC] |
| `aws-penetration-testing` | Penetration test AWS environments | [SEC] |
| `cloud-penetration-testing` | Penetration test cloud infrastructure | [SEC] |
| `web-security-testing` | Test for OWASP Top 10 vulnerabilities | [SEC] |
| `sql-injection-testing` | Test for SQL injection flaws | [SEC] |
| `xss-html-injection` | Test for cross-site scripting attacks | [SEC] |
| `html-injection-testing` | Test for HTML injection flaws | [SEC] |
| `file-path-traversal` | Test for path traversal vulnerabilities | [SEC] |
| `idor-testing` | Test for insecure direct object references | [SEC] |
| `broken-authentication` | Test for authentication weaknesses | [SEC] |
| `ssh-penetration-testing` | Penetration test SSH services | [SEC] |
| `smtp-penetration-testing` | Penetration test SMTP services | [SEC] |
| `wordpress-penetration-testing` | Penetration test WordPress sites | [SEC] |
| `sqlmap-database-pentesting` | Automate SQL injection testing with SQLMap | [SEC] |
| `api-fuzzing-bug-bounty` | Fuzz APIs for bug bounty targets | [SEC] |
| `ffuf-claude-skill` | Web fuzzing with ffuf | [SEC] |
| `ffuf-web-fuzzing` | Expert guidance for ffuf web fuzzing | [SEC] |
| `top-web-vulnerabilities` | Reference the most common web vulnerabilities | [SEC] |

## Offensive Tools
| Skill | What it does | Level |
|-------|-------------|-------|
| `metasploit-framework` | Use the Metasploit exploitation framework | [SEC] |
| `burp-suite-testing` | Intercept and test with Burp Suite | [SEC] |
| `burpsuite-project-parser` | Parse Burp Suite project files | [SEC] |
| `scanning-tools` | Run security scanning tools | [SEC] |
| `shodan-reconnaissance` | Perform reconnaissance with Shodan | [SEC] |
| `wireshark-analysis` | Analyze network packets with Wireshark | [SEC] |
| `semgrep-rule-creator` | Create custom Semgrep rules | [SEC] |
| `semgrep-rule-variant-creator` | Create Semgrep rule variants | [SEC] |

## Red Team & Attack
| Skill | What it does | Level |
|-------|-------------|-------|
| `red-team-tactics` | Apply MITRE ATT&CK tactics | [SEC] |
| `red-team-tools` | Use red team tooling and techniques | [SEC] |
| `active-directory-attacks` | Test Active Directory attack paths | [SEC] |
| `privilege-escalation-methods` | Apply privilege escalation methods | [SEC] |
| `linux-privilege-escalation` | Escalate privileges on Linux systems | [SEC] |
| `windows-privilege-escalation` | Escalate privileges on Windows systems | [SEC] |
| `attack-tree-construction` | Build attack tree diagrams | [SEC] |
| `ethical-hacking-methodology` | Follow structured ethical hacking methods | [SEC] |

## Threat Modeling
| Skill | What it does | Level |
|-------|-------------|-------|
| `threat-modeling-expert` | Perform comprehensive threat modeling | [SEC] |
| `stride-analysis-patterns` | Apply the STRIDE threat methodology | [SEC] |
| `threat-mitigation-mapping` | Map threats to security controls | [SEC] |

## Reverse Engineering
| Skill | What it does | Level |
|-------|-------------|-------|
| `reverse-engineer` | Analyze compiled binaries | [SEC] |
| `firmware-analyst` | Analyze firmware images | [SEC] |
| `binary-analysis-patterns` | Disassemble and analyze binary patterns | [SEC] |
| `anti-reversing-techniques` | Apply anti-reverse-engineering protections | [SEC] |
| `protocol-reverse-engineering` | Reverse engineer network protocols | [SEC] |
| `memory-forensics` | Perform memory forensics analysis | [SEC] |
| `malware-analyst` | Analyze malware for defensive purposes | [SEC] |
| `memory-safety-patterns` | Apply RAII and ownership safety patterns | [SEC] |
| `dwarf-expert` | Work with DWARF debug information | [SEC] |

---

## Enriched Skills

### `auth-implementation-patterns`
**What you need:** Shows you how to add login, signup, and access control to your app the right way. Covers common approaches like OAuth (sign in with Google), JWT tokens, and session-based auth so your users stay safe.
**Level:** Intermediate
**Tags:** #authentication #authorization #oauth #jwt #sessions #login #security
**When to use:**
- You need to add user login and signup to your app
- You want to implement "Sign in with Google/GitHub" or other social logins
- You need to control who can access what (roles and permissions) in your application
**Combine with:** `react-nextjs-development` > `auth-implementation-patterns` > `backend-architect` > `secrets-management`
**Example prompt:** > /auth-implementation-patterns Set up email/password auth plus Google OAuth for my Next.js app with JWT tokens and refresh token rotation
**Don't use when:** You just need to plug in a managed auth service like Clerk — use `clerk-auth` for that

### `clerk-auth`
**What you need:** Adds a complete, ready-to-use login system to your app using Clerk, which handles sign-up, sign-in, user profiles, multi-factor authentication, and session management so you do not have to build auth from scratch.
**Level:** Beginner
**Tags:** #clerk #authentication #auth #login #signup #user-management #sessions
**When to use:**
- You want to add user login and registration to your app without building it yourself
- You need social logins (Google, GitHub, etc.), magic links, or multi-factor authentication
- You are building a Next.js, React, or other JavaScript app and want auth that works in minutes
**Combine with:** `clerk-auth` > `react-nextjs-development` > `stripe-integration` > `saas-mvp-launcher`
**Example prompt:** > /clerk-auth Add Clerk authentication to my Next.js app with Google and GitHub social login, protected dashboard routes, and a user profile page
**Don't use when:** You need full control over your auth system or are using a non-JavaScript backend -- consider `firebase` auth or building custom auth with `security` guidance

---

[Back to All Categories](../../README.md#categories) | [Skill Combos](../../guide/en/skill-combos.md) | [How to Choose](../../guide/en/how-to-choose-skills.md)
