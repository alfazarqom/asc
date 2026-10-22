# Constraints & Approval Gates

**Status:** Kandidat V3.0.0. Modul kanonis untuk batas izin.

## Matriks persetujuan

| Tindakan | Izin minimum |
|---|---|
| Membaca dan audit read-only | Permintaan audit yang jelas |
| Menyusun draft/diff/SQL tanpa menjalankan | Permintaan penyusunan |
| Mengedit file lokal dan menjalankan tes lokal | Persetujuan implementasi lokal |
| Menulis file/commit ke GitHub | Persetujuan eksplisit untuk perubahan repository |
| Push, merge, atau mengubah branch target | Persetujuan eksplisit terpisah |
| Migration atau perubahan database aktif | Persetujuan terpisah yang menyebut target dan migration |
| Mengubah secrets, RLS/grants, atau konfigurasi keamanan aktif | Persetujuan terpisah dan rencana verifikasi |
| Mengubah cloud resources atau Storage aktif | Persetujuan terpisah |
| Deploy staging/production | Persetujuan deployment eksplisit |
| Transaksi/pembayaran nyata | Persetujuan terpisah; bukan tes biasa |

Persetujuan hanya berlaku untuk tindakan dan cakupan yang disebutkan. Jangan menyimpulkan izin lebih luas.

## Batas perubahan
- Pertahankan stack, struktur, dan kontrak kecuali perubahan disetujui.
- Jangan menghapus sistem lama tanpa audit pemanggil dan dependensi.
- Jangan melakukan migration, mengubah secrets, deploy, atau transaksi nyata hanya karena patch kode disetujui.
- Jangan mengungkap nilai secret; verifikasi nama dan referensi tanpa membocorkan nilainya.
- Jika perubahan di luar scope diperlukan, laporkan dan minta persetujuan.

## Integritas transaksi dan pembayaran
- Perubahan order, payment, reservasi, dan stok yang saling terkait harus konsisten dan atomik menggunakan transaksi database atau RPC terkontrol yang sesuai.
- Jangan mengganti transaksi atomik dengan beberapa request frontend yang dapat gagal di tengah.
- Callback wajib diverifikasi, divalidasi, dan idempoten.
- Redirect/return, query parameter, atau status frontend bukan bukti pembayaran.
- Pembayaran setelah reservasi habis masuk rekonsiliasi; jangan otomatis mengonfirmasi stok yang tidak tersedia.
- Cegah pengurangan stok ganda dan transisi status yang tidak sah.

## Pelaporan tes
Gunakan LULUS, GAGAL, BELUM DIUJI, TERHAMBAT, atau TIDAK BERLAKU. Jangan klaim tes lulus bila tidak dijalankan atau buktinya tidak tersedia.
