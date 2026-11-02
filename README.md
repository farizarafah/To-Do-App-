# Papan Kerja Desain (Firebase + Vercel)

Isi folder: `index.html` (aplikasi), `firebase-config.js` (kamu isi), `firestore.rules` (aturan keamanan).
Tidak ada proses build, jadi cukup diunggah apa adanya.

## 1. Siapkan Firebase
1. Buka console.firebase.google.com, klik **Add project**, beri nama, Google Analytics boleh dimatikan.
2. **Build > Authentication > Get started > Google > Enable**, pilih email dukungan, Save.
3. **Build > Firestore Database > Create database**, pilih mode produksi dan lokasi terdekat (misalnya Jakarta). Lokasi tidak bisa diubah nanti.
4. **Project settings (ikon roda gigi) > Your apps > ikon web `</>`**, daftarkan aplikasi, lalu salin isi `firebaseConfig` ke `firebase-config.js`.
5. **Firestore > Rules**, tempel isi `firestore.rules`, ganti daftar email dengan email Google anggota tim, lalu **Publish**.

## 2. Coba di komputer sendiri
Jalankan di dalam folder ini: `python3 -m http.server 8000` (atau `npx serve`), lalu buka http://localhost:8000.
`localhost` sudah ada di daftar domain yang diizinkan Firebase.

## 3. Deploy ke Vercel
Lewat GitHub:
1. Buat repo baru di GitHub dan unggah ketiga file (jangan ada yang tertinggal).
2. Di vercel.com klik **Add New > Project**, pilih repo itu.
3. Framework Preset: **Other**. Kosongkan Build Command dan Output Directory. Klik **Deploy**.

Tanpa GitHub: jalankan `npx vercel` di dalam folder ini dan ikuti petunjuknya.

## 4. Izinkan domain Vercel
**Firebase > Authentication > Settings > Authorized domains > Add domain**, isi alamat dari Vercel (misalnya `papan-kerja.vercel.app`). Tanpa ini, tombol masuk Google akan gagal.

## Menambah anggota tim
Tambahkan email Google mereka di `firestore.rules` lalu Publish ulang. Nama mereka muncul di daftar penanggung jawab setelah mereka masuk sekali.

## Catatan
- Gambar referensi disimpan langsung di Firestore (diperkecil otomatis). Cukup untuk tim kecil, tapi cek batas paket gratis Firebase di situsnya sebelum dipakai ramai.
- Notifikasi tugas baru hanya muncul saat aplikasi dibuka.
