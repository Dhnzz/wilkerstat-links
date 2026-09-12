# 06 — Deploy Netlify + domain custom

Type: task
Status: resolved
Blocked by: 03, 05

## Question

Rencana deploy ke Netlify (gratis) dengan domain custom user (nama custom + suffix `.netlify.app` di belakang tidak masalah).

- Opsi deploy: drag-and-drop folder vs Git (GitHub/GitLab) + continuous deploy — rekomendasi untuk user yang edit manual HTML.
- Langkah domain custom di Netlify: add custom domain, DNS (Netlify DNS vs external CNAME), HTTPS auto (Let's Encrypt).
- Checklist pre-deploy: favicon, meta OG, 404 fallback, `_redirects` jika perlu.
- Estimasi biaya: Netlify free tier limit & custom domain (domain beli terpisah — Netlify tidak jual domain).

Deliverable: SOP langkah-demi-langkah deploy + setup domain custom (checklist yang bisa diikuti user tanpa dev).

## Answer

**SOP dikunci di `docs/panduan-deploy.md` + halaman `index.html` final sudah di-build.**

**Build final:**
- `index.html` (22KB, single-file vanilla, no build step) — sudah jadi, siap deploy. Copy dari `prototype.html` + polish: meta OG/WhatsApp, favicon placeholder, 9 placeholder link dengan `TODO` comment + `is-disabled` + toast "Segera hadir", copy final Tiket 04, palet Tiket 02, struktur Tiket 03.
- 10 `TODO` comments, 9 link placeholder (semua `is-disabled`), siap diisi panitia via edit manual HTML.

**Deploy — rekomendasi:**
- **Opsi A (Drag & Drop) ⭐ utama:** Edit `index.html` lokal → drag folder ke https://app.netlify.com → live di `https://wilkerstat-gorontalokab.netlify.app` (bisa rename site). Update link tinggal edit + drag lagi — tanpa Git/CLI.
- **Opsi B (Git):** Hubungkan repo `Dhnzz/wilkerstat-links` → auto-deploy tiap `git push` (build command kosong, publish dir `.`).

**Domain custom:**
- Beli domain terpisah (~Rp 100–300rb/tahun, `.my.id` termurah) — Netlify tidak jual domain.
- Tambah di Netlify: Domain settings → Add custom domain → pilih Netlify DNS (ganti nameserver) atau External DNS (CNAME `wilkerstat` → `*.netlify.app`).
- HTTPS Let's Encrypt otomatis setelah DNS verifikasi.

**Checklist pre-deploy & biaya:** ada di `docs/panduan-deploy.md` — Free tier Netlify 100GB/bulan cukup untuk ~4 juta pageview Linktree.

File: `index.html` (siap deploy) + `docs/panduan-deploy.md` (SOP).

## Comments

Resolved — task HITL. Build final + SOP deploy selesai. Halaman siap live via drag-and-drop.
