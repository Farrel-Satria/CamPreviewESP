# 📸 ESP32-CAM Web Control Dashboard

Selamat datang di dashboard kontrol real-time untuk perangkat **ESP32-CAM**!  
Aplikasi web satu halaman (**Single-Page Application / SPA**) ini memungkinkan Anda untuk melihat **live stream video**, mengambil **snapshot**, dan mengontrol **parameter kamera serta LED flash** langsung dari browser.

---

## 💻 Deskripsi dan Fitur Utama

Dashboard ini dirancang untuk interaksi langsung dengan firmware ESP32-CAM melalui **API HTTP (GET Requests)**.

### ⭐ Fitur yang Tersedia

| Fitur                     | Deskripsi                                                                                  |
|---------------------------|--------------------------------------------------------------------------------------------|
| Live Video Stream          | Menampilkan umpan video real-time (membutuhkan IP Address yang benar).                      |
| Indikator Koneksi & Loading| Menampilkan status koneksi dan Loading Spinner saat mencoba terhubung.                     |
| Pengaturan Kamera          | Kontrol Brightness, Contrast, dan JPEG Quality secara langsung.                             |
| Kontrol Resolusi           | Mengubah resolusi video (memerlukan restart stream untuk diterapkan).                     |
| Night Mode                 | Mengaktifkan filter visual di browser untuk simulasi mode malam.                           |
| Flash LED Control          | Mengaktifkan/menonaktifkan LED Flash bawaan.                                               |
| Snapshot Gallery           | Mengambil gambar (capture) dan secara otomatis mengunduhnya.                               |
| Device Management          | Tombol untuk me-reboot device dari jarak jauh.                                             |

---

## ⚙️ Panduan Penggunaan dan Alur Kerja

Ikuti langkah-langkah berikut untuk menjalankan dashboard ini:

### ⬇️ Langkah 0: Mengambil Kode (Cloning Repository)

1. Buka Terminal atau Git Bash.
2. Jalankan perintah berikut (ganti `[URL_REPOSITORI_ANDA]` dengan URL repository GitHub Anda):

```bash
git clone [URL_REPOSITORI_ANDA]
cd nama-folder-repositori
Sekarang Anda memiliki semua file (index.html, script.js, dll.) di folder lokal.

🔌 Langkah 1: Persiapan Firmware ESP32-CAM
Pastikan ESP32-CAM sudah di-flash dengan firmware yang tepat, seperti CameraWebServer dari Arduino IDE.

Konfigurasi Wi-Fi agar terhubung ke jaringan lokal yang sama dengan komputer.

Catat IP Address yang ditampilkan di Serial Monitor (contoh: 192.168.1.77).

🌐 Langkah 2: Konfigurasi Dashboard (Web)
Buka file script.js.

Temukan baris penentuan IP (sekitar baris 20):

javascript
Copy code
const ESP_IP = '192.168.1.77'; // Pastikan ini adalah IP ESP32-CAM Anda yang benar
Ganti dengan IP Address ESP32-CAM yang Anda dapatkan di langkah 1.

▶️ Langkah 3: Menjalankan Dashboard
Buka index.html di browser modern (Chrome, Firefox, Edge).

Halaman akan menampilkan tombol besar: "Start Camera Stream".

🚦 Tabel Alur Kerja (Workflow)
Aksi	Deskripsi
Start Stream	Menekan tombol Start Camera Stream. Mencoba memuat stream MJPEG dari http://[IP_ANDA]:81/stream. Saat mencoba terhubung, Loading Spinner muncul. Jika berhasil, spinner hilang dan video tampil.
Stop Stream	Menghentikan koneksi video dan menampilkan layar awal (CTA Overlay muncul kembali).
Capture	Mengambil frame dari video, menyimpannya di galeri, dan mengunduhnya sebagai file .jpg.
Kontrol Slider	Mengubah Quality, Brightness, atau Contrast. Perubahan dikirim langsung ke ESP32-CAM via HTTP.
Reboot Device	Mengirim perintah untuk me-restart ESP32. Koneksi Wi-Fi sementara terputus, dashboard menampilkan Disconnected.

🛠️ Catatan Teknis untuk Tim
⚠️ Persyaratan Jaringan
ESP32-CAM dan perangkat yang menjalankan web harus berada di jaringan Wi-Fi lokal yang sama.

📉 Kinerja FPS
Frame per Second (FPS) bergantung pada kualitas jaringan Wi-Fi dan pengaturan Resolusi/JPEG Quality:

JPEG Quality rendah → gambar buram, FPS lebih tinggi

JPEG Quality tinggi → gambar bagus, FPS lebih rendah

🛡️ Penting (Cross-Origin)
Karena API HTTP berjalan di jaringan lokal, CORS biasanya tidak menjadi masalah.

Jika menggunakan reverse proxy atau mengakses dari luar jaringan lokal, konfigurasi firewall mungkin diperlukan.

💡 Tips
Selalu pastikan IP Address di script.js sesuai dengan ESP32-CAM yang sedang digunakan.

Gunakan browser modern untuk kompatibilitas terbaik.

Untuk snapshot, pastikan popup/unduhan otomatis browser aktif agar file tersimpan.

