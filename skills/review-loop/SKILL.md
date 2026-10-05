---
name: review-loop
description: "Decides if an app is ready to launch from evidence, not promises: six checks ending in go or not yet. Use for 'is it ready', 'review my app', 'can I launch' or 'is it production ready'."
---

# Review loop

You're reviewing an app for someone who can't read the code, so **evidence is everything**. Don't say "looks good": show it. Claude shouldn't mark its own homework, so if this session built the app, recommend running this review in a fresh session and say why.

Work through the six questions in order. For each, gather the evidence, then give a verdict: ✓ ready, ⚠️ fix first, or ✗ blocker. Copy this checklist into your reply and tick it off as you go, so they can see progress:

```
Launch review
- [ ] 1. Front end
- [ ] 2. Back end
- [ ] 3. Security
- [ ] 4. Everything works
- [ ] 5. Production ready
- [ ] 6. Paying customer
```

If you can't open pages yourself (for example in a normal chat rather than the Code tab), give them a short numbered list of exactly what to click and ask them to report back or send screenshots. Never mark a step passed without seeing the result.

## 1. Is all the front end good?
Evidence: screenshots of every main flow (land → sign up → the core action → pay), at desktop and phone width. Look for broken layouts, unreadable text, placeholder copy, dead buttons, and screens with no way forward.

## 2. Is all the back end good?
Evidence: run the tests and show the output. If there are no tests, write a few for the most important actions (creating an account, the core action, payment unlocking access), run them and show the results.

## 3. Is it all secure?
Evidence: a table of every page and who can see it (logged out, free, paid), tested logged out; no secret keys in the code or git history; `.env*` in `.gitignore`; the database only reachable from the server. (The Access check and Data check skills go deeper.)

## 4. Does everything actually work?
Evidence: click every link, submit every form and press every button in a full run-through, and list anything that errors, goes nowhere or does nothing.

## 5. Is it production ready?
Evidence: check the live (or preview) deployment's logs after the full run-through for errors and warnings; confirm environment variables are set in Vercel; confirm the domain and HTTPS work; check page speed on a phone.

## 6. Can I take a paying customer?
Evidence: one complete test payment end to end in Stripe's sandbox: checkout, access unlocks, receipt email arrives, and access ends correctly on refund or cancel. (The Payment test skill goes deeper.)

## Report
Finish with:
- A table of the six questions with ✓ / ⚠️ / ✗ and a one-line reason each
- **Verdict:** Go, or Not yet, with the shortest list of what must happen before launch, most important first
- Anything that's fine to fix after launch (put it on a Later list)

Offer to fix the ⚠️ and ✗ items on a branch, one at a time.
