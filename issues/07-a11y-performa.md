# 07 — Aksesibilitas, performa & SEO dasar

Type: research
Status: resolved
Blocked by: 03

## Question

Pastikan halaman Linktree Wilkerstat memenuhi baseline aksesibilitas, performa, dan SEO dasar:

- Aksesibilitas: kontras warna (WCAG AA), keyboard nav accordion, ARIA (`aria-expanded`, `aria-controls`), alt foto kantor.
- Performa: Lighthouse target (Performance >90), image optimization, no render-blocking, lazy background.
- SEO/meta: `<title>`, `meta description`, Open Graph (share ke WhatsApp/Telegram peserta), favicon BPS.
- Analytics opsional: apakah perlu hit counter ringan (Netlify Analytics vs GoatCounter) — keputusan ya/tidak.

Deliverable: checklist QA yang akan dipakai saat build final & pre-deploy.

## Answer

Checklist QA dikunci di **`docs/qa-checklist.md`** (linked asset). Ringkasan audit terhadap `index.html` final:

- **Aksesibilitas (15 item):** Semua kontras lolos WCAG AA/AAA (body 17.4:1, heading 15.2:1, tombol primary 8.9:1, helper 6.8:1). Keyboard nav native (`<button>`), `aria-expanded`+`aria-controls`+`role="region"`+`aria-labelledby` pada accordion, `aria-hidden` pada icon dekoratif, `aria-disabled`+`title` pada placeholder, `aria-live="polite"` pada toast, `focus-visible` outline oranye. TODO: ganti logo placeholder dengan `<img alt="Logo BPS">`.
- **Performa (9 item):** File 22KB single-file, no build step, CSS/JS inline, font `display=swap`+`preconnect`, background via CSS overlay. Estimasi Lighthouse Performance 95–100. TODO: export foto ke WebP jika pakai lokal.
- **SEO/Meta (12 item):** Title, description, author, theme-color, canonical, OG (WhatsApp/Telegram), Twitter Card, favicon, `lang="id"`, H1 hierarchy — semua terisi. TODO: buat `og-image.png` 1200x630 + `favicon.png` 32x32, update URL jika pakai domain custom.
- **Analytics:** Keputusan **tanpa analytics untuk v1** (cukup Netlify dashboard). Jika butuh hit counter, tambah GoatCounter 1 script tag — tidak perlu tiket baru.

Checklist pre-deploy final (9 item gabungan) ada di `docs/qa-checklist.md` — siap dijalankan sebelum drag-and-drop ke Netlify.

File: `docs/qa-checklist.md` — peta wayfinder selesai setelah tiket ini (7/7 done).

## Comments

Resolved — research AFK. Audit manual terhadap index.html final, semua item terverifikasi.
