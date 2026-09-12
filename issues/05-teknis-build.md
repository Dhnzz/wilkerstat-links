# 05 — Teknis build statis & edit link manual

Type: research
Status: open
Blocked by: 01, 03

## Question

Keputusan teknis build halaman statis agar link mudah diedit manual via file HTML (sesuai preferensi user: edit file HTML langsung):

- Struktur file: single `index.html` vs `index.html` + `config.js`/`links.json` untuk daftar link (tradeoff: kemudahan edit tanpa sentuh markup).
- Cara placeholder link: `href="#"` + class `is-disabled` vs `data-link` + JS, serta handling link kosong (disabled state, tooltip).
- Optimasi: minify, image WebP, font loading, no build step (agar drag-and-drop Netlify tetap simpel).
- Dokumentasi singkat cara update link (komentar di HTML + README).

Deliverable: rekomendasi struktur file + contoh snippet placeholder link yang akan dipakai build final.

## Comments
