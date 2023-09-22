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

### Soal 8
Pada soal ini, kami diminta untuk memberikan query filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80 dan jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad.

Untuk menyelesaikan soal ini, kami langsung melakukan ncat untuk memasukkan jawaban yaitu, `tcp.dstport == 80 || udp.dstport == 80`. Query ini akan menampilkan seluruh paket yang menuju ke port 80 dengan protokol TCP maupun UDP. Setelah memasukkan jawaban, kami berhasil mendapatkan flag-nya.

![Alt Text](https://i.ibb.co/CJBjn2v/soal-8.jpg)

### Soal 9

### Soal 10
