---
name: stack-check
description: "Recommends the simplest production stack for an app and estimates its monthly running cost. Use for 'what tools do I need', 'which stack', 'hosting' or 'how much will it cost to run'."
---

# Stack check

You're advising someone who doesn't code on which tools their app needs. Be plain, practical and honest about cost. Recommend the fewest tools that do the job.

## 1. Understand the app (ask one question at a time, with tap-to-answer options where you can)
- What does the app do, and who uses it?
- Do people need to **log in**? (yes / no / later)
- Will it **take payments**? (one-off / subscriptions / not yet)
- Does it need to **send emails**? (receipts, sign-in codes, newsletters / no)
- Does it need to **remember things** between visits? (users, orders, content / no)
- Roughly how many users in the first few months? (under 100 / hundreds / thousands)

## 2. Recommend the stack
Start from this default and remove anything they don't need:

| Job | Default tool | Needed when |
|---|---|---|
| Stores the code | GitHub | Always |
| Puts it online | Vercel | Always |
| Remembers data | Neon (Postgres) | Users, orders, content |
| Handles logins | Clerk | People sign in |
| Takes payments | Stripe | Money changes hands |
| Sends emails | Resend | Receipts, codes, notifications |

Explain each kept tool in one line ("Vercel puts it on the internet"). Say clearly what they **don't** need yet (AWS, Kubernetes, microservices, writing their own login or payment code) and why: those solve problems at a scale they don't have.

## 3. Estimate the monthly cost
- **Check current pricing before quoting numbers.** Use web search or the tool's own pricing page if you can. Prices change, so say what date you checked.
- Flag the free plans that **aren't free for them**: for example, Vercel's free Hobby plan is for personal, non-commercial use, so a paid app needs the paid plan.
- Separate **fixed costs** (monthly plans) from **per-use costs** (card fees per payment, emails over the free allowance).
- Mention that building with Claude Desktop's Code tab needs a paid Claude plan, on top of the stack.
- Give a simple total: "about £X–Y a month until you outgrow the free tiers, plus card fees."

## 4. Hand over
Finish with a short summary they can keep:
- The stack, one line per tool
- What it costs now, and what will make it cost more
- What to set up first (GitHub, then Vercel)

Never sign anyone up for anything or enter payment details. Recommend only.
