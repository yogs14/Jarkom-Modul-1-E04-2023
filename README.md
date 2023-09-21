Lapres Praktikum Modul 1 
Wireshark

1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP.
   nc 10.21.78.111 12345
   Solving:
   Masuk ke dalam netcat dan perhatikan soal yang diinginkan! Berikutnya analisis lewat file packet capture yang diberikan.
![Windows PowerShell 9_21_2023 9_55_19 AM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/29dcc7d7-0bb1-4949-9db8-75c4d26feb05)

   Pada wireshark lakukan filter dengan keyword "FTP" karena clue yang diberikan oleh soal adalah aktivitas yang terjadi pada protokol FTP.
   Lalu, pusatkan perhatian pada "STOR" yang terdapat pada info paket yang terekam karena diduga kuat itu merupakan aktivitas yang dimaksud.
   ![soal 1 FTP](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/b52564f0-f8d7-41de-ba41-d6e7f3c361c5)

2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
   nc 10.21.78.111 13579
   Solving:
   Masuk ke dalam packet capture dan karena soal menginginkan server maka ikuti protokol http dari file pcap tersebut karena server pasti menempel pada protokol http
   ![Wireshark · Follow HTTP Stream (tcp stream eq 2) · Wi-Fi 9_18_2023 8_02_15 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/371d18eb-049c-4d0d-9f79-bdcb26c31a95)

3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
   nc 10.21.78.111 13590
   Solving:
   Masuk ke dalam netcat untuk mengetahui persis apa yang diminta. Setelah masuk, soal menginginkan kita untuk menghitung berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 
   239.255.255.250 dengan port 3702 maka kita lakukan analisis dengan melakukan filter menggunakan keyword "(ip.src ==   239.255.255.250  && udp.port == 3702) || (ip.dst 239.255.255.250 &&  tcp.port 3702)"
   ![soal no 3](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/8ce211ba-f1cb-4316-ae90-2ba1ef093a34)
   ![soal3 pcap 9_18_2023 8_11_39 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/1aa1e41b-0b64-47c4-a0db-e0a52f7dafc3)
   
   Lalu, hitung paket dengan menggunakan statistics lalu pilih packet length dan terapkan kembali display filter nya dan bisa dilihat panjang dari paket adalah 21
![Wireshark · Packet Lengths · soal3 (1) pcap 9_21_2023 5_07_24 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/4ba18292-e42e-4df0-bc92-53a949e7a196)

   Setelah itu, soal juga menanyakana protokol layer apa yang digunakan. Dan jelas jawabannya adalah UDP karena paket tersebut yang terekam.
   
4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?
   nc 10.21.78.111 13591
   Solving:
   Cari paket dengan nomer 130 lalu telusuri nilai checksum pada User Datagram Protocol
   ![Wireshark · Packet 130 · soal4 pcapng 9_18_2023 8_23_16 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/e89ef38e-7fd2-42c4-80c1-e0872c5be6a0)

5. Elshe menemukan suatu file packet capture yang menarik. Bantulah elshe untuk menganalisis file packet capture tersebut.
   Solving:
   Diberikan dua file berupa zip dan pcap, lalu kita coba analisis terlebih dahulu dari zip nya. Setelah coba diekstrak tampak bahwa file ini memerlukan password agar bisa diekstrak sepenuhnya.
   ![66% complete 9_21_2023 5_22_59 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/bba2ecad-c366-4259-9247-fe8118153998)

   Maka, selanjutnya coba kita analisis pada file pcap. Dan tampak sesuatu yang mencurigakan pada paket dengan protokol SMTP dimana pada bagian info terdapat seperti ada **"password"** yang tercapture. 
   Selanjutnya, coba kita ikuti arus paket TCP nya. Dan kita dapatkan sebuah pesan sebagai berikut. 
