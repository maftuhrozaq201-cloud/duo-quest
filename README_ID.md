# DUO QUEST 30 Hari — PWA

Aplikasi game kebiasaan sehat pasangan dengan misi harian, XP, level, achievement, dan hadiah yang bisa ditukar. Tampilan berbahasa Indonesia, cute pastel.

## Yang sudah tersedia
- 30 hari misi (6 misi per hari), misi bisa dicentang/uncentang.
- XP dan poin hadiah, level, achievement.
- Hadiah bawaan dan hadiah buatan sendiri.
- Mode lokal bisa langsung dicoba.
- Sinkronisasi dua HP memakai Firebase Authentication anonim + Cloud Firestore.
- PWA installable dan cache dasar untuk membuka aplikasi kembali saat offline. Sinkronisasi tetap butuh internet.

## Penting
Mode lokal langsung berfungsi, tetapi **tidak** tersinkron ke HP kedua. Untuk sinkronisasi online, kamu perlu membuat proyek Firebase sendiri dan meng-host file ini lewat HTTPS. Aku tidak bisa membuat proyek Firebase atas namamu atau menerbitkan aplikasi ke akunmu dari sini.

## A. Aktifkan sinkronisasi Firebase (gratis sesuai kuota layanan)
1. Buka https://console.firebase.google.com/ lalu buat project baru.
2. Di Project settings, tambahkan Web App (ikon `</>`). Salin konfigurasi Firebase.
3. Buka file `firebase-config.js`, ganti seluruh nilai `ISI_...` dengan nilai konfigurasi dari Firebase Console.
4. Firebase Console → Authentication → Get started → Sign-in method → aktifkan **Anonymous**.
5. Firebase Console → Firestore Database → Create database.
6. Buka tab Rules dan ganti rules dengan isi file `firestore.rules`, lalu Publish.
7. Simpan perubahan file. **Jangan bagikan kode ruang**; siapa pun yang mengetahui kode ruang bisa mengakses data ruangan dengan rules sederhana ini. Simpan hanya progres game, bukan data sensitif.

## B. Publikasikan supaya bisa dipasang di Android
Cara mudah: GitHub Pages
1. Buat akun/login di https://github.com/ dan buat repository baru, misalnya `duo-quest`.
2. Unggah seluruh isi folder ini ke root repository (jangan unggah folder ZIP-nya sebagai satu file).
3. Repository → Settings → Pages → pilih `Deploy from a branch`, branch `main`, folder `/(root)`, lalu Save.
4. Tunggu sampai GitHub Pages memberi URL HTTPS, misalnya `https://USERNAME.github.io/duo-quest/`.
5. Buka URL itu di Chrome Android. Pastikan `firebase-config.js` sudah diisi sebelum menghubungkan ruang.

Alternatif hosting HTTPS juga boleh, asalkan semua file dalam folder diunggah bersama.

## C. Pasang di HP kamu dan pasangan
1. Buka URL HTTPS aplikasi di Chrome Android.
2. Tekan menu tiga titik `⋮` → **Tambahkan ke layar utama** atau **Install app** (teks bisa berbeda).
3. Ulangi di HP pasangan.
4. Di HP pertama, masukkan kode ruang rahasia (minimal 4 karakter, disarankan kombinasi unik) lalu tekan **Sambungkan ruang**.
5. Di HP kedua, masukkan **kode yang persis sama** dan tekan **Sambungkan ruang**.
6. Centang misi dari salah satu HP; data seharusnya ikut muncul di HP lain saat online.

## Jika gagal
- Pastikan URL memakai HTTPS, bukan `file://`.
- Pastikan `firebase-config.js` berisi konfigurasi yang benar.
- Pastikan Authentication Anonymous aktif dan Firestore sudah dibuat.
- Pastikan rules Firestore sudah dipublikasikan.
- Buka ulang aplikasi setelah mengubah konfigurasi.
- Mode lokal tetap bisa dipakai jika belum menyiapkan Firebase.

## Catatan kesehatan
Misi bersifat ringan dan fleksibel, bukan target penurunan berat badan. Ubah atau lewati misi sesuai kondisi tubuh. Tidak ada hukuman atau streak yang putus.
