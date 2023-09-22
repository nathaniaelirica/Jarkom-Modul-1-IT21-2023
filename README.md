# Praktikum Modul 1 Jarkom 2023

### Kelompok IT-21

* Maria Teresia Elvara Bumbungan (5027211042)
* Nathania Elirica Aliyah (5027211057)

### Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file. Di soal ini, kami diminta untuk mencari raw sequence number dan acknowledgement number dari request untuk mengunggah file dan response-nya. 

Untuk menyelesaikan soal ini, kami membuka file wireshark yang diberikan dan melakukan filtering dengan query `ftp || ftp-data`. Hal ini dilakukan untuk memfilter paket dengan protokol FTP sesuai timeline agar dapat menemukan paket yang melakukan request upload file dan response-nya dengan mudah. 

Selanjutnya, kami mencari command STOR sebab command ini merupakan command untuk mengunggah suatu file. Berikut hasil pencarian kami:

![Alt Text](https://i.ibb.co/7Jvh6MQ/soal-1.jpg)

Paket 147 merupakan request untuk mengunggah file dan paket 149 merupakan response-nya. Untuk mendapatkan raw sequence number dan acknowledgement number dari kedua paket tersebut, kami mengklik kedua paket tersebut dan menuju ke header Transmission Control Protocol. Setelah di-drop down, kami menemukan raw sequence number dan acknowledgement number-nya.

**Paket 147**

![Alt Text](https://i.ibb.co/2smhq3r/soal-1-req.jpg)

**Paket 149**

![Alt Text](https://i.ibb.co/19BVZXJ/soal-1-resp.jpg)

Setelah itu, kami melakukan ncat untuk memasukan jawaban yang kami temukan untuk mendapatkan flag. Dengan demikian, kami berhasil mendapatkan flag-nya.

![Alt Text](https://i.ibb.co/vJNVKQ5/soal-1-nc.jpg)

### Soal 2
__Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!__
 

![Teks alternatif](https://i.ibb.co/hcYLFVH/Whats-App-Image-2023-09-22-at-6-06-35-PM.jpg)

a. Untuk mengetahui server yang dijalankan, kami menggunakan curl -I http://10.21.78.111:8080, Ini akan meminta server untuk mengirimkan informasi header dari respons yang akan diterima seperti pada gambar. Ini termasuk status respons (seperti 200 OK atau 404 Not Found), tipe konten, tanggal, dan informasi header lainnya.

b. Lalu server diperlihatkan gunicorn.

c. Untuk mendapatkan flag, ketik nc 10.21.78.111 13579, lalu masukkan gunicorn setelah itu muncul flag yang diinginkan.

### Soal 3
Pada soal ini, kami diminta untuk mencari tahu berapa banyak paket yang tercapture dengan IP source maupun destination address 239.255.255.250 dengan port 3702 dan protokol layer transport apa yang digunakan.

Untuk menyelesaikan soal ini, kami melakukan filtering dengan query `ip.addr == 239.255.255.250 && udp.port == 3702`. Setelah itu, kami menemukan terdapat 21 paket yang muncul sesuai dengan query tadi.

![Alt Text](https://i.ibb.co/WPR4bPB/soal-3.jpg)

Berdasarkan hasil filtering tersebut, dapat terlihat juga bahwa protokol layer transport yang digunakan adalah UDP. Kami melakukan ncat untuk memasukkan kedua jawaban tersebut dan berhasil mendapatkan flag-nya.

![Alt Text](https://i.ibb.co/Jct5sZz/soal-3-nc.jpg)

### Soal 4
Pada soal ini, kami diminta untuk mencari tahu berapa nilai checksum yang didapat dari header pada paket nomor 130. Untuk menyelesaikan soal ini, kami melakukan filtering untuk mendapatkan paket nomor 130 dengan query `frame.number == 130`. Nilai checksum berada di header User Datagram Protocol. Kami men-drop down header tersebut dan menemukan nilai checksum-nya.

![Alt Text](https://i.ibb.co/wBQPmtc/soal-4.jpg)

Selanjutnya, kami melakukan ncat untuk memasukkan jawaban tersebut dan berhasil mendapatkan flag-nya.

![Alt Text](https://i.ibb.co/XZfJ8NH/soal-4-nc.jpg)

### Soal 7
__Berapa jumlah packet yang menuju IP 184.87.193.88?__

a. Buka di wireshark bagian filter dan ketik ip.dst == 184.87.193.88, tujuannya filter di Wireshark yang digunakan untuk menampilkan hanya paket-paket yang memiliki alamat tujuan  ke 184.87.193.88 dan ditampilkan 6 paket

![Teks alternatif](https://i.ibb.co/jHvpN90/image.png)
b. Lalu untuk menemukan flag ketik nc 10.21.78.111 6565, dan masukkan 6 lalu muncul flag

![Teks alternatif](https://i.ibb.co/mFJNwFc/image.png)

### Soal 8
Pada soal ini, kami diminta untuk memberikan query filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80 dan jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad.

Untuk menyelesaikan soal ini, kami langsung melakukan ncat untuk memasukkan jawaban yaitu, `tcp.dstport == 80 || udp.dstport == 80`. Query ini akan menampilkan seluruh paket yang menuju ke port 80 dengan protokol TCP maupun UDP. Setelah memasukkan jawaban, kami berhasil mendapatkan flag-nya.

![Alt Text](https://i.ibb.co/CJBjn2v/soal-8.jpg)

### Soal 9
__Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!__

![Teks alternatif](https://i.ibb.co/tZvJMbj/image.png)

a. Untuk menemukan flag, ketik nc 10.21.78.111 7272

b. Lalu masukkan ip.src == 10.51.40.1 && ip.dst != 10.39.55.34 untuk:

- Filter ini membatasi tampilan hanya pada paket-paket yang berasal dari alamat IP 10.51.40.1.Jika paket yang sedang ditangkap memiliki alamat sumber yang bukan 10.51.40.1, paket tersebut tidak akan muncul dalam hasil tampilan
- Filter ini memastikan bahwa paket-paket yang memiliki alamat tujuan (destination address) kecuali 10.39.55.34 akan ditampilkan.Jika paket yang sedang ditangkap memiliki alamat tujuan ke 10.39.55.34, maka paket tersebut tidak akan muncul dalam hasil tampilan.
e. Setelah itu, akan keluar flag nya


### Soal 10
__Buka wireshark, dan filter dengan telnet di wireshark__

a. Buka wireshark, dan filter dengan telnet di wireshark


![Teks alternatif](https://i.ibb.co/tpZRCQk/image.png)

b. Coba satu-satu dan cari dan ditemukan dengan username:password yaitu dhafin:kesayangannyak0k0

![Teks alternatif](https://i.ibb.co/Y7Gr3qg/image.png)

c. Lalu masukkan nc 10.21.78.111 7373 untuk mendapatkan flag

![Teks alternatif](https://i.ibb.co/6v4LqVX/image.png)
)
