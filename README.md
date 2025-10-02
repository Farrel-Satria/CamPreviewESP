📸 Proyek: ESP32-CAM Web Control Dashboard
Selamat datang di dashboard kontrol real-time untuk perangkat ESP32-CAM!

Aplikasi web satu halaman (Single-Page Application / SPA) ini memungkinkan Anda untuk melihat live stream video dari ESP32-CAM, mengambil snapshot, dan mengontrol parameter kamera serta LED flash dari browser Anda.

💻 Deskripsi dan Fitur Utama
Dashboard ini dirancang untuk interaksi langsung dengan firmware ESP32-CAM melalui API HTTP (GET Requests).

⭐ Tabel Fitur yang Tersedia
Fitur

Deskripsi

Live Video Stream

Menampilkan umpan video real-time (membutuhkan IP Address yang benar).

Indikator Koneksi & Loading

Menampilkan status koneksi dan Loading Spinner saat mencoba terhubung.

Pengaturan Kamera

Kontrol Brightness, Contrast, dan JPEG Quality secara langsung.

Kontrol Resolusi

Mengubah resolusi video (memerlukan restart stream untuk diterapkan).

Night Mode

Mengaktifkan filter visual di browser untuk simulasi mode malam.

Flash LED Control

Mengaktifkan/menonaktifkan LED Flash bawaan.

Snapshot Gallery

Mengambil gambar (capture) dan secara otomatis mengunduhnya.

Device Management

Tombol untuk me-Reboot Device dari jarak jauh.

⚙️ Panduan Penggunaan dan Alur Kerja
Ikuti langkah-langkah berikut untuk menjalankan dashboard ini.

⬇️ Langkah 0: Mengambil Kode (Cloning Repositori)
Tim Anda dapat mengunduh dan mulai bekerja dengan kode ini menggunakan perintah git clone.

Buka Terminal atau Git Bash di komputer Anda.

Jalankan perintah berikut. Ganti [URL_REPOSitori_ANDA] dengan alamat HTTPS repository GitHub Anda:

git clone [URL_REPOSitori_ANDA]
cd nama-folder-repositori

Anda sekarang memiliki semua file (index.html, script.js, dll.) di folder lokal.

🔌 Langkah 1: Persiapan Firmware ESP32-CAM
Pastikan perangkat ESP32-CAM Anda sudah di-flash dengan firmware yang tepat, seperti contoh CameraWebServer dari Arduino IDE.

Konfigurasi Wi-Fi: Ubah konfigurasi Wi-Fi di kode ESP32-CAM agar terhubung ke jaringan lokal yang sama dengan komputer Anda.

Dapatkan IP: Setelah di-upload dan terhubung, catat IP Address yang ditampilkan oleh ESP32-CAM di Serial Monitor (Contoh: 192.168.1.77).

🌐 Langkah 2: Konfigurasi Dashboard (Web)
Ini adalah langkah krusial untuk menghubungkan web ke ESP32 Anda!

Buka file script.js.

Temukan baris penentuan IP (sekitar baris 20):

const ESP_IP = '192.168.1.77'; // Pastikan ini adalah IP ESP32-CAM Anda yang benar

Ganti nilai '192.168.1.77' dengan IP Address asli yang Anda dapatkan di Langkah 1.

▶️ Langkah 3: Menjalankan Dashboard
Buka file index.html di browser modern mana pun (Chrome, Firefox, Edge).

Halaman akan menampilkan tombol besar: "Start Camera Stream".

🚦 Tabel Alur Kerja (Workflow)
Berikut adalah ringkasan aksi dan dampak langsung pada perangkat atau dashboard:

Aksi

Deskripsi

Start Stream

Menekan tombol "Start Camera Stream". Ini akan mencoba memuat stream MJPEG dari http://[IP_ANDA]:81/stream. Saat mencoba terhubung, Loading Spinner akan muncul. Jika berhasil, spinner hilang dan video tampil.

Stop Stream

Menghentikan koneksi video dan mengembalikan tampilan ke layar awal (CTA Overlay muncul kembali).

Capture

Mengambil frame dari video yang sedang ditampilkan, menyimpannya di galeri, dan secara otomatis mengunduhnya sebagai file .jpg.

Kontrol Slider

Mengubah nilai Quality, Brightness, atau Contrast. Setiap perubahan pada slider akan segera mengirim perintah HTTP ke ESP32-CAM untuk memperbarui pengaturan kamera.

Reboot Device

Mengirim perintah ke ESP32 untuk me-restart. Ini akan memutuskan koneksi Wi-Fi sementara dan dashboard akan menampilkan status Disconnected.

🛠️ Catatan Teknis untuk Tim
⚠️ Persyaratan Jaringan
Dashboard ini hanya akan bekerja jika ESP32-CAM dan perangkat yang menjalankan web berada dalam jaringan Wi-Fi lokal yang sama.

📉 Kinerja FPS
Kinerja Frame Per Second (FPS) sangat bergantung pada kualitas jaringan Wi-Fi dan pengaturan Resolusi/Kualitas JPEG yang Anda pilih. Kualitas JPEG rendah (nilai kecil) = kualitas gambar buruk & FPS lebih tinggi. Kualitas JPEG tinggi (nilai besar) = kualitas gambar bagus & FPS lebih rendah.

Pastikan semua anggota tim mengkonfigurasi IP Address di script.js sebelum menggunakannya. Selamat mencoba!
