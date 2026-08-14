# Halda — The college guide that grows with you

Halda is an AI college guide that meets students before the application season, stays with them across web, SMS, email, and voice, and builds a richer student profile every time they return.

Built for the **HALDA Bounty HITLAB World Cup: Innovation Hackathon (July 2026)**, the prototype pairs a student-first advising experience with a consent-first university lead console. It is designed around a simple idea: students should receive genuinely useful guidance while retaining control of the information they choose to share.

[Project presentation](https://docs.google.com/presentation/d/1efNcCPl4x_Slr9Akek9G6KfbtpO7F0HontobqiM4prE/edit?slide=id.p1#slide=id.p1) · [Project brief and roadmap](https://docs.google.com/document/d/1dsByvWHcOy1PeOUWmxzcf87Wjw33_9hIs61p9e9GFVs/edit?tab=t.0)

## Why Halda

College exploration is fragmented: students move between search sites, social platforms, school counselors, and application portals—often starting only when deadlines are close. Halda starts earlier, helps students make sense of their options, and remembers the context they have already shared.

As a student’s interests, goals, budget, activities, and academic history become clearer, Halda can offer more relevant guidance and better school matches. That accumulated, consented profile is valuable to the student first; it can become a high-intent, privacy-respecting connection to universities only when the student opts in.

## What the prototype includes

### For students

- A conversational AI guidance counselor that can update a student profile as the conversation develops
- Personalized school exploration and matching using real college data, including trade-school options
- Career exploration, scholarship suggestions, application tasks, milestones, and gamified progress
- A simulated admissions committee that shows how a profile may read to reviewers
- Web chat, voice input, SMS, and email handoffs that share one student context
- Community and cohort experiences that help students explore alongside peers
- Spanish-language support and consent-aware handling for students and families

### For university partners

- A tenant-aware lead console at `/partner`
- Consent-gated student leads, with masked data until a lead is purchased
- A frozen profile snapshot for purchased leads rather than live access to a student’s data
- Demo tools and seeded personas for reliable presentations

## Product principles

1. **Student-first.** The core product must be useful before it is a recruiting channel.
2. **Profile-building through help.** Students should not need to fill out a long form to be understood; each useful interaction can improve their profile.
3. **Consent-first by design.** Students control when their information is shared. The product is built with minors and FERPA-aware workflows in mind.
4. **Meet students where they are.** The same guide should be available across the channels students actually use.
5. **Real information, not generic advice.** School data, affordability signals, ratings, scholarships, and deadlines inform the experience.

## Demo flow

The presentation uses two example students:

- **Jordan**, a 15-year-old sophomore who is still exploring, demonstrates a career-first guidance path.
- **Maya**, a 17-year-old first-generation student interested in nursing with a $15K budget, demonstrates personalized matching, affordability guidance, scholarship suggestions, and multichannel handoff.

During a demo, update a detail in either profile and watch Halda carry it through the profile, guidance, and recommendations. The simulated admissions committee is the culminating moment: it makes the value of a profile that grows over time visible.

## Growth strategy

Halda’s go-to-market plan focuses on classroom-scale adoption instead of paid acquisition. College- and career-readiness plans create a natural school channel; one counselor or teacher can onboard an entire cohort. Student ambassadors, partner programs, referrals, organic discovery, and earned media extend that foundation.

The goal is to seed 62,000 sign-ups through these channels and use a referral loop to reach 100,000 students within six months—without relying on paid advertising.

## Technical overview

This is a Next.js App Router application with a separate Express bridge for SMS and email services.

- `/` — student mobile-style app experience
- `/partner` — university partner lead console
- `/simulator` — data-driven student and college simulator
- `app/api/*` — chat, profile extraction, voice, SMS, school data, lead, evaluation, and demo-seeding endpoints
- `lib/useHalda.tsx` — shared student state, profile updates, matching, consent, tasks, credits, and local persistence
- `lib/halda-agent.ts` and `app/api/gemini/route.ts` — Gemini-powered agent and tool calling
- `lib/agent.ts` and `app/api/chat/route.ts` — deterministic fallback and server/SMS chat path
- `backend/` — Surge SMS and email-provider bridge

The app includes deterministic fallbacks for demo reliability. Gemini features require the API keys described in `.env.example`.

## Run locally

```bash
pnpm install
cp .env.example .env.local
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000).

For a production-style demo run:

```bash
pnpm demo
```

To type-check the project:

```bash
node_modules/.bin/tsc --noEmit
```

## Next opportunities

- Deeper career-to-program alignment
- Scholarship matching that becomes more precise as a profile grows
- A student cohort and community layer
- College-readiness scoring and progress tracking
- Extracurricular and portfolio coaching
- University-authored profiles and admissions guidance
- Additional agent roles, such as peer mentor, industry scout, profile critic, and contrarian reviewer

## Team

Halda was created as a team project for the HALDA Bounty HITLAB World Cup: Innovation Hackathon.
