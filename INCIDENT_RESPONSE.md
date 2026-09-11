# Incident Response Plan — Issue Hierarchy Tree

Scoped to this app's actual footprint: a stateless Forge app with no database, no logs held outside Atlassian's own Forge logging, and no static API keys or secrets. This plan focuses on the controls that are actually meaningful at this scale, not generic enterprise boilerplate.

## Contacts

- **Primary contact:** Andrei Danilchankau — bim.eleck@gmail.com
- **Atlassian Marketplace Security:** via the Developer Console's "Marketplace Security" ticket, or security@atlassian.com for urgent platform-level issues.

## Source code backup

The app's full source is version-controlled in a private GitHub repository, enabling rollback to any prior commit at any time. Deployment history is also independently retained by Forge itself (`forge deploy` versions per environment), giving a second, platform-level rollback path.

## What counts as an incident here

Given the app's minimal footprint (read-only Jira data, no storage, no secrets), realistic incident scenarios are narrow:

1. A vulnerability is found in the app's code that could expose issue data beyond what the viewing user already has permission to see.
2. A vulnerable dependency is disclosed (tracked via periodic `npm audit`).
3. Atlassian notifies us of a platform-level concern affecting the app.

## Response steps

1. **Confirm and scope** — reproduce the issue, identify which code path is affected, and confirm whether it's actually exploitable (e.g., does it bypass Jira's own permission model, which `asUser()` should prevent by design).
2. **Contain** — if actively exploitable, deploy the app to `Not sharing` in the Developer Console's Distribution settings, or unpublish the version, to stop new installs/usage while a fix is prepared.
3. **Fix and deploy** — patch the code, run `forge lint` and `npm audit`, deploy a new version (`forge deploy -e production`), and verify the fix.
4. **Notify** — report to Atlassian's Marketplace Security team via the Developer Console, and to any customers who reported the issue directly, via the support email.
5. **Review** — record what happened and update this plan if the incident revealed a gap.

## Prevention already in place

- All Jira API calls use `asUser()`, so the app can never return data beyond the viewing user's own Jira permissions — the largest class of realistic incidents for a read-only app is structurally prevented.
- No static secrets or API keys exist in the codebase to leak.
- Dependencies are minimal and checked with `npm audit` before releases.
