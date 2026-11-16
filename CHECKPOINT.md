# Checkpoint — INITIAL-BASELINE

Tanggal: 2026-11-16  
Repository: `Roughall/cybersecurity` · Branch: `main`  
Workstation pengguna: Kali GNU/Linux Rolling 2026.2 (output pengguna, 2026-11-16)  
Status: **Assessment teknis terfokus Point 1.10 sedang berjalan; hasil scanner SCA belum tersedia**

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


## Update checkpoint — hasil pemeriksaan paket distribusi SIMRS dan persiapan SCA — 2026-11-16

### Perubahan status dan koreksi cakupan
- Pemeriksaan teknis Point 1.10 telah berlanjut dari review repository dokumentasi ke pemeriksaan statis paket distribusi SIMRS yang tersedia secara lokal di workstation pengguna.
- Lokasi paket yang diperiksa: `/run/media/kali/DATA/KhanzaHMSWindows`. Paket tersebut merupakan distribusi aplikasi, bukan source tree/build project lengkap.
- Inventaris awal menemukan **867 file JAR**. Hasil ini adalah jumlah file JAR pada folder distribusi saat inventaris dibuat; bukan jumlah dependency unik atau jumlah komponen yang sudah terverifikasi.
- Tidak ditemukan `build.xml`, `pom.xml`, `ivy.xml`, `manifest.mf` pada tingkat project, atau `gradle.properties` dalam pemeriksaan awal. Karena itu, source-level white-box review dan rekonstruksi dependency build belum dilakukan.
- Pernyataan di bagian sebelumnya bahwa belum ada artefak dependency pada repository dokumentasi tetap benar untuk repository GitHub, tetapi tidak lagi menggambarkan seluruh bahan yang tersedia: paket distribusi lokal kemudian diperiksa secara terpisah.

### Hasil pemeriksaan statis yang telah dilakukan
1. **Dependency discovery/inventory:** 867 JAR terdaftar dalam `jar-inventory.txt`.
2. **Metadata dan manifest:** metadata manifest dikumpulkan ke `jar-metadata.txt` dan `jar-metadata-all.txt`. Ditemukan beberapa versi library lama/beragam, termasuk Log4j 1.2.15/1.2.17, Jackson 1.9.0 dan 2.1.x/2.2.3, Spring Core 2.5.5/5.1.4, Spring Web 3.1.0.M2/3.2.1, Apache POI 3.0.2-beta1/3.2/3.7/3.9/4.1.0, JasperReports 3.7.0/5.1.2/6.8.0/6.20.0, serta MySQL Connector/J 5.1.39/5.1.47.
3. **Hash dan duplikasi:** salinan Connector/J 5.1.47 pada beberapa direktori memiliki SHA-256 yang sama: `a98bd1d92dc9007d2b95a9695923d2c7c6f1c3e8bdcf2cfac47ae1aa9b156d75`. Salinan updater Connector/J 5.1.39 memiliki SHA-256 `75adfb38992d3c0cf119bff7123fdb05019d376ec31e4375676d4df3b9ec0d28`.
4. **Manifest aplikasi:** `SIMRSKhanza.jar` merujuk ke `lib/mysql-connector-java-5.1.47.jar` melalui Class-Path; file tersebut tersedia pada lokasi yang dirujuk.
5. **Static dependency analysis:** perintah `jdeps --multi-release base -verbose:class --class-path "$TARGET/lib/*" "$TARGET/SIMRSKhanza.jar"` berhasil (exit status 0). Output berisi 283.149 baris; terhitung 4.383 referensi JDBC, 0 kelas not-found, dan 466 split-package warnings. Salah satu referensi langsung yang teramati: `fungsi.koneksiDB -> com.mysql.jdbc.jdbc2.optional.MysqlDataSource`, dipetakan ke Connector/J 5.1.47.
6. **Log4j inspection:** kelas `SocketServer.class` ada pada salinan Log4j 1.2.15/1.2.17. Pencarian konfigurasi/literal yang telah dilakukan tidak menemukan referensi eksplisit ke SocketServer; ini bukan bukti bahwa seluruh jalur penggunaan atau risiko Log4j tidak ada.
7. **Runtime:** pemeriksaan proses Java saat itu tidak menemukan proses Java aktif. Oleh karena itu, pemuatan library saat runtime belum dibuktikan.

### Penilaian sementara Point 1.10
- Terdapat **potential finding** pada penggunaan MySQL Connector/J 5.1.47. Versi dan referensi statisnya teridentifikasi, tetapi kecocokan advisory/CVE, kondisi konfigurasi, exploitability, patch/backport, dan konteks runtime masih harus divalidasi.
- Rentang versi CVE yang hanya berdasarkan nomor versi tidak cukup untuk menyatakan aplikasi exploitable. Jangan menetapkan PASS atau NOT PASS final hanya dari hasil ini.
- Status kontrol 1.10 untuk saat ini: **BELUM DIVERIFIKASI — terdapat potential finding yang menunggu validasi CVE/advisory dan cross-check scanner**.
- Source-code review, verifikasi dependency runtime, pemeriksaan Bootstrap/jQuery, dan pemeriksaan komponen non-JAR belum lengkap.

