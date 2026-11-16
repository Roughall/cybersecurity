# Methodology

## Pendekatan
Lakukan assessment bertahap dengan dampak minimum:
1. Document review — telaah dokumen, arsitektur, kebijakan, konfigurasi yang diberikan secara sah.
2. Static review — analisis source code/dependency tanpa menyerang sistem.
3. Configuration review — verifikasi read-only pada konfigurasi yang diizinkan.
4. Dynamic validation — hanya pada lingkungan dan akun uji yang eksplisit diizinkan.

## Alur
1. Konfirmasi pemilik, target, versi, lingkungan, otorisasi, rules of engagement, jadwal, dan kontak.
2. Catat baseline Kali Linux dan versi tools.
3. Inventaris aset/komponen berdasarkan informasi pemilik.
4. Petakan eviden untuk setiap kontrol di AUDIT_SCOPE.md.
5. Kumpulkan bukti dengan metode berdampak paling rendah.
6. Validasi temuan dan false positive secara manual.
7. Catat risiko, rekomendasi, keterbatasan, dan retest.
8. Minta review manusia sebelum status final/laporan eksternal.

## Tools yang mungkin relevan
grep/ripgrep, Semgrep atau analyzer statis; Dependency-Check/OSV-Scanner/SBOM; Nmap hanya untuk discovery jaringan yang secara eksplisit diotorisasi; OpenSSL atau penguji TLS untuk endpoint yang disetujui; perintah read-only untuk service/firewall server. Ini daftar kandidat, bukan pernyataan tools telah terpasang atau dijalankan. Catat versi dan hasil aktual.

## Standar dan referensi
Acuan template: OWASP Top 10:2021, OWASP ASVS 4.0 (Authentication, Access Control, Validation/Injection), CVE/NVD. Gunakan advisory vendor resmi. Catat tanggal akses dan versi komponen. Jangan menganggap CVE berlaku tanpa memeriksa kondisi terdampak dan patch.

## Penilaian
Setiap temuan memuat kontrol, aset/versi, cakupan/prasyarat, metode/waktu, hasil/eviden, dampak, severity dan alasan, rekomendasi, batasan, serta retest. Severity (bila digunakan) bukan pengganti status checklist PASS/NOT PASS.

## Chain of custody dan sanitasi
Simpan file asli sensitif di penyimpanan institusi yang disetujui, bukan di repository ini. Hanya unggah salinan tersanitasi. Catat pengambil, penyunting, reviewer, dan hash SHA-256 bila relevan. Jangan unggah screenshot/log yang menampilkan pasien, token, kredensial, atau rahasia internal.

## Pelaporan
Laporan mencakup ringkasan, ruang lingkup, metode, hasil per kontrol, temuan, eviden, keterbatasan, rekomendasi, status retest, reviewer, dan persetujuan.
