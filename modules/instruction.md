# Instructions & Workflow

**Status:** Kandidat V3.0.0.

## Alur wajib
1. Klarifikasi tujuan, repository, branch, lingkungan, dan batas perubahan.
2. Audit read-only: petakan file, entry point, pemanggil, data flow, integrasi, schema, konfigurasi, dan tes.
3. Laporkan temuan dengan bukti, prioritas, dampak, dan tingkat kepastian.
4. Berikan opsi rekomendasi dengan scope dan risiko.
5. Tinjau requirement dan pisahkan fakta aktual, kontrak eksternal, requirement bisnis yang disetujui, serta acceptance criteria.
6. Minta persetujuan implementasi eksplisit dengan cakupan dan tindakan yang disebutkan.
7. Implementasikan perubahan minimal sesuai persetujuan.
8. Jalankan tes relevan; catat perintah, hasil, kegagalan, dan keterbatasan.
9. Tinjau diff, risiko residual, dan kesiapan rilis. Tindakan berisiko tinggi memerlukan approval tersendiri.
10. Tutup tahap dengan status, hasil terverifikasi, pekerjaan yang tidak dilakukan, risiko, keputusan, dan langkah berikutnya.

## Sumber kebenaran
- **Kondisi aktual:** source, schema aktif, konfigurasi, runtime, log, dan hasil tes yang benar-benar diperiksa.
- **Kontrak eksternal:** dokumentasi resmi provider/API.
- **Requirement bisnis:** keputusan eksplisit pemilik proyek yang berlaku untuk tugas ini.
- **Acceptance criteria:** kriteria terukur untuk audit atau implementasi.

Jika kategori bertentangan, jelaskan konflik. Kode yang ada tidak otomatis benar; dokumen target tidak membuktikan implementasi.

## Sumber Duitku
- POP: https://docs.duitku.com/pop/id/
- API: https://docs.duitku.com/api/id/
- FAQ: https://www.duitku.com/frequently-asked-questions/

Verifikasi endpoint, method, fields, signature, acknowledgment, status, expiry, redirect/return, metode pembayaran, kredensial, dan kasus sandbox berdasarkan dokumentasi resmi. Jangan mengarang kontrak.

## Kontrol tahap
Audit read-only bukan izin edit. Persetujuan requirement bukan izin implementasi. Persetujuan patch lokal bukan izin push, merge, migration, secrets, deployment, atau transaksi nyata. Jika scope berubah, berhenti dan minta keputusan.
