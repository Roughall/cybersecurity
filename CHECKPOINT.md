# Checkpoint — INITIAL-BASELINE

Tanggal: 2026-11-16  
Repository: `Roughall/cybersecurity` · Branch: `main`  
Workstation pengguna: Kali GNU/Linux Rolling 2026.2 (output pengguna, 2026-11-16)  
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
Versi kernel/arsitektur; identitas dan versi target; arsitektur dan framework; lingkungan dan alamat target; izin tertulis dan rules of engagement; akses source code; akun uji/role; OS server, database, antivirus/EDR, firewall, TLS, webserver; jadwal dan kontak penanggung jawab. Jangan mengisi hal-hal ini dengan asumsi.

## Keputusan ruang lingkup assessment — 2026-11-16
- Pemeriksaan teknis terfokus sesuai arahan pengguna pada kontrol **1.10 (library vulnerable)**, yaitu bagian yang diberi instruksi eviden berwarna merah pada template.
- Pengumpulan/rekap eviden tetap dicatat untuk seluruh 15 kontrol agar laporan lengkap. Kontrol selain 1.10 tidak menjalani pengujian teknis dalam pekerjaan terfokus ini; statusnya tidak boleh dianggap PASS.
- Pemeriksaan 1.10 menggunakan repository dokumentasi `Roughall/cybersecurity`. Repository ini bukan source code aplikasi SIMRS dan saat ini tidak menyediakan manifest dependency atau SBOM yang dapat dipindai.
- Pencarian repository untuk `package.json`, `pom.xml`, `build.gradle`, `composer.json`, `requirements.txt`, `go.mod`, dan `Cargo.toml` tidak menghasilkan file yang cocok. Ini hanya menyatakan manifest tersebut tidak ditemukan melalui pencarian repository yang dilakukan; bukan bukti bahwa aplikasi tidak memakai library.
- Karena identitas dependency dan versinya tidak tersedia, pencocokan CVE/NVD belum dapat dilakukan secara valid. Kontrol 1.10 tetap **BELUM DIVERIFIKASI**.
- Laporan status dan matriks bukti dibuat di `reports/SECURITY-ASSESSMENT-STATUS-2026-11-16.md`.

## Matriks status assessment
Status seluruh 15 kontrol dicatat dalam laporan. Semua tetap **BELUM DIVERIFIKASI** karena repository dokumentasi tidak memuat bukti teknis aplikasi/server. Kontrol 1.10 telah diperiksa dari sisi ketersediaan artefak dependency, tetapi belum dapat diverifikasi dari sisi keamanan library.

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


## Hasil Tahap 1 — Baseline Kali Linux — 2026-11-16
Output command diberikan langsung oleh pengguna. Ini adalah hasil pemeriksaan workstation, bukan hasil scan dependency aplikasi.

| Komponen | Hasil aktual | Evaluasi terhadap template |
|---|---|---|
| OS | Kali GNU/Linux Rolling 2026.2 | Tercatat |
| GNU grep | 3.12 | Tersedia; dapat digunakan |
| ugrep | Tidak terpasang | Bukan blocker karena template menyebut grep/ugrep |
| Java | OpenJDK 25.0.5-ea (Debian build) | Tidak sesuai dengan OpenJDK 17 BellSoft Liberica yang ditentukan |
| Apache Ant | Tidak ditemukan | Belum tersedia |
| Apache NetBeans | Tidak ditemukan di PATH | Belum terverifikasi/tersedia |
| MariaDB client | 11.8.6-MariaDB, client 15.2 | Client tersedia; bukan bukti versi server database |

### Eviden
- Output terminal yang disampaikan pengguna pada 2026-11-16, pukul 10:32:06 WIB.
- Belum ada file screenshot atau log mentah yang diunggah ke repository. Simpan screenshot asli pada penyimpanan eviden yang disetujui; unggah hanya salinan tersanitasi.
- Baseline ini belum membuktikan library aplikasi bebas CVE.

### Langkah berikutnya
1. Jangan mengganti Java global atau memasang tool secara membabi buta.
2. Dapatkan path source code/build JAKSIMRS/KHANZA versi 17.002.20261026002 pada lingkungan pengembangan yang diizinkan.
3. Identifikasi library/JAR dan versi aktual dari source/build aplikasi.
4. Gunakan GNU grep/ugrep untuk penelusuran manual sesuai template.
5. Cocokkan setiap library dan versi dengan NVD/CVE serta advisory vendor; dokumentasikan URL dan status relevansinya.
6. Siapkan OpenJDK 17 BellSoft Liberica, Apache Ant, dan NetBeans bila diperlukan untuk build/review sesuai lingkungan yang disepakati. Hindari mengubah Java default workstation tanpa kebutuhan.
7. Verifikasi versi server MariaDB hanya jika akses yang sah dan kebutuhan pemeriksaan telah dikonfirmasi.

## Riwayat tambahan
| Tanggal | Checkpoint | Ringkasan |
|---|---|---|
| 2026-11-16 | STAGE-01-KALI-BASELINE | Kali 2026.2 teridentifikasi; GNU grep dan MariaDB client tersedia; Java tidak sesuai spesifikasi, Ant/NetBeans belum tersedia. |
