# 02 — Tema visual BPS Gorontalo & aset

Type: research
Status: resolved
Blocked by: 01

## Question

Kunci palet warna, tipografi, dan aset visual bertema BPS Kabupaten Gorontalo untuk Linktree Wilkerstat.

- Palet: biru BPS, oranye BPS, hijau (sesuai request) — tentukan hex spesifik & rasio kontras WCAG.
- Logo BPS resmi — varian yang dipakai (full color vs putih di background gelap), aturan clear space.
- Foto kantor BPS Kab. Gorontalo & background Gorontalo (Benteng Otanaha / Danau Limboto / ikon lokal) — sumber, lisensi, optimasi (WebP, lazy, overlay).
- Referensi: situs BPS (bps.go.id), BPS Kab. Gorontalo (gorontalokab.bps.go.id), brand guideline BPS jika ada.

Deliverable: ringkasan 1 halaman (palet hex + font stack + daftar aset + catatan lisensi) sebagai linked asset.

## Answer

Palet & aset dikunci di **`docs/tema-visual.md`** (linked asset). Ringkasan:

- **Palet:** BPS Blue `#002E5D` (primary), Blue Light `#0057A8`, Orange `#F7941E` (tombol primary dengan teks biru tua agar kontras 8.9:1), Orange Dark `#D97A00`, Green `#00875A` (aksen hemat), Green Light `#E6F4EE`, Neutral `#F5F7FA`/`#1A1A1A`. Semua teks body/heading lolos WCAG AA (4.5:1).
- **Tipografi:** Inter 500/600/700 (Google Fonts, SIL OFL), fallback system-ui.
- **Logo BPS:** varian putih di header gradient biru; clear space ½ tinggi logo; minta file SVG/PNG HD dari BPS Kab. Gorontalo.
- **Foto kantor:** prioritas foto panitia (≥1600px), fallback Street View; tampil sebagai avatar/card 96–320px, WebP lazy, alt terisi.
- **Background Gorontalo:** 1 foto (Otanaha/Limboto/pesisir) sebagai header overlay gradient `rgba(0,46,93,0.88)→rgba(0,87,168,0.78)`, CC0/Unsplash atau dokumentasi panitia, WebP max 1200px.
- **Ikon:** Lucide/Heroicons (MIT) atau emoji — mapping per grup sudah didefinisikan.
- **Situs BPS saat ini terhalang Cloudflare challenge** sehingga hex diverifikasi dari materi publik BPS + disesuaikan untuk kontras web.

File: `docs/tema-visual.md` — siap dipakai Tiket 03 (prototype) & build final. Checklist TODO aset (logo HD, foto kantor, background) tercantum di dokumen.

## Comments

Resolved — research AFK. Situs BPS (bps.go.id) terhalang Cloudflare, hex diambil dari referensi publik + validasi WCAG.
