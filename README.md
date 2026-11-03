# Aliplus Web

Premium redesign of the France Aliplus animal nutrition experience — modern editorial UI, same business structure (concept, products, calculator, FAQ, contact).

## Stack

- Next.js 16 (App Router)
- React 19
- Tailwind CSS 4

## Development

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Build

```bash
npm run build
npm start
```

## Notes

- The calculator is a front-end demo.
- The contact form posts to `/api/contact`, which sends email over SMTP. Configure `SMTP_USER` and `SMTP_PASS` as server-side environment variables available to Netlify Functions. For Gmail, use an App Password with two-step verification enabled.
- Optional email settings: `SMTP_HOST` (defaults to Gmail), `SMTP_PORT` (defaults to 465), `CONTACT_TO` (defaults to the requested test inbox, `valonsh101@gmail.com`), and `CONTACT_FROM` (defaults to the SMTP login). Redeploy after changing environment settings.
- The form confirms success only when SMTP accepts the message; failures preserve the enquiry for retry.
- Photography via Unsplash (configured in `next.config.ts`).

## Gmail delivery setup

In Netlify, open Project configuration → Environment variables. Edit `SMTP_PASS` and paste the Google App Password into its **Value** field. Save it with Functions scope and availability in production (and Deploy Previews if testing previews). Do not use your regular Google password or put credentials in source code.

Generate the App Password at https://myaccount.google.com/apppasswords while signed into the account used for `SMTP_USER`. Google requires two-step verification first. The sender account and recipient can be different; changing only the recipient does not require a new App Password.

The default test recipient is `valonsh101@gmail.com`. An existing `CONTACT_TO` setting overrides that default. For the real inbox, set `CONTACT_TO` to `alipluskosova.shpk@gmail.com`. Redeploy after saving environment changes, then submit the website contact form and check the recipient inbox and spam folder.
