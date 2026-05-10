# PeakSpan Fat Loss Readiness Quiz

Lead-capture quiz + 5-email nurture sequence for PeakSpan Health (Australian medically supervised weight management telehealth).

**Architecture:** static HTML quiz → GHL inbound webhook → GHL workflow creates contact → tag fires 5-email sequence. No N8N. No backend.

**Compliance:** every public-facing piece of copy in this repo has been written to comply with the TGA Therapeutic Goods Advertising Code. No named prescription medicines, no substitute terms ("weight loss injections", "script and go"), no testimonials, no before/after claims. See the bottom of `email-sequence.md` for the compliance checklist.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The 10-question quiz page. Single-file static HTML/CSS/JS. POSTs to GHL webhook on submit. |
| `email-1-thank-you.html` | Immediate post-quiz email |
| `email-2-protein.html` | Week 1 — protein |
| `email-3-strength-training.html` | Week 2 — strength training |
| `email-4-weight-loss-face.html` | Week 3 — common mistakes |
| `email-5-final-cta.html` | Week 4 — final CTA |
| `email-sequence.md` | Full email copy (subjects + bodies) and the GHL workflow setup guide |
| `Brand Guidelines.docx`, `Logo*.png`, `*.pdf` | Brand assets |
| `TGA Guidelines.docx`, `PeakSpan_Social_Media_Compliance_Guidelines.docx` | Compliance reference docs |

---

## Hosting

### Primary: GoHighLevel custom page

1. In GHL, create a new custom page.
2. Open the HTML element / code-edit mode and paste the entire contents of `index.html`.
3. Publish.

When you change the quiz, repeat: copy `index.html` → paste into GHL → republish. There is no auto-sync; GHL hosting is manual.

### Backup: Vercel (auto-deploys from this repo)

1. Push this repo to GitHub.
2. In Vercel, **Add New Project** → import the GitHub repo.
3. Framework preset: **Other** (it's a static site, no build step).
4. Output directory: `Peakspan/` (or move `index.html` to repo root if you prefer Vercel default).
5. Deploy. Vercel auto-deploys on every push to `main`.
6. Optionally set a custom domain (e.g. `quiz.peakspan.com.au`).

---

## GHL workflow setup

Full step-by-step is in `email-sequence.md`. Two workflows total:

1. **`Fat Loss Readiness Quiz - Webhook`** — Inbound Webhook trigger → Create/Update Contact → Add Tags → Update Custom Fields → Add Note. This replaces the old N8N flow.
2. **`Fat Loss Readiness Quiz - Email Sequence`** — Tag Added (`Quiz Completed`) → 5 emails over 4 weeks.

### One-time wiring

1. Create Workflow 1 in GHL, add the Inbound Webhook trigger, copy the URL it generates.
2. In `index.html`, find `const GHL_WEBHOOK_URL = 'YOUR_GHL_INBOUND_WEBHOOK_URL_HERE';` and paste the URL in.
3. Re-publish (GHL custom page) or `git push` (Vercel).
4. Submit a test quiz → verify the contact appears in GHL with all tags + custom fields.

---

## Pre-publish checklist

- [ ] Medical/compliance review of `index.html` and all 5 emails (per PeakSpan SOP)
- [ ] GHL Workflow 1 (Webhook) published and tested with a sample submission
- [ ] GHL Workflow 2 (Email Sequence) published, all 5 emails uploaded
- [ ] `GHL_WEBHOOK_URL` in `index.html` replaced with the real URL (not the placeholder)
- [ ] Booking iframe in `index.html` (line ~681) still points at the correct calendar widget
- [ ] Live site loaded in browser, full quiz taken end-to-end, contact arrived in GHL

---

## Webhook payload reference

What `index.html` POSTs to GHL on quiz submission:

```json
{
  "firstName": "...",
  "email": "...",
  "phone": "...",
  "notes": "Formatted multi-line summary of all answers",
  "tags": ["Quiz Completed", "Risk: HIGH|MODERATE|LOW", "Lead Quality: HOT|WARM|COLD", "May 2026 Campaign", "Fat Loss Quiz"],
  "riskScore": "HIGH|MODERATE|LOW",
  "leadQuality": "HOT|WARM|COLD",
  "quizCompletedDate": "ISO-8601 timestamp",
  "customFields": {
    "primaryMotivation": "a|b|c|d",
    "primaryMotivationText": "human-readable answer",
    "weightLossAttempts": "...",
    "weightLossAttemptsText": "...",
    "weightGoal": "...",
    "weightGoalText": "...",
    "bodyChanges": "...",
    "bodyChangesText": "...",
    "strengthTraining": "...",
    "strengthTrainingText": "...",
    "proteinIntake": "...",
    "proteinIntakeText": "...",
    "energyLevels": "...",
    "energyLevelsText": "...",
    "biggestChallenge": "...",
    "biggestChallengeText": "...",
    "investmentReadiness": "...",
    "investmentReadinessText": "...",
    "currentSupport": "...",
    "currentSupportText": "..."
  }
}
```

The `*Text` fields are the human-readable answer strings (use these in custom fields). The unsuffixed fields are the raw `a/b/c/d` values (useful for if/else branching).
