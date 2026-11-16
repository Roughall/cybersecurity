# AI Agent Handoff

## Misi
Mendukung pelaksanaan dan evaluasi Security Self-Assessment SIM Faskes berdasarkan SPPTI-SEC-FORM-001 v1.1, dengan dokumentasi yang dapat ditinjau manusia.

## Wajib dibaca
1. README.md
2. CHECKPOINT.md
3. AUDIT_SCOPE.md
4. docs/METHODOLOGY.md
5. Instruksi folder evidence/reports/scripts.

## Konteks
- Repository: `Roughall/cybersecurity`
- Fungsi: dokumentasi assessment, eviden tersanitasi, laporan, skrip pendukung.
- Workstation: Kali Linux; versi belum dikonfirmasi.
- Audit teknis belum dimulai; seluruh 15 kontrol masih BELUM DIVERIFIKASI pada checkpoint terakhir.
- Assessment diprioritaskan untuk target penyerahan 2026-11-16.
- Diagnostic & Evidence Collector direncanakan sebagai modul pendukung di repository ini; implementasi penuh ditunda sampai pekerjaan assessment mendesak tidak terganggu.

## Aturan wajib
- Baca checkpoint dan kondisi branch terbaru sebelum bekerja.
- Jangan menganggap status awal sebagai hasil audit.
- Jangan memberi status PASS tanpa eviden yang memadai.
- Pisahkan fakta teramati, pernyataan pemilik sistem, inferensi, dan rekomendasi.
- Catat versi tool, waktu, metode, target/cakupan, hasil, keterbatasan, dan referensi eviden.
- Jangan mengarang output, screenshot, CVE, versi, atau hasil scan.
- Jangan melakukan tindakan destruktif atau mengubah konfigurasi target.
- Dilarang melakukan pemindaian aktif, eksploitasi, brute force, atau uji autentikasi/otorisasi sebelum izin tertulis, target, jadwal, dan rules of engagement dikonfirmasi.
- Bila tindakan berpotensi mengganggu layanan, hentikan dan minta persetujuan.
- Jangan memasukkan data pasien, kredensial, token, private key, cookie/session, dump database, atau rahasia operasional ke repository.
- Jangan mengirim data sensitif ke layanan AI eksternal/scanner publik.
- Akses repository tidak sama dengan akses ke workstation Kali Linux atau sistem target.
- Hindari dua agent mengubah file yang sama secara bersamaan. Koordinasikan satu penulis per file dan tinjau diff sebelum commit.

## Rencana Diagnostic & Evidence Collector
Tujuan: mengurangi pengiriman screenshot/manual copy-paste dengan mengumpulkan output perintah ke file lokal terstruktur, kemudian menghasilkan laporan yang dapat ditinjau AI.

Tahapan:
1. MVP setelah tenggat assessment: collector lokal read-only untuk baseline workstation dan troubleshooting.
2. Simpan output mentah secara lokal pada media institusi yang disetujui.
3. Terapkan sanitasi sebelum membuat salinan untuk repository.
4. Hasil tersanitasi berupa Markdown/JSON dengan waktu, command, exit code, versi tool, dan batasan.
5. Tambahkan generator laporan dan dokumentasi penggunaan.
6. Jangan otomatis push log mentah atau menjalankan scan target.

Folder yang direncanakan:
- `diagnostics/baseline/`
- `diagnostics/troubleshooting/`
- `diagnostics/reports/`
- `scripts/diagnostic-collector/`

Folder tersebut adalah rancangan; jangan menganggap sudah dibuat atau skrip sudah tersedia sebelum commit implementasi.

## Multi-agent workflow
- Semua agent yang diberi akses harus membaca README.md, CHECKPOINT.md, AGENT_HANDOFF.md, AUDIT_SCOPE.md, dan metodologi.
- GitHub adalah sumber bersama untuk dokumentasi dan artefak tersanitasi.
- Agent wajib menyebutkan file/commit yang menjadi dasar analisis.
- Setiap perubahan harus memiliki ringkasan, alasan, dan commit yang dapat ditinjau.
- Jangan mengasumsikan agent lain memiliki akses terminal, akun, konektor, atau izin yang sama.
- Perubahan yang berpotensi mengubah status kontrol harus ditinjau manusia.

## Format temuan
Setiap temuan mencatat ID unik, kontrol terkait, judul/ringkasan, status verifikasi, aset/versi/lingkungan, metode/tanggal, evidence ID, dampak, severity dan alasannya, rekomendasi, keterbatasan, serta langkah retest.

## Format eviden
Nama: `EV-<CONTROL-ID>-<NN>-<YYYYMMDD>-<description>.<ext>`

Metadata: Evidence ID, kontrol, waktu/zona waktu, tool dan versi, target alias/cakupan, hasil, sanitasi, pengambil/reviewer, dan SHA-256 bila relevan.

## Hasil yang diharapkan
- Checkpoint dan changelog terbarui.
- Matriks 15 kontrol.
- Inventaris aset/komponen yang terkonfirmasi.
- Eviden tersanitasi dan dapat ditelusuri.
- Temuan, rekomendasi, keterbatasan, pertanyaan terbuka.
- Handoff untuk agent berikutnya.

## Sesi pertama
Hanya lakukan discovery lokal non-intrusif: versi Kali Linux, kernel, arsitektur, dan ketersediaan tools. Jangan scan jaringan/host target. Laporkan command dan output aktual, tanpa mengarang.
