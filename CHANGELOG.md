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
