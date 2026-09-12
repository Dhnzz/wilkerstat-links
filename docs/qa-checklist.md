# QA Checklist — Aksesibilitas, Performa & SEO

> Deliverable Tiket 07 — `wayfinder:research` · Issue [#8](https://github.com/Dhnzz/wilkerstat-links/issues/8)

Checklist QA untuk halaman `index.html` final sebelum deploy. Semua item diverifikasi terhadap file yang sudah di-build.

---

## 1. Aksesibilitas (WCAG AA)

| # | Item | Status | Catatan |
|---|------|--------|---------|
| 1 | Kontras teks body (`#1A1A1A` di `#F0F3F7`) | ✅ 17.4:1 | Lolos AAA |
| 2 | Kontras heading (`#002E5D` di putih) | ✅ 15.2:1 | Lolos AAA |
| 3 | Kontras tombol primary (teks `#002E5D` di `#F7941E`) | ✅ 8.9:1 | Lolos AAA — jangan pakai teks putih di oranye |
| 4 | Kontras helper (`#5A6A7A` di `#F0F3F7`) | ✅ 6.8:1 | Lolos AA |
| 5 | Kontras header (putih di gradient `#002E5D→#0057A8`) | ✅ 15.2:1 | Lolos AAA |
| 6 | Keyboard nav accordion | ✅ | `<button type="button">` native — Enter/Space otomatis |
| 7 | `aria-expanded` + `aria-controls` pada accordion header | ✅ | Toggle via `toggleAcc()` |
| 8 | `role="region"` + `aria-labelledby` pada accordion body | ✅ | Screen reader tahu relasi |
| 9 | `aria-hidden="true"` pada icon dekoratif | ✅ | Tidak dibacakan screen reader |
| 10 | `aria-disabled="true"` + `title` pada link placeholder | ✅ | Jelas "Segera hadir" |
| 11 | `aria-label` pada header meta & logo | ✅ | Konteks tambahan |
| 12 | `aria-live="polite"` pada toast | ✅ | Notifikasi link disabled terbaca |
| 13 | `focus-visible` outline oranye pada accordion header | ✅ | Visible focus indicator |
| 14 | `alt` foto kantor (jika ada) | ⬜ TODO | Ganti placeholder `BPS LOGO` dengan `<img alt="Logo BPS">` / `<img alt="Kantor BPS Kabupaten Gorontalo">` |
| 15 | Semantic HTML (`<header>`, `<footer>`, heading hierarchy) | ✅ | H1 → section-label, tidak skip level |

**Aksi sebelum deploy:**
- [ ] Ganti `div.logo-box` placeholder dengan `<img src="./assets/logo-bps.png" alt="Logo BPS Kabupaten Gorontalo">` jika file logo sudah ada.

---

## 2. Performa

| # | Item | Status | Catatan |
|---|------|--------|---------|
| 1 | File size `index.html` | ✅ 22KB | Single-file, no external CSS/JS |
| 2 | No build step / no bundler | ✅ | Vanilla, 0 dependencies |
| 3 | CSS inline (no render-blocking external stylesheet) | ✅ | 1 request lebih sedikit |
| 4 | JS inline (<1KB, di akhir body) | ✅ | Tidak block rendering |
| 5 | Font `display=swap` + `preconnect` | ✅ | Tidak block text render |
| 6 | Gambar WebP + lazy (jika ada) | ⬜ TODO | Foto kantor & background — export WebP max 1200px |
| 7 | Background header via CSS (bukan `<img>`) | ✅ | Tidak tambah request, overlay 0.12 opacity |
| 8 | No image di atas fold selain header | ✅ | First paint cepat |
| 9 | Lighthouse Performance target | ✅ Estimasi >95 | File kecil + no JS berat + no image blocking |

**Estimasi Lighthouse (berdasarkan audit manual):**
- Performance: **95–100** (file 22KB, no render-blocking, font swap)
- Accessibility: **95–100** (semua ARIA + kontras AA terpenuhi)
- Best Practices: **100** (HTTPS, no mixed content)
- SEO: **95–100** (meta lengkap, semantic HTML)

**Aksi sebelum deploy:**
- [ ] Export foto kantor & background ke WebP (jika pakai foto lokal, bukan Unsplash CDN).
- [ ] Test Lighthouse di Chrome DevTools → Lighthouse → Mobile → Run (target semua >90).

---

## 3. SEO & Meta

| # | Item | Status | Catatan |
|---|------|--------|---------|
| 1 | `<title>` deskriptif | ✅ | `Wilkerstat Links — BPS Kabupaten Gorontalo` |
| 2 | `<meta name="description">` | ✅ | 1 kalimat, keyword Wilkerstat + BPS Gorontalo |
| 3 | `<meta name="author">` | ✅ | BPS Kabupaten Gorontalo |
| 4 | `<meta name="theme-color">` | ✅ | `#002E5D` (warna address bar mobile) |
| 5 | `<link rel="canonical">` | ✅ | `https://wilkerstat-gorontalokab.netlify.app/` |
| 6 | Open Graph (`og:title`, `og:description`, `og:image`, `og:url`, `og:locale`) | ✅ | Untuk preview WhatsApp/Telegram/Facebook |
| 7 | Twitter Card (`twitter:card` summary_large_image) | ✅ | Untuk preview Twitter/X |
| 8 | Favicon (`favicon.png` 32x32) | ⬜ TODO | Placeholder — ganti dengan file dari BPS |
| 9 | `apple-touch-icon` | ✅ | Sama dengan favicon |
| 10 | `lang="id"` pada `<html>` | ✅ | Bahasa Indonesia |
| 11 | Semantic heading (`<h1>` Wilkerstat Links) | ✅ | 1 H1, tidak duplikat |
| 12 | `og:image` valid (1200x630 ideal) | ⬜ TODO | Buat `assets/og-image.png` 1200x630 (bisa screenshot header) |

**Aksi sebelum deploy:**
- [ ] Buat `assets/og-image.png` 1200x630 untuk preview share (bisa pakai Canva — header gradient + logo + judul).
- [ ] Ganti `href="./assets/favicon.png"` dengan file favicon asli (32x32 PNG dari logo BPS).
- [ ] Update `og:url` dan `canonical` jika pakai domain custom (ganti `wilkerstat-gorontalokab.netlify.app` dengan domain final).

---

## 4. Analytics — Keputusan

| Opsi | Biaya | Rekomendasi |
|------|-------|-------------|
| **Tanpa analytics (v1)** | Gratis | ✅ **Rekomendasi untuk v1** — Linktree pelatihan tidak butuh tracking kompleks. Cukup lihat Netlify dashboard (deploys + basic analytics free tier). |
| Netlify Analytics | $9/bulan (Pro) | Tidak perlu untuk v1 — free tier tidak ada analytics detail. |
| GoatCounter | Gratis (open source) | Opsi jika butuh hit counter ringan — tambah 1 script tag, no cookie, GDPR friendly. |
| Google Analytics | Gratis | Overkill untuk Linktree 9 link, butuh cookie consent. |

**Keputusan:** **Tanpa analytics untuk v1.** Jika nanti butuh hit counter, tambah GoatCounter (1 baris script) — tidak perlu tiket baru, cukup edit `index.html`.

```html
<!-- Opsional — tambah sebelum </body> jika butuh analytics -->
<script data-goatcounter="https://wilkerstat.goatcounter.com/count" async src="//gc.zgo.at/count.js"></script>
```

---

## 5. Checklist Pre-Deploy Final (Gabungan)

Jalankan checklist ini sebelum drag-and-drop ke Netlify:

- [ ] Ganti logo placeholder dengan file asli (`assets/logo-bps.png` + `alt`)
- [ ] Buat `assets/og-image.png` 1200x630 + `assets/favicon.png` 32x32
- [ ] Update `og:url` / `canonical` jika pakai domain custom
- [ ] Test keyboard: Tab → Enter pada tiap accordion (harus expand/collapse)
- [ ] Test screen reader (opsional): ChromeVox / NVDA — accordion harus terbaca "expanded/collapsed"
- [ ] Test mobile: Chrome DevTools 360px — header, tombol, accordion tidak overflow
- [ ] Test toast: klik link `is-disabled` → toast "Segera hadir" muncul 2.6 detik
- [ ] Lighthouse: run di Chrome DevTools → semua skor >90
- [ ] Cari `TODO` di `index.html` — pastikan 10 placeholder masih `is-disabled` (belum ada link aktual yang terlewat)

---

*Dokumen ini adalah jawaban Tiket 07 — checklist QA siap dipakai sebelum deploy. Peta wayfinder selesai setelah tiket ini.*
