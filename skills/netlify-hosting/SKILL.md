---
name: netlify-hosting
description: Publish or update a partner-owned web application on Netlify after its application-specific build and preview are ready. Use when a launch workflow or user selects Netlify hosting, including authentication, site ownership, deployment, and verification.
---

# Host an application on Netlify

Use this skill for the shared hosting workflow. The calling application skill owns its build, framework configuration, environment variables, security requirements, application checks, and any separate activation process. Read those requirements first and follow them throughout; a Next.js app with server routes and a static SPA require different deployments. Do not assume a static upload works for every app.

## Authorization and preparation

- Respect the user's provider choice and stated limits. A request to launch or deploy authorizes publishing to the intended account within those limits; it does not authorize spending, paid upgrades, DNS changes, domain purchases, messages to third parties, or transactions. Follow any stricter instructions in the calling workflow. Obtain preview acceptance when required, unless the user delegated finalization.
- Read the app's existing deployment record and verify the source, intended account/team, site ID, stable URL, build settings, environment and outstanding checks. Reuse the owned site and existing authorization for updates. Do not create a replacement just because the session expired or access is blocked.
- Check [current Netlify pricing](https://www.netlify.com/pricing/) and the actual account plan, limits and overage or pause behavior. Observe any free-only constraint. If costs or terms cannot be verified, prepare the local build and report that publication is blocked. Ask before any spending or paid change.
- Keep credentials private: the user signs in or consents in their own browser. Never ask for passwords, tokens, keys or seed phrases in chat, print token stores, or save secrets in source, logs, public variables or deployment records.

## Account and site

1. Prefer an already connected, sufficient Netlify tool. Otherwise use the installed CLI or prepare it in user space; consult the [current CLI guide](https://docs.netlify.com/api-and-cli-guides/cli-guides/get-started-with-cli/). Check authentication and account/team with a read-only operation such as `netlify status --json`. An unlinked folder, network error or permission error does not prove login expired.
2. If authentication is needed, start `netlify login` and direct the user to the actual provider-generated login URL or browser window. Let them handle their own credentials and MFA; resume when authorization is observable. Verify the intended account and site. Ask only when account ownership or access is genuinely ambiguous.
3. Reuse a verified site and URL on updates. For a new site, use an address already supplied or delegated; otherwise ask for a preferred `name.netlify.app` address or permission to use a generated one. Validate against [current naming rules](https://docs.netlify.com/manage/projects/customize-project-name-and-cover-image/). Confirm availability through Netlify's authenticated validation or the intended project's create/name operation; DNS, a browser 404 and a search of the user's sites do not establish availability. Do not create throwaway sites. If the name is taken, ask for another or a generated name; do not silently substitute it. Record the provider-confirmed site ID and stable URL.
4. Disable the project-wide [Powered by Netlify badge](https://docs.netlify.com/manage/projects/powered-by-netlify-badge/) when available, using documented authenticated tools or the provider UI. A visitor-only dismissal is not sufficient. If the setting is unavailable or would require an upgrade, report it and do not upgrade automatically.

## Deploy and verify

1. Follow the calling app's framework-specific build and deployment instructions. Inspect linked site, build context and configuration before deploying. Configure required production and preview environment variables with the right build/runtime scopes; don't assume local env files are uploaded. Use Netlify's current framework documentation and CLI help. Keep any app-specific security and rate-limit prerequisites intact.
2. Deploy a draft to the verified owned site, then run the calling workflow's draft checks. Publish the same reviewed source, build and settings only when publication is authorized and required checks pass. If they change, repeat affected checks. Never use an anonymous claim-later site for a durable partner launch.
3. Verify the stable production URL and relevant direct routes in a clean browser, including the app-specific checks and badge status. Report actual failures or blocked checks instead of claiming success. Publication does not itself establish trading activation.
4. Update the application's deployment record with non-secret account/team and site identifiers, draft and stable URLs, environment variable names and configured status, pricing source/date, checks and unresolved blockers. Preserve application-specific handoff and activation instructions.
