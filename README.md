# BangunBrandmu Website

Repository khusus website umbrella brand
[bangunbrandmu.id](https://bangunbrandmu.id).

Website saat ini berbentuk static single-page website. HTML, CSS, JavaScript,
quiz, dan sebagian besar aset visual berada dalam satu file `index.html`.

Repository ini hanya menyimpan aset website BangunBrandmu. Project klien
berada di luar repository, pada folder sejajar `../Projects/`.

## File yang dicatat dalam Git

| File | Fungsi |
| --- | --- |
| `index.html` | Website utama, styling, Brand & Marketing Audit, hasil audit, dan CTA |
| `live.html` | Landing page BangunBrandmu Live, seri event, host, funnel, dan priority-list form |
| `BangunBrandmu_logo_premium.png` | Master logo BangunBrandmu |
| `ChatGPT Image May 27, 2026, 02_41_15 AM.png` | Source visual/logo alternatif |
| `ChatGPT Image May 27, 2026, 02_48_35 AM.png` | Source visual alternatif |
| `ChatGPT Image May 27, 2026, 09_39_10 AM.png` | Source visual alternatif |
| `ChatGPT Image May 27, 2026, 09_46_40 AM.png` | Source visual alternatif |
| `README.md` | Dokumentasi website dan alur perubahan |
| `.gitignore` | Mencegah dokumen lokal/confidential ikut masuk repository |

## Struktur Website

Urutan section pada `index.html`:

1. Navbar dan hero dengan CTA utama menuju BangunBrandmu Live
2. BangunBrandmu Live dan sesi perdana
3. Masalah yang dihadapi target market
4. Strategic reframe
5. Penjelasan Brand & Marketing Audit
6. Quiz audit 18 pertanyaan
7. Lead capture dan hasil audit
8. Layanan BangunBrandmu
9. Target client
10. Cara kerja
11. Trust/profile
12. Skenario layanan
13. FAQ
14. Final CTA dan WhatsApp

`live.html` menjadi landing page event dan memuat:

1. Sesi BangunBrandmu Live berikutnya
2. Format sesi kerja 60 menit
3. Tiga topik seri pertama
4. Jalur Live → Audit → Growth Check → Implementasi
5. Profil Radhit sebagai host
6. Priority-list form

## Lead Capture

Setelah menyelesaikan 18 pertanyaan, pengunjung diminta mengisi:

- Nama
- Nama bisnis
- Industri
- Nomor WhatsApp
- Email
- Instagram/website (opsional)
- Range omzet (opsional)

Data dan hasil audit dikirim ke Google Apps Script melalui fungsi
`submitLeadData()` di dalam `index.html`.

Form priority list pada `live.html` menggunakan webhook yang sama dan menambahkan
`source: BangunBrandmu Live Priority List` agar sumber lead dapat dibedakan.

> Jangan mengganti URL webhook tanpa memastikan Apps Script dan Google Sheet
> tujuan sudah benar. Hindari memasukkan password, API key, atau credential
> privat ke dalam HTML karena source website dapat dilihat publik.

## Menjalankan Website Secara Lokal

Dari folder project:

```bash
python3 -m http.server 8765
```

Kemudian buka:

```text
http://127.0.0.1:8765/index.html
```

Gunakan local server, bukan membuka file langsung, agar perilakunya mendekati
website online.

## Checklist Sebelum Publish

- Periksa tampilan desktop dan mobile.
- Jalankan seluruh 18 pertanyaan audit.
- Periksa navigasi dari homepage menuju `live.html`.
- Uji form priority list dengan data test yang jelas dan cek Google Sheet.
- Pastikan tombol kembali dan lanjut bekerja.
- Pastikan hasil score, strengths, priorities, dan rekomendasi tampil.
- Uji lead menggunakan data test yang jelas, lalu cek Google Sheet.
- Pastikan CTA WhatsApp menggunakan nomor dan pesan yang benar.
- Periksa browser console untuk error.
- Pastikan tidak ada dokumen klien atau credential yang ikut di-commit.
- Bandingkan website online setelah deployment.

## Workflow Perubahan

Sebelum mengubah file:

```bash
git status
git pull
```

Setelah melakukan perubahan:

```bash
git diff
git add index.html README.md
git commit -m "Jelaskan perubahan secara singkat"
git push
```

Contoh pesan commit:

```text
Improve mobile hero spacing
Add privacy consent to audit form
Fix lead webhook error handling
Update service copy
```

Satu commit sebaiknya mewakili satu perubahan yang jelas. Dengan begitu setiap
versi dapat dibandingkan atau dikembalikan tanpa mengganggu perubahan lain.

## Deployment

Website aktif di:

- Production: https://bangunbrandmu.id
- Source repository: belum dicatat pada salinan lokal ini
- Deployment platform: perlu dikonfirmasi dari repository/DNS

Setelah URL repository diketahui, tambahkan sebagai remote:

```bash
git remote add origin URL_REPOSITORY_GITHUB
git branch -M main
git push -u origin main
```

Jangan menjalankan perintah `git remote add origin` sebelum URL repository
dipastikan benar.

## Improvement Backlog

Prioritas berikutnya berdasarkan audit 31 Juli 2026:

1. Tambahkan privacy policy dan consent pada lead form.
2. Perbaiki error handling webhook agar kegagalan pengiriman tidak dianggap sukses.
3. Tingkatkan accessibility label form dan pilihan quiz.
4. Tambahkan canonical URL, Open Graph, Twitter Card, dan structured data.
5. Tambahkan `robots.txt` dan `sitemap.xml`.
6. Tambahkan `rel="noopener noreferrer"` pada link yang membuka tab baru.
7. Pertimbangkan pemisahan CSS, JavaScript, dan assets saat website berkembang.
