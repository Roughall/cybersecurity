# Checkpoint — INITIAL-BASELINE

Tanggal: 2026-11-16  
Repository: `Roughall/cybersecurity` · Branch: `main`  
Workstation pengguna: Kali Linux (versi belum dicatat)  
Status: **Persiapan dokumentasi — audit teknis belum dimulai**

## Fakta terkonfirmasi
- Repository ini disiapkan sebagai tempat dokumentasi hasil security assessment, bukan source code SIMRS.
- Pengguna menggunakan Kali Linux sebagai workstation pemeriksaan.
- Acuan: formulir SECURITY SELF-ASSESSMENT SIM FASKES, SPPTI-SEC-FORM-001 versi 1.1.
- Formulir memuat 10 aspek frontend dan 5 aspek backend/server.
- Repository dapat diakses melalui integrasi GitHub; branch aktif yang diperiksa adalah `main`.
- Izin integrasi GitHub yang terdeteksi mencakup Pull dan Push. Akses baca file telah diuji; perubahan pada checkpoint ini menjadi uji tulis melalui GitHub.

## Keputusan workflow terbaru
- Assessment tetap menjadi prioritas utama karena hasilnya ditargetkan untuk diserahkan pada 2026-11-16.
- Diagnostic & Evidence Collector direncanakan sebagai modul pendukung di repository yang sama, bukan repository terpisah.
- Rancangan awal modul: `diagnostics/` untuk hasil diagnostik workstation/troubleshooting; `scripts/diagnostic-collector/` untuk collector, sanitasi, dan generator laporan.
- Implementasi penuh collector ditunda sampai kebutuhan penyerahan assessment hari ini tidak terganggu. Untuk kebutuhan mendesak, gunakan pengumpulan output lokal secara sederhana dan tinjau/sanitasi sebelum berbagi.
- Log mentah dan artefak sensitif disimpan lokal pada media yang disetujui institusi. Hanya laporan yang telah disanitasi dan disetujui yang boleh masuk repository.
- Repository menjadi sumber dokumentasi bersama bagi AI agent yang diberi akses. Setiap agent wajib membaca checkpoint dan handoff terbaru sebelum bekerja. Akses repository tidak berarti akses ke workstation atau sistem target.
- Perubahan file harus dikoordinasikan agar tidak terjadi penulisan bersamaan; gunakan satu agent sebagai penulis untuk file yang sama pada satu waktu.


## Keputusan penyimpanan eviden dan akses AI — 2026-11-16
- Google Drive ditetapkan sebagai **rancangan pusat penyimpanan eviden** untuk screenshot, pesan error, log diagnostik, dan berkas pendukung assessment, terpisah dari repository GitHub.
- GitHub tetap menjadi pusat dokumentasi proyek: checkpoint, handoff, scope, metodologi, status kontrol, temuan yang telah ditinjau, dan laporan akhir. Bila diperlukan, dokumentasi GitHub hanya memuat referensi/tautan ke eviden Drive yang aksesnya dibatasi.
- Struktur folder Drive yang diusulkan: `00-ADMIN/`, `01-FRONTEND/`, `02-BACKEND/`, `03-DIAGNOSTICS/`, `04-AI-REVIEW/`, dan `05-FINAL-REPORT/`. Struktur ini masih berupa rancangan; belum dibuat atau diverifikasi.
- Alur yang direncanakan: Kali Linux menghasilkan screenshot/output → pemeriksaan dan sanitasi → unggah ke folder Drive yang disetujui institusi → AI yang memiliki konektor/akses sah meninjau file terpilih → hasil review dan status kontrol dicatat di GitHub.
- GitHub tidak otomatis meneruskan atau mengarahkan AI untuk membaca Google Drive. ChatGPT, Claude, dan AI lain harus memiliki koneksi/integrasi Drive masing-masing atau mekanisme akses yang disetujui. Link Drive saja tidak menjamin file dapat dibaca.
- Jenis akun Drive (pribadi atau Google Workspace RSUD), kebijakan institusi, koneksi Drive pada masing-masing AI, izin folder, dan mekanisme otomasi belum dikonfirmasi.
- Belum ada folder Drive dibuat, file eviden diunggah, konektor AI diuji, atau otomasi sinkronisasi diimplementasikan.
- Data mentah/sensitif tetap disimpan pada media yang disetujui institusi. Sebelum berbagi ke Drive atau AI, periksa dan samarkan data pasien, kredensial, token, cookie/session, alamat/hostname internal, serta informasi infrastruktur yang tidak diperlukan. Hindari akses publik/“Anyone with the link”; terapkan akses minimum sesuai kewenangan.
- Jangan menganggap Drive sebagai lokasi penyimpanan yang telah disetujui institusi sebelum pemilik data/penanggung jawab mengonfirmasi kebijakan penyimpanannya.

