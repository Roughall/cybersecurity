# Security Self-Assessment SIM Faskes — Status & Evidence Register

**Tanggal:** 16 November 2026  
**Acuan:** SPPTI-SEC-FORM-001 versi 1.1  
**Repository dokumentasi:** `Roughall/cybersecurity`  
**Workstation:** Kali GNU/Linux Rolling 2026.2 (output baseline dari pengguna, 16 November 2026)  
**Jenis dokumen:** Laporan status assessment dan gap eviden — bukan sertifikasi keamanan atau hasil PASS final.

## 1. Ringkasan eksekutif

Atas arahan pengguna, pemeriksaan teknis difokuskan pada kontrol **1.10 — tidak menggunakan library yang vulnerable**. Pada saat yang sama, register bukti disusun untuk seluruh 15 kontrol pada formulir agar kekurangan bukti dapat disampaikan secara transparan.

Repository yang diperiksa merupakan repository dokumentasi assessment, bukan source code SIMRS. Pencarian repository untuk manifest dependency umum (`package.json`, `pom.xml`, `build.gradle`, `composer.json`, `requirements.txt`, `go.mod`, `Cargo.toml`) tidak menemukan hasil. Tidak ditemukan SBOM, daftar dependency beserta versi, atau source bundle aplikasi target dalam bahan repository yang diperiksa.

**Kesimpulan:** kontrol 1.10 belum dapat diverifikasi karena komponen dan versinya tidak tersedia untuk pencocokan CVE/advisory. Empat belas kontrol lainnya juga belum dapat dinilai dari repository dokumentasi ini. Tidak ada kontrol yang dinyatakan PASS atau NOT PASS. Dokumen ini layak digunakan sebagai laporan status/gap untuk diserahkan hari ini, tetapi tidak boleh dipresentasikan sebagai bukti bahwa assessment teknis 15 kontrol telah selesai.

## 2. Ruang lingkup dan metode

- Review repository GitHub `Roughall/cybersecurity` pada branch `main`.
- Review checkpoint, scope, handoff, README, dan changelog.
- Pencarian file/artefak dependency untuk nama manifest umum.
- Tidak dilakukan pemindaian terhadap host/server, pengujian aplikasi, pengujian login, atau perubahan konfigurasi.
- Tidak ada output scanner dependency atau hasil pencocokan CVE yang tersedia pada repository saat review.

## 3. Register hasil 15 kontrol

| ID | Aspek pemeriksaan | Bukti yang tersedia saat review | Status |
|---|---|---|---|
| 1.1 | XSS pada setiap form input | Tidak ada source code/form test evidence di repository dokumentasi | BELUM DIVERIFIKASI |
| 1.2 | SQL Injection pada setiap form input | Tidak ada source code/query review atau hasil uji | BELUM DIVERIFIKASI |
| 1.3 | Pembatasan percobaan login | Tidak ada konfigurasi atau hasil uji autentikasi | BELUM DIVERIFIKASI |
| 1.4 | Lockout temporer setelah 3 kali gagal | Tidak ada konfigurasi atau hasil uji akun uji | BELUM DIVERIFIKASI |
| 1.5 | Warning “Gagal Login” | Tidak ada screenshot uji login | BELUM DIVERIFIKASI |
| 1.6 | Pesan gagal login tidak membedakan username/password | Tidak ada perbandingan respons akun uji | BELUM DIVERIFIKASI |
| 1.7 | Kompleksitas password | Tidak ada kebijakan atau hasil uji password | BELUM DIVERIFIKASI |
| 1.8 | Akses menu sesuai kewenangan | Tidak ada matriks role/permission atau hasil uji | BELUM DIVERIFIKASI |
| 1.9 | Broken Access Control / akses data antar-user | Tidak ada hasil uji otorisasi atau bukti kepemilikan data | BELUM DIVERIFIKASI |
| 1.10 | Tidak menggunakan library vulnerable | Manifest/SBOM/dependency dan versi tidak ditemukan; CVE matching belum dapat dilakukan | BELUM DIVERIFIKASI |
| 2.1 | Antivirus server | Tidak ada output/status antivirus server | BELUM DIVERIFIKASI |
| 2.2 | Firewall dan inbound rules | Tidak ada ruleset atau bukti listener server | BELUM DIVERIFIKASI |
| 2.3 | TLS minimal 1.2 | Tidak ada konfigurasi atau hasil uji TLS endpoint | BELUM DIVERIFIKASI |
| 2.4 | Keamanan versi webserver | Tidak ada identitas versi/build webserver | BELUM DIVERIFIKASI |
| 2.5 | Keamanan framework/bahasa pemrograman | Tidak ada inventaris runtime/framework dan versi target | BELUM DIVERIFIKASI |

## 3A. Baseline workstation (Tahap 1)

Output terminal yang diberikan pengguna pada 16 November 2026 pukul 10:32:06 WIB:

