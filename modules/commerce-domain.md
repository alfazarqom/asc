# Commerce Domain: Order, Payment & Inventory

## Data dan harga
Simpan uang sebagai angka dalam satuan Rupiah sesuai schema/kontrak; hindari floating-point untuk perhitungan yang memerlukan presisi. Simpan snapshot item, varian/SKU, kuantitas, harga, diskon, ongkir, dan total agar riwayat order tidak berubah saat katalog diperbarui. Validasi ulang harga, stok, varian, dan total di server. Bedakan order status, payment status, dan shipment status.

## State dan transisi
Gunakan state machine eksplisit dengan prasyarat, aktor berwenang, dan perilaku idempoten. Tolak transisi tidak sah. Status harus mengikuti requirement yang disetujui; petakan dan laporkan konflik jika schema/behavior aktual berbeda.

## Ongkir manual dan reservasi
Jika admin menetapkan ongkir setelah meninjau alamat, tetapkan kebijakan reservasi eksplisit dan batas expiry. Batas pembayaran dimulai sesuai requirement setelah invoice dibuat. Perubahan ongkir/total harus konsisten pada invoice dan snapshot order. Saat expiry, lepaskan reservasi sesuai aturan yang disetujui.

## Pembayaran terlambat
1. Verifikasi signature callback dan identitas transaksi.
2. Cocokkan reference, amount, currency, dan status provider.
3. Periksa status order dan stok saat ini.
4. Jangan konfirmasi stok yang tidak tersedia atau mengurangi stok dua kali.
5. Masukkan kasus ke rekonsiliasi/manual review atau refund sesuai kebijakan yang disetujui.
6. Catat keputusan dan hasil untuk audit.

## Atomicity dan concurrency
Pembaruan payment/order/reservation/inventory yang terkait harus atomik menggunakan transaksi database atau RPC terkontrol. Hindari beberapa request frontend terpisah untuk langkah yang harus berhasil/gagal bersama. Gunakan unique constraints/idempotency keys, locking atau conditional updates bila sesuai, serta tes callback paralel/retry.

## Pengiriman dan privasi
Validasi alamat dan kontak, batasi akses data pelanggan, dan pisahkan status pengiriman dari status pembayaran.
