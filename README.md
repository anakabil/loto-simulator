# LOTO Simulator, paket deploy Vercel

Isi paket:
- index.html  : seluruh aplikasi (satu berkas, mandiri, memuat three.js dari cdnjs dan font dari Google Fonts)
- vercel.json : header Permissions-Policy agar giroskop, layar penuh, dan WebXR diizinkan untuk mode VR
- vo/         : rekaman suara dialog (MP3, nama berkas sesuai ID naskah, misalnya PJA-001.mp3).
                Dimuat per misi saat misi dimulai. Folder ini harus selalu berada di samping index.html.

## Cara 1, Vercel CLI (paling cepat, 5 menit)

1. Pasang Node.js (https://nodejs.org) bila belum ada.
2. Buka terminal di folder ini, lalu:
   npm install -g vercel
   vercel login
   vercel --prod
3. Jawab pertanyaan: Set up and deploy? Y, pilih scope akun Anda, link to existing project? N,
   project name: loto-simulator, directory: ./ (tekan Enter), modify settings? N.
4. Vercel mencetak alamat produksi, misalnya https://loto-simulator.vercel.app

Setiap ada versi baru, ganti index.html dan isi folder vo/, lalu jalankan lagi: vercel --prod

## Cara 2, lewat GitHub (deploy otomatis tiap perubahan)

1. Buat repositori baru di GitHub, unggah index.html, vercel.json, dan folder vo/.
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

## Alur pembaruan saat ini

Repositori ini (github.com/anakabil/loto-simulator) sudah tersambung ke proyek Vercel loto-simulator.
Setiap versi baru didorong langsung ke branch main, lalu Vercel mendeploy otomatis.
Riwayat versi bisa dilihat di tab Commits, dan versi lama bisa dipulihkan dari sana bila perlu.
