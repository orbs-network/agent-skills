---
name: walletconnect-setup
description: Configure or hand off WalletConnect mobile-wallet pairing for a partner-owned web app using its own Reown project and published origin. Use during an app launch or a later WalletConnect setup request.
---

# Set up WalletConnect

The application-specific launch skill owns its environment variable names, build, deployment and wallet behavior. Follow it alongside this workflow. A WalletConnect project ID is a public client identifier, distinct from the partner ID; never invent one or use another partner's project.

## During a launch

- Reuse a supplied project ID and any verified partner-owned project. If the ID is optional and missing, continue the launch as directed by the application skill and provide concise follow-up instructions instead of requiring an account walkthrough. Do not report pairing as working until it is tested.
- Do not open an account setup or alter a Reown project merely to complete an unrelated launch. If access, an origin check or pairing is unavailable, record the actual limitation and leave it pending. A WalletConnect ID does not activate trading.

## When setup is requested

1. Direct the user to sign in to their own [Reown Dashboard](https://dashboard.reown.com/) and create an app-specific project or reuse the existing project for this app. Check [current pricing](https://reown.com/pricing) before accepting charges. The user handles their own authentication; never request passwords, private keys, recovery phrases or tokens.
2. Use the real verified production origin, including scheme and any port, without a path. Preserve existing needed allowlist entries, and include a draft origin only when testing pairing there. Follow the current [Reown allowlist documentation](https://docs.reown.com/cloud/relay#allowlist): hostname, specified scheme and port must match; an empty allowlist allows all origins and changes can take time to propagate. If the production origin is not known, do not invent it. Modify account settings only when the user has requested or authorized that work.
3. Configure the supplied public project ID using the application's own environment variable and deployment instructions. Preserve unrelated settings; rebuild and redeploy to the verified existing site when requested, or prepare a new build for self-hosting. A dashboard environment change does not alter an already-built static upload.
4. Verify QR/mobile pairing on the actual origin when reachable, separately from merely displaying a wallet option. Report the actual result and any access, activation or connectivity blockers. Record only non-secret project ownership, configured/deferred/skipped status, origins, checks and follow-up steps in the app's deployment record.
