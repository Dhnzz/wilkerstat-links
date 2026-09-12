# Teknis Build — Wilkerstat Links

> Deliverable Tiket 05 — `wayfinder:research` · Issue [#6](https://github.com/Dhnzz/wilkerstat-links/issues/6)

Keputusan teknis untuk build final halaman Linktree Wilkerstat agar link mudah diedit manual via file HTML.

---

## 1. Struktur File Final

```
wilkerstat-links/
├── index.html          # halaman utama (single-file, siap deploy)
├── prototype.html      # prototype Tiket 03 (arsip, tidak di-deploy)
├── assets/
│   ├── logo-bps.png    # logo BPS (PNG/SVG, minta dari BPS Kab. Gorontalo)
│   ├── kantor.webp     # foto kantor BPS Kab. Gorontalo
│   └── bg-gorontalo.webp # background Gorontalo (Otanaha/Limboto)
├── docs/
│   └── tema-visual.md  # palet & aset (arsip)
├── map.md              # wayfinder map
├── issues/             # tiket wayfinder (arsip)
└── README.md           # cara update link + deploy
```

**Keputusan:** Single `index.html` — **tidak pakai `links.json` / `config.js` terpisah.**

**Alasan:**
- User preferensi: edit file HTML langsung (paling simpel, tidak perlu paham JSON/JS).
- 9 link saja — overhead file terpisah tidak sepadan.
- Drag-and-drop Netlify paling simpel jika hanya 1 file HTML + folder `assets/`.
- Jika nanti link bertambah banyak (>20), baru pertimbangkan `links.json` + JS render — untuk v1 tidak perlu.

---

## 2. Placeholder Link — Cara Edit

### Pola placeholder

Setiap link yang belum ada URL-nya ditulis sebagai:

```html
<!-- TODO: ganti href="#" dengan URL aktual -->
<a class="sub-link is-disabled" href="#" data-placeholder="Zoom Meeting" aria-disabled="true" title="Segera hadir — link akan aktif H-1 pelatihan">
  <span class="sub-link-icon">🎥</span>
  <span class="sub-link-text"><strong>Zoom Meeting</strong><small>Link ruang kelas virtual</small></span>
  <span class="sub-link-arrow">›</span>
</a>
```

- `href="#"` — placeholder standar.
- `class="is-disabled"` — untuk styling (opacity 0.55, cursor not-allowed) + JS cegah navigasi.
- `aria-disabled="true"` — aksesibilitas.
- `title` — tooltip "Segera hadir".
- `data-placeholder` — untuk JS deteksi link kosong.

Saat link sudah ada, ganti menjadi:

```html
<a class="sub-link" href="https://zoom.us/j/xxxx" target="_blank" rel="noopener">
  <span class="sub-link-icon">🎥</span>
  <span class="sub-link-text"><strong>Zoom Meeting</strong><small>Link ruang kelas virtual</small></span>
  <span class="sub-link-arrow">›</span>
</a>
```

- Hapus `is-disabled`, `aria-disabled`, `title`, `data-placeholder`.
- Tambah `target="_blank" rel="noopener"` agar buka tab baru (eksternal link).

### Standalone juga sama

```html
<!-- Daftar Hadir — placeholder -->
<a class="standalone-primary is-disabled" href="#" data-placeholder="Daftar Hadir" aria-disabled="true" title="Segera hadir">
  ...
</a>

<!-- Daftar Hadir — sudah ada link -->
<a class="standalone-primary" href="https://forms.gle/xxxx" target="_blank" rel="noopener">
  ...
</a>
```

### JS handler untuk link kosong (sudah ada di prototype, tinggal pakai)

```js
document.querySelectorAll('a.is-disabled').forEach(a => {
  a.addEventListener('click', e => {
    e.preventDefault();
    // opsional: toast "Segera hadir — hubungi panitia"
  });
});
```

---

## 3. Optimasi (No Build Step)

| Aspek | Keputusan |
|-------|-----------|
| **Build tool** | Tidak pakai (no Vite/Webpack/Parcel) — vanilla HTML/CSS/JS saja |
| **CSS** | Inline di `<style>` dalam `index.html` (single-file, 1 request, no FOUC) |
| **JS** | Inline di `<script>` akhir body (hanya accordion toggle + disabled handler, <1KB) |
| **Font** | Google Fonts `Inter` dengan `display=swap` + `preconnect` |
| **Gambar** | WebP (quality 80), max 1200px wide, `loading="lazy"` untuk foto kantor, background via CSS `url()` dengan overlay |
| **Minify** | Tidak perlu untuk v1 (file ~18KB, sudah kecil). Jika mau: pakai https://www.toptal.com/developers/html-minifier atau Netlify auto-minify |
| **Favicon** | `assets/favicon.ico` atau `favicon.png` (32x32, dari logo BPS) |

### Font loading optimal

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@500;600;700;800&display=swap" rel="stylesheet">
```

---

## 4. Cara Update Link (untuk Panitia)

> **Langkah update link (edit manual HTML):**
> 1. Buka `index.html` di code editor (VS Code / Notepad++).
> 2. Cari label tombol yang mau diisi (mis. `Zoom Meeting`) — ada komentar `<!-- TODO: ganti href="#" -->` di atasnya.
> 3. Ganti `href="#"` dengan URL aktual (mis. `href="https://zoom.us/j/1234567890"`).
> 4. Hapus `class="is-disabled"`, `aria-disabled="true"`, `title`, dan `data-placeholder` pada tag `<a>` tersebut.
> 5. Tambahkan `target="_blank" rel="noopener"` agar link buka di tab baru.
> 6. Save, lalu drag-and-drop folder ke Netlify (atau `git push` jika pakai Git).

Komentar `<!-- TODO -->` sudah ada di setiap placeholder di `index.html` final — panitia tinggal search `TODO` untuk lihat link mana yang masih kosong.

---

## 5. Checklist Build Final

- [ ] `index.html` single-file (CSS+JS inline) — copy dari `prototype.html` + polish
- [ ] 9 placeholder link dengan `is-disabled` + `TODO` comment
- [ ] Copy final dari Tiket 04 (label + helper + microcopy)
- [ ] Palet & tipografi dari `docs/tema-visual.md`
- [ ] Struktur accordion dari `prototype.html` (sudah final)
- [ ] Favicon dari logo BPS
- [ ] Meta OG untuk share WhatsApp (judul + deskripsi + image)
- [ ] Test di mobile (Chrome DevTools) + keyboard nav

---

*Dokumen ini adalah jawaban Tiket 05 — dipakai langsung untuk build `index.html` final & Tiket 06 (deploy).*