### Workstation dan kesiapan tools — output pengguna 2026-11-16
- Kali GNU/Linux Rolling 2026.2, x86_64.
- OpenJDK 25.0.5-ea (Debian build); `jdeps` 25.0.5-ea.
- Memori: total 15 GiB, available sekitar 2,2 GiB; swap 15 GiB, tersedia sekitar 10 GiB.
- Filesystem root: 452 GB total, 337 GB tersedia (22% terpakai).
- OSV-Scanner, OWASP Dependency-Check, dan CycloneDX CLI **belum terpasang** pada saat pemeriksaan kesiapan.
- Target tetap read-only. Tools dan hasil pemeriksaan ditempatkan di direktori kerja/evidence terpisah di home pengguna.

### Tahap berikutnya — belum dijalankan
1. Siapkan dan verifikasi instalasi OSV-Scanner V2.
2. Siapkan dan verifikasi OWASP Dependency-Check serta pembaruan database NVD.
3. Tentukan cara menghasilkan SBOM CycloneDX dari JAR/metadata paket; tandai komponen yang tidak dapat diidentifikasi, jangan mengklaim SBOM lengkap tanpa validasi.
4. Jalankan scan terhadap salinan/target read-only, simpan laporan HTML/JSON, SBOM, log, versi dan hash tool.
5. Cross-check hasil OSV dan Dependency-Check; validasi manual temuan berdasarkan komponen, versi, hash, rentang versi terdampak, advisory vendor, konfigurasi, dan kemungkinan false positive.
6. Simpan eviden mentah secara lokal pada media yang disetujui institusi; hanya unggah laporan tersanitasi ke GitHub. Jangan unggah JAR proprietary, source code, kredensial, data pasien, atau log sensitif.

### Riwayat tambahan
| Tanggal | Checkpoint | Ringkasan |
|---|---|---|
| 2026-11-16 | STAGE-02-DISTRIBUTION-STATIC-REVIEW | Inventaris 867 JAR; metadata/manifest dan hash; jdeps berhasil; Connector/J 5.1.47 dirujuk SIMRSKhanza.jar; potential finding menunggu validasi. |
| 2026-11-16 | STAGE-03-SCA-TOOLS-PREPARATION | Kondisi Kali diverifikasi; ketiga tool SCA/SBOM belum terpasang; instalasi dan pemindaian belum dilakukan. |


## Update checkpoint — SCA full distribution dan pemetaan OSV — 2026-11-16

### Status pekerjaan Point 1.10
Pemeriksaan statis dan SCA terhadap paket distribusi lokal SIMRS Khanza telah dilanjutkan. Target lokal: `/run/media/kali/DATA/KhanzaHMSWindows`. Target diperiksa secara read-only; artefak mentah tetap berada di workstation pengguna dan tidak diunggah ke repository.

### Hasil terkonfirmasi dari output pengguna
- Inventaris awal: **867 file JAR**.
- Syft menghasilkan SBOM CycloneDX untuk direktori `lib`: **574 paket terindeks**.
- Syft menghasilkan SBOM CycloneDX full distribution (dengan pengecualian cache JCEF dan direktori manual printer): **2.044 komponen**.
- OSV Scanner memproses **1.037 paket** dari SBOM full; **77 paket lokal/unscannable** difilter. Warning komponen tanpa CPE/PURL berarti tidak dapat dicocokkan sebagai package oleh OSV, bukan bukti vulnerability.
- Hasil OSV JSON: **163 rekaman vulnerability pada 44 paket/versi**, dengan **131 CVE unik**.
- Pemetaan awal hanya berhasil 106/163. Penyebabnya adalah skrip memakai field SBOM `group` yang kosong, padahal identitas Maven tersedia dalam PURL.
- Skrip pemetaan v2 membaca group/artifact/version dari PURL dan menghasilkan **163/163 rekaman terpetakan**, **0 belum terpetakan**, **44 kombinasi paket/versi**, dan **131 CVE unik**.
- File register lokal: `evidence/point-1.10/osv/cve-priority-register.csv`; file pemetaan: `evidence/point-1.10/osv/osv-location-mapping-v2.txt`. File-file ini belum dimasukkan ke GitHub karena merupakan output lokal dan belum melalui sanitasi/review.
- Inventaris aset web di luar JAR setelah mengecualikan cache browser dan manual printer: 9 file HTML/CSS dan tidak ditemukan file JS eksternal pada cakupan tersebut.
- Inventaris isi arsip JAR: 1.072 entri JS/CSS/HTML; mencakup dokumentasi, contoh, aset runtime, dan duplikasi, sehingga bukan 1.072 library runtime unik.
- jQuery 3.3.1 dan RequireJS 2.3.6 teridentifikasi pada JAR terpisah; identitas dan SHA-256 salinan telah dibandingkan. Keberadaan aset dalam JAR belum membuktikan pemuatan runtime.
- Dependency-Check 13.0.0 terpasang, tetapi pembaruan NVD gagal karena API key kosong/tidak tersedia. Pengguna menyatakan API key masih dalam validasi. CISA KEV berhasil diperbarui. Belum ada hasil scan Dependency-Check yang dapat dipakai sebagai cross-check.
- OSV-Scanner 2.7.1, Syft 1.57.1, dan OSV-Scalibr 0.5.3 terpasang dan versi diverifikasi.

