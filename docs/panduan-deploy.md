# Panduan Deploy — Wilkerstat Links ke Netlify

> Deliverable Tiket 06 — `wayfinder:task` · Issue [#7](https://github.com/Dhnzz/wilkerstat-links/issues/7)

SOP langkah-demi-langkah deploy halaman Wilkerstat Links ke Netlify (gratis) + setup domain custom. Bisa diikuti panitia tanpa background dev.

---

## 0. Prasyarat

- File `index.html` sudah final (ada di repo ini — single-file, siap deploy).
- Akun Netlify (gratis) — daftar di https://app.netlify.com/signup (bisa pakai GitHub login).
- (Opsional) Domain custom — beli terpisah di penyedia domain (Niagahoster, Domainesia, Cloudflare Registrar, Namecheap, dll). Netlify **tidak menjual domain**, hanya hosting.

---

## 1. Opsi Deploy — Rekomendasi

| Opsi | Cara | Cocok untuk |
|------|------|-------------|
| **A. Drag & Drop** ⭐ Rekomendasi | Upload folder via browser | Panitia edit manual HTML, paling simpel |
| **B. Git (Continuous Deploy)** | Hubungkan repo GitHub → auto-deploy tiap push | Jika panitia sudah pakai Git |

**Rekomendasi untuk Wilkerstat:** **Opsi A (Drag & Drop)** — karena link diedit manual via `index.html`, tidak perlu setup Git. Cukup edit file → drag folder ke Netlify → live.

Jika nanti ingin auto-deploy, bisa migrasi ke Opsi B kapan saja (hubungkan repo `Dhnzz/wilkerstat-links`).

---

## 2. Deploy via Drag & Drop (Opsi A)

### Langkah:

1. **Siapkan folder deploy:**
   - Folder berisi `index.html` + folder `assets/` (jika ada gambar/logo).
   - Untuk Wilkerstat saat ini: cukup `index.html` saja sudah bisa live (gambar pakai placeholder/Unsplash).

2. **Buka Netlify:**
   - Login ke https://app.netlify.com
   - Di dashboard, cari area **"Add new site" → "Deploy manually"** atau drag area di halaman utama.

3. **Drag & Drop:**
   - Drag folder (atau file `index.html`) ke area deploy Netlify.
   - Tunggu upload selesai — Netlify akan kasih URL acak seperti `https://wilkerstat-xxxxx.netlify.app`.

4. **Ganti nama site (opsional tapi disarankan):**
   - Masuk ke **Site settings → Change site name**
   - Ganti jadi mis. `wilkerstat-gorontalokab` → URL jadi `https://wilkerstat-gorontalokab.netlify.app` (lebih rapi, mudah diingat).

5. **Update link:**
   - Edit `index.html` lokal (ganti `href="#"` dengan URL aktual — lihat `docs/teknis-build.md`).
   - Drag & drop lagi folder yang sudah diupdate — Netlify akan redeploy otomatis (atau pakai **Deploys → Drag and drop** lagi).

### Kelebihan Drag & Drop:
- Tidak perlu Git, tidak perlu command line.
- Update link tinggal edit file + drag lagi.

---

## 3. Deploy via Git (Opsi B — Alternatif)

1. Push repo ke GitHub (sudah ada: `Dhnzz/wilkerstat-links`).
2. Di Netlify: **Add new site → Import an existing project → GitHub → pilih `wilkerstat-links`**.
3. Build settings:
   - **Build command:** (kosongkan — tidak ada build step)
   - **Publish directory:** `.` (root) atau `/` — karena `index.html` di root.
4. Klik **Deploy** — Netlify akan deploy otomatis tiap `git push` ke `main`.

---

## 4. Setup Domain Custom

> User: "Gapapa nanti ada netlify di belakang" — artinya domain custom + suffix `.netlify.app` tidak masalah. Tapi jika ingin domain sendiri (mis. `wilkerstat.bpsgorontalo.id`), ikuti langkah ini.

### 4a. Beli Domain (jika belum punya)

- Beli di penyedia domain Indonesia/internasional (harga ~Rp 100–300rb/tahun untuk `.id`/`.com`).
- Contoh: `wilkerstat-gorontalo.my.id`, `wilkerstat.bpsgorontalo.id`.

### 4b. Tambah Domain di Netlify

1. Di Netlify dashboard → pilih site Wilkerstat → **Domain settings → Add custom domain**.
2. Masukkan domain yang sudah dibeli (mis. `wilkerstat-gorontalo.my.id`).
3. Netlify akan kasih instruksi DNS — pilih salah satu:

   **Opsi 1: Netlify DNS (paling mudah, jika domain baru & belum dipakai)**
   - Ganti nameserver domain di registrar ke nameserver Netlify (mis. `dns1.p06.nsone.net`).
   - Netlify akan kelola DNS otomatis + HTTPS.

   **Opsi 2: External DNS (jika domain sudah dipakai untuk hal lain)**
   - Tambah **CNAME** di DNS registrar:
     - `wilkerstat` → `wilkerstat-gorontalokab.netlify.app`
   - Atau **A record** jika pakai apex domain (`wilkerstat-gorontalo.my.id` tanpa subdomain).

4. Tunggu propagasi DNS (5 menit – 24 jam, biasanya <1 jam).

### 4c. HTTPS Otomatis

- Netlify otomatis provision **Let's Encrypt** SSL setelah domain terverifikasi.
- Cek di **Domain settings → HTTPS → Verify DNS configuration** → klik **Renew certificate** jika belum aktif.
- Setelah aktif, site bisa diakses via `https://` (gembok hijau).

---

## 5. Checklist Pre-Deploy

Sebelum deploy final, pastikan:

- [ ] `index.html` sudah final (copy final, palet, struktur accordion — semua tiket done)
- [ ] 9 placeholder link ada `TODO` comment + `is-disabled` (siap diisi panitia)
- [ ] Favicon ada di `./assets/favicon.png` (atau pakai placeholder — tidak block deploy)
- [ ] Meta OG sudah terisi (title, description, image) — untuk share WhatsApp/Telegram
- [ ] Test lokal: buka `index.html` di browser, klik accordion, cek toast untuk link disabled
- [ ] Test mobile: Chrome DevTools → responsive 360px, cek header & tombol tidak overflow
- [ ] (Opsional) Buat file `_redirects` jika perlu redirect (untuk single-page tidak wajib)

---

## 6. Estimasi Biaya

| Item | Biaya |
|------|-------|
| **Netlify Hosting (Free tier)** | **Gratis** — 100GB bandwidth/bulan, 300 build minutes, 1 site. Cukup untuk Linktree statis (traffic pelatihan <10K kunjungan). |
| **Domain custom** | **Berbayar terpisah** — ~Rp 100–300rb/tahun (`.my.id` paling murah, `.id`/`.com` ~Rp 150–300rb). Beli di registrar, bukan di Netlify. |
| **HTTPS (Let's Encrypt)** | **Gratis** — auto via Netlify. |
| **Total untuk v1** | **Rp 0** jika pakai `*.netlify.app` saja. **Rp 100–300rb/tahun** jika tambah domain custom. |

**Batas Free Tier Netlify (cukup untuk Wilkerstat):**
- Bandwidth 100GB/bulan (Linktree ~22KB → bisa handle ~4 juta pageview/bulan).
- Build 300 menit/bulan (tidak relevan — no build step).
- Jika butuh lebih, upgrade ke Pro $19/bulan — tidak perlu untuk v1.

---

## 7. Pemeliharaan Pasca-Live

- **Update link:** Edit `index.html` lokal → ganti `href="#"` → drag & drop lagi ke Netlify (atau `git push` jika pakai Git). Lihat `docs/teknis-build.md` untuk 6 langkah detail.
- **Monitoring:** Cek Netlify dashboard → **Deploys** untuk riwayat deploy, **Analytics** (opsional, free tier ada basic).
- **Backup:** Repo GitHub `Dhnzz/wilkerstat-links` adalah backup — semua file ter-version.

---

*Dokumen ini adalah jawaban Tiket 06 — SOP siap diikuti panitia tanpa dev.*
