---
name: deploy-doctor
description: Diagnoses a failed or broken Vercel deployment. Reads the build and runtime logs through the Vercel connector, explains what went wrong in plain English, and fixes it on a branch. Use when someone says "my deploy failed", "the site is broken", "Vercel error", "build failed", or "why isn't my change live?".
---

# Deploy doctor

You're helping someone who doesn't code fix a deployment. Diagnose first, explain plainly, then fix safely.

## 1. Find the problem
1. Using the Vercel connector, find the project and its most recent deployments. Identify the failed one (or the latest one if the site is live but broken).
2. Read its **build logs** (and runtime logs if the build passed but the site errors). Find the first real error, not the noise after it.
3. Check whether the live site is still on the last working version. (Vercel keeps the last good deployment live when a build fails, so visitors usually aren't affected. Confirm this and reassure them if so.)

## 2. Explain it
In one short paragraph, plain English:
- **What broke:** e.g. "The build stopped because a page imports a file that doesn't exist."
- **Why:** e.g. "It was renamed in the last change, but one page still uses the old name."
- **Is the live site affected?** yes or no.
No stack traces unless they ask.

## 3. Common causes to check
- A **missing environment variable** (a key set on the computer but not in Vercel). Say which name is missing and where to add it in Vercel's settings. **Never ask for the key's value, and never put it in code.** They add it themselves.
- A typo, a renamed or missing file, or a missing package.
- A type or lint error that only fails on the build server.
- A database or API the app can't reach from Vercel.

## 4. Fix it safely
- Make the fix on a **branch**, push it, and use the **preview deployment** to confirm the build passes.
- Tell them what you changed in plain English and share the preview link.
- Only merge to `main` (which deploys live) when they say so.

## 5. If the live site is broken right now
Offer the fast, safe option first: **roll back** to the previous working deployment in Vercel (one or two clicks, or via the connector if they say yes), then fix calmly. Note: after a rollback, new pushes don't go live automatically until the rollback is undone. Remind them to undo it once the fix is ready.
