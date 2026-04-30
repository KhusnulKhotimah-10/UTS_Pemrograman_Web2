# UTS_Pemrograman_Web2

# Web Security Lab: SQL Injection Mechanism & Mitigation in PHP

Repositori ini berisi analisis mendalam dan simulasi eksperimen mengenai kerentanan **SQL Injection (SQLi)** pada aplikasi web berbasis PHP, serta strategi mitigasi menggunakan *industry standard practices*.

## 🚀 Ringkasan Proyek
Proyek ini bertujuan untuk mendemonstrasikan bagaimana celah keamanan pada input form dapat dimanipulasi untuk melewati proses autentikasi dan bagaimana cara menutup celah tersebut secara total.

### 🔍 Eksperimen: Simulasi Kerentanan
Dalam simulasi ini, saya menggunakan skrip login PHP sederhana yang rentan terhadap manipulasi query.

**Payload yang digunakan:**
`admin' --`

**Logika Serangan:**
Karakter kutip tunggal (`'`) digunakan untuk memutus string pada SQL, sementara double dash (`--`) memerintahkan database untuk mengabaikan sisa perintah (termasuk verifikasi password).



### 🛡️ Solusi Keamanan: Prepared Statements
Cara paling efektif untuk mencegah serangan ini adalah dengan memisahkan **logika SQL** dari **data pengguna**. Saya mengimplementasikan **PDO (PHP Data Objects)** untuk memastikan input diproses sebagai parameter, bukan sebagai perintah yang dieksekusi.

```
php
// Snippet kode aman menggunakan PDO
$stmt = $pdo->prepare('SELECT * FROM users WHERE username = :user');
$stmt->execute(['user' => $username]);
$user = $stmt->fetch();
```
📊 Perbandingan KeamananMetodeTingkat KeamananKeteranganString ConcatenationSangat RendahSangat mudah diserang (Default)Sanitasi ManualSedangRentan terhadap bypass encodingPrepared StatementsTinggiStandar industri, risiko SQLi 0%📚 ReferensiOWASP SQL Injection Prevention Cheat SheetPHP Documentation: PDO ClassProyek ini disusun oleh Khusnul Khotimah sebagai bagian dari tugas UTS Pemrograman Web di Universitas Pelita Bangsa.
---


<img width="593" height="236" alt="image" src="https://github.com/user-attachments/assets/9571635e-e368-4b0c-b073-893da19f1eb6" />

# Publikasi Artikel
Analisis lengkap mengenai proyek ini telah dipublikasikan di Medium. Anda dapat membaca artikel selengkapnya melalui tautan berikut:
👉 Mekanisme SQL Injection dan Strategi Keamanan - Medium
```
https://medium.com/@husnulkhotimah100105/mekanisme-sql-injection-dan-strategi-keamanan-8cb1f71f8977
```

🛡️ Quality Assurance: Content Integrity Report
Proyek ini telah melalui proses verifikasi keaslian konten untuk menjamin integritas karya akademik.

Hasil Pemeriksaan Plagiarisme (30-04-2026):

Unique Content: 95%.

Plagiarism Score: 5% (Identifikasi pada terminologi teknis standar).

Total Data: 443 kata / 3.327 karakter.

Analisis Laporan:
Skor unik sebesar 95% membuktikan orisinalitas konten yang sangat tinggi. Kecocokan sebesar 5% adalah hal wajar karena penggunaan istilah teknis keamanan web yang baku serta referensi query SQL yang memang bersifat standar dalam pemrograman PHP.

Disusun oleh: Khusnul Khotimah | Tugas UTS Pemrograman Web - Universitas Pelita Bangsa.

Read Time: Estimasi waktu baca sekitar 3 menit.  

Analisis Hasil:
Skor unik sebesar 95% menunjukkan tingkat orisinalitas yang sangat tinggi. Persentase kecil (5%) yang terdeteksi sebagai kecocokan persis (Exact Match) disebabkan oleh penggunaan istilah teknis standar keamanan web, cuplikan kode SQL umum, serta kutipan referensi dari dokumentasi resmi yang tidak dapat diubah.
