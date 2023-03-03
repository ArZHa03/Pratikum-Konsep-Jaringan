**Environment Linux Ubuntu**

1. **Kernel Linux**

Kernel dalam sistem operasi komputer adalah program yang berjalan di level paling dasar pada komputer dan bertanggung jawab untuk mengontrol seluruh proses yang berjalan pada sistem. Kernel bertindak sebagai jembatan antara perangkat keras komputer dan perangkat lunak (software) yang dijalankan pada sistem.

Kernel bertanggung jawab untuk mengatur penggunaan memori, manajemen proses, manajemen file system, pengaturan jaringan, dan akses terhadap perangkat keras seperti harddisk, printer, dan sebagainya. Kernel juga bertanggung jawab untuk menjaga keamanan sistem operasi dan mencegah pengguna yang tidak berwenang dari mengakses sumber daya sistem.

Untuk melihat informasi kernel pada sistem operasi Linux, Anda dapat menggunakan perintah "uname". Berikut ini adalah beberapa opsi yang bisa digunakan pada perintah "uname":

![](RackMultipart20230303-1-2gqkfn_html_43e63f005cc1092c.png)

- Untuk melihat versi kernel, gunakan opsi -r.
- Untuk melihat nama host komputer, gunakan opsi -n.
- Untuk melihat nama sistem operasi, gunakan opsi -o.
- Untuk melihat arsitektur CPU, gunakan opsi -m.
- Untuk melihat nama kernel, gunakan opsi -s.
- Untuk melihat informasi lengkap tentang kernel, gunakan opsi -a.

1. **Directory Structure**

Directory Structure pada sistem operasi Linux Ubuntu memuat sejumlah direktori yang digunakan untuk menyimpan berbagai jenis file dan konfigurasi pada sistem. Setiap direktori dalam struktur memiliki fungsi dan kegunaannya masing-masing. Berikut ini adalah beberapa direktori penting dalam struktur direktori Linux Ubuntu:

![](RackMultipart20230303-1-2gqkfn_html_38bd927e2d87d41e.png)

1. / : direktori root atau direktori utama pada sistem operasi. Semua direktori lainnya berada di bawah direktori ini. Di dalam direktori root, terdapat berbagai file sistem yang penting, seperti file konfigurasi boot loader dan file sistem yang digunakan oleh kernel.
2. /bin : direktori yang berisi file executable atau file biner yang digunakan oleh sistem operasi dan pengguna untuk menjalankan program.
3. /boot : direktori yang berisi file yang diperlukan untuk booting sistem, seperti file konfigurasi bootloader, kernel, dan initramfs.
4. /dev : direktori yang berisi file perangkat atau file karakter dan blok yang merepresentasikan perangkat keras pada sistem, seperti harddisk, CD-ROM, atau printer.
5. /etc : direktori yang berisi file konfigurasi sistem operasi dan aplikasi yang diinstal pada sistem.
6. /home : direktori yang berisi direktori home (rumah) dari setiap pengguna yang terdaftar pada sistem. Direktori home digunakan untuk menyimpan file pribadi dan konfigurasi pengguna.
7. /lib : direktori yang berisi file library yang digunakan oleh sistem operasi dan aplikasi yang diinstal pada sistem.
8. /media : direktori yang berisi mount point atau titik pemasangan untuk perangkat penyimpanan eksternal seperti USB flash drive atau CD-ROM.
9. /mnt : direktori yang berisi mount point atau titik pemasangan untuk sistem file yang dimount secara manual.
10. /opt : direktori yang berisi aplikasi yang diinstal secara manual oleh pengguna atau administrator sistem.
11. /proc : direktori yang berisi informasi tentang proses yang berjalan pada sistem operasi. Informasi ini disimpan dalam bentuk file virtual.
12. /root : direktori home (rumah) untuk pengguna root atau superuser pada sistem.
13. /run : direktori yang berisi file runtime seperti file socket dan file PID.
14. /sbin : direktori yang berisi file executable atau file biner untuk sistem atau superuser yang digunakan untuk mengkonfigurasi sistem atau mengatur aplikasi pada sistem.
15. /srv : direktori yang berisi data atau file yang digunakan oleh layanan (service) yang dijalankan pada sistem.
16. /tmp : direktori yang digunakan untuk menyimpan file sementara atau temporary.
17. /usr : direktori yang berisi file executable, file library, dan file data yang digunakan oleh pengguna pada sistem.
18. /var : direktori yang berisi file variable atau file data yang dapat berubah-ubah ukurannya. Direktori ini umumnya digunakan untuk menyimpan log, file cache, dan file data yang dapat berubah ukuran yang dihasilkan oleh aplikasi.

