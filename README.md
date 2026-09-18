# QY Pumps — Export Website

Single-file static website (English, B2B) for the pump export business.
Serves on `qypumps.com` after deployment.

## Content

- **5 views** (hash-routed single page): Home / Products / Product Detail / About / Contact
- **53 product series**: 22 centrifugal + 31 submersible
- **126 product photos** served from CDN (https://aka.doubaocdn.com/s/...)
- Inquiry form is **front-end simulation only** — no backend. Replace with a real
  form service (Formspree, Getform, etc.) or an email endpoint before going live.

## Brand & contact info (already configured)

| Item | Value |
| --- | --- |
| Brand name | QY PUMPS |
| Company | YIWU QY PUMPS CO., LTD. |
| Email | anthonya@qypumps.com |
| Phone / WhatsApp | +86 13456875813 |
| Address | No. 88 Industrial Avenue, Pump Manufacturing Zone, Yiwu, Zhejiang 322000, China |

> Note: the street address is still a placeholder — replace it with the real
> factory address if different. All brand/contact strings live in the `SITE`
> object at the bottom of `index.html` (search for `QY PUMPS`).

## Deploy

### Vercel (recommended, free)
1. Push this folder to a GitHub repo (or use `vercel deploy` CLI from this dir).
2. Import the repo in Vercel → framework preset: **Other** → it's plain static.
3. After first deploy you get a `*.vercel.app` URL.
4. **Bind your domain**: Project → Settings → Domains → add `qypumps.com`.
   Vercel asks to verify ownership → creates the CNAME record for you (target
   usually `cname.vercel-dns.com`), or gives you the DNS records to add manually.
5. In Aliyun DNS console, add the records Vercel shows:
   - `CNAME  @ -> cname.vercel-dns.com` (or A record to Vercel IP)
   - `CNAME  www -> cname.vercel-dns.com`
   Wait a few minutes for propagation; HTTPS is automatic.

### Netlify (alternative)
- `netlify.toml` included. Drag-and-drop the folder at app.netlify.com, or
  `netlify deploy --prod` from this dir. Domains: Site settings → Domain management.

### Aliyun OSS static hosting (alternative)
- Bucket → 静态页面 → 默认首页 `index.html`; bind the domain via CDN; HTTPS needs a certificate.

## Notes

- All images referenced via CDN URL (permanent doubaocdn links). If you ever want
  fully self-hosted assets, download them into `assets/` and update the `imgs`
  entries in `index.html` accordingly.
- Model tables per series are based on typical industry naming conventions and
  should be checked against your actual catalog before going live.
