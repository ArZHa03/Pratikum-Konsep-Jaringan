
3121600010 – Arga Rafi I.M
3121600025 – Ahmad Shonhaji

3121600023 – Arianto Zaki hamdalah


LAPORAN MINGGU-6 DNS

1. ETC HOSTNAME

Ketikkan pada console terminal seperti gambar dibawah

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.001.png)

Pada perintah diatas baris pertama berfungsi untuk mengeset hostname.

Pada baris kedua tes print namahost untuk pengecekan.[^1]

1. ETC HOST

Ketikkan pada cli perintah berikut ini lalu akan membuka file hosts.

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.002.png)

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.003.png)

Pada gambar diatas dapat diakses dengan perintah bisa dengan nano/gedit atau editor yang lain, contoh : gedit /etc/hosts.

Lalu tambahkan ip dari setiap router kelompok lain bagian interface ethernet 1 seperti gambar diatas.

Setelah selesai menambahkan ip kelompok lain maka akan dilakukan tes ping. Dengan menggunakan command #ping rt01 dan nanti akan diarahkan ke ip sesai daftar ip diatas. 

1. ETC NS SWITCH

Ketikkan pada console seperti di bawah

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.004.png)

Maka akan membuka edit untuk file nsswitch.conf

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.005.png)

Pada baris ke 12 bisa di balik tetapi secara default akan mengakses file hosts sebelumnya

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.006.png)

Pengujian dilakukan dengan menambahkan ip PENS namun di daftarkan dengan nama domain [www.kompas.com](http://www.kompas.com)

Pada pengetesan dengan browser kita mencoba membuka domain [www.kompas.com](http://www.kompas.com) maka yang muncul adalah website PENS seperti gambar dibawah

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.007.png)

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.008.png)

1. FLOW DNS

![](Aspose.Words.5a3d84ed-f862-482d-a755-44c82fe087df.009.png)


[^1]: 