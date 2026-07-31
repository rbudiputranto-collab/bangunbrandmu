# BangunBrandmu Website

Repository untuk website utama [bangunbrandmu.id](https://bangunbrandmu.id).

Website saat ini berbentuk static single-page website. HTML, CSS, JavaScript,
quiz, dan sebagian besar aset visual berada dalam satu file `index.html`.

## File yang dicatat dalam Git

| File | Fungsi |
| --- | --- |
| `index.html` | Website utama, styling, Brand & Marketing Audit, hasil audit, dan CTA |
| `BangunBrandmu_logo_premium.png` | Master logo BangunBrandmu |
| `ChatGPT Image May 27, 2026, 02_41_15 AM.png` | Source visual/logo alternatif |
| `ChatGPT Image May 27, 2026, 02_48_35 AM.png` | Source visual alternatif |
| `ChatGPT Image May 27, 2026, 09_39_10 AM.png` | Source visual alternatif |
| `ChatGPT Image May 27, 2026, 09_46_40 AM.png` | Source visual alternatif |
| `README.md` | Dokumentasi website dan alur perubahan |
| `.gitignore` | Mencegah dokumen lokal/confidential ikut masuk repository |

Folder `Santi Story/` sengaja tidak dicatat dalam Git karena berisi dokumen
klien dan materi internal.

## Struktur Website

Urutan section pada `index.html`:

1. Navbar dan hero
2. Masalah yang dihadapi target market
3. Strategic reframe
4. Penjelasan Brand & Marketing Audit
5. Quiz audit 18 pertanyaan
6. Lead capture dan hasil audit
7. Layanan BangunBrandmu
8. Target client
9. Cara kerja
10. Trust/profile
11. Skenario layanan
12. FAQ
13. Final CTA dan WhatsApp

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

