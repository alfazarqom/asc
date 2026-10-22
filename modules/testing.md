# Testing, Verification & Release Readiness

## Jenis tes
Pilih sesuai risiko: unit (validasi, signature, status mapping); integration (database, RPC, Edge Functions, provider sandbox); end-to-end; security; regression; dan operational (retry, timeout, log, rekonsiliasi, rollback).

## Kasus minimum commerce/payment
Uji total/harga palsu; stok habis dan checkout bersamaan; invoice timeout/retry; callback signature invalid, reference/amount mismatch, duplikat/paralel; callback sukses/gagal/expiry/status tak dikenal; redirect sukses tanpa callback valid; pembayaran terlambat setelah reservasi habis; stok tidak tersedia; pengurangan stok ganda; akses tidak sah; dan kompatibilitas pemanggil endpoint lama.

## Status hasil
- **LULUS:** dijalankan dan memenuhi kriteria.
- **GAGAL:** dijalankan dan tidak memenuhi kriteria.
- **BELUM DIUJI:** belum dijalankan.
- **TERHAMBAT:** tidak dapat dijalankan karena akses/prasyarat.
- **TIDAK BERLAKU:** tidak relevan, dengan alasan.

Catat perintah, lingkungan, exit code/hasil, bukti, dan keterbatasan. Inspeksi kode saja bukan bukti tes lulus.

## Acceptance criteria audit
Scope dan baseline teridentifikasi; alur dan pemanggil dipetakan; temuan memiliki bukti/status kepastian, risiko, rekomendasi, dependensi, dan tes; area yang tidak dapat diakses disebutkan; tidak ada perubahan tanpa izin.

## Acceptance criteria implementasi
Diff sesuai scope; lint/build/unit/integration/E2E relevan dijalankan atau hambatannya dijelaskan; regression/security checks relevan selesai; tidak ada secret, migration, deployment, atau perubahan tambahan di luar izin; dokumentasi dan hasil verifikasi diperbarui; risiko residual dan pemulihan didokumentasikan.

## Release readiness
Sebelum menyatakan siap rilis, acceptance criteria harus terpenuhi, environment diverifikasi tanpa membocorkan secret, migration/deployment memiliki approval terpisah, observability/rollback tersedia, dan P0/P1 diselesaikan atau diterima secara eksplisit.
