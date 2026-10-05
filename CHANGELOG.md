# Changelog

## v1.1.1 · 5 October 2026
Checked every skill against Anthropic's current skill docs and fixed what didn't match:
- **Uploads work on claude.ai.** Every description is now under claude.ai's 200-character limit (they were 280–340, so uploads would have been rejected). Trigger phrases are kept.
- **Works in a normal chat too.** Access check, Payment test and Review loop now give you exact click-by-click steps when Claude can't open your app itself, and never mark a step passed without seeing the result.
- **Review loop** shows a checklist it ticks off as it goes.
- Payment test now confirms each payment, refund and webhook on Stripe's side.

## v1.1 · 5 October 2026
Thirteen new skills, covering an app from idea to first customers:
- **Plan:** Idea to MVP, Stack check, Sketch it
- **Set up:** Keys checklist
- **Build:** Safe change, Make it yours
- **Check:** Access check, Data check, Payment test, Review loop
- **Ship:** Deploy doctor, Domain helper, First ten

Also new: `all-skills.zip` with every skill, and a Claude Code plugin so you can install them all with two commands.

## v1.0 · 5 October 2026
- **Project starter**: checks every connected tool with read-only calls, runs an adaptive interview about your idea, and writes `CLAUDE.md` with your stack and four safety rules.
