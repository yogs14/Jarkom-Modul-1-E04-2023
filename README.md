Lapres Praktikum Modul 1 
Wireshark

1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP.
   nc 10.21.78.111 12345
   Solving :
   Masuk ke dalam netcat dan perhatikan soal yang diinginkan! Berikutnya analisis lewat file packet capture yang diberikan.
![Windows PowerShell 9_21_2023 9_55_19 AM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/29dcc7d7-0bb1-4949-9db8-75c4d26feb05)

Pada wireshark lakukan filter dengan keyword "FTP" karena clue yang diberikan oleh soal adalah aktivitas yang terjadi pada protokol FTP.
Lalu, pusatkan perhatian pada "STOR" yang terdapat pada info paket yang terekam karena diduga kuat itu merupakan aktivitas yang dimaksud.
![soal 1 FTP](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/b52564f0-f8d7-41de-ba41-d6e7f3c361c5)

2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!
   nc 10.21.78.111 13579
   Solving :
   Masuk ke dalam packet capture dan karena soal menginginkan server maka ikuti protokol http dari file pcap tersebut karena server pasti menempel pada protokol http
   ![Wireshark · Follow HTTP Stream (tcp stream eq 2) · Wi-Fi 9_18_2023 8_02_15 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/371d18eb-049c-4d0d-9f79-bdcb26c31a95)

3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
   nc 10.21.78.111 13590
   Solving :
   Masuk ke dalam netcat untuk mengetahui persis apa yang diminta. Setelah masuk, soal menginginkan kita untuk menghitung berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702 maka kita lakukan analisis dengan melakukan filter menggunakan keyword "(ip.src ==   239.255.255.250  && udp.port == 3702) || (ip.dst 239.255.255.250 &&  tcp.port 3702)"
   ![soal no 3](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/8ce211ba-f1cb-4316-ae90-2ba1ef093a34)
   
Lalu, hitung paket dengan menggunakan statistics lalu pilih packet length dan terapkan kembali display filter nya dan bisa dilihat panjang dari paket adalah 21
![Wireshark · Packet Lengths · soal3 (1) pcap 9_21_2023 5_07_24 PM](https://github.com/yogs14/Jarkom-jarkoman/assets/121499055/4ba18292-e42e-4df0-bc92-53a949e7a196)

Setelah itu, soal juga menanyakana protokol layer apa yang digunakan. Dan jelas jawabannya adalah UDP karena paket tersebut yang terekam.

