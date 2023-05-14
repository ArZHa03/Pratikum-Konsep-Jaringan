
# Kelompok – 2
3121600010 – Arga Rafi I.M
3121600023 – Arianto Zaki Hamdalah
3121600025 – Ahmad Shonhaji

## Instalasi Laravel dan Deployment

### 1. Install composer terlebih dahulu pada website ini https://getcomposer.org/
   lalu ketikkan pada terminanl
- curl -sS https://getcomposer.org/installer | php

Pastikan Composer dapat digunakan dan dijalankan secara global. Tambahkan perintah di bawah ini.

- sudo mv composer.phar /usr/local/bin/composer
- sudo chmod +x /usr/local/bin/composer

## 2. Install Laravel dengan menggunakan composer
![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.001.png)

Setelah Laravel terinstall ketikkan php artisan serve untuk mengaktifkan server Laravel, dan bisa dilihat di localhost akan menampilkan template laravel

![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.002.png)![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.003.png)

## 3. Deployment Laravel
Pindah folder Laravel ke var/www/html/
- sudo mv kel-02 /var/www/html/

Lalu atur permission untuk memastikan proyek dapat berjalan tanpa masalah:
- sudo chmod -R 775 /var/www/html/kel-02/storage

Buat virtual host baru untuk proyek ini dengan menjalankan perintah berikut:
![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.004.png)

Maka akan terbuka laravel\_project.conf dengan menggunakan nano
![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.005.png)

Pada gambar terlihat saya menambahkan public setelah html/ dan ganti thedomain.com dengan nama server kelompok masing masing, lalu simpan dan tutup file.

Refresh file konfigurasi virtual host di Apache dengan menjalankan perintah ini:

- sudo a2dissite 000-default.conf
- sudo a2ensite laravel\_project

Aktifkan Apache rewrite module, lalu restart layanan Apache:

- sudo a2enmod rewrite
- sudo systemctl restart apache2

Maka saat membuka domain kampus-02 akan muncul template Laravel
![](Aspose.Words.b3462b2d-22c8-4349-ac75-633b7e683105.006.png)







