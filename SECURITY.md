# Security Policy

Moto Finance ("Moto") treats security as a first-class concern. This document explains how to report vulnerabilities and how we respond.

1. [Reporting security problems](#reporting-security-problems)
2. [Incident response process](#incident-response-process)
3. [Scope](#scope)
4. [Responsible disclosure](#responsible-disclosure)

## Reporting security problems

**Do not open a public issue to report a security problem.** Instead, email **security@moto-card.com** with:

- A clear description of the vulnerability
- Reproduction steps
- The affected component (program, API, app surface)
- Your GitHub username so we can add you to a private security advisory for further discussion

We do not accept attachments over email; share proof-of-concept code and screenshots inside the private advisory thread.

We recommend enabling multi-factor authentication on your GitHub account before submitting.

## Incident response process

When a report is received or an incident is discovered, we follow this process:

### 1. Acknowledge and triage

A member of Moto's security team will respond within **24 hours** to acknowledge receipt, and will:

- Open a private security advisory on GitHub against the relevant repository
- Add the reporter and the Moto security team to the advisory
- Begin reproducing and assessing the issue

If the report originates from a formal audit, the advisory title is prefixed with `[Audit]`.

### 2. Severity assessment

Within the advisory, Moto's security team and the reporter discuss severity and impact. Moto retains final say on classification, in consultation with the reporter.

### 3. Patch development

Fixes are developed in a private fork. Multiple Moto engineers review the patch, and the reporter is invited (but not required) to review.

### 4. Deployment

For on-chain programs: a patched build is tested on devnet and upgraded via Moto's program-update multisig. For off-chain components: patches ship through normal release channels with priority and, where relevant, hotfix paths.

### 5. Public disclosure

Once the fix is live, we publish an advisory describing the issue, impact, and remediation. The reporter is credited unless they request anonymity. Broader disclosure happens via Moto's blog and official channels.

## Scope

### In scope

- **On-chain programs** deployed by Moto on Solana mainnet:
  - `moto_vault` — collateral and authorization management
  - `moto_bridge` — cross-chain settlement (CCTP v2)
  - `moto_earn` — yield aggregation
- **Production APIs** at `*.moto-card.com`
- **Moto mobile app** — latest published iOS and Android releases on the App Store and Google Play

### Out of scope

- Code in third-party dependencies — please report upstream
- Internal admin tooling not exposed to end users
- Findings that require social engineering of Moto staff or customers
- Self-XSS, missing security headers without demonstrable impact, clickjacking on pages with no sensitive action
- Rate-limiting or brute-force findings on unauthenticated endpoints without demonstrated impact
- Output of automated scanners without proof of exploitation
- Issues in staging, devnet, or other non-production environments
- Findings already documented in published audit reports
- Issues fixed in a more recent release than the one tested

## Responsible disclosure

Moto does not currently operate a paid bug bounty program. We still deeply value security research and will work with researchers in good faith.

If you comply with the terms below, Moto will not pursue legal action or report your activity to law enforcement in connection with your good-faith research:

- You give us reasonable time — at least **90 days**, or until a fix is deployed, whichever is sooner — before publicly disclosing the issue
- You make a good-faith effort to avoid privacy violations, data destruction, or service disruption
- You do not exploit the issue beyond what is necessary to demonstrate it — no exfiltration of user data, no movement of funds, no persistent access
- You do not test against accounts, wallets, or cards you do not own or have explicit permission to access
- You do not violate any applicable law
- You are not located in, or a resident of, a country subject to U.S., E.U., or U.K. sanctions, nor an individual subject to such sanctions

We credit reporters publicly in the advisory and on our security acknowledgements page, unless you prefer to remain anonymous.
