# Application & Data Security

## Prinsip
Terapkan least privilege, defense in depth, validasi server-side, kerahasiaan secrets, integritas data, dan logging yang tidak membocorkan informasi sensitif.

## Identitas dan akses
- Verifikasi autentikasi dan otorisasi server-side untuk operasi yang memerlukannya.
- Anon key bukan mekanisme otorisasi; jangan mengekspos service-role key ke frontend.
- Jika aplikasi tidak memakai Supabase Auth, petakan mekanisme identitas alternatif dan risikonya.
- Batasi grants, RLS, Storage policies, dan fungsi privileged.
- Untuk SECURITY DEFINER, tinjau pemilik, hak eksekusi, search_path, dan input yang dikendalikan pemanggil.

## Validasi dan data
Validasi tipe, format, rentang, panjang, relasi, dan state transition di server. Hitung ulang harga, diskon, ongkir, total, dan stok dari sumber tepercaya. Gunakan query berparameter/API aman. Hindari mass assignment, IDOR, replay, race condition, dan operasi ganda. Minimalkan data pribadi.

## Secrets dan log
Simpan kredensial provider dan service-role hanya di secret store server-side. Jangan menaruh secret dalam source, log, error publik, commit, atau bundle frontend. Audit nama secret dan referensi kode tanpa menyalin nilainya. Log harus mendukung audit/rekonsiliasi tanpa token, signature sensitif, atau data personal berlebihan.

## Integritas transaksi
Order/payment/reservation/inventory harus memiliki batas transaksi atomik yang jelas. Verifikasi signature callback, reference/amount/currency sesuai kontrak, dan idempotensi. Terapkan kontrol concurrency dan validasi transisi status. Pembayaran terlambat atau konflik stok masuk rekonsiliasi, bukan konfirmasi otomatis.

Bedakan kerentanan yang terbukti dari indikasi dan rekomendasi penguatan. Sertakan bukti, prasyarat, dampak, mitigasi, dan tes; jangan menyimpulkan seluruh sistem aman dari satu tes/file.
