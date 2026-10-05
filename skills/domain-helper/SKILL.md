---
name: domain-helper
description: Walks someone through putting their app on their own domain (yourname.com instead of vercel.app), step by step in plain English, including the DNS records and checking it worked. Use when someone says "add my domain", "custom domain", "connect my domain to Vercel", or "set up DNS".
---

# Domain helper

You're helping someone who doesn't code connect their own domain to their app. DNS is fiddly; keep each step tiny and check it worked before moving on.

## 1. Gather the facts (one question at a time)
- What's the domain? (e.g. `slotbook.co.uk`)
- Where did they buy it? (the registrar, e.g. GoDaddy, Namecheap, Cloudflare, Google/Squarespace)
- Should the app live on the main domain, `www`, or a subdomain like `app.`?
- Is the domain already used for anything, especially **email**? If yes, be careful not to touch existing email records (MX and related TXT records).

## 2. Add the domain in Vercel
Using the Vercel connector (with a yes), or by guiding them through Vercel → Project → Settings → Domains, add the domain. Vercel then shows the exact DNS records it needs. **Use the records Vercel shows**, not remembered values, because they can differ per project.

## 3. Add the DNS records at the registrar
Give them a short, exact list to copy into their registrar's DNS settings:

| Type | Name / Host | Value | Notes |
|---|---|---|---|

Tell them where the DNS settings usually are for their registrar, in one line. Warn them not to delete existing email records.

## 4. Check it worked
- DNS can take minutes to a few hours to update. Check the domain's status in Vercel (via the connector if available) and tell them in plain English whether it's verified.
- Once verified, confirm HTTPS (the padlock) is working and that both `www` and the main domain go to the right place.

## 5. Follow-ups
Remind them to update anything that uses the old address: login service allowed URLs (e.g. Clerk), payment webhooks and success URLs (e.g. Stripe), email sending domains (e.g. Resend), and links on their site. Offer to find and update these in the code on a branch.
