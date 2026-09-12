# Map — Wilkerstat Linktree BPS Kabupaten Gorontalo

## Destination

Halaman web Linktree Wilkerstat BPS Kabupaten Gorontalo **sudah live** di Netlify (subdomain `*.netlify.app` + domain custom milik user) — single-page statis (HTML/CSS/JS vanilla, tanpa build step) yang menampilkan 9 tautan terkelompok dalam section/accordion, bertema BPS (biru–oranye–hijau + logo resmi), berfoto kantor BPS Kab. Gorontalo & background Gorontalo, dengan semua link sebagai placeholder yang mudah diedit manual via file HTML. Siap dibagikan ke peserta pelatihan Wilkerstat.

## Notes

- **Domain:** Linktree statis untuk pelatihan Wilkerstat (Wilayah Kerja Statistik) BPS Kab. Gorontalo — bukan CMS, bukan app dinamis.
- **Stack preferensi:** Vanilla HTML/CSS/JS, deploy Netlify (drag-and-drop atau Git), domain custom via Netlify DNS/CNAME, gratis.
- **Bahasa:** Indonesia. Audiens: peserta & panitia Wilkerstat (mobile-heavy).
- **Sumber aset visual:** Logo BPS resmi, foto kantor BPS Kab. Gorontalo (dari user/publik), background Gorontalo (mis. Benteng Otanaha / Danau Limboto / pesisir Gorontalo) — perlu cek lisensi & optimasi.
- **Skills yang dirujuk tiap sesi:** `prototype` untuk mockup, `research` untuk Netlify/docs BPS branding, `grilling` untuk copy & IA.
- **Wayfinder mode:** Planning — peta selesai = semua keputusan terkunci & siap handoff ke sesi build (atau build langsung jika Notes mengizinkan eksekusi). Jangan lompat ke coding sebelum tiket frontier selesai.

## Decisions so far

<!-- satu baris per tiket tertutup: gist + link — jangan restate detail -->

- [01 — Pengelompokan & IA 9 tautan Wilkerstat](https://github.com/Dhnzz/wilkerstat-links/issues/2) — 3 grup accordion + 2 standalone: Daftar Hadir (atas, primary) → Kelas Virtual (Zoom+VB) → Materi & Jadwal → Evaluasi & Tugas (Pre→Tugas→Post) → Q&A (bawah, secondary); default collapsed, multi-expand.
- [02 — Tema visual BPS Gorontalo & aset](https://github.com/Dhnzz/wilkerstat-links/issues/3) — Palet BPS Blue #002E5D / Orange #F7941E / Green #00875A (WCAG AA), Inter font, logo putih di header gradient, foto kantor + background Gorontalo (Otanaha/Limboto) WebP overlay; detail di `docs/tema-visual.md`.
- [03 — Struktur halaman & interaksi accordion](https://github.com/Dhnzz/wilkerstat-links/issues/4) — Prototype `prototype.html` (single-file vanilla): header gradient + Daftar Hadir primary → 3 accordion (Kelas Virtual, Materi & Jadwal, Evaluasi & Tugas) → Q&A secondary → footer; accordion collapsed default, multi-expand, ARIA + keyboard.
- [04 — Copy, label tombol & microcopy](https://github.com/Dhnzz/wilkerstat-links/issues/5) — Tone ramah+emoji, ejaan "Tugas Asynchronus 1" & "Pre Test/Post Test" tanpa hyphen; copy final per grup/sub-link + header/footer + microcopy link kosong siap tempel.

## Not yet specified

<!-- fog — in-scope tapi belum tajam untuk jadi tiket; akan graduate setelah frontier maju -->

- **Sumber link Q&A / Pre-Test / Post-Test / Tugas:** Apakah link eksternal (Google Form / LMS) atau embed iframe? Butuh konfirmasi format link aktual & apakah perlu embed vs redirect — belum bisa dispesifikasi sebelum tiket grouping & konten selesai.
- **Jadwal Pelatihan — format data:** Apakah jadwal statis (tabel di halaman) atau link ke Google Sheet/Calendar eksternal? Implikasi ke desain section.
- **Daftar Hadir — mekanisme:** Link ke Google Form absensi atau sistem BPS internal? Perlu tahu apakah butuh parameter prefill.
- **Virtual Background — delivery:** Download langsung (zip/jpg) vs link Google Drive? Pengaruh ke UX tombol & icon.
- **Analitik & pelacakan klik:** Apakah perlu hit counter sederhana (GoatCounter/Netlify Analytics) atau cukup tanpa tracking? Menunggu keputusan setelah hosting.
- **Pemeliharaan pasca-live:** Siapa yang update link & seberapa sering? Sudah diputuskan "edit manual HTML", tapi perlu SOP singkat & dokumentasi di repo.

## Out of scope

<!-- kerja yang sadar dikeluarkan dari effort ini; tidak pernah graduate -->

- Backend/CMS dinamis, login, database, atau panel admin — out of scope, halaman statis only.
- Pembayaran, e-commerce, atau integrasi SSO BPS — tidak relevan untuk Linktree pelatihan.
- PWA/offline-first & push notification — nice-to-have, tidak untuk v1.
- Multi-bahasa (ID/EN) — v1 Indonesia only.
