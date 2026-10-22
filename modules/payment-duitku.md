# Duitku POP Integration

## Sumber kontrak resmi
- POP: https://docs.duitku.com/pop/id/
- API: https://docs.duitku.com/api/id/
- FAQ: https://www.duitku.com/frequently-asked-questions/

Jangan menebak endpoint, fields, signature formula, acknowledgment, status, expiry, atau perilaku metode pembayaran. Catat halaman/versi yang diperiksa dan cocokkan kontrak dengan kode aktual.

## Invoice dan request
Verifikasi endpoint/method; merchant code; merchant order reference; amount; product/details; customer fields; callback/return URL; expiry; payment method; request signature dan formatnya; respons invoice/payment URL/provider reference; error handling; serta idempotensi untuk retry/timeout. Total harus dihitung dari sumber server-side, bukan dipercaya dari klien.

## Callback/webhook
- Validasi signature sesuai dokumentasi resmi.
- Cocokkan reference transaksi, amount, merchant order ID, dan status.
- Buat pemrosesan idempoten; callback duplikat tidak boleh menggandakan efek.
- Terapkan transaksi atomik untuk payment/order/inventory.
- Kembalikan acknowledgment sesuai kontrak provider.
- Simpan informasi minimum yang dibutuhkan untuk audit dan rekonsiliasi.

## Redirect/return
Redirect hanya untuk pengalaman pengguna dan tampilan status. Query parameter, halaman sukses, dan data frontend bukan bukti pembayaran. Status final harus bersumber dari callback terverifikasi dan/atau pemeriksaan server-side yang sesuai.

## Status, expiry, dan rekonsiliasi
Petakan status provider ke status internal secara eksplisit. Definisikan timeout, expiry, callback terlambat, status tak dikenal, status check, retry, dan rekonsiliasi. Pembayaran setelah reservasi habis mengikuti `commerce-domain.md`; jangan otomatis mengonfirmasi stok yang tidak tersedia.

## Secrets dan environment
Pisahkan sandbox dan production. Simpan kredensial hanya di Supabase secrets/secret store server-side. Jangan menaruh merchant key/private secret di frontend, log, atau dokumentasi publik. Jangan melakukan transaksi nyata tanpa persetujuan terpisah.

## Checklist
- [ ] Request/response cocok dengan dokumentasi resmi.
- [ ] Request/callback signature diuji valid dan invalid.
- [ ] Callback duplikat/paralel tidak menggandakan efek.
- [ ] Amount/reference mismatch ditolak atau dikarantina.
- [ ] Timeout, expiry, callback terlambat, dan status tak dikenal ditangani.
- [ ] Status frontend tidak dapat memaksa pembayaran menjadi berhasil.
- [ ] Tes menggunakan sandbox kecuali ada izin transaksi nyata.
