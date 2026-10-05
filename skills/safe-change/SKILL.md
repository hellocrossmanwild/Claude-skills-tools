---
name: safe-change
description: "Makes code changes safely: a branch, plain-English save points, a pull request and easy undo. Use for changes to a live app, or 'undo that', 'go back', 'what changed' or 'open a PR'."
---

# Safe change

You're making changes for someone who doesn't read code. Your job is to keep the live version safe, explain every change in plain English, and make undoing easy. Use the GitHub connector where it helps.

## Before changing anything
1. Say in one or two plain sentences what you're about to change and why.
2. If the project is already live, make a **branch** for this change (name it after the change, e.g. `add-booking-reminders`). Never work straight on `main` once real people use the app. For a brand-new project's first build, working on `main` is fine.
3. Check there are no unsaved changes lying around. If there are, ask what to do with them before starting.

## While changing
- Keep each change small and about one thing.
- After each piece works, make a **save point** (commit) with a note a non-developer would understand: "Add a reminder email the day before a booking", not "refactor scheduler".
- Push the branch to GitHub so the work is backed up.

## When it's ready
Open a **pull request** with:
- **What changed:** plain-English bullet points
- **Why:** one sentence
- **How to check it:** the exact steps to try it (and the preview link if Vercel made one)
- **Anything risky:** data changes, new keys needed, things that can't easily be undone
Then stop and let them review. Don't merge unless they say so.

## Undo
If they say "undo", "go back" or "that broke it":
1. List the recent save points in plain English, newest first.
2. Ask which one to go back to.
3. Go back **without losing history**: prefer reverting (a new save point that undoes the change) over deleting history. Never force-push or delete branches without a clear yes.
4. Confirm what's now live and what was undone.

## Explaining a change
If they ask "what changed?" or "explain this", describe the change in plain English: which screens or behaviour it affects, not file names or code.
