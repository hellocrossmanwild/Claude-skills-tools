---
name: keys-checklist
description: Lists every secret key and setting an app needs, what each must be called, whether it's secret or safe to show, and where it goes. It never asks for or handles the actual values. Use when someone asks "what keys do I need", "set up my environment variables", "what goes in .env", or is connecting a new service.
---

# Keys checklist

You're helping someone who doesn't code set up their app's keys (environment variables) safely. The golden rule: **you never see, ask for, or handle a real key value.** They add values themselves.

## 1. Work out which keys the app needs
Read the project (code and CLAUDE.md) and list every environment variable it uses or will need for its services: database, logins, payments, email and anything else.

## 2. Make the checklist
Show a table:

| Name (exactly) | What it's for | Secret? | Where to get it | Where it goes |
|---|---|---|---|---|

- **Secret?** Yes for anything that grants access (database URLs, secret API keys, webhook secrets). "Public" only for keys designed to be shown in the browser (often prefixed `NEXT_PUBLIC_`). If unsure, treat it as secret.
- **Where to get it:** the exact page in that service's dashboard.
- **Where it goes:** Vercel → Project → Settings → Environment Variables (for the live app), and `.env.local` on this computer (for local building).

## 3. Prepare the empty spaces
- Create or update `.env.local` with every name and an **empty** value, plus a comment saying where to get it. They paste the values in themselves.
- Make sure `.env*` files are listed in `.gitignore` so they never reach GitHub. Check, and fix it if not.
- Optionally create `.env.example` (names only, no values) so the project documents what it needs.

## 4. Safety checks
- Search the code for anything that looks like a real key (long random strings, `sk_live`, `sk_test`, database URLs with passwords). If you find one: tell them, explain the risk in one line, move it to an environment variable, and recommend they **rotate** (regenerate) that key in the service's dashboard, since it may have been exposed.
- If they paste a key into the chat, gently tell them not to, recommend rotating it, and don't repeat it back.
- Suggest a password manager for keeping keys to reuse later.

## 5. Finish
Give them the checklist as a file to keep, with tick boxes for "added locally" and "added in Vercel".
