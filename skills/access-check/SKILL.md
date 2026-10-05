---
name: access-check
description: Checks who can see what in an app. Builds a page-by-page table for visitors, signed-in users and paying members, then actually tests the pages while logged out. Use when someone asks "who can see this page", "is my paywall working", "check my logins", or after adding sign-in or payments.
---

# Access check

You're checking that the right people see the right things. The person doesn't code, so report in a table they can read at a glance.

## 1. List every page and action
Read the app and list every page (and important actions, like "download", "watch", "edit"). Include sign-in and account pages.

## 2. Say who should see what
Ask (with tap-to-answer options) or infer from their brief, then show the intended rules:

| Page / action | Visitor (logged out) | Signed in, free | Paying member | Admin |
|---|---|---|---|---|

Use ✓, ✗ or "preview only".

## 3. Test it for real
- Run the app (or use the preview link) and **open each page while logged out**. Record what actually happens: shows the content, redirects to sign-in, or shows an error.
- Check the obvious ways around a paywall: opening a paid page's URL directly, direct links to files or videos, thumbnails or links that leak a paid item's ID, and API routes that return paid content without checking who's asking.
- If you can, test as a signed-in free user too.

## 4. Report
Show the table again with what **actually** happened next to what **should** happen, and highlight every mismatch in plain English: "A visitor can open /videos/12 directly and watch it without paying."
For each problem, explain the fix in one line, and offer to make it on a branch. Don't change anything without a yes.

## 5. Sign-in sanity
Briefly confirm sign-in itself is handled by a login service (such as Clerk), not home-made password code, and that pages check sign-in on the server, not just by hiding buttons.
