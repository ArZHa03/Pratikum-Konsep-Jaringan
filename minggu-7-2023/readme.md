3121600010 – Arga Rafi I.M  
3121600025 – Ahmad Shonhaji  
3121600023 – Arianto Zaki Hamdalah  


LAPORAN MINGGU-7 Instalasi DNS

## 1. **Update dan upgrade paket**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.001.png)

Dengan menggunakan perintah apt update dan apt upgrade akan mengupdate dan memperbarui daftar paket pada system

## 2. **Ubah Hostname**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.002.png)

Ubah nama hostname sesuai topologi, karena kami kelompok 2 maka nama hostnamenya yaitu : kampus-02.takehome.com

## 3. **Install Bind9**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.003.png)

Kita menginstal bind9 yang digunakan pada sistem Debian untuk mengelola dan menyediakan layanan DNS pada jaringan lokal atau internet.

## 4. **Install bind9utils**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.004.png)

Kita menginstal bind9utils untuk bisa menggunakan utilitas yang terkait dengan server DNS BIND9 seperti : dig, nslookup, rndc, dnssec-keygen dll.

## 5. **Konvigurasi DNS Server**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.005.png)

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.006.png)

Zone editor adalah fitur yang memungkinkan untuk membuat, edit, dan hapus DNS, dan ini adalah zone recordnya

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.007.png)

Zone sendiri adalah suatu wilayah atau domain yang dikelola oleh sebuah server DNS tertentu. Setiap zona DNS dapat berisi informasi mengenai nama domain, alamat IP, atau informasi lainnya yang terkait dengan domain tersebut.

## 6. **Setting file forward**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.008.png)

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.009.png)

Ada beberapa singkatan yang ada pada file forward :

|TTL|Time To Life adalah parameter yang menentukan berapa lama suatu catatan DNS (DNS record) akan di-cache oleh DNS resolver atau server yang meminta informasi tersebut.|
| - | - |
|IN|singkatan dari "Internet" yang menandakan kelas jaringan untuk catatan DNS. Nilai IN digunakan untuk semua catatan DNS dalam file forward DNS Debian.|
|SOA|singkatan dari "Start of Authority" yang digunakan untuk menentukan server DNS utama untuk domain dan informasi lainnya seperti email administrator DNS, serial number, dan parameter lainnya.|
|A|singkatan dari "Address" yang digunakan untuk menentukan alamat IPv4 untuk sebuah nama domain. Catatan A menghubungkan sebuah nama domain dengan alamat IPv4.|
|AAAA|singkatan dari "IPv6 Address" yang digunakan untuk menentukan alamat IPv6 untuk sebuah nama domain. Catatan AAAA menghubungkan sebuah nama domain dengan alamat IPv6.|
|NS|singkatan dari "Name Server" yang digunakan untuk menentukan server DNS yang bertanggung jawab untuk domain tertentu.|
|PTR|singkatan dari "Pointer" yang digunakan untuk menentukan sebuah nama domain berdasarkan alamat IP.|
|Serial|Parameter serial digunakan untuk menandai perubahan pada DNS zone. Setiap kali ada perubahan pada zone file, misalnya menambah, menghapus, atau mengubah catatan DNS, nilai serial harus ditingkatkan untuk menandakan perubahan tersebut. Nilai serial harus berupa bilangan bulat positif dan meningkat setiap kali terjadi perubahan pada DNS zone.|
|Refresh|Parameter refresh menentukan waktu dalam detik antara server DNS utama melakukan refresh pada zone file dan server DNS sekunder meminta pembaruan terbaru dari server utama. Jadi, refresh menandakan seberapa sering server sekunder meminta pembaruan dari server utama.|
|Retry|Parameter retry menentukan waktu dalam detik antara server DNS sekunder meminta pembaruan dari server DNS utama jika upaya pertama tidak berhasil. Jadi, retry menandakan berapa sering server sekunder mencoba memperbarui data dari server utama jika gagal pada upaya pertama.|
|Expire|Parameter expire menentukan waktu dalam detik setelah server sekunder harus menganggap data yang tersimpan dalam cache tidak valid lagi jika server DNS utama tidak tersedia. Jadi, expire menandakan seberapa lama data DNS yang disimpan dalam cache akan berlaku jika server utama tidak tersedia.|
|Negative Cache TTL|Parameter ini menentukan waktu dalam detik bahwa server DNS akan menyimpan hasil pencarian DNS yang gagal (misalnya, ketika domain tidak ada). Hal ini memungkinkan server DNS untuk menampung sementara informasi negatif dalam cache dan menghindari melakukan permintaan DNS yang berlebihan.|

Ubah localhost menjadi nama hostname yang sudah di setting sebelumnya

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.010.png)

## 7. **Buat file Reserve**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.011.png)

Buat file reserve dengan mengcopy file db.127 pada direktori yang sama dengan forward

` `![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.012.png)

Sama seperti sebelumnya ubah localhost menjadi hostname yang telah di setting dan juga ganti ip menjadi 249 sesuai dengan ip sebelumnya

## 8. **Tambahkan name server**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.013.png)

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.014.png)

Daftarkan IP dari Debian kedalam file resolv.conf

## 9. **Restart layanan DNS**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.015.png)

Setelah setting selesai lakukan restart untuk mengupdate setting yang telah di ubah

## 10. **Pindahkan file**

Sebelumnya kita menaruh file bind di etc, pindahkan kedalam folder chace yang berlokasi di computer/var/cache/bind, file yang dipindah yairu forward dan reverse

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.016.png)

## 11. **Pengecekan nslookup dan service**

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.017.png)

Terlihat bahwa dns yang dibuat sudah terdeteksi

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.018.png)

![](Aspose.Words.959c2954-c2de-4028-9abb-dca56bf5285c.019.png)

Service sudah berhasil running yang menandakan instalasi dns sudah selesai.
