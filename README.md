# Asri Collection — Repository Dokumentasi

Repository ini menyimpan acuan untuk penelitian, audit, perancangan, dan pengembangan terkontrol proyek Asri Collection. Dokumen target atau prompt tidak membuktikan bahwa fitur telah diterapkan pada repository aplikasi.

## Status dokumen
- `0.md`: kandidat master prompt V3.0.0 untuk alur kerja engineering terkontrol.
- `STRUCTURE.md`: referensi struktur target; bukan bukti struktur aplikasi aktual.
- `modules/`: modul tematik pendukung master prompt.
- Versi kandidat V3.0.0 menggambarkan rancangan modular; keputusan penerapan/penetapan sebagai versi aktif harus mengikuti proses review proyek.

## Struktur dokumentasi

```text
asc/
├── README.md
├── 0.md
├── STRUCTURE.md
└── modules/
    ├── role.md
    ├── instruction.md
    ├── constraint.md
    ├── project-context.md
    ├── audit.md
    ├── security.md
    ├── commerce-domain.md
    ├── payment-duitku.md
    ├── testing.md
    └── reporting.md
```

## Indeks modul
| File | Fungsi |
|---|---|
| [role.md](modules/role.md) | Peran dan standar kerja |
| [instruction.md](modules/instruction.md) | Workflow, sumber kebenaran, dan sumber resmi |
| [constraint.md](modules/constraint.md) | Approval gates dan batas perubahan |
| [project-context.md](modules/project-context.md) | Konteks awal yang harus diverifikasi |
| [audit.md](modules/audit.md) | Audit repository/sistem dan standar bukti |
| [security.md](modules/security.md) | Keamanan aplikasi dan data |
| [commerce-domain.md](modules/commerce-domain.md) | Order, pembayaran, reservasi, stok, pengiriman |
| [payment-duitku.md](modules/payment-duitku.md) | Integrasi Duitku POP |
| [testing.md](modules/testing.md) | Tes, verifikasi, dan kesiapan rilis |
| [reporting.md](modules/reporting.md) | Format laporan, prioritas, penutupan tahap |

## Workflow yang disarankan
1. Identifikasi repository, branch, commit, environment, dan scope.
2. Audit read-only dengan bukti konkret.
3. Tinjau temuan dan rekomendasi.
4. Sepakati requirement final.
5. Minta persetujuan eksplisit sebelum implementasi.
6. Terapkan perubahan minimal sesuai approval, uji, dan verifikasi.

## Batas persetujuan
Audit tidak mengizinkan edit; persetujuan requirement bukan izin implementasi. Push/merge, migration/database aktif, secrets, cloud resources, deployment, dan pembayaran nyata memerlukan persetujuan terpisah. Baca [constraint.md](modules/constraint.md).

## Sumber Duitku
- [Dokumentasi POP](https://docs.duitku.com/pop/id/)
- [Dokumentasi API](https://docs.duitku.com/api/id/)
- [FAQ Duitku](https://www.duitku.com/frequently-asked-questions/)

## Catatan
Konteks aplikasi harus diverifikasi pada repository aplikasi yang benar. Jangan menyimpulkan kondisi produksi dari dokumen ini saja.
