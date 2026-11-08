<div align="center">

<img src="static/images/logo.png" alt="Logo LabKeeper" width="110">

# 🔬 LabKeeper

**Sistem Manajemen Peminjaman Alat Laboratorium Sekolah berbasis QR Code**

Pinjam alat lab cukup dengan scan QR — pantau, kembalikan, selesai.

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0-black?logo=flask&logoColor=white)
![SQLite](https://img.shields.io/badge/Database-SQLite-003B57?logo=sqlite&logoColor=white)
![License](https://img.shields.io/badge/Lisensi-MIT-green)

*Proyek sekolah — dibuat agar siswa dan laboran mengelola alat lab dengan rapi, cepat, dan tercatat.*

<img src="static/images/gambar_samping.jpeg" alt="Tampilan LabKeeper" width="720">

</div>

---

## 📋 Daftar Isi

1. [Apa itu LabKeeper?](#-apa-itu-labkeeper)
2. [Fitur Utama](#-fitur-utama)
3. [Cara Menjalankan di Laptop (5 Menit)](#-cara-menjalankan-di-laptop-5-menit)
4. [Alur Peminjaman Singkat](#-alur-peminjaman-singkat)
5. [Tech Stack](#-tech-stack)
6. [Struktur Proyek](#%EF%B8%8F-struktur-proyek)
7. [Script Pembantu](#-script-pembantu)
8. [Deployment ke VPS](#-deployment-ke-vps)
9. [Keamanan](#-keamanan)
10. [Lisensi](#-lisensi)

---

## 🤔 Apa itu LabKeeper?

Masalah yang biasa terjadi di lab sekolah:

| 😩 Sebelum | ✅ Dengan LabKeeper |
|---|---|
| Peminjaman dicatat di buku tulis manual | Semua tercatat otomatis saat siswa scan QR |
| Alat hilang, tidak tahu siapa yang pinjam terakhir | Riwayat peminjaman lengkap per alat |
| Tidak tahu alat harus kapan dikembalikan | Countdown timer real-time + status *Aktif / Kembali / Terlambat* |
| Laboran harus absen terus di lab | Monitoring via dashboard dari HP atau laptop |

LabKeeper mendukung **Multi-Sekolah (Multi-Tenant)** — satu aplikasi bisa dipakai banyak sekolah dengan data yang terisolasi 100%, dan setiap sekolah punya aturan durasi peminjaman sendiri.

---

## ✨ Fitur Utama

<details open>
<summary><b>📱 Untuk Siswa</b></summary>

* **Scan QR Code Alat** — pinjam alat lewat kamera HP (Android & iOS), tanpa ketik apa pun.
* **Live Countdown Timer** — sisa waktu peminjaman berjalan real-time.
* **Perpanjangan Waktu** — ajukan perpanjangan langsung dari dashboard (maks. 2x).
* **Riwayat Peminjaman** — semua riwayat pinjam tercatat rapi.
* **Ganti Kata Sandi** — dengan invalidasi sesi di semua perangkat lain.

</details>

<details open>
<summary><b>🛠️ Untuk Admin / Laboran</b></summary>

* **Dashboard Live Monitoring** — status peminjaman dengan indikator warna (*Aktif / Kembali / Terlambat*).
* **Kelola Alat + QR Otomatis** — tambah alat, QR Code PNG ter-generate otomatis.
* **Cetak Label QR** — cetak stiker QR massal atau terpilih.
* **Import & Export Excel** — import data siswa/alat dari `.xlsx` dengan preview validasi.
* **Verifikasi Dua Langkah** — peminjaman dan pengembalian dikonfirmasi dua pihak.

</details>

<details>
<summary><b>🏫 Multi-Sekolah & Lainnya</b></summary>

* **Isolasi data per sekolah** — data alat, siswa, admin, dan riwayat tidak pernah bercampur antar sekolah.
* **Durasi peminjaman independen** — Sekolah A bisa 3 jam, Sekolah B bisa 24 jam.
* **Registrasi sekolah baru** — cukup jalankan script `add_school.py`.
* **Web GUI Database** — layanan `sqlite-web` (seperti phpMyAdmin untuk SQLite) di port 8080.

</details>

---

## 🚀 Cara Menjalankan di Laptop (5 Menit)

Cukup 3 langkah — tanpa database server, tanpa konfigurasi rumit.

**1. Siapkan file & environment:**

```bash
git clone https://github.com/Hanzyzy/labkeeper-public.git
cd labkeeper-public
python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate
pip install -r requirements.txt
```

**2. Atur password akun demo lalu buat database:**

```bash
# Windows (CMD):
set LABKEEPER_ADMIN_PASSWORD=admin12345
set LABKEEPER_STUDENT_PASSWORD=siawa12345

# Linux/Mac:
export LABKEEPER_ADMIN_PASSWORD=admin12345
export LABKEEPER_STUDENT_PASSWORD=siawa12345

python reset_db.py
```

**3. Jalankan:**

```bash
python app.py
```

Buka browser: **http://localhost:5000** 🎉

| Akun | Username | Password |
|---|---|---|
| Admin | `admin` | `admin12345` *(contoh di atas — sesuaikan)* |
| Siswa | `1001` – `1005` | `siawa12345` *(contoh di atas — sesuaikan)* |

> Catatan: password minimal 8 karakter, diatur lewat environment variable agar tidak pernah tersimpan di dalam kode.

---

## 🔄 Alur Peminjaman Singkat

```text
Scan QR  →  Konfirmasi Pinjam  →  Verifikasi Admin  →  Alat Dipakai (countdown jalan)
                │
                └→  Ajukan Kembali  →  Verifikasi Admin  →  Alat Kembali ke Lab
```

---

## 🛠️ Tech Stack

| Komponen | Teknologi |
|---|---|
| Core Framework | Python 3.11 / Flask 3.0 |
| Database & ORM | SQLite 3 / Flask-SQLAlchemy 3.1 |
| Autentikasi | Werkzeug Security (Scrypt & PBKDF2) |
| QR Code | `qrcode[pil]` (Pillow) |
| Excel | `openpyxl` (import & styled export) |
| Zona Waktu | `Asia/Jakarta` (WIB, UTC+7) |
| Frontend | Jinja2, HTML5, Vanilla CSS (Bento Grid), Vanilla JS |
| Production | Gunicorn (3 workers) + Nginx + Certbot SSL |

---

## 🗂️ Struktur Proyek

```text
labkeeper-public/
├── app.py                  # Aplikasi Flask utama (routes & logic)
├── models.py               # Model database (School, Admin, Student, Tool, Borrowing)
├── auth.py                 # Helper autentikasi & decorator session
├── datetime_utils.py       # Helper zona waktu WIB
├── qr_utils.py             # Generator QR Code (Pillow)
├── reset_db.py             # Reset & seed data awal
├── add_school.py           # Tambah sekolah & admin baru (interaktif)
├── fix_db.py               # Perbaikan format tanggal database
├── deploy_vps.sh           # Deployment VPS otomatis
├── requirements.txt        # Dependensi Python
├── static/                 # CSS, JS, gambar, QR code alat
└── templates/              # Semua halaman (Jinja2)
    └── admin/              # Halaman khusus admin/laboran
```

---

## 🔧 Script Pembantu

| Script | Fungsi |
|---|---|
| `add_school.py` | Daftarkan sekolah baru + akun admin-nya |
| `reset_db.py` | Hapus & isi ulang database dengan data awal |
| `fix_db.py` | Perbaiki format tanggal lama di SQLite |

---

## 🌐 Deployment ke VPS

Sudah disiapkan script otomatis:

```bash
bash deploy_vps.sh
```

Script ini memasang venv, dependensi, service systemd, Nginx reverse proxy, dan SSL Certbot. Untuk update aplikasi di server:

```bash
cd /var/www/labkeeper
git pull && sudo systemctl restart labkeeper
```

Konfigurasi environment disalin dari `.env.example` — **jangan pernah commit file `.env` asli**.

---

## 🔐 Keamanan

* Password di-hash (Scrypt/PBKDF2) — tidak pernah disimpan sebagai teks biasa.
* `SECRET_KEY` di-generate acak per deployment, tidak hardcoded.
* Isolasi data antar sekolah di level query.
* Ganti password mem-invalidasi sesi di perangkat lain (password versioning).
* Cookie session bisa dipaksa HTTPS (`SESSION_COOKIE_SECURE`).

---

## 📜 Lisensi

Dilisensikan di bawah [Lisensi MIT](LICENSE) — bebas dipelajari, dipakai, dan dikembangkan untuk kepentingan pendidikan di Indonesia.

<div align="center">

**Dibuat dengan 🔬 dan ☕ oleh [Hanzyzy](https://github.com/Hanzyzy)**

*Kalau proyek ini membantu, ⭐ star di repo ini sangat diapresiasi!*

</div>
