# Panwar Knitwear website

Static site. No build step — every page is plain HTML and loads `support.js` from the same folder.

## Pages

| File | Page |
| --- | --- |
| `index.html` | Home |
| `zonixa.html` | ZONIXA top wear |
| `msp-sports.html` | MSP Sports bottom wear |
| `product.html` | Product detail |
| `about.html` | About us |
| `contact.html` | Contact / bulk enquiry |

## Deploy to GitHub + Vercel

1. **Create the repo** — on github.com, New repository, name it `panwar-knitwear`, keep it empty (no README).
2. **Push this folder** from your machine:
   ```bash
   cd site
   git init
   git add .
   git commit -m "Panwar Knitwear website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/panwar-knitwear.git
   git push -u origin main
   ```
3. **Deploy on Vercel** — go to vercel.com, Add New → Project, import the repo.
   - Framework Preset: **Other**
   - Build Command: leave empty
   - Output Directory: leave empty (root)
   - Click Deploy.
4. **Custom domain** — Vercel project → Settings → Domains → add `panwarknitwear.com`, then point the domain's DNS at Vercel (A record `76.76.21.21`, or the CNAME Vercel shows you) in your registrar's panel.

`cleanUrls` is on, so pages are served at `/zonixa`, `/about`, `/contact` without the `.html`.

## Before going live

This is the improvement plan from Session 2, reviewed and revised in Session 3.

### Done

- **Add a WhatsApp contact route** — done in Session 3.

  *The problem:* the site had no WhatsApp link and no email address on any of the 6 pages.
  A buyer ready to order could only hand-copy a phone number, or use a contact form that
  silently sends nothing. That is real lost business, because the site sells bulk knitwear to
  wholesalers across India, where WhatsApp is the default trade channel.

  *What changed:* a floating "Chat on WhatsApp" button now sits bottom-right on all 6 pages
  (`.pk-wa` in each page's `<helmet><style>` block, with the markup just before the closing
  `</div></x-dc>`). It opens `wa.me/919876045457` with a pre-filled enquiry message that is
  tailored per page — ZONIXA top wear on the ZONIXA and product pages, MSP Sports bottom wear
  on the MSP page, and a general bulk-pricing enquiry elsewhere. It collapses to icon-only
  under 560px so it does not cover content on phones.

  *Why this one:* it is purely additive, so it could not break the existing layout, and it is
  visible on both desktop and mobile.

### Still open

- The contact form shows a thank-you message but does not send anything yet — connect it to a
  form service (Formspree, Web3Forms) or a Vercel serverless function. **This is now the most
  important remaining item:** the WhatsApp button gives buyers a working contact route, but
  anyone who still uses the form is silently ignored.
- Replace the MSP Sports placeholder product images and the "Product 1–5" names with real
  photos and names.
- Add a real email address (the site lists phone numbers and WhatsApp, but still no email).
- Give the mobile header a hamburger menu. At 375px the 5 nav links plus the "Send enquiry"
  pill wrap onto three rows and eat roughly 190px before any content starts.
