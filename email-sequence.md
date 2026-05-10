# PeakSpan Fat Loss Readiness Quiz Email Sequence

> Educational content only. Not medical advice. Every email below has been written to comply with the TGA Therapeutic Goods Advertising Code: no named prescription medicines, no substitute terms (e.g. "weight loss injections"), no testimonials, no before/after claims.

## Email 1: Immediate (Thank You)
**Subject:** Your fat loss readiness results are in, {{contact.first_name}}

---

Hi {{contact.first_name}},

Thanks for taking our Fat Loss Readiness Quiz.

Your results are ready - and whether your risk came back as high, moderate, or low, here's what matters most:

**Without the right approach, a significant portion of the weight you lose in a calorie deficit can come from muscle, not fat.**

That's not a reason to panic. It's a reason to be strategic.

Over the next few weeks, I'll share the key things you can do to protect your muscle while losing weight - so you don't just get lighter, you get healthier.

In the meantime, if you'd like personalised guidance from our medical team, you can book a free 20-minute call here:

[Book Your Free Call](https://api.leadconnectorhq.com/widget/booking/hZX1brCCPwcLIBDsb5u0)

Speak soon,

The PeakSpan Team

---

## Email 2: Week 1 (Protein)
**Subject:** The #1 mistake people make with food when losing weight

---

Hi {{contact.first_name}},

Here's something most people miss when they start losing weight:

When you eat less overall, that's great for the calorie deficit you need... but it's terrible for getting enough protein.

**Why this matters:**

Your body needs protein to maintain muscle. When you eat less overall, you're often getting far less protein than your body needs - exactly when it needs MORE.

**The research suggests you need 1.2-1.6g of protein per kg of bodyweight** to protect muscle during weight loss. For most people, that's 80-120g per day.

Quick wins:
- Prioritise protein at every meal (eggs, chicken, fish, Greek yoghurt)
- Consider a protein shake if appetite is low
- Eat protein FIRST before filling up on other foods

This one change can make a significant difference in what kind of weight you lose.

Next week: Why cardio alone isn't enough (and what to do instead).

The PeakSpan Team

P.S. Want a protein target specific to your body and goals? [Book a free call](https://api.leadconnectorhq.com/widget/booking/hZX1brCCPwcLIBDsb5u0) and we'll work it out together.

---

## Email 3: Week 2 (Strength Training)
**Subject:** Cardio won't save your muscle (here's what will)

---

Hi {{contact.first_name}},

I see this all the time:

Someone starts a weight loss journey, the scale begins dropping, they feel motivated... so they hit the treadmill.

Walking, running, cycling - all great for your heart. But here's the thing:

**Cardio doesn't signal your body to keep muscle.**

When you're in a calorie deficit, your body looks for energy wherever it can find it. Without the right signals, it will happily break down muscle for fuel.

**Strength training is that signal.**

Even 2-3 sessions per week tells your body: "Hey, I need this muscle. Burn the fat instead."

You don't need to become a bodybuilder. Simple exercises like:
- Squats (or sit-to-stand from a chair)
- Push-ups (or wall push-ups)
- Rows (with dumbbells or resistance bands)

These basics, done consistently, can dramatically change your results.

Next week: The 3 mistakes that lead to "weight loss face."

The PeakSpan Team

P.S. Not sure where to start with strength training? Our team can create a programme tailored to your fitness level. [Book a free call](https://api.leadconnectorhq.com/widget/booking/hZX1brCCPwcLIBDsb5u0).

---

## Email 4: Week 3 (Common Mistakes / Weight Loss Face)
**Subject:** Why some people age 10 years while losing weight

---

Hi {{contact.first_name}},

You've probably seen it - that gaunt, aged look some people get after rapid weight loss. There's even a name floating around for it: "weight loss face."

It's not inevitable. But it IS common when people make these mistakes:

**Mistake #1: Losing weight too fast**
Rapid weight loss doesn't give your skin time to adjust, and it often means you're losing muscle along with fat.

**Mistake #2: Not eating enough protein**
Your face has muscles too. When you lose muscle mass overall, it shows in your face first.

**Mistake #3: No resistance training**
Without strength training, your body loses its shape - including the structure that keeps your face looking full and healthy.

**Mistake #4: No medical supervision**
A one-size-fits-all approach means no one is monitoring your body composition. You might be celebrating the number on the scale while losing the wrong kind of weight.

The good news? All of these are preventable with the right approach.

Next week: How to know if you're on track (and when to ask for help).

The PeakSpan Team

P.S. Concerned about how your weight loss is affecting your appearance or energy? [Let's talk](https://api.leadconnectorhq.com/widget/booking/hZX1brCCPwcLIBDsb5u0).

---

## Email 5: Week 4 (Final CTA)
**Subject:** {{contact.first_name}}, here's what happens next

---

Hi {{contact.first_name}},

Over the past few weeks, I've shared the three keys to protecting your muscle while losing weight:

1. **Optimised protein intake** (1.2-1.6g per kg)
2. **Strategic strength training** (2-3x per week)
3. **Proper medical supervision** (not just a one-and-done plan)

Here's the truth: knowing what to do and actually doing it are two different things.

Most people lose weight alone. They jump from one approach to the next with no follow-up, no body composition monitoring, and no real plan.

**That's where PeakSpan is different.**

We combine:
- Doctor-led medical supervision
- Personalised nutrition guidance
- Tailored exercise programming
- Regular check-ins and adjustments

All designed to help you lose fat, not muscle - and keep it off long-term.

**Ready to do this properly?**

[Book your free 20-minute call](https://api.leadconnectorhq.com/widget/booking/hZX1brCCPwcLIBDsb5u0)

We only take on a limited number of clients each month to ensure everyone gets the attention they deserve. If you've been thinking about it, now's the time.

The PeakSpan Team

---

# GoHighLevel Setup

You'll create **two workflows** in GHL. The first replaces what N8N used to do (receive the quiz POST, create the contact, apply tags). The second runs the 5-email sequence off the `Quiz Completed` tag.

---

## Workflow 1: Webhook → Contact

This is the new GHL-native replacement for the N8N webhook.

### Step 1 — Create the workflow

1. **Automation** → **Workflows**
2. **+ Create Workflow** → **Start from Scratch**
3. Name: `Fat Loss Readiness Quiz - Webhook`

### Step 2 — Add the inbound webhook trigger

1. **Add New Trigger** → **Inbound Webhook**
2. GHL generates a unique URL — **copy it**
3. **Save**

### Step 3 — Paste the URL into the quiz HTML

1. Open `index.html`
2. Find: `const GHL_WEBHOOK_URL = 'YOUR_GHL_INBOUND_WEBHOOK_URL_HERE';`
3. Replace the placeholder with the URL from Step 2
4. Re-publish (paste updated HTML into your GHL custom page, or `git push` if using Vercel)

### Step 4 — Capture a sample payload

1. Take the quiz once with a test email
2. Back in the workflow, click the **Inbound Webhook** trigger — GHL needs a sample payload to map fields against
3. The captured JSON gives you fields you can reference in later actions as `{{inboundWebhookRequest.<field>}}`

> Note: exact merge-field syntax (`{{inboundWebhookRequest.x}}` vs `{{trigger.body.x}}` vs `{{webhook.x}}`) varies by GHL workflow-builder version. Use whatever the dropdown shows for your account.

### Step 5 — Add **Create/Update Contact** action

Map the top-level webhook fields:

| Contact field | Webhook reference |
|---|---|
| First Name | `{{inboundWebhookRequest.firstName}}` |
| Email | `{{inboundWebhookRequest.email}}` |
| Phone | `{{inboundWebhookRequest.phone}}` |

### Step 6 — Add tags (Add Contact Tag actions)

- `Quiz Completed`
- `Risk: {{inboundWebhookRequest.riskScore}}` (resolves to `Risk: HIGH` / `MODERATE` / `LOW`)
- `Lead Quality: {{inboundWebhookRequest.leadQuality}}` (`HOT` / `WARM` / `COLD`)
- `May 2026 Campaign`
- `Fat Loss Quiz`

### Step 7 — Map custom fields (recommended)

For each quiz answer you want stored on the contact, add an **Update Contact Field** action. Use the `*Text` versions for human-readable values (the raw `a/b/c/d` values are also available).

| Custom field | Webhook reference |
|---|---|
| Primary Motivation | `{{inboundWebhookRequest.customFields.primaryMotivationText}}` |
| Weight Loss Attempts | `{{inboundWebhookRequest.customFields.weightLossAttemptsText}}` |
| Weight Goal | `{{inboundWebhookRequest.customFields.weightGoalText}}` |
| Past Body Changes | `{{inboundWebhookRequest.customFields.bodyChangesText}}` |
| Strength Training | `{{inboundWebhookRequest.customFields.strengthTrainingText}}` |
| Protein Intake | `{{inboundWebhookRequest.customFields.proteinIntakeText}}` |
| Energy Levels | `{{inboundWebhookRequest.customFields.energyLevelsText}}` |
| Biggest Challenge | `{{inboundWebhookRequest.customFields.biggestChallengeText}}` |
| Investment Readiness | `{{inboundWebhookRequest.customFields.investmentReadinessText}}` |
| Current Support | `{{inboundWebhookRequest.customFields.currentSupportText}}` |
| Risk Score | `{{inboundWebhookRequest.riskScore}}` |
| Lead Quality | `{{inboundWebhookRequest.leadQuality}}` |
| Quiz Completed Date | `{{inboundWebhookRequest.quizCompletedDate}}` |

### Step 8 — Add a contact note (optional but useful)

Add an **Add Note** action with body: `{{inboundWebhookRequest.notes}}` — gives the sales team a one-glance summary of the quiz results.

### Step 9 — Publish

Toggle **Publish** to ON. Test by submitting the quiz once and confirming the contact appears in GHL with all tags + custom fields populated.

---

## Workflow 2: Email Sequence

Triggered by the `Quiz Completed` tag that Workflow 1 applies.

### Step 1 — Create the workflow

1. **+ Create Workflow** → **Start from Scratch**
2. Name: `Fat Loss Readiness Quiz - Email Sequence`

### Step 2 — Set the trigger

1. **Add New Trigger** → **Tag Added**
2. Tag: `Quiz Completed`
3. **Save**

### Step 3 — Email 1 (immediate)

1. **+** → **Send Email**
2. Subject: `Your fat loss readiness results are in, {{contact.first_name}}`
3. Body: paste Email 1 content above, or upload `email-1-thank-you.html`

### Step 4 — Wait + Email 2

1. **+** → **Wait** → **7 days**
2. **+** → **Send Email** → use Email 2 / `email-2-protein.html`

### Step 5 — Repeat for Emails 3, 4, 5

Pattern: **Wait 7 days → Send Email**. Files in order: `email-3-strength-training.html`, `email-4-weight-loss-face.html`, `email-5-final-cta.html`.

### Step 6 — Publish

Verify the structure (Trigger → Email 1 → Wait → Email 2 → Wait → Email 3 → Wait → Email 4 → Wait → Email 5), **Save**, toggle **Publish** ON.

---

## Optional enhancements

- **If/Else** on the `Risk: HIGH/MODERATE/LOW` tag to personalise email copy
- **Stop on booking** — if a contact books a call, remove them from the email sequence
- **SMS** follow-ups for `Lead Quality: HOT` contacts

---

# Compliance Notes

- All five emails strip named medications (GLP-1, Ozempic, etc.) and substitute terms ("weight loss injections", "script and go")
- "Ozempic face" reframed as the generic "weight loss face"
- Footer on every email carries the required disclaimer: "Educational content only. Not medical advice. Speak to a qualified doctor for personalised guidance."
- CTA stays consultation-general ("Book a free 20-minute call"), never treatment-specific
- Pre-publish review by a medical practitioner or compliance-trained team member is still required per PeakSpan SOP
