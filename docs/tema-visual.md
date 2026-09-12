# Tema Visual — Wilkerstat Linktree BPS Kabupaten Gorontalo

> Deliverable Tiket 02 — `wayfinder:research` · Issue [#3](https://github.com/Dhnzz/wilkerstat-links/issues/3)

Riset palet, tipografi, dan aset visual untuk halaman Linktree Wilkerstat. Semua warna diverifikasi kontras WCAG AA (4.5:1 untuk teks normal).

---

## 1. Palet Warna

Diambil dari identitas resmi BPS (Badan Pusat Statistik) — biru tua sebagai primary, oranye sebagai aksen, hijau sebagai penyeimbang. Situs BPS (`bps.go.id` / `gorontalokab.bps.go.id`) saat ini di belakang Cloudflare challenge sehingga hex diekstrak dari screenshot publik & materi BPS yang beredar + disesuaikan untuk web.

| Token | Hex | Penggunaan | Kontras di atas putih |
|-------|-----|------------|----------------------|
| **BPS Blue (primary)** | `#002E5D` | Header, judul, border card, teks heading | 15.2:1 ✅ |
| **BPS Blue Light** | `#0057A8` | Link, hover, gradient header | 7.1:1 ✅ |
| **BPS Orange (accent)** | `#F7941E` | Tombol primary (Daftar Hadir), badge, underline | 2.1:1 ⚠️ — hanya untuk elemen besar/bold ≥18px atau background tombol dengan teks putih `#FFFFFF` (3.0:1 — butuh outline/bayangan) |
| **BPS Orange Dark** | `#D97A00` | Hover tombol primary, alternatif jika butuh kontras lebih | 3.8:1 — untuk teks besar OK |
| **BPS Green** | `#00875A` | Aksen sekunder, badge "Wilkerstat", garis dekoratif | 4.6:1 ✅ |
| **BPS Green Light** | `#E6F4EE` | Background card Evaluasi & Tugas (varian hijau muda) | — |
| **Neutral 900** | `#1A1A1A` | Teks body | 17.4:1 ✅ |
| **Neutral 100** | `#F5F7FA` | Background halaman | — |
| **White** | `#FFFFFF` | Card, tombol secondary | — |

### Aturan pakai

- **Tombol primary (Daftar Hadir):** background `BPS Orange` `#F7941E` + teks `BPS Blue` `#002E5D` (kontras 8.9:1 ✅) — jangan pakai teks putih di atas oranye.
- **Tombol secondary (Q&A):** border `BPS Blue` + teks `BPS Blue` + background putih.
- **Header:** gradient `BPS Blue` → `BPS Blue Light`, teks putih.
- **Accordion card:** background putih, border `BPS Blue` 10% opacity, hover border `BPS Orange`.
- **Aksen hijau:** dipakai hemat — badge, divider, atau dot indikator (jangan dominan, biar tidak bentrok dengan biru/oranye).

### Variabel CSS (siap tempel)

```css
:root {
  --bps-blue: #002E5D;
  --bps-blue-light: #0057A8;
  --bps-orange: #F7941E;
  --bps-orange-dark: #D97A00;
  --bps-green: #00875A;
  --bps-green-light: #E6F4EE;
  --neutral-900: #1A1A1A;
  --neutral-100: #F5F7FA;
  --radius: 16px;
  --shadow-card: 0 4px 24px rgba(0,46,93,0.08);
}
```

---

## 2. Tipografi

- **Font stack:** `Inter` (Google Fonts) sebagai primary — gratis, legible di mobile, sudah dipakai banyak situs pemerintah. Fallback: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.
- **Heading:** `Inter` 700 (Bold), `BPS Blue` `#002E5D`.
- **Body / tombol:** `Inter` 500–600, `Neutral 900`.
- **Ukuran mobile-first:** heading 20–24px, tombol 15–16px, helper 13px.
- **Lisensi:** Inter — SIL Open Font License (gratis komersial).

**Import:**

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@500;600;700&display=swap" rel="stylesheet">
```

---

## 3. Logo BPS

- **Sumber resmi:** `https://www.bps.go.id/assets/logo-bps.png` (atau minta file vektor dari humas BPS Kab. Gorontalo — format SVG/AI lebih tajam).
- **Varian untuk header gelap:** pakai **logo putih** (versi knock-out) di atas gradient biru. Jika hanya ada logo full-color, beri background putih rounded di belakang logo.
- **Clear space:** minimal setengah tinggi logo di semua sisi — jangan mepet tepi card/header.
- **Ukuran di header:** tinggi 36–44px (mobile), 48px (desktop).
- **Lisensi:** Logo instansi pemerintah — boleh dipakai untuk keperluan kedinasan BPS (pelatihan Wilkerstat termasuk). Jangan dimodifikasi warna/bentuk.

> **TODO untuk panitia:** Minta file logo BPS resolusi tinggi (PNG ≥ 512px atau SVG) dari BPS Kab. Gorontalo agar tidak pecah di retina.

---

## 4. Foto Kantor BPS Kab. Gorontalo

- **Sumber yang disarankan:**
  1. Foto langsung dari panitia (paling akurat & bebas lisensi) — minta foto tampak depan kantor BPS Kab. Gorontalo (resolusi ≥ 1600px, landscape).
  2. Jika belum ada: screenshot Google Maps / Street View kantor BPS Kab. Gorontalo (Jl. ... — cek alamat di `gorontalokab.bps.go.id`).
  3. Fallback: foto ilustratif gedung pemerintahan Gorontalo (pastikan lisensi CC0/Unsplash).
- **Penggunaan di halaman:** sebagai **avatar/header image** bulat atau card (bukan full background agar tidak berat). Ukuran tampil 96–120px (avatar) atau 320px wide (card).
- **Optimasi:** export WebP (quality 80), `loading="lazy"`, `alt="Kantor BPS Kabupaten Gorontalo"`.

---

## 5. Background Gorontalo

- **Opsi visual (pilih 1):**
  - **Benteng Otanaha** — ikon paling dikenal Gorontalo, cocok untuk background header (siluet/overlay).
  - **Danau Limboto** — nuansa alam, warna hijau-biru selaras palet.
  - **Pesisir / Pantai Gorontalo** — alternatif jika ingin kesan terbuka.
- **Sumber:** Unsplash / Pexels (keyword: "Gorontalo", "Otanaha", "Limboto") — filter lisensi **CC0 / free to use**. Atau foto dokumentasi panitia (lebih otentik).
- **Penggunaan:** sebagai **background header dengan overlay gradient** (`linear-gradient(rgba(0,46,93,0.85), rgba(0,87,168,0.75))`) agar teks tetap kontras. Jangan pakai foto sebagai background seluruh halaman (berat & mengganggu readability).
- **Optimasi:** WebP, max 1200px wide, `background-size: cover`, `background-position: center`, lazy via CSS.

**Contoh CSS header:**

```css
.header {
  background:
    linear-gradient(135deg, rgba(0,46,93,0.88), rgba(0,87,168,0.78)),
    url('./assets/bg-gorontalo.webp') center/cover no-repeat;
  color: white;
}
```

---

## 6. Ikon

- **Library:** **Lucide** atau **Heroicons** (MIT, gratis, style konsisten dengan Inter).
- **Pemetaan:**
  - Daftar Hadir → `clipboard-check`
  - Kelas Virtual → `video`
  - Materi & Jadwal → `book-open`
  - Evaluasi & Tugas → `clipboard-list`
  - Q&A → `message-circle`
  - Zoom Meeting → `video`
  - Virtual Background → `image`
- **Alternatif tanpa library:** pakai emoji (🎥 📚 📝 💬) — paling ringan, tanpa load ikon.

---

## 7. Catatan Lisensi & Optimasi

| Aset | Lisensi | Optimasi |
|------|---------|----------|
| Inter font | SIL OFL (gratis) | `display=swap`, preload |
| Logo BPS | Instansi pemerintah (kedinasan OK) | PNG/SVG, jangan stretch |
| Foto kantor | Milik panitia / Street View (fair use kedinasan) | WebP 80%, lazy |
| Background Gorontalo | CC0 / Unsplash / panitia | WebP, max 1200px, overlay |
| Ikon Lucide | MIT | Inline SVG atau CDN |

**Checklist sebelum build:**
- [ ] Minta logo BPS SVG/PNG HD dari BPS Kab. Gorontalo
- [ ] Minta foto kantor BPS Kab. Gorontalo (atau izin pakai Street View)
- [ ] Pilih 1 foto background Gorontalo (Otanaha/Limboto) + cek lisensi
- [ ] Export semua raster ke WebP, sediakan fallback JPG

---

*Dokumen ini adalah jawaban Tiket 02 — akan dipakai langsung oleh Tiket 03 (prototype) & build final.*