Struktur direktori pada Linux Ubuntu dapat diakses melalui terminal atau file manager. Setiap pengguna sistem operasi Linux Ubuntu harus memahami struktur direktori ini untuk dapat mengelola file dan konfigurasi sistem dengan baik.

1. **Perbedaan sudo dan su**

Di sistem operasi Linux, terdapat dua perintah utama yang digunakan untuk menjalankan perintah sebagai superuser atau root, yaitu "sudo" dan "su". Berikut ini adalah penjelasan lengkap mengenai kedua perintah tersebut:

1. "sudo"

Perintah "sudo" (superuser do) digunakan untuk menjalankan perintah sebagai superuser atau root dengan memasukkan password pengguna yang mempunyai hak akses sebagai superuser. Perintah ini sangat berguna untuk mencegah penggunaan perintah sebagai superuser secara tidak sengaja, sehingga dapat mengurangi risiko kesalahan pengguna dalam penggunaan sistem operasi. Contoh penggunaan perintah "sudo":

sudo apt-get update

Penjelasan: Perintah di atas digunakan untuk menjalankan perintah "apt-get update" sebagai superuser. Sebelumnya, sistem akan meminta pengguna memasukkan password sebagai tanda pengguna memiliki hak akses sebagai superuser.

1. "su"

Perintah "su" (switch user) digunakan untuk mengganti identitas pengguna menjadi superuser atau root tanpa memasukkan password superuser. Pengguna harus memasukkan password pengguna saat ini untuk menjalankan perintah sebagai superuser atau root. Perintah "su" sangat berguna untuk menghindari penggunaan perintah sebagai superuser secara tidak sengaja dan untuk menghindari penggunaan password superuser yang sering kali dianggap tidak aman. Contoh penggunaan perintah "su":

su -

Penjelasan: Perintah di atas digunakan untuk mengganti identitas pengguna menjadi superuser atau root. Tanda "-" digunakan untuk mengganti direktori kerja menjadi direktori home dari superuser. Setelah pengguna memasukkan password pengguna saat ini, pengguna dapat menjalankan perintah sebagai superuser.

![](RackMultipart20230303-1-2gqkfn_html_f93a69e61bda0e05.png)

Kesimpulan: Kedua perintah "sudo" dan "su" digunakan untuk menjalankan perintah sebagai superuser atau root. Perbedaan utama antara kedua perintah tersebut adalah pada cara akses hak akses superuser. Perintah "sudo" meminta pengguna memasukkan password pengguna yang mempunyai hak akses sebagai superuser, sedangkan perintah "su" meminta pengguna memasukkan password pengguna saat ini sebelum dapat menjalankan perintah sebagai superuser.

1. **Jenis Repository Bawaan pada Linux Ubuntu**

Repository pada sistem operasi Linux Ubuntu adalah tempat dimana software package (perangkat lunak) disimpan dan tersedia untuk diunduh dan diinstall oleh pengguna. Repository bawaan (default) pada Linux Ubuntu terdiri dari beberapa jenis, diantaranya adalah:

1. Main Repository Main Repository merupakan repository bawaan yang paling utama pada Linux Ubuntu. Repository ini berisi software package yang dikelola oleh Canonical, pengembang utama Linux Ubuntu. Software package di Main Repository telah diuji coba dan dijamin stabilitasnya, serta mendapatkan dukungan dari komunitas pengembang.
2. Universe Repository Universe Repository berisi software package yang tidak termasuk ke dalam Main Repository, tetapi tetap dikelola oleh komunitas pengembang Ubuntu. Software package di Universe Repository tidak dijamin stabilitasnya dan mendapatkan dukungan terbatas dari komunitas pengembang.
3. Restricted Repository Restricted Repository berisi software package yang tidak bersifat open-source (bersifat propietary) dan perlu lisensi khusus untuk penggunaannya. Software package di Restricted Repository diatur oleh undang-undang hak cipta dan dilindungi oleh hukum.
4. Multiverse Repository Multiverse Repository berisi software package yang tidak bersifat open-source dan mengandung kode-kode yang tidak dijamin keamanannya. Software package di Multiverse Repository sangat tidak disarankan untuk penggunaan pada sistem operasi yang membutuhkan keamanan tinggi.
   ![](RackMultipart20230303-1-2gqkfn_html_a0ff7cc35b3c25e7.png)

