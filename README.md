# Patient Portal — Phase 0 + 1 prototype

**File:** `patient-portal.html` · **Status:** front-end skeleton on SIMULATED DATA ONLY.
Open it in any browser (double-click) — no build step, no install, works offline. Best viewed
on a phone or a narrow window (it's designed mobile-first).

---

## What this IS
A working, clickable patient-facing app shell — **separate from the staff app** — with a
five-tab bottom nav (**Home · Visits · Results · Messages · More**):
- **Patient login** (email/phone → one-time code, then optional Face ID) — the OTP auth *flow* (demo: any input works)
- **Home** — "your next step", tonight's injection reminder, a results-released nudge, and a
  visual "where you are" journey timeline
- **Visits** — upcoming + past appointments (view-only), with "add to calendar"
- **Results** — clinician-released results only, each behind a "confirm it's you" gate and shown
  with the clinician's note (sensitive results like beta-hCG are shared by phone, never silently posted)
- **Messages** — one-way updates from the clinic + a "request a callback" action (not two-way chat; not for emergencies)
- **More** — Treatment plan, your care team, **Medicines** (how-to per drug; dosing/timing comes
  from the doctor, not the app), **Learn** (six warm education guides), **Your consents** (read-only,
  with a "talk to your team to change" note), details & privacy, about, sign out

Design: deliberately calm and warm (soft paper, one gentle teal accent, generous space, kind
plain-language copy) — built for an anxious, hopeful patient, NOT as a clinical dashboard.

## What this is NOT (the safety gates — read this)
- **No real data. No database. No network calls.** Everything is local, fake, and badged "DEMO"
  at the top of every screen so simulated data can never be mistaken for real.
- **No Row-Level Security yet.** The real security layer (the thing that guarantees Patient A
  can NEVER see Patient B's data) is NOT in this file — it's database/auth work in Supabase that
  must be built and tested against the real backend, with proper review. This prototype
  deliberately doesn't touch any of that.
- **Not connected to the staff app's data.** When it's real, the portal will read each patient's
  own journey through a secured, patient-scoped layer — only after the compliance review.

## The go-live gate (unchanged, non-negotiable)
Before this shows ONE piece of real patient data, ALL of these must be true:
1. **Legal/compliance review done** (DHA/MOHAP + UAE PDPL, GDPR if any EU patients).
2. **Patient consent-to-portal flow** in place.
3. **Row-Level Security isolation tests green** — proven that a patient can reach only their own
   rows.
Until then: build and demo on simulated data, badged. That's exactly what this is.

## Good next steps
- **Show it to people** (co-founder, a trusted patient, staff) and gather reactions — it's a
  prototype precisely so you can react to the experience before the hard backend work.
- **Decide the Tier-2/3 policy questions** (see DESIGN_patient_portal.md §6): which lab results
  to show and who releases them; medication reminders yes/no; chat model.
- **Plan the real security layer** as a reviewed spec — NOT live-pasted SQL — for when the
  backend is set up properly. This is the careful step that protects patients.

## Honest note
This is a *prototype of the experience*, and a strong one — but the genuinely hard, important
part of a patient portal is the security and compliance layer underneath, which is deliberately
NOT in this file. Treat this as the "what it feels like" piece; the "is it safe" piece comes
next, separately, and carefully.
