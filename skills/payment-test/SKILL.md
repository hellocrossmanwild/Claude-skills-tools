---
name: payment-test
description: Tests an app's payments end to end in Stripe's sandbox, like a real customer would. Runs successful, declined, refunded and cancelled payments, checks the right thing unlocks, and confirms the emails arrive. Use when someone says "test my payments", "check checkout works", "is Stripe set up right", or before switching to live mode.
---

# Payment test

You're testing payments for someone who doesn't code. Everything happens in Stripe's **sandbox (test mode)**: no real money moves. Never switch to live mode, create live charges, or handle real card details.

## 1. Confirm test mode
Using the Stripe connector, confirm you're in the sandbox and list the products and prices the app uses. If anything looks like live mode, stop and tell them.

## 2. Check the plumbing
- How does the app learn that someone paid? Usually a **webhook**. Confirm it exists, which events it listens for (e.g. `checkout.session.completed`, `customer.subscription.deleted`), and that its signing secret is an environment variable, not in code.
- Confirm what should unlock after payment and where that's stored in the database.

## 3. Run the scenarios
Use Stripe's published **test card numbers** (from Stripe's docs) to run each one through the app's checkout. Use the preview link or run the app locally:

| Scenario | Expect | Result |
|---|---|---|
| Successful payment | Unlocks the right thing, receipt email arrives | |
| Card declined | Clear error, nothing unlocks | |
| Card needs extra authentication (3D Secure) | Challenge appears, then succeeds | |
| Refund (from the Stripe dashboard or connector) | Access removed if that's the rule | |
| Subscription cancelled (if subscriptions) | Access ends at the right time | |

For each, check the app **and** the database actually changed, not just that Stripe says it worked.

## 4. Check the emails
If Resend (or another email service) is connected, confirm the receipt and welcome emails were sent, which address they came from, and that the sending domain is verified. Flag anything that would land in spam (an unverified domain, or sending from a free email address).

## 5. Report
Fill in the table with ✓ or ✗ and a plain-English note for each failure: what happened and the likely fix. Offer to fix on a branch.

## 6. Before going live
List what must change for real payments: live API keys in Vercel (they add them; never in chat or code), a live webhook endpoint and its new signing secret, and live prices. Remind them to check Stripe's current fees for their country.
