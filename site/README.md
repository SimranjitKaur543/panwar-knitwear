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

- Replace the MSP Sports placeholder product images and the "Product 1–5" names with real photos and names.
- Add a real email address (the site currently lists phone numbers only).
- The contact form shows a thank-you message but does not send anything yet — connect it to a form service (Formspree, Web3Forms) or a Vercel serverless function.