| Komponen | Hasil | Penilaian |
|---|---|---|
| OS | Kali GNU/Linux Rolling 2026.2 | Teridentifikasi |
| GNU grep | 3.12 | Tersedia |
| ugrep | Tidak terpasang | Opsional karena grep tersedia |
| Java | OpenJDK 25.0.5-ea (Debian build) | Tidak sesuai OpenJDK 17 BellSoft Liberica pada template |
| Apache Ant | Tidak ditemukan | Belum tersedia |
| Apache NetBeans | Tidak ditemukan di PATH | Belum terverifikasi |
| MariaDB client | 11.8.6-MariaDB, client 15.2 | Client tersedia; versi server belum diketahui |

Baseline workstation bukan hasil scan library aplikasi. Belum ada perubahan konfigurasi atau instalasi tool yang dilakukan. Screenshot/log mentah harus disimpan pada penyimpanan eviden yang disetujui dan disanitasi sebelum dibagikan.

## 4. Pemeriksaan khusus kontrol 1.10

### Kriteria
Memastikan library yang digunakan tidak memiliki kerentanan keamanan yang diketahui, misalnya Bootstrap, jQuery, dan komponen sejenis, sesuai butir 1.10 pada formulir.

### Hasil review repository
Pencarian dilakukan untuk nama manifest dependency berikut:
- `package.json`
- `pom.xml`
- `build.gradle`
- `composer.json`
- `requirements.txt`
- `go.mod`
- `Cargo.toml`

Tidak ada hasil file yang cocok dari pencarian repository. Repository yang tersedia berisi dokumentasi assessment dan bukan source code aplikasi SIMRS. Karena itu, belum ada daftar nama library, versi, dependency transitif, atau SBOM yang dapat dianalisis.

### Penilaian
**BELUM DIVERIFIKASI.** Ketiadaan manifest pada repository dokumentasi bukan bukti bahwa aplikasi tidak menggunakan library vulnerable. Tanpa daftar komponen dan versi aktual, pencocokan CVE/NVD tidak dapat menghasilkan kesimpulan yang dapat dipertanggungjawabkan.

### Eviden yang dibutuhkan
1. SBOM (CycloneDX atau SPDX) dari build aplikasi yang sesuai versi target; atau
2. manifest dan lockfile dependency yang digunakan untuk membangun versi aplikasi target; atau
3. daftar library, versi, sumber, dan komponen transitif yang dikonfirmasi vendor/pengelola SIMRS.

Setelah diterima, lakukan pencocokan terhadap advisory vendor dan basis data CVE/NVD, periksa rentang versi terdampak, status patch/backport, serta validasi false positive. Simpan hasil scanner dan ringkasan validasi sebagai eviden tersanitasi.

## 5. Gap dan permintaan data untuk menuntaskan assessment

| Prioritas | Data/eviden yang diminta | PIC/sumber yang disarankan |
|---|---|---|
| Tinggi — 1.10 | SBOM atau manifest/lockfile dan versi build SIMRS target | Vendor/pengelola SIMRS |
| Tinggi — 1.1–1.9 | Source review yang disetujui, screenshot, kebijakan, matriks role, akun uji, hasil uji staging | PIC SIMRS/vendor |
| Tinggi — 2.1–2.5 | Bukti antivirus, firewall, TLS, webserver, runtime/framework dari server | Administrator server/Diskominfotik |
| Administratif | Identitas versi target, lingkungan, tanggal, otorisasi, reviewer | PIC assessment dan pemilik sistem |

Jangan mengirim data pasien, kredensial, token, private key, cookie/session, dump database, atau konfigurasi rahasia. Simpan eviden mentah pada media institusi yang disetujui; unggah hanya salinan yang sudah disanitasi.

## 6. Pernyataan keterbatasan

- Review ini terbatas pada repository dokumentasi yang tersedia.
- Baseline OS dan sebagian tools workstation telah diberikan: Kali GNU/Linux Rolling 2026.2, GNU grep 3.12, OpenJDK 25.0.5-ea, MariaDB client 11.8.6. ugrep tidak terpasang, Apache Ant tidak ditemukan, dan NetBeans tidak ditemukan di PATH. Kernel dan arsitektur belum diberikan.
- Tidak ada akses atau bukti langsung dari aplikasi dan server produksi yang ditinjau.
- Pencarian manifest yang tidak menghasilkan temuan tidak membuktikan ketiadaan dependency.
- Tidak ada pengujian dinamis atau pemindaian jaringan dilakukan.
- Status checklist resmi harus diputuskan oleh PIC yang berwenang setelah bukti lengkap ditinjau.

## 7. Kesimpulan untuk penyerahan

Pada tanggal laporan, assessment belum dapat dinyatakan selesai secara teknis untuk 15 kontrol. Pemeriksaan terfokus pada kontrol 1.10 telah dilakukan pada repository dokumentasi, tetapi hasilnya **BELUM DIVERIFIKASI** karena artefak dependency aplikasi target belum tersedia. Seluruh kontrol lainnya juga berstatus **BELUM DIVERIFIKASI** karena eviden teknis belum tersedia pada repository.

