# Security Self-Assessment SIM Faskes

Repository ini merupakan pusat dokumentasi, koordinasi, eviden, dan pelaporan Security Self-Assessment SIM Faskes RSUD Kramat Jati.

## Status awal
- Checkpoint: `INITIAL-BASELINE`
- Status audit: **Belum dimulai**
- Workstation: Kali Linux (versi dan konfigurasi belum dicatat)
- Acuan: SPPTI-SEC-FORM-001 versi 1.1
- Target aplikasi yang direncanakan: SIM Faskes JAKSIMRS/KHANZA; identitas dan versi target harus dikonfirmasi.

## Mulai dari sini
1. Baca [CHECKPOINT.md](CHECKPOINT.md).
2. Baca [AGENT_HANDOFF.md](AGENT_HANDOFF.md) sebelum AI agent bekerja.
3. Baca [AUDIT_SCOPE.md](AUDIT_SCOPE.md).
4. Ikuti [docs/METHODOLOGY.md](docs/METHODOLOGY.md).
5. Simpan hanya eviden tersanitasi di `evidence/` dan laporan di `reports/`.

## Prinsip keamanan
- Repository ini bukan tempat source code SIMRS atau data produksi.
- Dilarang menyimpan data pasien, kredensial, token, private key, dump database, atau konfigurasi rahasia.
- Jangan melakukan pemindaian aktif, eksploitasi, brute force, fuzzing, atau pengujian produksi tanpa otorisasi tertulis dan rules of engagement.
- Jangan menyatakan PASS hanya karena tidak ditemukan temuan.
- Gunakan **BELUM DIVERIFIKASI** jika bukti belum cukup.
- Catat metode, cakupan, waktu, versi tool, hasil, keterbatasan, dan referensi eviden.

## Struktur
```
README.md
CHECKPOINT.md
AGENT_HANDOFF.md
AUDIT_SCOPE.md
CHANGELOG.md
.gitignore
docs/METHODOLOGY.md
evidence/README.md
reports/README.md
scripts/README.md
```

Lihat [CHANGELOG.md](CHANGELOG.md) untuk riwayat perubahan.
