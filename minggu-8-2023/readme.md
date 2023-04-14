
Kelompok – 2

3121600010 – Arga Rafi I.M

3121600023 – Arianto Zaki Hamdalah

3121600025 – Ahmad Shonhaji


Membuat Web Server

1. Instalasi web server, php, dan database

Masukkan perintah dibawah untuk menginstall webserver (apache2), php dan database(mariadb-server).

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.001.png)

kemudian enter dan tunggu proses instalasi. Setelah itu akan muncul tampilan untuk mengatur webserver yang akan digunakan untuk phpMyAdmin

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.002.png)

pilih apache2 dengan tekan spasi, kemudian enter. Kemudian akan diarahkan lagi untuk mengatur	

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.003.png)

pilih yes dan enter dan tunggu sampai selesai.

Untuk mengecek apakah webserver sudah terinstall, masukkan perintah sudo systemctl status apache2

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.004.png)

**mariadb-server**

Pada langkah sebelumnya mariadb sudah berhasil terinstall, namun belum ada konfigurasi. Masukkan perintah dibawah untuk mengkonfigurasi

sudo mysql\_secure\_installation

Setelah di enter, maka akan dihadapkan beberapa pilihan konfigurasi seperti password dan lain-lain. Kemudian tunggu sampai proses selesai

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.005.png)

**Login User sebagai Root**

Pertama masuk ke root user dengan perintah

sudo mysql -u root password <password>

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.006.png)

















**Setting Apache.conf**

Buka file apache dengan command diabawah ini

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.007.png)

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.008.png)

Cari baris kode AccessFileName .htaccess. Jika di depannya ada tanda pagar (#) silakan dihapus.

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.009.png)

Kemudian temukan baris kode dengan script di bawah ini.

<Directory /var/www/>

`     `Options Indexes FollowSymLinks

`     `AllowOverride None

`     `Require all granted

</Directory>

Kemudian ganti kata “None” menjadi “All”

AllowOverride All

Selanjutnya aktifkan ModRewrite dengan mengetikkan perintah. “sudo a2enmod rewrite” setelah itu restart service dari apache.

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.010.png)


1. Instalasi Konfigurasi FTP server

**Install Package Proftpd**

Lakukan instalasi dengan memasukkan perintah

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.011.png)

Pada saat install proFTPD akan ada pertanyaan “Do you want to continue?[Y/n]”

Anda hanya perlu menekan "Y" dan enter, Maka proses install akan berjalan. perlu diingat computer harus connect pada internet.

**Melakukan Backup**

Sebelum mengedit file anda perlu melakukan backup paa file proftpd.conf dengan mengetikan perintah berikut.

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.012.png)

**Melakukan edit pada file proftpd.conf**

Untuk mengedit file proftpd.conf dengan mengetikan perintah berikut.

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.013.png)

**Menambah User FTP server**

Membuat user untuk ftp server agar bisa di akses oleh client di domain yang sama dan login menggunakan akun yang dibuat.

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.014.png)

**Pengujian FTP server**

Anda bisa menggunakan file exploler pada windows atau dengan file exploler lainnya.

jika anda menggunakan file exploler pada windows, anda dapat mengetikan alamat ip servic seperti berikut

![](Aspose.Words.a7060404-3148-4f3b-9dc3-0382026a3ce0.015.png)

Kemudian tekan Enter dan anda akan di arahkan untuk melakukan login dengan memasukkan username dan password.

Setelah itu masukan Username and Password anda lalu tekan Log On. dan selamat anda sudah dapat melakukan Upload file pada server.
