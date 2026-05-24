# DataShield — Vercel Deployment

## What This Is
A standalone static site that captures name + email for the DataShield scan service. Submits to the webhook endpoint running on the work PC tunnel.

## Quick Deploy

### Option 1: Vercel CLI
```bash
npm i -g vercel
cd vercel-site
vercel --prod
```

### Option 2: Vercel Dashboard
1. Go to https://vercel.com/new
2. Import this folder (or push to GitHub and import from there)
3. Set environment variable:
   - `NEXT_PUBLIC_API_URL=https://datashieldnow.com/api/datashield/webhook/scan`

### Option 3: GitHub
1. Push this folder to a repo
2. Connect Vercel to the repo
3. Done

## How It Works
1. User enters name + email on the landing page
2. Vercel site POSTs to `https://datashieldnow.com/api/datashield/webhook/scan`
3. Work PC receives webhook, runs scan asynchronously
4. Results are emailed back via Brevo

## Custom Domain
- Point the domain at Vercel's nameservers or add a CNAME record
- Or keep it as a subfolder: `datashieldnow.com` → Vercel, `api.datashieldnow.com` → Cloudflare tunnel
