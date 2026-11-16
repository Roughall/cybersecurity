# Changelog

## 2026-11-16 — Google Drive evidence-storage workflow
- Memperbarui CHECKPOINT.md: Google Drive ditetapkan sebagai rancangan pusat penyimpanan screenshot, error, log, dan eviden; GitHub tetap menjadi pusat dokumentasi assessment.
- Mendokumentasikan alur Kali Linux → sanitasi → Drive → review AI berizin → pencatatan hasil di GitHub.
- Menegaskan bahwa GitHub tidak otomatis mengarahkan ChatGPT/Claude/AI lain ke Drive; konektor dan izin harus dikonfigurasi secara terpisah.
- Mencatat bahwa jenis akun Drive, persetujuan kebijakan institusi, konektor AI, struktur folder, dan otomasi belum dikonfirmasi atau diimplementasikan.
- Menetapkan prinsip akses minimum dan sanitasi data sensitif sebelum eviden dibagikan.


## 2026-11-16 — Workflow checkpoint and multi-agent planning
- Memperbarui CHECKPOINT.md: assessment diprioritaskan untuk tenggat 2026-11-16.
- Menetapkan Diagnostic & Evidence Collector sebagai modul pendukung dalam repository yang sama; implementasi penuh ditunda agar tidak menghambat assessment.
- Menetapkan prinsip pemisahan log mentah lokal dan laporan/eviden tersanitasi untuk repository.
- Memperbarui AGENT_HANDOFF.md untuk koordinasi multi-agent, pembatasan akses, dan pencegahan konflik perubahan.
- Belum ada collector yang diimplementasikan, belum ada diagnostic run, dan belum ada audit teknis atau kontrol yang diverifikasi.

## 2026-11-16 — Initial baseline
- Menetapkan repository sebagai pusat dokumentasi security assessment.
- Menambahkan checkpoint awal dan instruksi handoff AI agent.
- Mendokumentasikan 15 kontrol SPPTI-SEC-FORM-001 v1.1.
- Menambahkan metodologi, panduan eviden, laporan, skrip, dan .gitignore.
- Belum ada audit teknis atau kontrol yang diverifikasi.


## 2026-11-16 — Focused assessment and evidence register
- Menetapkan pemeriksaan teknis terfokus pada kontrol 1.10 sesuai arahan pengguna; rekap eviden tetap mencakup 15 kontrol.
- Mencatat pencarian dependency manifest pada repository dokumentasi yang tidak menemukan manifest yang dapat dipindai.
- Menegaskan kontrol 1.10 belum dapat diverifikasi karena identitas library/versi dan SBOM/source bundle target belum tersedia.
- Menambahkan laporan status assessment dengan matriks 15 kontrol, eviden yang tersedia, gap, dan kebutuhan tindak lanjut.


## 2026-11-16 — Stage 01 Kali Linux baseline
- Mencatat output baseline Kali GNU/Linux Rolling 2026.2 yang diberikan pengguna.
- GNU grep 3.12 dan MariaDB client 11.8.6 tersedia; ugrep tidak terpasang.
- OpenJDK 25.0.5-ea tidak sesuai spesifikasi OpenJDK 17 BellSoft Liberica pada template.
- Apache Ant tidak ditemukan dan NetBeans tidak ditemukan di PATH.
- Menegaskan baseline workstation bukan hasil scan dependency dan belum membuktikan kontrol 1.10 PASS/NOT PASS.


## 2026-11-16 — Point 1.10: distribusi SIMRS, static review, dan persiapan SCA
- Memperbarui CHECKPOINT.md dan AGENT_HANDOFF.md dengan hasil pemeriksaan paket distribusi SIMRS lokal.
- Mencatat inventaris awal 867 JAR, metadata manifest, hash, dan hasil jdeps.
- Mencatat referensi SIMRSKhanza.jar ke MySQL Connector/J 5.1.47 dan potential finding yang menunggu validasi advisory/CVE.
- Memperbarui laporan status agar membedakan hasil review repository dokumentasi dari pemeriksaan paket distribusi lokal.
- Mencatat batasan: source review dan runtime verification belum dilakukan; OSV-Scanner, OWASP Dependency-Check, dan CycloneDX CLI belum terpasang.
- Tidak mengunggah paket JAR proprietary atau eviden mentah/sensitif ke repository.


## 2026-11-16 — Point 1.10 full SBOM, OSV scan, dan pemetaan lokasi
- Memperbarui CHECKPOINT.md dan AGENT_HANDOFF.md dengan hasil SCA pada distribusi SIMRS lokal.
- Mencatat Syft full distribution SBOM: 2.044 komponen; OSV memproses 1.037 paket dan memfilter 77 paket lokal/unscannable.
- Mencatat 163 rekaman vulnerability pada 44 paket/versi dan 131 CVE unik; membedakan rekaman dari CVE unik.
- Mencatat pemetaan lokasi JAR v2 berhasil 163/163 setelah membaca identitas Maven dari PURL; 0 belum terpetakan.
- Mencatat inventaris aset web di luar JAR dan 1.072 entri aset web di dalam JAR, dengan batasan bahwa entri tersebut mencakup dokumentasi/contoh/duplikasi dan bukan library runtime unik.
- Mencatat bahwa Dependency-Check 13.0.0 terpasang tetapi NVD update menunggu API key; belum ada hasil scan Dependency-Check.
- Menegaskan OSV match adalah indikasi awal, bukan bukti exploitability; kontrol 1.10 tetap BELUM DIVERIFIKASI sampai validasi advisory, versi, runtime, dan false positive selesai.
- Artefak scanner dan eviden mentah tetap lokal; tidak mengunggah JAR proprietary atau data sensitif ke GitHub.
