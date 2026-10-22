# Asri Collection — Struktur Referensi Aplikasi

> **Status dokumen:** Referensi arsitektur dan struktur direktori.  
> **Penting:** Tree di bawah adalah struktur target yang diusulkan, bukan inventaris file yang sudah ada. Jangan menganggap file atau folder telah diimplementasikan sebelum memeriksa repository aktual.

## 1. Tujuan

Dokumen ini menjadi acuan bersama bagi developer dan AI saat membaca, mengaudit, merencanakan, atau mengembangkan aplikasi Asri Collection.

Prinsipnya:
- Pertahankan arsitektur yang telah disepakati kecuali ada persetujuan perubahan.
- Audit struktur dan implementasi aktual sebelum mengusulkan pemindahan, penghapusan, atau pembuatan file.
- Pisahkan frontend, backend Supabase, pengujian, dan dokumentasi.
- Dokumentasi ini sendiri tidak memberikan izin untuk mengubah kode, database, secrets, konfigurasi aktif, atau deployment.

## 2. Stack dan batas arsitektur

Target arsitektur referensi:
- Frontend: React, Vite, TypeScript, Tailwind CSS, React Router, lucide-react.
- State keranjang: Zustand dengan persistensi localStorage.
- Backend: Supabase Database dan Edge Functions.
- Pembayaran: Duitku POP; proses sensitif dan verifikasi pembayaran dilakukan di backend.
- UI: mobile-first/mobile-only sesuai baseline desain proyek.
- Halaman dibagi menjadi `MainPages` dan `StandalonePages`, dengan `MainLayout` dan `StandaloneLayout`.

Detail versi paket, konfigurasi, schema database, dan nama fungsi yang benar-benar aktif harus diverifikasi dari repository serta proyek Supabase aktual.

## 3. Contoh struktur tree target

```text
asricollectionapps/
├── public/
│   ├── favicon.svg
│   └── images/
├── src/
│   ├── app/
│   │   ├── App.tsx
│   │   ├── router.tsx
│   │   └── providers.tsx
│   ├── layouts/
│   │   ├── MainLayout.tsx
│   │   └── StandaloneLayout.tsx
│   ├── pages/
│   │   ├── MainPages/
│   │   │   ├── HomePage.tsx
│   │   │   ├── CategoryPage.tsx
│   │   │   ├── ProductDetailPage.tsx
│   │   │   ├── CartPage.tsx
│   │   │   ├── CheckoutPage.tsx
│   │   │   ├── PaymentPage.tsx
│   │   │   └── AccountPage.tsx
│   │   └── StandalonePages/
│   │       ├── LoginPage.tsx
│   │       ├── RegisterPage.tsx
│   │       ├── OrderDetailPage.tsx
│   │       └── NotFoundPage.tsx
│   ├── components/
│   │   ├── navigation/
│   │   ├── products/
│   │   ├── cart/
│   │   ├── checkout/
│   │   └── payment/
│   ├── features/
│   │   ├── products/
│   │   ├── cart/
│   │   ├── orders/
│   │   ├── shipping/
│   │   └── payments/
│   ├── services/
│   │   ├── supabase.ts
│   │   ├── products.service.ts
│   │   ├── orders.service.ts
│   │   └── payments.service.ts
│   ├── stores/
│   │   └── cart.store.ts
│   ├── hooks/
│   ├── types/
│   ├── utils/
│   ├── styles/
│   └── main.tsx
├── supabase/
│   ├── config.toml
│   ├── migrations/
│   ├── functions/
│   │   ├── duitku-create-invoice/
│   │   │   └── index.ts
│   │   ├── duitku-callback/
│   │   │   └── index.ts
│   │   ├── get-payment-status/
│   │   │   └── index.ts
│   │   ├── reconcile-payment/
│   │   │   └── index.ts
│   │   └── expire-pending-payments/
│   │       └── index.ts
│   └── tests/
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/
│   ├── architecture.md
│   ├── database-schema.md
│   ├── payment-flow.md
│   ├── security.md
│   └── testing.md
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.ts
├── tailwind.config.ts
├── eslint.config.js
├── README.md
└── STRUCTURE.md
```

Nama file di atas adalah contoh target. Jangan membuat seluruh daftar secara otomatis hanya karena tercantum di dokumen ini.

