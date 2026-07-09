# Jangan Lupa Hapus Komen Saat Seeding Database Baru!

# Tambahkan source seeders lain pada line 26 DatabaseSeeder!

# Kurang Tabel Setoran dan Penarikan

# Relation pada model jenis sampah, setoran, dan, nasabah belum ditambahkan

# Jangan lupa buat SRS kalo ada waktu

# Seeder setoran belum dibuat

# Ketika pull project dari github, jangan lupa:
1. composer install
2. cp .env.example .env (Sesuaikan konfigurasinya dulu.)
3. php artisan key:generate

1. php artisan migrate
2. php artisan db:seed

1. npm install
2. npm run dev


=============================================================================
Yafi, 16/05/26
-Menambahkan laravel breeze untuk menampilkan UI login
-Breeze stack blade with alphine
-Test framework pest(original)

Tentang migrasi:
Migrasi akan lebih baik jika tidak dilakukan secara bersama-sama (batch)
Migrasi satu persatu lebih baik, dan terkoordinir secara urutan sehingga memudahkan untuk rollback

Tentang seeder:
Database seeder tidak langsung menyambung atau mengerti arah seedernya mau di bawa ke tabel apa, 
maka dari itu kamu perlu menambahkan model yang terkait dengan tabel yang kamu ingin isi, misalnya:
`use App/Models/Produk;`

`bcrypt`
Adalah semacam mekanisme hashing untuk menghindari bruteforce, lebih tepatnya algorimta yang berjalan
searah, artinya karakter yang sudah di konversi ke
hash tidak bisa dikembalikan ke bentuk karakter aslinya

_Setup auth sederhana berhasil dibuat, 16:00_
=============================================================================
Yafi, 16/05/2026
-Menambahkan controller untuk CRUD nasabah
**Eloquent** => Adalah Object Relational Mapping (ORM) yang merepresentasikan:
# Tabel sebagai model
# Baris data sebagai objek
Apa maksudnya? Aku ngga tau.

-file .blade.php harus dibuat manual ya! (kecuali login xixixi)

Daftar nasabah sudah bisa dilihat di /nasabah, btw pake Eloquent bukan Query Builder
menyesuiakan materi pak miftah.

Ada paket bootstrap yang di install tapi belum di setting config import, npm run dev (compile dengan vite)
Pada ui blade dipakaikan bootstrap untuk styling yang di panggil lewat CDN

Let's call it a day! _17/05/26, 00:45_

Class penarikan masih jadi kosong lagi tuh!
=============================================================================
Yafi, 17/05/2026
-Melanjutkkan menambahkan controller untuk CRUD nasabah
-Fokus pada bagian create/input

Kemarin lupa mencatatat, sudah ada dua data dummy yang bisa untuk demo
Bingung di bagian `Nasabah::create`, salahnya ditulis `created`
Sekarang, fungsi _Create_ sudah bisa di pakai.
Selanjutnya untuk membuat nomor rekening di variabel no_rekening yang sekarang, sementara di setel **NULL**

Blade templating enggine, templating enggine bawaan laravel yang bertugas memisahkan logika backend dengan tampilan HTML. Contohny sintaks `{{ $var }}`

Let's call it a day! _17/05/2026 , 23:35_

=============================================================================
Letak repo projek SIBASI dari akun github tiana di pindah ke akun github yafi.

_19/05/2026, 20:55_

<!-- Nothing to report -->

_18/06/2026. 20:10_

Merge conflict karena merubah repo lokal dan keduluan commit sama yang lain. Lebih tepatnya dipersilahkan mendahului.

=============================================================================
tgl/wak: 21/06/2026. 18:38

Yafi lagi...
Terdapat beberapa penyesuaian di sini. pada controller function edit, store-pada with dan penambahan generator nomor rekening.
juga pada `->with` pada redirect diganti menjadi satu, untuk mendeteksi dan menampilkan error lebih susah dari yang diperkirakan.

untuk struktur file nasabah juga diubah sesuai sidebar yang dibuat pada rancangan awal,
maka akan jadi seperti ini:
../public/nasabah
nasabah
|---index.blade.php
|---create.blade.php
|---edit.blade.php (update)

terdapat kesalaham pada tabel view nasabah, ada yang tertukar dan tidak urut, sudah di selesaikan.

pada tahap ini fungsi CRUD pada modul nasabah, telah diselesaikan.

Btw, tampilan website home yang dikerjakan rekan-rekan juga bagus (ngga bohong, entah disitu terlibat kating atau tidak)

