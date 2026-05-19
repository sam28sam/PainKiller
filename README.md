# PainKiller Consulting — Website Repository

## Files in this repo

| File | Purpose |
|---|---|
| `index.html` | Homepage |
| `audit.html` | On-Site Audit conversion page |
| `services.html` | Full service stack + pricing (TODO) |
| `about.html` | Founder story (TODO) |
| `results.html` | Case studies (TODO) |
| `tools.html` | Operational toolkit + downloads (TODO) |
| `book.html` | Booking / contact page (TODO) |
| `docksync.html` | DockSync bridge page (TODO) |
| `privacy.html` | Privacy policy (TODO) |
| `terms.html` | Terms & conditions (TODO) |
| `CNAME` | Custom domain config — do not delete |

---

## GitHub Pages Setup (one-time)

1. Create a GitHub account at github.com if you don't have one
2. Create a new **public** repository named `painkillerconsulting`
3. Upload all files in this folder to the repo (drag and drop in the GitHub UI, or use Git)
4. Go to **Settings → Pages**
5. Under "Source" select **Deploy from a branch** → `main` branch → `/ (root)`
6. Under "Custom domain" enter: `painkillerconsulting.co.uk`
7. Tick "Enforce HTTPS"
8. Save

GitHub will confirm the site is live at `https://painkillerconsulting.co.uk` once DNS is pointed correctly (see below).

---

## DNS Configuration (point domain to GitHub Pages)

Log in to your domain registrar (123-reg, GoDaddy, Namecheap, etc.) and make these changes:

### Delete existing Wix DNS records
Remove all A records and CNAME records currently pointing to Wix.

### Add these A records (GitHub Pages IPs)
```
Type: A    Name: @    Value: 185.199.108.153
Type: A    Name: @    Value: 185.199.109.153
Type: A    Name: @    Value: 185.199.110.153
Type: A    Name: @    Value: 185.199.111.153
```

### Add this CNAME record
```
Type: CNAME    Name: www    Value: [your-github-username].github.io
```
Replace `[your-github-username]` with your actual GitHub username.

### DNS propagation
Allow up to 48 hours. You can check progress at https://dnschecker.org

**Important: Keep the Wix site live until you confirm the GitHub site is loading on the custom domain.**

---

## Stripe Integration

### Step 1: Create a Stripe account
Go to https://stripe.com and sign up. No monthly fee — you pay 1.4% + 20p per successful UK card transaction.

### Step 2: Create Payment Links
In your Stripe Dashboard → **Payment Links → Create new**

Create these links:

| Product | Price | Notes |
|---|---|---|
| Operations Toolkit | £49 | One-time, instant |
| Rapid-Resolve | £297 | One-time, includes intake form link in confirmation email |
| Audit Deposit — Standard | £475 | 50% of £950 |
| Audit Deposit — Extended | £625 | 50% of £1,250 |
| Operational Health Retainer | £650/month | Recurring subscription |

### Step 3: Replace placeholder links in HTML
Search for `https://buy.stripe.com/YOUR_` in `index.html` and `audit.html` and replace with your actual Stripe payment link URLs.

### Step 4: Set up confirmation emails
In Stripe Dashboard → Settings → Email → enable "Successful payment" emails. Customise with:
- Your logo
- A message like: "Thanks for booking. I'll be in touch within 24 hours to arrange next steps. In the meantime, [Calendly link] is available if you'd like to schedule straight away."

---

## Calendly Setup

1. Go to https://calendly.com and sign up (free tier is fine)
2. Create one event type: **"20-Minute Diagnostic Call"**
   - Duration: 20 minutes
   - Location: Google Meet or Zoom (whichever you use)
   - Add a description: "A short, no-commitment call to discuss your operation and whether PainKiller is the right fit."
3. Copy the Calendly link and replace `book.html` CTAs with it, or embed using the Calendly embed script
4. Set your availability to exclude times that conflict with your day job

---

## Zapier Automation (optional, set up when ready)

When a Stripe payment is confirmed → send a customised follow-up email with the Calendly booking link.

1. Sign up at https://zapier.com (free tier: 100 tasks/month)
2. Create a Zap: **Trigger: Stripe → New Payment** → **Action: Gmail → Send Email**
3. Email template for Rapid-Resolve:
   > "Hi [customer name], thanks for booking a Rapid-Resolve session. To schedule your call, please use this link: [Calendly link]. I'll also send a short intake form (5 questions) before the session so we don't waste time on basics. Looking forward to it. — Sam"

---

## Email List (for toolkit buyers)

1. Sign up at https://www.brevo.com (free up to 300 emails/day)
2. Create a list called "Toolkit Buyers"
3. Add a Zapier step: **Stripe payment for Toolkit → Add contact to Brevo list**
4. Set up a 3-email welcome sequence:
   - Email 1 (immediate): Toolkit download link + "here's how to get the most out of it"
   - Email 2 (Day 5): "The most common thing I find in audits that these templates help surface..."
   - Email 3 (Day 12): Offer for a discounted Rapid-Resolve session at £247 (£50 off for toolkit buyers)

---

## Pages still to build

Copy and adapt the HTML structure from `index.html` for each remaining page. The design tokens (fonts, colours, spacing) are all defined in the `<style>` block at the top of each file — keep them consistent.

Pages remaining:
- `services.html` — full product stack with all four tiers + retainer
- `about.html` — Sam's story, credentials, and the founder quote section
- `results.html` — three case studies expanded with sector/size context
- `tools.html` — toolkit product card + free lead magnet download
- `book.html` — Calendly embed + direct Stripe links + email/phone
- `docksync.html` — brief bridge page to DockSync

---

## Wix cancellation

Cancel Wix **only after** confirming:
- [ ] GitHub site is live on `painkillerconsulting.co.uk`
- [ ] HTTPS is working
- [ ] All Stripe payment links are tested
- [ ] Calendly is embedded on `book.html`
- [ ] All nav links work correctly

Check your Wix renewal date to avoid an unwanted auto-renewal charge.
