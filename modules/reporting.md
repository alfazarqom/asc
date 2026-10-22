# Reporting & Evidence Standard

## Status bukti
- **TERVERIFIKASI:** dibuktikan langsung lewat source, schema, log, runtime, atau tes.
- **INDIKASI:** bukti mengarah pada kemungkinan, tetapi belum cukup untuk konfirmasi.
- **ASUMSI:** dugaan kerja yang belum dibuktikan.
- **BELUM DIKETAHUI:** belum tersedia atau belum diperiksa.
- **TERHAMBAT:** verifikasi terhalang akses/prasyarat.

## Prioritas
- **P0 — Kritis:** risiko langsung sangat berat pada keamanan, pembayaran, atau integritas data.
- **P1 — Tinggi:** dampak besar pada keamanan atau alur transaksi utama.
- **P2 — Sedang:** masalah penting dengan mitigasi/cakupan terbatas.
- **P3 — Rendah:** kualitas, maintainability, atau risiko kecil.
- **P4 — Informasional:** saran tanpa risiko langsung yang terbukti.

Prioritas harus didukung dampak dan konteks, bukan digunakan untuk melebih-lebihkan kepastian.

## Sepuluh elemen temuan wajib
1. ID; 2. prioritas; 3. kategori; 4. status bukti; 5. referensi konkret; 6. perilaku aktual; 7. perilaku yang diharapkan; 8. dampak/risiko; 9. rekomendasi; 10. dependensi dan tes verifikasi.

## Format laporan audit
1. Ringkasan eksekutif dan keputusan yang dibutuhkan.
2. Scope, repo/branch/commit, lingkungan, dan batas akses.
3. Metode dan sumber bukti.
4. Peta arsitektur/data flow yang relevan.
5. Temuan berdasarkan prioritas.
6. Area yang tidak diperiksa/belum terverifikasi.
7. Risiko residual dan dependensi.
8. Rekomendasi bertahap dan acceptance criteria.
9. Status tes/verifikasi.
10. Opsi berikutnya, rekomendasi terbaik beserta alasan, prasyarat, risiko, scope, dan persetujuan yang diperlukan.

## Ringkasan implementasi
Laporkan file ditambah/diubah/dihapus, diff, alasan, hasil tes, tindakan yang tidak dilakukan, commit/branch, risiko residual, dan approval berikutnya. Pisahkan fakta, interpretasi, rekomendasi, dan keputusan pemilik proyek. Jangan klaim deployment/perubahan sistem berhasil tanpa bukti langsung.