## Belum dikonfirmasi
Versi Kali/kernel/arsitektur; identitas dan versi target; arsitektur dan framework; lingkungan dan alamat target; izin tertulis dan rules of engagement; akses source code; akun uji/role; OS server, database, antivirus/EDR, firewall, TLS, webserver; jadwal dan kontak penanggung jawab. Jangan mengisi hal-hal ini dengan asumsi.

## Matriks status awal
Seluruh kontrol berstatus **BELUM DIVERIFIKASI**. Ini bukan pernyataan aman atau rentan.

| ID | Kontrol | Status |
|---|---|---|
| 1.1 | XSS pada form input | BELUM DIVERIFIKASI |
| 1.2 | SQL Injection pada form input | BELUM DIVERIFIKASI |
| 1.3 | Pembatasan percobaan login | BELUM DIVERIFIKASI |
| 1.4 | Lockout temporer setelah 3 kali gagal | BELUM DIVERIFIKASI |
| 1.5 | Warning “Gagal Login” | BELUM DIVERIFIKASI |
| 1.6 | Pesan gagal login tidak membedakan username/password | BELUM DIVERIFIKASI |
| 1.7 | Kompleksitas password | BELUM DIVERIFIKASI |
| 1.8 | Akses menu sesuai kewenangan | BELUM DIVERIFIKASI |
| 1.9 | Broken Access Control / akses data antar-user | BELUM DIVERIFIKASI |
| 1.10 | Library tidak vulnerable | BELUM DIVERIFIKASI |
| 2.1 | Antivirus server | BELUM DIVERIFIKASI |
| 2.2 | Firewall dan inbound rules | BELUM DIVERIFIKASI |
| 2.3 | TLS minimal 1.2 | BELUM DIVERIFIKASI |
| 2.4 | Keamanan versi webserver | BELUM DIVERIFIKASI |
| 2.5 | Keamanan framework/bahasa | BELUM DIVERIFIKASI |

## Batasan bukti
Analisis repository dokumentasi tidak membuktikan keamanan aplikasi/server. Source review memerlukan source code versi target; pemeriksaan server memerlukan eviden server; uji autentikasi/otorisasi memerlukan akun uji dan lingkungan yang disetujui. Scanner hanya memberi indikasi yang perlu divalidasi.

## Definisi status
- **PASS**: kontrol diuji pada cakupan jelas dan bukti mendukung pemenuhan kriteria.
- **NOT PASS**: pengujian mengonfirmasi kontrol tidak memenuhi kriteria/ada kelemahan.
- **BELUM DIVERIFIKASI**: belum diuji atau bukti/akses tidak memadai.
- **NOT APPLICABLE**: hanya dengan alasan dan persetujuan yang terdokumentasi.

## Langkah berikutnya
1. Prioritaskan penyelesaian assessment dan pengumpulan eviden yang tersedia untuk tenggat 2026-11-16.
2. Konfirmasi target, versi, lingkungan, pemilik, otorisasi, rules of engagement, dan batas pengujian.
3. Lakukan pemeriksaan hanya pada cakupan yang diizinkan; jangan mengarang hasil jika eviden tidak tersedia.
4. Catat hasil per kontrol, metode, waktu, versi tool, referensi eviden, keterbatasan, dan reviewer.
5. Setelah kebutuhan penyerahan terpenuhi, bangun Diagnostic Collector MVP: collector lokal read-only, sanitasi, metadata, dan laporan Markdown/JSON.
6. Verifikasi akses agent lain secara terpisah; akses GitHub tidak memberikan akses otomatis ke Kali Linux atau sistem target.

## Riwayat
| Tanggal | Checkpoint | Ringkasan |
|---|---|---|
| 2026-11-16 | INITIAL-BASELINE | Dokumentasi diinisialisasi; audit teknis belum dimulai. |
| 2026-11-16 | Workflow decision | Assessment diprioritaskan untuk tenggat hari ini; Diagnostic Collector direncanakan sebagai modul pendukung dalam repository yang sama dan implementasi penuh ditunda. |
