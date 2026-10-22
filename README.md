# Asri Collection — Repository Dokumentasi

Repository ini menyimpan dokumen acuan untuk proses penelitian, audit, perancangan, dan pengembangan terkontrol proyek Asri Collection.

Repository ini berfokus pada dokumentasi dan prompt kerja. Keberadaan dokumen arsitektur atau contoh struktur di sini **tidak berarti** kode aplikasi, konfigurasi backend, database, maupun deployment terkait telah dibuat atau diverifikasi.

## Dokumen utama

| File | Tujuan |
|---|---|
| [`0.md`](./0.md) | Master Prompt V2.1 untuk riset repository, audit keamanan, rekomendasi, implementasi terkontrol, pengujian, dan verifikasi. |
| [`STRUCTURE.md`](./STRUCTURE.md) | Referensi struktur direktori aplikasi Asri Collection, tanggung jawab direktori, konvensi penamaan, dan batas keamanan. |

## Cara menggunakan dokumen

1. Baca `0.md` untuk memahami peran, prinsip kerja, dan workflow perubahan yang diharapkan.
2. Gunakan `STRUCTURE.md` sebagai acuan konseptual ketika membahas struktur aplikasi.
3. Sebelum audit atau implementasi, pastikan repository aplikasi, branch, dan commit yang benar.
4. Periksa file serta konfigurasi aktual dan gunakan bukti yang dapat diverifikasi.
5. Bedakan temuan faktual, asumsi, rekomendasi, dan pekerjaan yang belum diverifikasi.
6. Dapatkan persetujuan eksplisit sebelum menjalankan perubahan yang memerlukan persetujuan pemilik proyek.

## Workflow perubahan

Workflow yang direkomendasikan:

**Audit → Analisis → Rekomendasi → Tinjauan requirement → Persetujuan eksplisit → Implementasi → Pengujian → Verifikasi**

Persetujuan untuk satu tahap atau satu cakupan tidak otomatis memberikan izin untuk cakupan lain.

## Batas dan keamanan

- `STRUCTURE.md` adalah **struktur referensi**, bukan inventaris yang membuktikan seluruh file atau folder telah tersedia.
- Jangan menyimpulkan implementasi berhasil hanya dari rencana, dokumentasi, atau kode yang belum diuji.
- Jangan mengubah database aktif, menjalankan migration, mengubah secrets, konfigurasi keamanan, atau melakukan deployment tanpa persetujuan eksplisit yang mencakup tindakan tersebut.
- Jangan menaruh API key, merchant key, token, password, atau secret lain di repository.
- Untuk integrasi pembayaran, verifikasi status harus berdasarkan bukti backend yang sah; redirect atau tampilan sukses di frontend bukan bukti final pembayaran.
- Audit harus mencantumkan cakupan, branch/commit, bukti temuan, risiko, keterbatasan, dan hasil pengujian yang benar-benar dijalankan.

## Pemeliharaan dokumentasi

- Perbarui dokumen ketika requirement atau keputusan arsitektur disepakati berubah.
- Pastikan perubahan dokumentasi tidak bertentangan dengan keputusan proyek terbaru.
- Jangan menandai fitur atau struktur sebagai sudah diterapkan sebelum diverifikasi di repository aplikasi yang tepat.
- Gunakan commit message yang menjelaskan tujuan perubahan secara ringkas.

## Catatan

Repository ini adalah sumber dokumentasi kerja. Untuk mengetahui kondisi implementasi aktual, audit repository aplikasi dan konfigurasi Supabase yang sesuai secara terpisah.
