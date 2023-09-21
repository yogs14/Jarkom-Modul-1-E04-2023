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

7. Berapa jumlah packet yang menuju IP 184.87.193.88? |
   nc 10.21.78.111 6565 <br>
   Solving : <br>
   Masuk ke dalam packet capture. Karena soal menanyakan tentang jumlah packet yang menuju IP 184.87.193.88, maka kita dapat menerapkan filter "ip.dst == 184.87.193.88"
   ![7 2](https://github.com/nabielvna/desktop-tutorial/assets/102472111/f8de0ce4-a8aa-40ca-858d-64211f4ff5a9)
   
   kemudian didapatkan jumlah packet yang menuju IP 184.87.193.88 sebanyak 6 packet
   ![7 3](https://github.com/nabielvna/desktop-tutorial/assets/102472111/45449545-703d-4dcb-960f-521a34f173d6)

8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80 (jika terdapat lebih dari 1 port maka urutkan sesuai abjad) |
   nc 10.21.78.111 7171 <br>
   Solving : <br>
   Jawaban -> filter port -> "tcp.dstport == 80 || udp.dstport == 80"
   ![8 1](https://github.com/nabielvna/desktop-tutorial/assets/102472111/332afc79-b8b1-4929-8fbd-236eabca5a5b)

9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34! |
   nc 10.21.78.111 7272 <br>
   Solving : <br>
   jawaban -> filter ip -> "ip.src == 10.51.40.1 && ip.dst != 10.39.55.34"
   ![9 1](https://github.com/nabielvna/desktop-tutorial/assets/102472111/58764efb-c6ae-4cd8-80b5-504c093f1860)

10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet, format [username]:[password]! |
    nc 10.21.78.111 7373 <br>
    Solving : <br>
    a. Masuk kedalam packet capture. <br>
    b. Soal menyebutkan aktivitas terjadi pada protokol Telnet. Maka terapkan filter dengan keyword "telnet". <br>
    c. cari aktivitas yang terdapat [username]:[password] di dalamnya. <br>
    ![10 1](https://github.com/nabielvna/desktop-tutorial/assets/102472111/d5e8d571-4f4d-4a1b-9894-80b676c9e30e)

    Kemudian didapatkan [username]:[password], yaitu: "dhafin:kesayangannyak0k0"
    ![10 2](https://github.com/nabielvna/desktop-tutorial/assets/102472111/e7819d74-5f20-484a-85e4-4d010456600c)
