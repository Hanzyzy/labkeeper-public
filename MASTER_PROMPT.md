# 🎨 MASTER PROMPT UI/UX DESIGN SYSTEM — LABKEEPER

> **System Prompt Desain Antarmuka & Pengalaman Pengguna (UI/UX):**  
> Gunakan Master Prompt ini sebagai sistem instruksi utama khusus untuk **Desain Visual, Estetika Antarmuka, Sistem Tipografi, Palet Warna, Komposisi Bento Grid, dan Pengalaman Pengguna (UX)** pada aplikasi **LabKeeper**.

---

## 🏛️ 1. Filosofi Desain & Karakter Visual

* **Konsep Utama**: *Modern Editorial & High-Contrast Monochrome Elegance*.
* **Impresi Pertama**: Mewah, bersih, state-of-the-art, intuitif, dan responsif.
* **Prinsip Tampilan**:
  * Menghindari warna generik yang polos. Menggunakan palet kontras tinggi yang terkurasi.
  * Komposisi kartu *Bento Grid* bertepi halus (*rounded corners*) dengan garis perbatasan (*border line*) yang tegas.
  * Pencahayaan dan efek kedalaman visual menggunakan *subtle card elevation & glassmorphism*.

---

## 🔤 2. Sistem Tipografi (Hierarchy & Typography Scale)

Sistem menggunakan **3 jenis font terkurasi dari Google Fonts** untuk hirarki visual yang jelas:

| Jenis Font | Nama Font | Penggunaan Utama |
|---|---|---|
| **Display / Header** | `Playfair Display` (Serif) | Judul utama landing page, tajuk halaman dashboard, dan highlight section. |
| **Interface / Body** | `Inter` (Sans-Serif) | Teks utama, navigasi menu, label form, tombol aksi, dan pesan notifikasi. |
| **Code & Data** | `JetBrains Mono` (Monospace) | Kode barang (`MTR-001`), NIS siswa, badge tanggal, dan live countdown timer. |

### Aturan Skala Tipografi:
* **Page Title (H1)**: `clamp(2rem, 5vw, 3.25rem)` — Font Display, Weight 800, Letter Spacing `-0.03em`.
* **Section Title (H2)**: `clamp(1.25rem, 3vw, 1.75rem)` — Font Display, Weight 800.
* **Card Heading (H3)**: `1.125rem` s/d `1.375rem` — Font Display, Weight 700.
* **Body Text**: `0.875rem` s/d `1rem` — Font Inter, Weight 400/500, Line Height `1.6`.
* **Eyebrow Tag / Metadata**: `0.6875rem` s/d `0.75rem` — Font Mono, Weight 700, Upper Case, Letter Spacing `0.1em`.

---

## 🎨 3. Palet Warna & Token Desain Visual

```css
:root {
  /* Surface & Background */
  --bg: #F8F9FA;         /* Soft Canvas Background */
  --paper: #FFFFFF;      /* Card / Container Surface */
  --line: #E5E7EB;       /* Border / Divider Line */

  /* Ink & Typography */
  --ink: #000000;        /* Deep Black Primary Text & Accent */
  --ink-2: #4B5563;      /* Secondary Dark Slate Text */
  --muted: #9CA3AF;      /* Muted Caption Text */

  /* Status Tokens */
  --status-active: #000000;   /* Aktif / Dipinjam */
  --status-returned: #059669; /* Dikembalikan (Emerald Green) */
  --status-overdue: #DC2626;  /* Telat / Overdue (Crimson Red) */
}
```

---

## 📱 4. Komposisi Tata Letak (Layout) & Bento Grid

### 1. Gateway Dual-Entry Landing Page
* **Visual**: Dua kartu utama berdampingan (*Side-by-Side Gateway Cards*) yang memisahkan **Portal Murid/Siswa** dan **Portal Sekolah/Admin**.
* **Elemen**: Icon container bundar `56px x 56px`, tag *eyebrow*, judul besar display, deskripsi ringkas, dan tombol aksi full-width.

### 2. Admin Dashboard (Bento Grid)
* **4 Metric Stat Cards**: Kartu indikator (*Total Alat, Tersedia, Dipinjam, Telat*) dengan angka besar menonjol.
* **Live Activity Feed**: Daftar aktivitas peminjaman terbaru dengan foto avatar bulat (`36px`), inisial nama, timestamp WIB, dan badge status warna.
* **Quick Actions Grid**: Grid tombol navigasi cepat 1-klik dengan ikon aksen.

### 3. Student Dashboard & Catalog
* **Profile Banner Header**: Menyajikan identitas siswa (Nama, NIS, Kelas, Sekolah) secara ringkas.
* **Bezel Card Peminjaman Aktif**: Kartu bergaris perbatasan tegas menyoroti waktu batas pengembalian (WIB) dan tombol pengembalian 1-klik.
* **Katalog Alat**: Layout grid responsif dengan foto/emoji alat, tag kategori, indikator ketersediaan, dan tombol detail.

### 4. Admin Settings Page (Bento Cards)
* **3 Card Sections**: Keamanan Akun Admin, Aturan Durasi Peminjaman Per-Sekolah (dengan tombol preset cepat 2h, 4h, 12h, 24h), dan Pemeliharaan Sistem / Danger Zone.

---

## 🖼️ 5. Proteksi Visual Logo & Aspek Rasio

Seluruh gambar logo (`logo.png`) diproteksi secara universal agar **tidak pernah gepeng, terdistorsi, atau ditarik** di layar HP dengan DPI apa pun:

```css
img[src*="logo.png"],
.nav-bar-logo img,
.nav-bar-logo-link img,
.login-logo img,
.admin-sidebar-brand img {
  width: auto !important;
  max-width: 100% !important;
  object-fit: contain !important;
  aspect-ratio: auto !important;
  flex-shrink: 0 !important;
}
```

---

## ✨ 6. Mikro-Interaksi & Motion Design

1. **Page Load Reveal Animation**:
   * Efek *fade-in & slide-up* yang halus saat membuka halaman menggunakan kurva `cubic-bezier(0.16, 1, 0.3, 1)`.
   ```css
   .reveal {
     animation: revealUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
   }
   ```
2. **Button Hover States**:
   * Tombol utama (*Primary Button*) bertransisi halus saat di-hover dengan pergeseran `-1px translateY` dan bayangan lembut.
   * Logo tautan membesar secara proporsional (`scale(1.05)`).
3. **Custom Confirmation Modals**:
   * Dialog konfirmasi pengembalian alat dan reset data menggunakan *backdrop overlay* gelap dengan modal papirus yang melayang di tengah layar.

---
*MASTER PROMPT UI/UX DESIGN SYSTEM LABKEEPER — 2026*
