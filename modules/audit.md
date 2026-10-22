# Repository & System Audit

## Tujuan
Membangun gambaran kondisi aktual berbasis bukti sebelum merekomendasikan atau mengubah sistem.

## Audit repository
Periksa sesuai scope: file tree, branch/commit, package dan lockfile, entry point, routing, layout, halaman, komponen, hooks, state, API clients, seluruh pemanggil lama/baru, validasi, loading/error, double submission, kebocoran data sensitif, dependencies, scripts, CI, build, lint, tests, dan penggunaan environment variables tanpa menampilkan nilainya.

## Audit commerce dan pembayaran
Petakan alur ujung ke ujung: frontend → API/Edge Function → database → payment provider → callback/webhook → verifikasi status → order/inventory. Identifikasi request/response, referensi transaksi, snapshot harga, total, ongkir, status, expiry, idempotency, retry, dan titik kegagalan.

## Audit Supabase
Periksa schema aktif vs migration; tabel/kolom/tipe/constraints/indexes/FK/triggers; RLS/policies/grants/roles; RPC dan SECURITY DEFINER/search_path; Edge Functions dan JWT config; nama secrets dan referensi kode; Storage bucket/path/MIME/size/policies; pemanggil frontend/backend dan tes regresi. Migration historis bukan bukti schema aktif. Nyatakan bila akses schema aktif tidak tersedia.

## Format setiap temuan (wajib)
1. ID; 2. prioritas P0–P4; 3. kategori; 4. status bukti; 5. referensi konkret; 6. perilaku aktual; 7. perilaku yang diharapkan; 8. dampak/risiko; 9. rekomendasi; 10. dependensi dan tes verifikasi.

Status bukti: TERVERIFIKASI, INDIKASI, ASUMSI, BELUM DIKETAHUI, atau TERHAMBAT. Jangan menyebut kemungkinan sebagai fakta.

## Penutupan audit
Laporkan cakupan diperiksa/tidak diperiksa, hasil terverifikasi, temuan prioritas, risiko residual, keputusan yang diperlukan, opsi berikutnya, rekomendasi terbaik, prasyarat, scope, dan persetujuan. Audit read-only tidak boleh berubah diam-diam menjadi implementasi.