Untuk melihat daftar repository yang terpasang di sistem operasi Linux, Anda dapat membuka file "/etc/apt/sources.list" menggunakan text editor seperti nano atau vim. File tersebut berisi daftar repository yang terpasang pada sistem operasi Ubuntu. Berikut adalah langkah-langkahnya:

1. Buka terminal pada sistem operasi Linux Ubuntu Anda.
2. Jalankan perintah "sudo nano /etc/apt/sources.list" untuk membuka file sources.list menggunakan text editor nano.
3. Anda dapat melihat daftar repository yang terpasang pada sistem operasi Ubuntu di dalam file tersebut. Repository tersebut terdiri dari beberapa jenis seperti Main, Universe, Restricted, dan Multiverse Repository.
4. Jika ingin menambahkan repository baru pada sistem operasi Ubuntu, Anda dapat menambahkan baris baru pada file sources.list tersebut dengan format yang benar.
5. Jangan lupa untuk menyimpan perubahan pada file sources.list dan melakukan perintah "sudo apt-get update" agar daftar repository pada sistem operasi Anda terupdate.

Catatan: Sebelum melakukan perubahan pada file sources.list, pastikan Anda telah memahami konsekuensi dari perubahan tersebut. Salah penulisan pada file sources.list dapat menyebabkan sistem operasi menjadi tidak stabil atau bahkan mengalami kerusakan.

1. **Perintah apt**

Apt (Advanced Package Tool) merupakan sebuah perangkat lunak manajemen paket pada sistem operasi Linux yang digunakan untuk mengelola paket-paket pada sistem operasi Linux. Apt digunakan pada beberapa distribusi Linux, termasuk Ubuntu, Debian, dan Linux Mint. Apt digunakan untuk menginstal, menghapus, dan memperbarui paket-paket pada sistem operasi Linux secara mudah. Berikut adalah beberapa perintah yang sering digunakan pada Apt:

1. "apt-get update": perintah ini digunakan untuk memperbarui daftar paket yang tersedia dari repository.
2. "apt-get upgrade": perintah ini digunakan untuk meng-upgrade semua paket pada sistem operasi Linux ke versi yang terbaru.
3. "apt-get install [nama\_paket]": perintah ini digunakan untuk menginstal paket pada sistem operasi Linux.
4. "apt-get remove [nama\_paket]": perintah ini digunakan untuk menghapus paket dari sistem operasi Linux.
5. "apt-cache search [kata\_kunci]": perintah ini digunakan untuk mencari paket-paket yang memiliki kata kunci tertentu pada deskripsi paket.
6. "apt-get autoclean": perintah ini digunakan untuk menghapus paket yang sudah tidak dibutuhkan pada sistem operasi Linux.
7. "apt-get autoremove": perintah ini digunakan untuk menghapus paket yang tidak terpakai lagi pada sistem operasi Linux.

Selain itu, terdapat beberapa opsi lain yang dapat digunakan pada perintah apt, antara lain:

1. "-y": opsi ini digunakan untuk menyetujui semua permintaan konfirmasi pada saat penginstalan paket.
2. "-q": opsi ini digunakan untuk mengurangi jumlah output yang ditampilkan pada saat menjalankan perintah apt.
3. "-d": opsi ini digunakan untuk mendownload paket-paket pada repository tanpa melakukan instalasi.

![](RackMultipart20230303-1-2gqkfn_html_a31a873f7be96943.png)

Dalam penggunaan apt, kita juga dapat mengelola beberapa repository yang terpasang pada sistem operasi Linux. Untuk menambahkan repository baru pada sistem operasi Linux, kita dapat menambahkan baris baru pada file "/etc/apt/sources.list" dengan format yang benar.

Dalam penggunaan apt, penting untuk selalu melakukan update terhadap daftar paket pada repository agar paket-paket yang terinstal pada sistem operasi Linux selalu terbarui. Selain itu, penting juga untuk memeriksa dan memastikan paket yang akan diinstal atau dihapus dari sistem operasi Linux. Hal ini dilakukan agar sistem operasi Linux tidak rusak akibat kesalahan penggunaan perintah apt.
