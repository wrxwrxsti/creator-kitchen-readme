<p align="center">
  <a href="https://www.creator.kitchen">
    <img src="https://www.creator.kitchen/opengraph-image.png" alt="Creator Kitchen - a content workspace for Instagram creators" width="100%" />
  </a>
</p>

# Creator Kitchen

**A content workspace for Instagram creators, with an AI coach grounded in their own numbers.**

[Website](https://www.creator.kitchen)

> This is a showcase repository. The source code is private. Happy to walk through it on a call: [cal.com/waris-hussain](https://cal.com/waris-hussain)

---

## The problem

Instagram creators keep ideas, saved posts and scripts in scattered places, and Instagram's insights show numbers without explaining them. General AI chatbots don't know a creator's own posts, so their advice is generic.

Creator Kitchen keeps everything in one workspace and gives coaching built from the creator's own posts and numbers, with the evidence under every answer.

## Who it's for

Instagram creators with a Creator or Business account.

## Features

- **Kira, the AI coach.** Answers questions from the creator's own posts, captions and numbers, and shows which posts back each point.
- **Analytics** for 7, 28 and 90 days: views, reach, interactions, saves, shares and follower growth, synced from Instagram.
- **What's working, what's not.** Pattern breakdowns by format, day, time posted and hook type, compared with the creator's own median.
- **Hook tagging.** Every post gets a hook type. A weekly research agent drafts new hook patterns with sources, and a human approves them before the coach uses them.
- **Ideas board** with stages from idea to posted. Import ideas from pasted text, a file, or a photo of handwritten notes.
- **Home briefing.** "Coach noticed" cards when a new post's numbers settle, plus a daily question that teaches the coach about the creator.

## How it works

1. Sign in with Google or an email link.
2. Connect an Instagram Creator or Business account through Instagram's official login.
3. Creator Kitchen scans posts and account numbers and builds a profile of the creator.
4. Use Home, Analytics and the Ideas board day to day. Numbers sync daily, or on demand.
5. Ask the coach anything. Answers cite the creator's own posts and numbers.

## Tech stack

| Layer | Tools |
| --- | --- |
| Frontend | Next.js 16 (App Router, Turbopack), React 19, Tailwind CSS 4, motion |
| Backend | Next.js server actions and route handlers, Inngest for scheduled and background jobs |
| Database | Supabase: Postgres with row-level security, Storage, Auth |
| AI | Anthropic Claude (Sonnet for the coach and research, Opus for profile building, Haiku for tagging and scoring), web search for the research agent, Voyage AI embeddings for semantic search |
| Integrations | Instagram API with Instagram Login (Meta Graph API), Resend, Sentry, Zod |
| Hosting | Vercel |

## Engineering highlights

- **The coach can't make up numbers.** Analytics facts are calculated in code, and the coach can only cite them by ID. A coverage test enforces it.
- **Human-approved research.** A weekly agent searches the web for new hook patterns and drafts them with sources. Nothing reaches the coach until a person approves it.
- **Security first.** Instagram tokens are encrypted with AES-256-GCM, row-level security is covered by 48 automated checks, and production admin access needs both an admin role and an allow-listed email.
- **Cost and failure guardrails.** Hard daily, monthly and per-creator AI budgets, plus an hourly watcher that alerts when spend passes 80%, the AI key is refused, or Instagram blocks the app.
- **Private by default.** Every non-public URL sends a noindex header and a crawl-safety test runs in CI. Public pages are structured for search engines and AI assistants (JSON-LD, FAQ schema, llms.txt).
- **CI on every change:** lint, type checks, 31 analytics tests, an admin-access guard, a production build, a secret scanner and the crawl-safety test.

## Privacy

Creator Kitchen reads Instagram data only through Meta's official API with the creator's permission, stores access tokens encrypted, and keeps each creator's data separate with database row-level security.

## Status

**Private beta in development.** Work started on 8 October 2026 and reached a working private beta in about three weeks. The Instagram integration is going through Meta's App Review before outside creators can connect their accounts.

## Built by

**[Waris Hussain](https://www.warishussain.com)**, founder: product direction, design direction, branding and the character art. Built with Claude Code as the engineering tool.

[Website](https://www.warishussain.com) · [LinkedIn](https://www.linkedin.com/in/waris-hussain/) · [X](https://x.com/WarisHussain57) · [GitHub](https://github.com/wrxwrxsti)
