# Audit Scope — SPPTI-SEC-FORM-001 v1.1

## Tujuan dan acuan
Mendokumentasikan pemeriksaan keamanan SIM Faskes untuk mendukung integrasi/bridging dengan Web Service BPJS Kesehatan. Acuan adalah template SECURITY SELF-ASSESSMENT SIM FASKES, kode SPPTI-SEC-FORM-001, versi 1.1, enam halaman.

Template menyebut telaah kode sumber manual, OWASP Top 10 (2021), OWASP ASVS 4.0 (Authentication, Access Control, Validation/Injection), inventaris versi library/komponen, dan pencocokan CVE/NVD.

## Frontend / aplikasi
| ID | Kriteria template | Contoh bukti |
|---|---|---|
| 1.1 | Tidak ada XSS pada setiap form input | Review encoding/escaping, inventaris input/output, uji aman di staging |
| 1.2 | Tidak ada SQL Injection pada setiap form input | Review query/parameterisasi dan validasi terkontrol |
| 1.3 | Pembatasan upaya login (CAPTCHA/delay atau mekanisme sejenis) efektif | Konfigurasi, alur autentikasi, uji terotorisasi terbatas |
| 1.4 | Lockout temporer setelah 3 kali salah login | Konfigurasi/kode dan uji akun khusus |
| 1.5 | Warning “Gagal Login” ditampilkan | Screenshot hasil uji akun |
| 1.6 | Pesan gagal login tidak membedakan username/password salah | Perbandingan respons akun uji |
| 1.7 | Password minimal 8 karakter dengan huruf besar, kecil, angka, karakter khusus | Kebijakan dan uji validasi |
| 1.8 | Menu hanya dapat diakses sesuai kewenangan | Matriks role-permission dan uji akun uji |
| 1.9 | Tidak ada broken access control/akses data user lain | Matriks kepemilikan data dan uji terotorisasi |
| 1.10 | Tidak menggunakan library vulnerable | Inventaris/SBOM, versi, CVE/advisory dan validasi |

## Backend / server
| ID | Kriteria template | Contoh bukti |
|---|---|---|
| 2.1 | Server terinstal antivirus | Produk/versi, status service/agent, update |
| 2.2 | Firewall aktif dan inbound sesuai ketentuan form | Ruleset dan listener aktual; dokumentasikan pengecualian |
| 2.3 | TLS minimal 1.2 | Konfigurasi dan hasil negosiasi TLS endpoint yang disetujui |
| 2.4 | Versi webserver tidak memiliki celah keamanan | Produk/build/modul dan advisory relevan |
| 2.5 | Framework/bahasa pemrograman tidak memiliki celah keamanan | Runtime/framework/dependency dan advisory relevan |

## Catatan interpretasi
- Kriteria di atas mengikuti template; rekomendasi tambahan harus ditandai sebagai tambahan.
- Kontrol 1.3 perlu mempertimbangkan ketentuan form terkait bypass, OCR, dan reuse CAPTCHA bila CAPTCHA digunakan.
- Untuk 2.2, dokumentasikan port yang benar-benar dibutuhkan dan minta keputusan pemilik sistem atas pengecualian.
- Template menyebut TLS dikelola Diskominfotik; koordinasikan eviden 2.3 dengan pengelola.
- Nomor versi saja tidak cukup untuk menyimpulkan komponen aman; pertimbangkan patch vendor, konfigurasi, dan kondisi terdampak advisory.
- Checklist resmi template menggunakan PASS/NOT PASS. Status internal BELUM DIVERIFIKASI digunakan sampai bukti tersedia.

## Di luar cakupan sampai ada persetujuan
Penetration test produksi, eksploitasi, brute force, DoS/stress test, pengambilan data pasien, perubahan konfigurasi, serta pengujian sistem BPJS/pihak ketiga tanpa otorisasi pemilik terkait.
