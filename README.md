# LOTO Simulator, paket deploy Vercel

Isi paket:
- index.html  : seluruh aplikasi (satu berkas, mandiri, memuat three.js dari cdnjs dan font dari Google Fonts)
- vercel.json : header Permissions-Policy agar giroskop, layar penuh, dan WebXR diizinkan untuk mode VR

## Cara 1, Vercel CLI (paling cepat, 5 menit)

1. Pasang Node.js (https://nodejs.org) bila belum ada.
2. Buka terminal di folder ini, lalu:
   npm install -g vercel
   vercel login
   vercel --prod
3. Jawab pertanyaan: Set up and deploy? Y, pilih scope akun Anda, link to existing project? N,
   project name: loto-simulator, directory: ./ (tekan Enter), modify settings? N.
4. Vercel mencetak alamat produksi, misalnya https://loto-simulator.vercel.app

Setiap ada versi baru, cukup ganti index.html lalu jalankan lagi: vercel --prod

## Cara 2, lewat GitHub (deploy otomatis tiap perubahan)

1. Buat repositori baru di GitHub, unggah index.html dan vercel.json.
2. Buka https://vercel.com/new, pilih Import Git Repository, pilih repositori tadi.
3. Framework Preset: Other. Build Command dan Output Directory dikosongkan. Klik Deploy.
4. Setiap push ke branch utama akan otomatis dideploy.

## Domain sendiri

Di dashboard Vercel: Project > Settings > Domains > tambahkan misalnya loto.nusasafety.co.id,
lalu buat record CNAME di DNS domain Anda mengarah ke cname.vercel-dns.com sesuai instruksi yang tampil.

## Catatan mode VR

- HTTPS wajib untuk giroskop dan layar penuh; Vercel sudah HTTPS otomatis.
- Buka alamatnya di Chrome Android, pilih misi, tekan Mulai di VR, lalu pasang ponsel di headset.
- Bila giroskop tidak merespons, pastikan Chrome diizinkan mengakses sensor gerak
  (Chrome > Setelan > Setelan situs > Sensor gerak).
