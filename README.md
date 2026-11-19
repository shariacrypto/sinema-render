# sinema-render

Mesin pembantu Shariacrypto yang memakai menit Actions gratis repo publik. Repo ini hanya berisi tiga workflow:

- `.github/workflows/render.yml` membagi render frame video ke 8 mesin GitHub Actions.
- `.github/workflows/deploy.yml` (tiap 30 menit, atau manual) menayangkan situs shariacrypto.id ke Cloudflare Pages
  bila `main` repo privat mengubah situs. Dipindahkan dari repo privat 19 Nov 2026 karena menit Actions repo privat habis.
- `.github/workflows/jaga.yml` (tiap 20 menit) memeriksa apakah ada video yang macet, lalu mengabari repo privat
  agar pemilik mendapat peringatan Telegram. Jadwal repo publik dimatikan GitHub setelah 60 hari tanpa commit.

- Dipicu oleh repo privat Shariacrypto; tidak bisa dijalankan orang lain (perlu akses tulis).
- Folder kerja dan mesin render diambil dari repo privat saat workflow berjalan, tidak disimpan di sini.
- Potongan video diunggah **terenkripsi** (AES-256) dan dihapus otomatis setelah 1 hari.

Secret yang dibutuhkan: `RENDER_TOKEN`, `SEG_KUNCI`; untuk deploy situs juga `CLOUDFLARE_API_TOKEN`,
`CLOUDFLARE_ACCOUNT_ID`, dan (opsional) `COINGECKO_API_KEY`, dengan nilai yang sama seperti di repo privat.
