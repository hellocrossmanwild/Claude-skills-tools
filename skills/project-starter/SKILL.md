---
name: project-starter
description: "Sets up a new app project: checks every connected tool works, interviews about the idea, writes CLAUDE.md. Use for 'project starter', 'set up my project', 'new app' or 'write my CLAUDE.md'."
---

# Project starter

You're helping someone who doesn't use the terminal set up a new app project. Keep every message short and in plain English. If you use a technical word, explain it in one line.

Work through the three steps in order. Tell them which step you're on.

## Step 1 · Check every connected tool

1. List every connector / MCP server you can see in this session: each one by name (for example GitHub, Vercel, Neon, Stripe, Resend, Clerk, Google Drive, Slack…). Don't limit yourself to any particular set.
2. For each one, make one small **read-only** call that proves the sign-in works. Pick the safest read the tool offers: list repos, list projects, get account info, search docs. Never create, change or delete anything in this step.
3. Report back as a simple table: tool, ✓ answered or ✗ failed, and a few words on what you saw (empty lists are fine on new accounts).
4. For anything that failed, say in one line how to fix it: "Go to Connectors, find X, disconnect and connect it again." Then carry on; a failed tool doesn't block the rest.
5. If they're building a typical web app, point out any of these that are missing so they know to add them later: GitHub (code), Vercel (hosting), Neon (database), Stripe (payments), Resend (email). Clerk's connector only helps write sign-in code, so it's fine if it's missing.

## Step 2 · Interview them about the idea

Interview until you could explain the app to a stranger in two sentences. Ask **one question at a time**, and wherever possible offer tap-to-answer options (multiple choice, pick several, or rank) instead of a blank question. Always allow "something else".

Cover, adapting to their answers and skipping anything already clear:
- What are you building, in a sentence or two?
- Who is it for?
- What's the one thing a user must be able to do?
- How will it make money? (Not sure yet is a fine answer.)
- What should it be called? (A working name is fine.)
- Any tools or must-haves you already know you want, or want to avoid?

Stop when it's clear, usually after 4–7 questions. Then play it back in two sentences and ask "Is that right?" before writing anything.

## Step 3 · Write CLAUDE.md

If a CLAUDE.md already exists, show them what it says and ask whether to add to it or start fresh. Never overwrite it without a yes.

Write CLAUDE.md with exactly these sections, filling the first two from the interview and Step 1:

```markdown
# <App name>

## What this is
<Two sentences: what it is, who it's for, the one thing users must be able to do, and how it makes money, in their words, tidied up.>

## Stack
- Next.js app, code in GitHub, hosted on Vercel
- Database: Neon (Postgres)
- Logins: Clerk
- Payments: Stripe (sandbox until I say go live)
- Email: Resend
- Connected tools right now: <the ✓ list from Step 1>
Don't add other services without asking me first and explaining why.

## Rules
- Secret keys only ever go in environment variables: in Vercel for the live app, in .env.local on this computer. Never in code, never in the chat, never committed. Make sure .env* files are in .gitignore.
- Every change happens on a branch, with a pull request I can read before it goes into main.
- Explain what you're about to do in plain English before you do it.
- Ask me before deleting files or data, or touching anything outside this project folder.
- Use the connected tools instead of asking me to run commands. If a command has to run, tell me what it does in one line first.
```

Where to save it:
- In the Code tab with a project folder open: save CLAUDE.md in the project folder.
- In a normal chat: give it to them as a file to download, and tell them to keep it. When they start building, it goes in the project folder.

## Finish

Tell them, in three short lines:
- CLAUDE.md is ready, and Claude reads it at the start of every session once it's in the project folder.
- Which tools are connected, and anything still to fix.
- They're ready to build.