## 4. Tanggung jawab direktori

| Direktori | Tanggung jawab |
|---|---|
| `src/app/` | Bootstrap aplikasi, provider, dan konfigurasi routing |
| `src/layouts/` | Layout utama dan halaman mandiri |
| `src/pages/MainPages/` | Halaman yang menggunakan navigasi/layout utama |
| `src/pages/StandalonePages/` | Halaman yang menggunakan layout terpisah |
| `src/components/` | Komponen UI yang dapat digunakan ulang |
| `src/features/` | Logika per domain fitur aplikasi |
| `src/services/` | Adapter komunikasi frontend dengan API/backend |
| `src/stores/` | State client-side, termasuk keranjang |
| `src/types/` | Tipe TypeScript bersama |
| `supabase/functions/` | Backend Edge Functions |
| `supabase/migrations/` | Perubahan schema database yang terversi |
| `supabase/tests/` | Pengujian yang terkait database/backend |
| `tests/` | Unit, integrasi, dan end-to-end test |
| `docs/` | Dokumentasi desain teknis dan prosedur |

## 5. Prinsip keamanan pembayaran

- Kunci merchant dan API secret Duitku hanya disimpan sebagai Supabase secrets atau konfigurasi server yang aman; jangan pernah memasukkannya ke frontend atau repository.
- Pembuatan invoice dilakukan oleh backend setelah memvalidasi pesanan dan nominal.
- Callback Duitku wajib memverifikasi signature sesuai dokumentasi resmi, memvalidasi data transaksi, dan menangani callback berulang secara idempoten.
- Redirect browser atau pesan sukses dari frontend bukan bukti final bahwa pembayaran berhasil.
- Perubahan status pembayaran dan pengurangan stok harus mengikuti transaksi backend yang aman dan konsisten.
- Pembayaran yang datang setelah reservasi berakhir harus masuk proses rekonsiliasi; jangan otomatis mengonfirmasi stok yang sudah tidak tersedia.
- Jangan mengubah database, secrets, RLS/grants, atau deployment hanya berdasarkan rekomendasi dalam dokumen ini.

Nama fungsi dalam tree adalah rancangan referensi. Keberadaan, konfigurasi JWT, dan implementasi aktualnya harus diaudit sebelum perubahan apa pun.

## 6. Konvensi penamaan

- Komponen React dan halaman: `PascalCase.tsx`, misalnya `ProductDetailPage.tsx`.
- Hooks: awali dengan `use`, misalnya `useCart.ts`.
- Services: akhiri dengan `.service.ts`, misalnya `orders.service.ts`.
- Store: gunakan akhiran `.store.ts`, misalnya `cart.store.ts`.
- Edge Functions: gunakan nama direktori yang deskriptif dan konsisten dengan kontrak API.
- Nama dan pola yang telah ada tidak boleh diubah secara massal tanpa audit dampak dan persetujuan.

## 7. Status struktur

Gunakan label berikut saat melakukan audit:
- **REFERENSI** — tercantum dalam dokumen ini sebagai target.
- **SUDAH ADA** — keberadaan file/folder telah diverifikasi di branch yang diaudit.
- **BELUM ADA** — telah diperiksa dan tidak ditemukan di lokasi/branch tersebut.
- **PERLU VERIFIKASI** — bukti belum cukup untuk menetapkan status.

Jangan mengubah label menjadi “SUDAH ADA” berdasarkan tree contoh saja.

## 8. Prosedur sebelum perubahan

1. Pastikan repository, branch, dan commit target.
2. Petakan tree aktual dan baca file yang relevan.
3. Bandingkan implementasi aktual dengan dokumen referensi ini.
4. Laporkan gap, dependensi, risiko, dan rencana perubahan.
5. Minta persetujuan eksplisit sebelum implementasi.
6. Uji perubahan yang disetujui dan laporkan bukti hasilnya.
7. Deployment, migration database aktif, dan perubahan secrets memerlukan persetujuan terpisah.

## 9. Pemeliharaan dokumen

Perbarui dokumen ini jika struktur target disepakati berubah. Catat perubahan yang bermakna dalam commit message atau dokumentasi proyek. Dokumen ini tidak menggantikan README, spesifikasi database, dokumentasi API, maupun hasil audit implementasi aktual.
