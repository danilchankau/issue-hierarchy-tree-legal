# Security Policy — Issue Hierarchy Tree

**Security contact:** [PLACEHOLDER — security/support email]

## Reporting a vulnerability

If you believe you've found a security vulnerability in this App, please email **[PLACEHOLDER — security email]** with details. We'll acknowledge reports within [PLACEHOLDER — e.g., 2 business days] and aim to resolve confirmed issues promptly. Please do not open public GitHub issues for security reports.

## How the App is built

- **Platform**: [Atlassian Forge](https://developer.atlassian.com/platform/forge/) — the App's code runs entirely on Atlassian's own infrastructure, not on servers we operate.
- **Permission model**: every Jira API call the App makes uses `asUser()`, meaning results are scoped to the permissions of the person currently viewing the issue. The App can never show a user Jira data they don't already have access to.
- **Scopes**: the App requests the minimum scope needed to read issue hierarchy, status, and links (`read:jira-work`). It cannot write, delete, or modify any Jira data.
- **No data storage**: the App does not persist any Jira data (no database, no Forge Storage). See [PRIVACY.md](./PRIVACY.md) for details.
- **No third-party services**: the App makes no network calls outside Atlassian's own infrastructure.

## Runs on Atlassian

This App is eligible for Atlassian's [Runs on Atlassian](https://www.atlassian.com/trust/runs-on-atlassian) program, meaning it runs and stores data (to the extent it stores any at all) entirely within Atlassian's trusted cloud environment rather than on infrastructure we control.

## Dependencies

The App's dependencies are kept minimal and are audited/updated as part of normal maintenance. [PLACEHOLDER — mention here if you run `npm audit` / Dependabot / similar as part of your process, once you set one up.]
