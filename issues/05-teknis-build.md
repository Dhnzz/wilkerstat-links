# 05 — Teknis build statis & edit link manual

Type: research
Status: resolved
Blocked by: 01, 03

## Question

Keputusan teknis build halaman statis agar link mudah diedit manual via file HTML (sesuai preferensi user: edit file HTML langsung):

- Struktur file: single `index.html` vs `index.html` + `config.js`/`links.json` untuk daftar link (tradeoff: kemudahan edit tanpa sentuh markup).
- Cara placeholder link: `href="#"` + class `is-disabled` vs `data-link` + JS, serta handling link kosong (disabled state, tooltip).
- Optimasi: minify, image WebP, font loading, no build step (agar drag-and-drop Netlify tetap simpel).
- Dokumentasi singkat cara update link (komentar di HTML + README).

Deliverable: rekomendasi struktur file + contoh snippet placeholder link yang akan dipakai build final.

## Answer

Keputusan dikunci di **`docs/teknis-build.md`** (linked asset). Ringkasan:

- **Struktur file:** Single `index.html` (CSS+JS inline, no build step) + folder `assets/` untuk gambar. Tidak pakai `links.json`/`config.js` — 9 link saja, edit HTML langsung paling simpel untuk panitia, drag-and-drop Netlify 1 file.
- **Placeholder:** `href="#"` + `class="is-disabled"` + `aria-disabled="true"` + `title="Segera hadir"` + `data-placeholder` + komentar `<!-- TODO: ganti href -->`. Saat link terisi: hapus disabled attrs, ganti href ke URL aktual, tambah `target="_blank" rel="noopener"`. JS handler cegah navigasi untuk link kosong.
- **Optimasi:** No build tool, CSS/JS inline (~18KB), font Inter `display=swap` + `preconnect`, gambar WebP max 1200px lazy, favicon dari logo BPS. Minify opsional (Netlify auto-minify atau manual).
- **Cara update link:** 6 langkah edit manual (cari TODO → ganti href → hapus disabled → tambah target blank → save → deploy) — sudah didokumentasikan di `docs/teknis-build.md` + akan ada komentar TODO di setiap placeholder di `index.html` final.

File: `docs/teknis-build.md` — siap dipakai untuk build `index.html` final & Tiket 06 (deploy).

## Comments

Resolved — research AFK. Struktur single-file terkonfirmasi dari prototype.html.
