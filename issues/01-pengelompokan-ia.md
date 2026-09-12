# 01 — Pengelompokan & IA 9 tautan Wilkerstat

Type: grilling
Status: resolved

## Question

Rekomendasi pengelompokan 9 tombol (Materi Pembelajaran, Zoom Meeting, Jadwal Pelatihan, Daftar Hadir, Virtual Background, Q&A, Pre-Test, Tugas Asynchronus 1, Post-Test) menjadi section/grup yang masuk akal untuk Linktree Wilkerstat — termasuk alasan tiap grup, urutan tampil, dan mana yang standalone vs masuk accordion.

Konteks: user setuju dikelompokkan, prefer single-page + accordion (klik grup → expand sub-link). Contoh awal user: Zoom Meeting berisi Virtual Background + link Zoom. Perlu validasi apakah itu pengelompokan terbaik atau ada alternatif (mis. grup "Kelas Virtual", "Evaluasi & Tugas", "Administrasi").

Deliverable tiket: keputusan final grouping (nama grup + anggota + urutan) yang akan dipakai tiket desain & copy. Referensi: Linktree BPS lain, UX pelatihan.

## Answer

### Keputusan Final Grouping — 3 Grup Accordion + 2 Standalone

**Prinsip:** Frekuensi klik + alur pelatihan (sebelum → saat → sesudah kelas) + minimal tap untuk aksi kritis.

**Urutan tampil di halaman (atas → bawah):**

#### 1. ✅ Daftar Hadir — STANDALONE (tombol besar, paling atas, 1 klik)
- **Isi:** 1 tombol — Daftar Hadir
- **Alasan:** Paling sering diklik tiap sesi, harus 1 tap tanpa expand. Ditaruh paling atas di bawah header agar langsung terlihat di first viewport (mobile).
- **Visual:** Tombol primary paling menonjol (warna oranye BPS / accent).

#### 2. 🎥 Grup A — Kelas Virtual (accordion)
- **Isi:** Zoom Meeting + Virtual Background
- **Alasan:** Keduanya dipakai *saat* sesi live. Mengelompokkan sesuai ide awal user (Zoom berisi VB) tapi dibalik: grup bernama "Kelas Virtual" lebih deskriptif daripada "Zoom Meeting" yang terkesan 1 link. Expand → 2 sub-tombol.
- **Label grup:** `Kelas Virtual` — ikon 🎥 / video

#### 3. 📚 Grup B — Materi & Jadwal (accordion)
- **Isi:** Materi Pembelajaran + Jadwal Pelatihan
- **Alasan:** Keduanya bersifat *referensi sebelum/saat* pelatihan. Peserta cek jadwal lalu buka materi — alur natural. Grup ini berisi informasi, bukan aksi.
- **Label grup:** `Materi & Jadwal` — ikon 📚

#### 4. 📝 Grup C — Evaluasi & Tugas (accordion)
- **Isi:** Pre-Test + Tugas Asynchronus 1 + Post-Test
- **Alasan:** Ketiganya adalah *evaluasi* dengan urutan kronologis: Pre → Tugas → Post. Dikelompokkan agar peserta paham progres. Q&A sengaja dikeluarkan (lihat standalone 2).
- **Label grup:** `Evaluasi & Tugas` — ikon 📝
- **Urutan di dalam grup:** Pre-Test (atas) → Tugas Asynchronus 1 → Post-Test (bawah)

#### 5. 💬 Q&A — STANDALONE (tombol di bawah, sebelum footer)
- **Isi:** 1 tombol — Q&A
- **Alasan:** Sesuai keputusan user: standalone di bawah agar mudah ditemukan kapan saja, tidak terkubur di accordion. Sifatnya ad-hoc (bisa diakses sebelum/saat/sesudah), jadi tidak cocok masuk grup kronologis.
- **Visual:** Tombol secondary / outline, ikon 💬

### Ringkasan Visual Halaman

```
[Header: Logo BPS + Judul Wilkerstat + Foto Kantor]
[Daftar Hadir — tombol besar primary]          ← standalone 1
[Kelas Virtual ▾] → Zoom Meeting, VB          ← accordion
[Materi & Jadwal ▾] → Materi, Jadwal          ← accordion
[Evaluasi & Tugas ▾] → Pre, Tugas, Post       ← accordion
[Q&A — tombol secondary]                      ← standalone 2
[Footer]
```

### Aturan Interaksi Accordion
- Default: semua accordion **collapsed** (rapi, tidak overwhelming).
- Satu grup boleh expanded bersamaan (tidak auto-collapse grup lain — biar peserta bisa bandingkan).
- Animasi: slide 200ms, `aria-expanded` + `aria-controls` untuk aksesibilitas.

### Alternatif yang Dipertimbangkan & Ditolak
- **4 grup granular** (Materi, Jadwal, Evaluasi, Administrasi) — ditolak: terlalu banyak accordion untuk 9 link, menambah tap.
- **Q&A masuk Evaluasi** — ditolak user: Q&A lebih sering dicari terpisah.
- **Q&A masuk Kelas Virtual** — ditolak: Q&A tidak hanya saat Zoom.
- **Daftar Hadir masuk grup Administrasi** — ditolak: aksi kritis jangan disembunyikan.

### Dampak ke Tiket Berikutnya
- Tiket 02 (tema visual): Daftar Hadir = primary button, Q&A = secondary, grup accordion = card style.
- Tiket 03 (prototype): pakai struktur 5 section di atas.
- Tiket 04 (copy): label grup final sudah dikunci di sini.

## Comments

Resolved via grilling — user konfirmasi: Daftar Hadir standalone atas, Q&A standalone bawah, 3 grup + 1 standalone (total 5 section).