![Wireshark · Follow TCP Stream (tcp stream eq 0) · soal5 pcap 9_21_2023 5_29_15 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/6a584d8c-2a19-4dc8-baac-416d3e2a9edd)

   Terdapat sebuah string password dan kita diminta mendekrip string tersebut dengan BASE64. Maka, kita dekrip saja string tersebut dengan decoder BASE64 online sebagai berikut.
![Base64 Decode and Encode - Online - Google Chrome 9_18_2023 9_55_05 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/37845b13-c220-4d81-b99a-fce6f95a5c92)

   Dan kita dapatkan sebuah password "plain" yang utuh dan nampaknya dapat kita gunakan untuk meneruskan ekstrak file zip tadi secara utuh. Password sudah kita masukkan, selanjutnya kita mendapatkan sebuah file 
    berekstensi "txt".Di dalamnya, kita diminta untuk mengakses netcat dan menjawab soal dari netcat tersebut.
![connect txt - Notepad 9_18_2023 9_58_00 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/b867591a-c8fe-4d64-9d82-2f42daec51ee)

   Setelah kita mengakses netcat tersebut kita dapatkan soal-soal yang dibutuhkan untuk mendapatkan flag. Terdapat soal untuk menghitung berapa jumlah packet yang tercapture dalam file pcap tersebut yang mana 
   dapat kita hitung melalui urutan no pada bagian kiri karena semua paket tercapture adalah terurut. Selanjutnya, terdapat soal untuk menjawab port berapakah yang digunakan untuk service SMTP yang mana dapat 
   kita lihat pada Transmission Control Protocol yang merupakan "25". Terakhir, terdapat soal untuk menjawa IP berapakah yang public yang mana ini dapat kita lihat pada skema aktivitas yang terjadi di log info 
   dimana terlihat IP 74.53.140.153 merupakan IP yang coba diakses dengan memasukkan kredensial. Maka, kita bisa menduga bahwa itulah public IP nya!
![Windows PowerShell 9_21_2023 5_50_02 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/f105d187-dfe6-441e-9242-d982b8bf6611)

6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah 
   hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di 
   google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
   nc 10.21.78.111 6666
   Clue 1: Sepertinya ada yang salah dengan penulisan tersebut secara KBBI. Ada sesuatu yang Besar di depan mata.
   Clue 2: Jenis cipher merupakan substitusi a1z26 Cipher
   Clue 3: Rentang Huruf yang digunakan Huruf A-R, 1-18 dengan Jawaban 6 Huruf.
   Clue 4: SOURCE ADDRESS ADALAH KUNCI SEMUANYA.
   Solving:
   Perhatikan hint pertama pada soal terlihat terdapat ada pengarahan sebuah clue dengan menempatkan huruf kapital yang tidak pada tempatnya (sesuai KBBI). Lalu, setelah ditelusuri semua terkumpullah semua 
   string 
   yang membentuk kata “SUBSTITUSI”. Selanjutnya, hint kedua Nampak memberi tahu bahwasanya sebuah angka bisa di konversi menjadi huruf dan begitu juga sebaliknya. Di hint ketiga, terlihat rentang nomer dan 
   huruf yang akan dipakai dan jawaban hanya berupa 6 huruf.Dan di hint terakhir, kita diarahkan hanya untuk menganalisis sebuah source address saja (Alamat ip).
![myits-app its ac id - Google Chrome 9_21_2023 1_28_30 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/c62c128f-1811-4285-b020-29f8e7dee1dc)

   Pada soal tersebut terdapat text  "server SOURCE ADDRESS 7812 is invalid" yang berarti kunci nya adalah alamat ip pada paket bernomor 7812. Maka setelah kita buka paket capture nya dan cari paket ke-7812 kita 
   dapatkan ip nya dan kita lakukan analisis pada ip tersebut. Didapatkan ip nya adalah blablabla sedangkan hint pada soal ingin kita mensubstitusi angka menjadi huruf. Sedangkan ip tersebut ada yang terpecah 
   menjadi 3 digit sehingga kita perlu memecahnya lagi dan kita lakukan konversi. Dan akhirnya didapatkan lah flagnya berupa 6 huruf dari konversi ip.




