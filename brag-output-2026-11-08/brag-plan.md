# Brag Plan: LabKeeper

## What is this app?
Sistem manajemen peminjaman alat laboratorium sekolah berbasis QR Code (Flask + SQLite), multi-sekolah, dengan verifikasi dua langkah — dibuat sebagai project sekolah.

## The angle
"Alat lab hilang dan tidak ada catatan" — masalah nyata setiap lab sekolah — diselesaikan dengan satu scan QR. Video presentasi sekolah berbahasa Indonesia dengan narasi suara.

## Hook (first 2-3 seconds)
"Alat lab hilang… dan tidak ada yang tahu siapa yang terakhir memakainya?" — teks besar + stempel merah "TIDAK ADA CATATAN".

## Key moments (the middle)
- Siswa scan QR → kartu peminjaman tercatat + countdown WIB berjalan.
- Dashboard bento admin: 4 stat cards (Total Alat / Tersedia / Dipinjam / Telat) muncul satu-satu.
- Verifikasi dua langkah: konfirmasi siswa → verifikasi admin, dua centang hijau.
- Stack: Flask 3.0, SQLite, Multi-Sekolah.

## Outro / punchline
QR code repositori GitHub tampil besar: "Scan untuk buka repo" — "LabKeeper. Pinjam, pantau, kembalikan."

## User flow worth showing
Scan QR alat (kamera HP) → konfirmasi pinjam → verifikasi admin → countdown aktif. Direkayasa ulang sebagai mockup phone frame.

## Tone
- Preset: polished
- Creative direction: presentasi project sekolah yang rapi dan meyakinkan, guru dan teman sekelas sebagai penonton
- Interpretation: pacing santai (narasi Bahasa Indonesia), gerak bersih, banyak hold, tanpa efek berlebihan

## Format: landscape — 1920x1080
## Duration: ±67 detik (kebutuhan sekolah: minimal 60 detik; melebihi jendela 15-25 detik default atas permintaan eksplisit)

## Visual identity (from the project)
- Background: #F8F9FA (paper) / kartu #FFFFFF
- Text: #000000 (ink), sekunder #4B5563
- Accent: #059669 (dikembalikan/ok), #DC2626 (telat)
- Display font: Playfair Display
- Body font: Inter
- Mono: JetBrains Mono
- Elemen visual terkuat: bento grid kartu admin, badge status, countdown mono, logo labkeeper

## Share copy (draft)
LabKeeper — pinjam alat lab cukup scan QR. Project sekolah, open source: github.com/Hanzyzy/labkeeper-public

## Audio direction
- Role: warm bed + narasi
- Music: happy-beats-business-moves-vol-1 (bundled), volume rendah ±0.18, duck implicit (narration on separate tracks)
- SFX: sparse — klik untuk card arrivals, scan beep untuk QR
- Restraint rule: musik tidak boleh menutupi narasi

## Voiceover script (Bahasa Indonesia, id-ID-ArdiNeural)
- s1 (5.3s): "Pernah kehilangan alat laboratorium, dan tidak ada yang tahu siapa yang terakhir memakainya?"
- s2 (7.9s): "Kenalkan, LabKeeper. Sistem manajemen peminjaman alat laboratorium sekolah, berbasis QR Code."
- s3 (8.9s): "Siswa cukup memindai QR code pada alat, konfirmasi, dan peminjaman langsung tercatat. Countdown waktu berjalan otomatis."
- s4 (8.3s): "Pengelola lab memantau semuanya lewat dashboard: total alat, tersedia, dipinjam, dan yang telat, secara real-time."
- s5 (6.3s): "Peminjaman dan pengembalian diverifikasi dua langkah, jadi datanya selalu akurat dan bisa dipercaya."
- s6 (5.9s): "Dibangun dengan Flask dan SQLite, mendukung banyak sekolah dengan data yang terisolasi sepenuhnya."
- s7 (3.7s): "Dan semua kode sumbernya, terbuka di GitHub."
- s8 (8.7s): "Pindai QR code ini untuk membuka repositorinya. LabKeeper. Pinjam, pantau, kembalikan."

## Storyboard
### Scene 1 — Hook masalah — 7s (0–7)
Teks display besar "Alat lab hilang…?" di paper bg, stempel merah miring "TIDAK ADA CATATAN" menempel keras (rotate+scale). Audio intent: narasi s1 mulai 0.8s; SFX stamp impact. Transition: clean → Scene 2.

### Scene 2 — Reveal logo — 9s (7–16)
Logo LabKeeper besar + wordmark Playfair "LabKeeper" + tagline Inter. Reveal fade-up halus. Narasi s2 di 7.8s. Transition: soft → Scene 3.

### Scene 3 — Alur siswa — 10.5s (16–26.5)
Phone frame: frame scan + QR alat (MTR-001), lalu kartu peminjaman slide-in dengan kode mono "MTR-001", countdown mono "02:59:41" berjalan (count-up teks deterministik via GSAP). Narasi s3 di 16.8s. Transition: slide → Scene 4.

### Scene 4 — Dashboard admin — 10s (26.5–36.5)
Bento grid 4 stat cards (Total Alat 42 / Tersedia 28 / Dipinjam 12 / Telat 2) muncul satu per satu, badge status warna. Narasi s4 di 27.3s. Transition: clean → Scene 5.

### Scene 5 — Verifikasi dua langkah — 7.5s (36.5–44)
Dua kartu langkah: "1. Konfirmasi Siswa" → "2. Verifikasi Admin", centang hijau (#059669) muncul berurutan. Narasi s5 di 37.3s. Transition: soft → Scene 6.

### Scene 6 — Tech stack — 7.5s (44–51.5)
Chip stack: Flask 3.0 · SQLite · QR Code · Multi-Sekolah, slide-in satu per satu. Narasi s6 di 44.8s. Transition: clean → Scene 7.

### Scene 7 — Open source — 5s (51.5–56.5)
"Open Source" besar + mono "github.com/Hanzyzy/labkeeper-public". Narasi s7 di 52.3s. Transition: soft → Scene 8.

### Scene 8 — Outro QR — 10.5s (56.5–67)
Kartu putih berisi QR code repo besar + logo + "Scan untuk buka repo" + tagline akhir. Hold penuh. Narasi s8 di 57.8s. Musik fade-out 3s terakhir.

**Music mood:** upbeat profesional, volume rendah.
**Audio summary:** narasi Bahasa Indonesia memandu 8 scene, musik hangat di bawahnya, SFX tipis di momen reveal.
