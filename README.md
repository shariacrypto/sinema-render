# sinema-render

Mesin render pembantu untuk video Shariacrypto. Repo ini hanya berisi dua workflow:

- `.github/workflows/render.yml` membagi render frame video ke 8 mesin GitHub Actions.
- `.github/workflows/jaga.yml` (tiap 20 menit) memeriksa apakah ada video yang macet, lalu mengabari repo privat
  agar pemilik mendapat peringatan Telegram. Jadwal repo publik dimatikan GitHub setelah 60 hari tanpa commit.

- Dipicu oleh repo privat Shariacrypto; tidak bisa dijalankan orang lain (perlu akses tulis).
- Folder kerja dan mesin render diambil dari repo privat saat workflow berjalan, tidak disimpan di sini.
- Potongan video diunggah **terenkripsi** (AES-256) dan dihapus otomatis setelah 1 hari.

Secret yang dibutuhkan: `RENDER_TOKEN`, `SEG_KUNCI`.