Dokumen ini dapat diserahkan sebagai **laporan status pemeriksaan dan daftar kekurangan eviden**, bukan sebagai pernyataan bahwa sistem telah memenuhi seluruh persyaratan keamanan. Assessment final memerlukan data dan eviden dari vendor/pengelola SIMRS serta administrator server yang berwenang.

---
*Disusun sebagai dokumentasi teknis internal. Kesimpulan final dan pengisian checklist resmi memerlukan review serta persetujuan PIC yang berwenang.*


## 4A. Pemeriksaan statis paket distribusi SIMRS — pembaruan 16 November 2026

### Cakupan dan sumber
Paket distribusi lokal yang diperiksa: `/run/media/kali/DATA/KhanzaHMSWindows`. Paket merupakan distribusi aplikasi, bukan source tree lengkap. Inventaris awal menghasilkan 867 file JAR. Folder target tidak diubah; pemeriksaan dilakukan secara statis.

### Metode yang telah digunakan
1. Dependency discovery: pencarian dan inventarisasi file JAR.
2. Metadata/manifest review: ekstraksi metadata JAR dan pemeriksaan Class-Path.
3. Hashing: SHA-256 untuk membandingkan salinan library.
4. Static dependency analysis: `jdeps --multi-release base -verbose:class` pada `SIMRSKhanza.jar`.
5. Library inspection: pemeriksaan isi arsip, kelas tertentu, konfigurasi, dan string bytecode terbatas.
6. Manual vulnerability triage: identifikasi versi kandidat dan kebutuhan validasi terhadap advisory/CVE.

### Hasil teramati
- Ditemukan 867 file JAR.
- `SIMRSKhanza.jar` merujuk melalui manifest ke `lib/mysql-connector-java-5.1.47.jar`; file tersebut tersedia.
- `jdeps` berhasil dengan exit status 0; output 283.149 baris, 4.383 referensi JDBC, 0 not-found, dan 466 split-package warnings.
- Referensi langsung yang teramati: `fungsi.koneksiDB -> com.mysql.jdbc.jdbc2.optional.MysqlDataSource`, berasal dari Connector/J 5.1.47.
- Salinan Connector/J 5.1.47 yang diperiksa memiliki SHA-256 `a98bd1d92dc9007d2b95a9695923d2c7c6f1c3e8bdcf2cfac47ae1aa9b156d75`.
- Terdapat salinan Connector/J 5.1.39 pada updater; jangan menganggap file ini menggantikan referensi 5.1.47 pada manifest aplikasi utama.
- Inventaris metadata juga menunjukkan beberapa versi library lama/beragam, termasuk Log4j 1.2.15/1.2.17, Jackson 1.x/2.x, Spring, Apache POI, JasperReports, dan lainnya. Inventaris ini perlu diproses lebih lanjut untuk pemetaan package/version yang dapat dipercaya.

### Penilaian sementara
Connector/J 5.1.47 adalah **potential finding** yang perlu dicocokkan dengan advisory vendor, OSV/NVD, rentang versi, kondisi konfigurasi, dan patch/backport. Nomor versi saja tidak membuktikan exploitability. Status kontrol 1.10 tetap **BELUM DIVERIFIKASI** sampai validasi selesai dan direview PIC.

### Batasan
- Source-level white-box review belum dilakukan; source code/build project tidak tersedia pada paket yang diperiksa.
- Runtime loading belum diverifikasi; saat pemeriksaan proses tidak ditemukan proses Java aktif.
- Belum dilakukan scan OSV-Scanner, OWASP Dependency-Check, atau pembuatan SBOM CycloneDX.
- Pemeriksaan Bootstrap/jQuery dan seluruh komponen non-JAR belum lengkap.
- `jdeps` memeriksa referensi statis; hasilnya bukan bukti seluruh dependency runtime.
- Kelas/konfigurasi yang tidak ditemukan melalui pencarian terbatas tidak membuktikan tidak adanya penggunaan dinamis.

## 4B. Kesiapan tiga tools — output pengguna 16 November 2026

| Item | Hasil |
|---|---|
| OS | Kali GNU/Linux Rolling 2026.2 |
| Arsitektur | x86_64 |
| Java | OpenJDK 25.0.5-ea (Debian build) |
| Memori | 15 GiB total; sekitar 2,2 GiB available saat dicek |
| Swap | 15 GiB total; sekitar 10 GiB tersedia |
| Disk root | 452 GB total; 337 GB tersedia |
| OSV-Scanner | Belum terpasang |
| OWASP Dependency-Check | Belum terpasang |
| CycloneDX CLI | Belum terpasang |

Instalasi dan pemindaian ketiga tools belum dilakukan. Tahap berikutnya adalah instalasi terverifikasi, pembuatan SBOM dengan keterbatasan identifikasi dicatat, pemindaian, dan validasi silang.

### Eviden dan penyimpanan
Inventaris, metadata, hash, dan output jdeps disimpan pada workstation pengguna di direktori evidence lokal. Repository ini hanya menerima dokumentasi dan hasil tersanitasi; jangan unggah JAR proprietary, source code, data pasien, kredensial, atau log sensitif.
