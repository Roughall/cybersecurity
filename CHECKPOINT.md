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
1. AI agent membaca dokumen root dan metodologi.
2. Discovery workstation lokal secara pasif: versi Kali, kernel, arsitektur, tools tersedia.
3. Konfirmasi target, versi, lingkungan, pemilik, otorisasi, dan batas pengujian.
4. Rencanakan eviden per kontrol.
5. Mulai pengujian hanya setelah ruang lingkup disetujui.

## Riwayat
| Tanggal | Checkpoint | Ringkasan |
|---|---|---|
| 2026-11-16 | INITIAL-BASELINE | Dokumentasi diinisialisasi; audit teknis belum dimulai. |
