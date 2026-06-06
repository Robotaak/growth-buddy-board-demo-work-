

# Growth Buddy Board – Lead & Launch Ops Dashboard

Growth Buddy Board is a lead tracking and launch operations dashboard built for a fictional coaching business, **Northbridge Growth Coaching**.

It gives online business coaches a single place to see:

- How many leads they have for the current launch,
- Where those leads came from,
- Who registered and attended the webinar,
- Who booked a sales call, and
- How much revenue has been generated vs. target.

🔗 **Live demo:** https://growth-buddy-board.lovable.app  

---

## Features

- **Pipeline overview KPIs**
  - Total leads in the system
  - Total revenue (auto‑calculated from enrollment + payment plan)
  - Webinar show rate (% of registrants who attended)
  - Sales conversion (% of attended calls that became clients)

- **Lead table with filters**
  - Sortable / searchable table of all leads
  - Columns for source, webinar status, sales call, decision, enrollment, and revenue
  - Quick filters for source and enrollment status to answer questions like:
    - “How many Instagram leads enrolled?”
    - “How many warm leads are still undecided?”

- **Add / edit lead workflow**
  - “Add lead” form to capture:
    - Name, email, source, date captured
    - Webinar registration + attendance (Live / Replay / No‑show)
    - Sales call / application status and outcome
    - Offer made, decision (Won / Lost / Not now / Ghosted)
    - Enrollment status and payment plan (Paid in full / Payment plan / N/A)
  - Revenue field auto‑calculates:
    - 0 for non‑clients
    - 1500 for pay‑in‑full clients
    - 1800 for payment plan clients

- **Sample data for a realistic launch**
  - Seed data for a 6‑week cohort launch:
    - Leads from Instagram, email list, LinkedIn, referrals and other channels
    - Mix of Live / Replay / No‑show webinar attendees
    - Won / Lost / Not now / Ghosted decisions
  - Lets you demo the app to a real coach without exposing any real client data.

---

## Data model

Each lead tracks (simplified):

- `id`
- `fullName`
- `email`
- `source` – Instagram, Email list, LinkedIn, Referral, Other
- `capturedAt` – date first captured
- `webinarRegistered` – boolean
- `webinarAttendance` – `"Live" | "Replay" | "No-show" | "Not registered"`
- `hasSalesCall` – boolean
- `callDate` – optional date
- `callOutcome` – `"Booked" | "Attended" | "No-show" | "Rescheduled" | null`
- `offerMade` – boolean
- `decision` – `"Won" | "Lost" | "Not now" | "Ghosted" | null`
- `enrollmentStatus` – `"Enrolled" | "Not enrolled"`
- `paymentPlan` – `"Paid in full" | "Payment plan" | "N/A"`
- `revenue` – numeric, derived from `enrollmentStatus` + `paymentPlan`
- `notes` – free text

This schema is designed so a coach (or their VA) can see the full journey of a lead from first touch to enrollment.

---

## Tech stack

> This app was generated and iterated using **Lovable**, an AI app builder for web apps. The underlying stack follows Lovable’s standard React front‑end setup. [^1]

- Frontend: React (generated via Lovable)
- Styling: Tailwind CSS / shadcn‑style component system (Lovable defaults)
- State: Front‑end state for demo data (no real backend in this public demo)

[^1]: Lovable’s official guides recommend building a small number of polished demo apps (landing page + dashboard + simple authenticated app) as proof of capability before pitching clients. [web:102]

You can inspect `package.json` in this repo for the exact dependencies.

---

## Getting started (local development)

```bash
# 1. Install dependencies
npm install
# or: pnpm install / yarn install

# 2. Start dev server
npm run dev

# 3. Open the local URL (usually http://localhost:3000)
```

If you’re using a different command (e.g. `npm start`), update this section accordingly.

---

## How a coach would use this in real life

1. **During a launch**
   - Add new leads as they come from Instagram, email, LinkedIn, or referrals.
   - Tag webinar registration and attendance after the live session.
   - Log calls, decisions, and payment plans.

2. **Daily review**
   - Check top‑level KPIs to see:
     - How many leads are in the pipeline,
     - How many calls are booked,
     - How close they are to their revenue goal.
   - Filter for “hot” leads (attended webinar, no decision yet) and follow up.

3. **Post‑launch**
   - Review conversion by source to see which channels brought the best clients.
   - Use insights to plan the next cohort’s marketing focus.

---

## Next ideas / roadmap

- Connect to a real backend (Supabase / Firebase / Airtable).
- Auth + multi‑cohort support.
- Per‑source conversion charts.
- Automated follow‑up task generation from lead status.

---

## About the creator

This project was built by **Aryan (“robotaak” on GitHub)** as part of a micro‑portfolio for Virtual Assistant and operations work for online coaches and agencies.

If you’d like a custom version of this dashboard for your coaching or agency business, reach out via:
- GitHub: https://github.com/robotaak
- robotaak48@gmail.com
