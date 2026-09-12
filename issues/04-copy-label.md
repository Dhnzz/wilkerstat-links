# 04 — Copy, label tombol & microcopy

Type: grilling
Status: resolved
Blocked by: 01

## Question

Finalisasi copy untuk halaman Wilkerstat Linktree:

- Judul & subjudul header (mis. "Wilkerstat BPS Kabupaten Gorontalo" + tagline pelatihan).
- Label tiap tombol/grup (mis. "Materi Pembelajaran" → "📚 Materi Pembelajaran" atau tetap formal? Singkatan?).
- Microcopy helper (mis. "Link akan aktif H-1 pelatihan", "Gunakan akun BPS untuk akses").
- Urutan kata & konsistensi (Pre-Test vs Pre Test, Asynchronus vs Asinkronus).
- Bahasa: formal kedinasan BPS vs santai ramah peserta.

Deliverable: daftar copy final per tombol/grup + header/footer yang siap tempel ke HTML.

## Answer

### Keputusan Gaya
- **Tone:** Ramah + emoji — menarik untuk peserta, tetap profesional (sesuai pilihan user).
- **Ejaan tugas:** Tetap **"Tugas Asynchronus 1"** sesuai brief awal (tidak diubah ke Asinkronus).
- **Pre/Post:** **"Pre Test"** dan **"Post Test"** tanpa hyphen (sesuai pilihan user).

### Copy Final — Siap Tempel ke HTML

#### Header
| Elemen | Copy |
|--------|------|
| Badge | `Pelatihan Wilkerstat 2026` |
| Logo text | `BADAN PUSAT STATISTIK` + `Kabupaten Gorontalo` |
| Judul (H1) | `Wilkerstat Links` (Wilkerstat putih, Links oranye `#F7941E`) |
| Subjudul | `Pusat tautan pelatihan Wilayah Kerja Statistik` + `BPS Kabupaten Gorontalo` |
| Meta chips | `📅 2026` · `📍 Gorontalo` · `👥 Peserta Wilkerstat` |

#### Daftar Hadir — Standalone Primary (paling atas)
| Elemen | Copy |
|--------|------|
| Label tombol | `✓ Daftar Hadir` |
| Helper | `Tap untuk absensi kehadiran →` |
| Aria-label | `Daftar Hadir — absensi kehadiran pelatihan` |

#### Grup A — Kelas Virtual (accordion 🎥)
| Elemen | Copy |
|--------|------|
| Judul grup | `🎥 Kelas Virtual` |
| Helper grup | `2 tautan · Zoom & Virtual Background` |
| Sub-link 1 | `🎥 Zoom Meeting` — helper `Link ruang kelas virtual` |
| Sub-link 2 | `🖼️ Virtual Background` — helper `Download background Zoom` |

#### Grup B — Materi & Jadwal (accordion 📚)
| Elemen | Copy |
|--------|------|
| Judul grup | `📚 Materi & Jadwal` |
| Helper grup | `2 tautan · Bahan ajar & jadwal pelatihan` |
| Sub-link 1 | `📚 Materi Pembelajaran` — helper `Slide, modul & bahan ajar` |
| Sub-link 2 | `📅 Jadwal Pelatihan` — helper `Rundown & pembagian sesi` |

#### Grup C — Evaluasi & Tugas (accordion 📝)
| Elemen | Copy |
|--------|------|
| Judul grup | `📝 Evaluasi & Tugas` |
| Helper grup | `3 tautan · Pre Test → Tugas → Post Test` |
| Sub-link 1 | `📝 Pre Test` — helper `Tes awal sebelum materi` |
| Sub-link 2 | `📋 Tugas Asynchronus 1` — helper `Tugas mandiri peserta` |
| Sub-link 3 | `✅ Post Test` — helper `Tes akhir setelah materi` |

#### Q&A — Standalone Secondary (paling bawah)
| Elemen | Copy |
|--------|------|
| Label tombol | `💬 Q&A` |
| Helper | `Tanya jawab & diskusi` |
| Aria-label | `Q&A — tanya jawab pelatihan` |

#### Footer
| Elemen | Copy |
|--------|------|
| Baris 1 | `BPS Kabupaten Gorontalo` (bold, BPS Blue) |
| Baris 2 | `Badan Pusat Statistik — Wilayah Kerja Statistik (Wilkerstat)` |
| Links | `gorontalokab.bps.go.id` · `bps.go.id` |
| Copyright | `© 2026 BPS Kabupaten Gorontalo` |

#### Microcopy Tambahan (opsional, untuk state link kosong)
- Link belum aktif: `Segera hadir — link akan aktif H-1 pelatihan`
- Link disabled tooltip: `Link belum tersedia, hubungi panitia`

### Catatan Konsistensi
- Semua label grup pakai emoji di depan (🎥 📚 📝) — konsisten.
- Standalone pakai icon di dalam tombol (✓ untuk Daftar Hadir, 💬 untuk Q&A).
- Helper selalu format: `X tautan · deskripsi singkat` untuk grup, deskripsi fungsi untuk sub-link.
- Ejaan "Pre Test" / "Post Test" tanpa hyphen — konsisten di semua tempat (grup helper, sub-link, microcopy).

## Comments

Resolved via grilling — user pilih: ramah+emoji, tetap "Tugas Asynchronus 1", "Pre Test/Post Test" tanpa hyphen.