Sedang berkerja pada sub modul jenis sampa
TO-DO List:
1. ~~Ganti struktur tabel sesuai yang direkomendasikan CO-Pilot~~
2. Pada modul nasabah: create, edit tambahkan layout app pada sidebar dan header

=============================================================================
tgl/wak: 22/06/2026. 23:50

Menambahkan pembaruan pada struktur tabel jenis sampah

Pada state ini, CRUD pada jenis sampah telah diselesaikan.

Beberapa hal yang perlu ditambahkan:
1. ~~Kolom status
2. Kolom Deskripsi
3. Kolom Aktif
4. Mengubah layout tabel menjadi card

=============================================================================
tgl/wak: 24/06/2026

Pada state ini semua unit manajemen telah berjalan sebagai MVP
beberapa hal ditambahkan

untuk jenis_sampah:
../public/jenis_sampah
|---create.blade.php
|---edit.blade.php
|---index.blade.php

untuk user:
../public/user:
|---create.blade.php
|---edit.blade.php
|---index.blade.php
|---reset.blade.php (Halaman tambahan untuk reset password)

Pada state ini yang perlu ditambahkan adalah:
1. Hapus user
2. Mengahpus user otomatis yang dibuat laravel
3. Menambahkan pagination
4. Menambahkan autentikasi tambahan untuk admin, batasan untuk petugas
5. Merapikan header bawaan, dan mengganti ke header section
6. Tambahkan pagination pada nasabah
7. Menambahkna ikon plus pada fitur tambah

User tidak bisa dihapus karena dikhawatirkan mempengaruhi relasi

Pada sesi sebelumnya, telah ditambahkan status dan deskripsi pada jenis sampah,
namun belum ditampilkan.

mempercantik tampilan sub modul user, dengan menambahkan _fontawesome_

=============================================================================
tgl/wak: 25/06/2026

Re-order pada tabel migrasi, jenis sampah turun ke setelah nasabah

Pengerjaan submodul transaksi: penarikan dan setoran
Pembuatan hierarki pada penarikan dan setoran.
../public/view/penarikan
|---create blade php
|---index blade php

../public/view/setoran
|---create blade php
|---index blade php

Sekaligus controller pada kedua sub modul tersebut telah dibuat, minimal.

To-do list:
1. Menghapus header pada setiap submodul
2. Menambahkan method delete/destroy pada submodul setoran
3. Menambahkan pagination

Model juga diberi relasi ke masing2nya, sehingga fungsi utama aplikasi dapat berjalan dengan baik.

Pembuatan modul statistik dengan chart.js: line pada fokus:
1. Setoran (berat)
2. Penarikan (Jumlah)

Mendapati masalah pada keasalahan penulisan nama field, field di atas adalah yang benar.
pada `querySetoran` dab `queryPenarikan` yang digunakan untuk penentuan fungsi tanggal
diclone deengan method clone (clone $queryName)->whereMonth ...

Pengambilan data dilakukan dengan loop.

Malasah intelphense yang tidak mendeteksi kode dengan baik, tidak diselesaikan 
dan diabikan. Soululsi penutupan kode @json dengan kutip satu membuat label menjadi rancu

=============================================================================
tgl/wak: 26/06/2026

Pembuatan modul laporan dengan fungsi lihat dan cetak by bulan ke pdf

Hierarki pada modul laporan:
../public/view/laporan
|---index.blade.php (penampil)
|---pdf.blade.php (layout untuk ekspor file pdf)

Penggantian pada struktur navbar pada /layout/app.blade.php
dengan sidebar di kiri namun bersama dengan main content disebelah kanan
Navabar di atas fixed.

Keunggulan: Navabar bisa menyesuaikan ukuran content.
Kekurangan: Tampilan tidak terlalu cocok untuk website fungsional pada umumnnya

Masalah pada tata letak elemen navbar diselesaikan dengan kombinasi bootstrap flex dan grid

1. Menghapus header pada setiap submodul
2. Menambahkan method delete/destroy pada submodul setoran
3. Menambahkan pagination
4. Belum ada opsi hapus untuk setoran
5. Tambahkan filter untuk sub modul penarikan, tambah penarikan

tgl/wak: 09/07/2026

Project sibangsa telah diterima dosen.
Project sibangsa untuk memenuhi proyek pemrograman pemweb II, semester 4, Sistem Informasi, UNIPDU Jombang - telah dinyatakan SELESAI.
terima kasih untuk anggota kelompk yang telah berpartisipasi menyumbangkan waktu dan tenaganya demi merampungkan projetc ini.
