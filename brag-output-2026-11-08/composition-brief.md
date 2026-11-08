# Hyperframes Composition Brief: LabKeeper

## Objective
Video presentasi project sekolah untuk LabKeeper, durasi ±67 detik, narasi Bahasa Indonesia, ditutup QR code repo GitHub.

## Output
- Composition directory: `composition/`
- Rendered video: `brag.mp4`
- Format: landscape — 1920x1080
- Duration: 67 seconds (kebutuhan eksplisit user: minimal 60 detik — override jendela default 15-25s)

## Source Material
- Project root: `E:/codinggan/labkeeper-public`
- Primary files read: README.md, DESIGN_SYSTEM.md, models.py, templates/
- Product name: LabKeeper
- Tagline: "Pinjam alat lab cukup scan QR — pantau, kembalikan, selesai."
- Key UI to recreate: dashboard bento 4 stat cards (Total Alat/Tersedia/Dipinjam/Telat), badge status warna, countdown mono, phone scan frame
- Copy verbatim: "MTR-001", "Aktif / Kembali / Terlambat", "github.com/Hanzyzy/labkeeper-public", "Pinjam, pantau, kembalikan."

## Creative Direction
- Tone preset: polished
- Interpretation: presentasi sekolah — pacing mengikuti narasi, hold cukup, motion bersih, tanpa strobo
- Hook: "Alat lab hilang…?" + stempel merah "TIDAK ADA CATATAN"
- Outro: QR code repo + tagline
- Avoid: bahasa SaaS generik, filler abstrak

## Visual Identity
- Background: #F8F9FA; kartu #FFFFFF; border #E5E7EB
- Text: #000000 / #4B5563
- Accent: #059669 (ok), #DC2626 (telat)
- Display: Playfair Display; Body: Inter; Mono: JetBrains Mono (Google Fonts)
- Referensi: logo.png, gambar hero, bento grid admin, kode mono alat

## Storyboard
Gunakan storyboard lengkap di `brag-plan.md`. Ringkasan:
1. Hook masalah — 7s — stempel "TIDAK ADA CATATAN"
2. Reveal logo — 9s — logo + wordmark + tagline
3. Alur siswa — 10.5s — phone frame scan QR → kartu pinjam + countdown
4. Dashboard admin — 10s — 4 stat cards bento satu per satu
5. Verifikasi dua langkah — 7.5s — dua centang hijau
6. Tech stack — 7.5s — chips Flask/SQLite/QR/Multi-Sekolah
7. Open source — 5s — URL GitHub mono
8. Outro QR — 10.5s — QR repo besar, hold, fade out

## Audio
- Audio role: warm bed + narasi
- Music: assets/music/music.mp3 (bundled happy-beats vol-1), volume 0.18, fade-out 3s akhir
- Voiceover: assets/voice/s1..s8.mp3, track 3-10, volume 1, start per storyboard (0.8/7.8/16.8/27.3/37.3/44.8/52.3/57.8)
- SFX: sparse — klik card, scan beep, stamp impact (dari assets/sfx brag skill)
- Audio-reactive: none (durasi 67s, prioritas kejelasan narasi)

## Hyperframes Instructions
- Ikuti kontrak komposisi standar (data-start/data-duration, .clip, timeline GSAP paused di window.__timelines["main"])
- Semua logika deterministik (countdown dianimasikan via GSAP, tanpa Date.now/Math.random)
- `npx hyperframes check` harus lolos sebelum render
- Render: `npm run render` → brag.mp4
