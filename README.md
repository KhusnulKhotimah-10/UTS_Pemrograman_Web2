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
