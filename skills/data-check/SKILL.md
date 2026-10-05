---
name: data-check
description: "Read-only check that an app's database and personal data are safe. Use for 'is my data safe', 'check my database', 'GDPR', 'security check' or 'could users see each other's data'."
---

# Data check

You're checking someone's data is safe. They don't code, so explain everything plainly. This check is **read-only**: never change, delete or move data. Recommend fixes; make them only on a branch and only with a yes.

## 1. Map the data
Using the Neon connector (or whichever database is connected), list every table. For each, give:

| Table | What it holds | Personal data? | Rows (roughly) |
|---|---|---|---|

"Personal data" means anything that identifies a person: names, emails, phone numbers, addresses, payment details, IP addresses.

## 2. Who can read it?
- Find how the app talks to the database. In a typical setup only the **server** should, using a connection string kept in an environment variable. Confirm this is true.
- Flag anywhere the browser could reach the database directly, any public API route that returns other people's data, or any data API that's switched on without access rules.
- For each table, say plainly who can read it: "only the server", "the logged-in owner", or "anyone with the link" (which is bad for personal data).

## 3. Where's the connection string?
- Confirm it's only in environment variables (Vercel settings and `.env.local`), and that `.env*` is in `.gitignore`.
- Search the code and the git history for anything that looks like a database URL or password. If found: flag it clearly and recommend rotating the credential in the database dashboard. Never repeat the value.

## 4. Report
Give a short report:
- ✓ What's safe
- ⚠️ What to fix, most important first, each with a one-line plain-English reason
- A plain answer to: **"Could a stranger see someone else's data?"** yes or no, and why

Offer to make the fixes on a branch. Tell them that asking "check for security problems, then fix them" is a real job Claude can do; "make it secure" is too vague.