### Penilaian sementara
- OSV adalah hasil pencocokan otomatis, bukan bukti final bahwa seluruh 163 rekaman dapat dieksploitasi pada SIMRS.
- Pemetaan 100% berarti setiap rekaman OSV dapat dihubungkan ke lokasi JAR pada SBOM; bukan 100% kerentanan terkonfirmasi.
- Sejumlah CVE sudah menunjukkan indikasi rentang versi cocok; sejumlah lainnya berpotensi false positive karena versi berada di luar rentang advisory. Contoh awal yang perlu ditandai untuk validasi: Commons IO 1.3.1 terhadap CVE-2021-29425 dan Jackson Databind 2.2.3 terhadap CVE-2026-59889.
- Kandidat prioritas untuk validasi advisory dan kondisi penggunaan: Jackson Databind 2.2.3, Log4j 1.2.15/1.2.17, Spring Framework, Apache POI, Apache Batik, Commons BeanUtils, Commons Compress, PDFBox, Xalan, Apache Ant, dan Bouncy Castle.
- Bouncy Castle terdeteksi sebagai versi `154`; perlu konfirmasi metadata JAR untuk memastikan interpretasi versi (kemungkinan 1.54) sebelum menetapkan kecocokan CVE.
- Log4j 1.x sudah EOL, tetapi prasyarat setiap CVE (mis. SocketServer/appender tertentu) tetap harus diverifikasi; keberadaan class di JAR tidak membuktikan konfigurasi/runtime aktif.
- Status kontrol 1.10: **BELUM DIVERIFIKASI — hasil SCA menunjukkan indikasi kerentanan; validasi rentang versi, advisory vendor, patch/backport, penggunaan runtime, dan false positive belum selesai.**
- Keempat belas kontrol lainnya tetap BELUM DIVERIFIKASI; pemeriksaan terfokus 1.10 tidak membuktikan kontrol lain.

### Artefak lokal utama
- `cyclonedx/simrs-khanza-lib.cdx.json`
- `cyclonedx/simrs-khanza-full.cdx.json`
- `osv/osv-full-results.json`
- `osv/osv-location-mapping-v2.txt`
- `osv/cve-priority-register.csv`
- `dependency-check/` (belum ada hasil scan final)
- `jar-inventory.txt`, `jar-metadata.txt`, `jar-metadata-all.txt`, `jdeps-full-output.txt`, `jar-web-assets-inventory.tsv`

### Langkah berikutnya
1. Validasi CVE berdasarkan advisory resmi, rentang versi affected/fixed, status patch/backport, dan prasyarat eksploitasi.
2. Periksa metadata JAR untuk versi yang ambigu, khususnya Bouncy Castle 154.
3. Verifikasi apakah komponen digunakan oleh aplikasi/runtime dan apakah jalur input/konfigurasi yang relevan aktif; jangan menganggap keberadaan JAR sebagai exploitability.
4. Setelah NVD API key disetujui, jalankan pembaruan database dan Dependency-Check untuk cross-check.
5. Buat register final dengan kategori confirmed affected, potential/conditional, false positive/not affected, dan undetermined; catat alasan dan sumber tiap keputusan.
6. Pertahankan eviden mentah lokal; hanya laporan tersanitasi yang telah direview boleh masuk GitHub.

### Riwayat tambahan
| Tanggal | Checkpoint | Ringkasan |
|---|---|---|
| 2026-11-16 | STAGE-04-FULL-SBOM-OSV | Full SBOM 2.044 komponen; OSV menghasilkan 163 rekaman pada 44 paket/versi, 131 CVE unik. |
| 2026-11-16 | STAGE-05-OSV-LOCATION-MAPPING | Pemetaan PURL v2 berhasil 163/163; 0 rekaman belum terpetakan. |
