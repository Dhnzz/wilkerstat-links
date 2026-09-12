# 03 — Struktur halaman & interaksi accordion

Type: prototype
Status: resolved
Blocked by: 01, 02

## Question

Desain struktur single-page Linktree Wilkerstat: header (logo + judul + subjudul Wilkerstat), section/grup hasil tiket 01, perilaku accordion (expand/collapse, animasi, aksesibilitas keyboard/ARIA), footer, dan responsif mobile-first.

Buat prototype fidelity rendah (wireframe HTML statis atau Figma-like mockup via HTML) yang menampilkan grouping, urutan, dan interaksi accordion — tanpa final polish visual. Link placeholder `#` cukup. Prototype ini yang akan di-review user sebelum build final.

Pertimbangan: jumlah grup ideal (3–4), max 2 level, tidak nested lebih dalam, state default (collapsed vs 1 expanded).

## Answer

**Prototype interaktif selesai:** `prototype.html` (single-file, vanilla HTML/CSS/JS, no build step).

**Struktur halaman (atas → bawah):**
1. **Header** — gradient BPS Blue `#002E5D → #0057A8` + overlay foto Gorontalo (Unsplash, opacity 0.12), badge "Pelatihan Wilkerstat 2026", logo placeholder (putih rounded), judul "Wilkerstat Links", subjudul, meta chips (📅 2026, 📍 Gorontalo, 👥 Peserta).
2. **Standalone primary — Daftar Hadir** — tombol besar oranye `#F7941E` + teks biru tua `#002E5D` (kontras 8.9:1), icon ✓, shadow oranye, 1 klik langsung (tanpa accordion).
3. **Accordion A — Kelas Virtual** (🎥, biru) → Zoom Meeting + Virtual Background (2 sub-link).
4. **Accordion B — Materi & Jadwal** (📚, hijau) → Materi Pembelajaran + Jadwal Pelatihan (2 sub-link).
5. **Accordion C — Evaluasi & Tugas** (📝, oranye) → Pre-Test → Tugas Asynchronus 1 → Post-Test (3 sub-link, urutan kronologis).
6. **Standalone secondary — Q&A** — card putih border biru, icon 💬, di bawah accordion.
7. **Footer** — BPS Kab. Gorontalo, link gorontalokab.bps.go.id & bps.go.id, copyright 2026.

**Perilaku accordion:**
- Default **collapsed** semua (rapi, tidak overwhelming).
- Multi-expand diperbolehkan (tidak auto-collapse grup lain).
- Animasi `max-height 0.28s ease`, chevron rotate 180° + background biru saat open.
- Aksesibilitas: `<button>` native (keyboard Enter/Space otomatis), `aria-expanded` + `aria-controls` + `role="region"`, `focus-visible` outline oranye.
- Hover: card shadow + border oranye 25%.

**Teknis:**
- Mobile-first, max-width 480px, centered.
- Palet & tipografi dari `docs/tema-visual.md` (Inter 500/600/700/800, variabel CSS `--bps-*`).
- Sub-link placeholder `href="#"` + `alert()` untuk demo; di build final akan diganti URL aktual.
- Banner kuning prototype di atas untuk penanda HITL review.

**Cara review:** buka `prototype.html` di browser (atau via preview pane). Klik tiap accordion untuk expand/collapse, cek urutan & label. Beri feedback sebelum build final — perubahan struktur di tahap ini murah.

**Dampak ke tiket berikutnya:**
- Tiket 04 (copy) — label grup & sub-link sudah final di prototype, tinggal polish microcopy.
- Tiket 05 (teknis build) — struktur file single `index.html` terkonfirmasi (prototype = struktur final).
- Tiket 06/07 — SOP deploy & QA akan pakai struktur ini.

## Comments

Prototype HITL — menunggu review user. File: `prototype.html` (17.7KB, single-file).
