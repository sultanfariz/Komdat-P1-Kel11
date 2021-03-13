# Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan Sistem :
- Unix, Linux atau Windows.
- Apache Web server 1.3+.
- PHP 5.2+.
- MySQL 5.0+.
- RAM minimal 64 Mb+

#### Proses Instalasi :
##### Membuat user baru :
1. Buka terminal Linux Anda dan login menggunakan SSH, setalah itu dianjurkan untuk membuat akun baru manggunakan _command_ `addUser`. Setelah berhasil membuat akun, berikan _privileges_ dengan mengubah ke _superuser_. Jika berhasil, login dengan akun baru tersebut. Berikut perintah yang harus dilakukan :
    ```
    # Login menggunakan SSH
    ssh root@your_server_ip

    # Membuat user baru menggunakan terminal
    adduser <user>
    
    # Berikan privileges pada akun baru tersebut
    usermod -aG sudo <user>

    # Lalu login dengan akun baru yang berhasil dibuat
    su - <user>
    ```
##### Memperbarui packages
2. Pastikan seluruh paket sistem kita _up-to-date_. Berikut perintah yang harus dilakukan :
    ```
    # Perbarui daftar packages
    sudo apt-get update

    # Perbarui packages yang sudah terinstall
    sudo apt-get upgrade
    ```
##### Install NGINX
3. Ghost CMS menggunakan server NGINX dan pengaturan dari SSL membutuhhkan NGINX 1.9.5 atau yang terbaru, sehingga dianjurkan untuk meng-_install_ versi yang terbaru atau jika belum ada _install_ NGINX. Jika ufw diaktifkan, firewall mengizinkan koneksi HTTP dan HTTPS. Berikut perintah yang harus dilakukan : 
    ```
    # Install NGINX
    sudo apt-get install nginx
    
    sudo ufw allow 'Nginx Full'
    ```
##### Install MySQL
4. Selanjutnya Anda harus meng-_install_ MySQL untuk digunakan pada tahap _production_. Jika Anda menjalankan Ubuntu 18.04 atau 20.04, diperlukan kata sandi untuk memastikan MySQL kompatibel dengan Ghost-CLI. Berikut perintah yang harus dilakukan :
    ```
   # Install MySQL (jika belum punya)
    sudo apt-get install mysql-serve
    
    # Setelah meng-install lalu set sebuah kata sandi dengan menjalankan perintah di bawah
    sudo mysql

    # Lalu update user dengan menggunakan perinta di bawah
    # Ganti kata 'password' dengan kata sandi Anda yang baru, namun jangan hapus tanda quote!
    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

    # Keluar dari MySQL
    quit

    # Login lagi menggunakan user yang telah ditetapkan sebelumnya
    su - <user>
    ```
##### Install Node.js
5. Anda harus memiliki versi Node yang didukung di seluruh sistem dengan cara yang dijelaskan di bawah ini. Jika Anda memiliki pengaturan yang berbeda, Anda mungkin mengalami masalah. Berikut perintah yang harus dilakukan :
    ```
    # Tambahkan NodeSource APT repository untuk Node 12
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash

    # Setelah itu install Node.js
    sudo apt-get install -y nodejs
    ```
##### Install Ghost-CLI
6. Ghost-CLI adalah alat _commandline_ untuk membantu Anda menginstal dan mengkonfigurasi Ghost untuk digunakan, dengan cepat dan mudah. Modul npm dapat dipasang dengan `npm` atau `yarn`. Berikut perintah yang harus dilakukan :
    ```
    sudo npm install ghost-cli@latest -g
    ```
##### Install Ghost
7. Ghost harus diinstal di direktorinya sendiri, dengan pemilik dan izin yang tepat. Sehingga kita terlebih dahulu membuat sebuah direktori sendiri dengan mengikuti panduan seperti di bawah ini setelah itu, lakukan instalasi Ghost. Berikut perinta yang harus dilakukan :
    ```
    # Buat direktori baru: ubah `sitename` sesuai nama yang akan Anda buat
    sudo mkdir -p /var/www/sitename

    # Set directory owner: ganti <user> dengan nama user yang telah Anda buat
    sudo chown <user>:<user> /var/www/sitename

    # Set sebuah permissions dengan benar
    sudo chmod 775 /var/www/sitename

    # Masuk ke dalam direktori yang telah dibuat
    cd /var/www/sitename
    
    # Terakhir adalah install Ghost
    ghost install
    ```
##### Hasil Install
8. Berikut hasil install Ghost jika berhasil :
    - Hasil instalasi dari terminal jika berhasil. Berikut _screenshot_-nya :
      ![1](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/terminal-ghost-01.png)
      ![2](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/terminal-ghost-02.png)
    - Jalankan `localhost:2368` untuk membuka Ghost Website. Berikut _screenshot_-nya :
      ![3](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/gohst-web-03.png)
    - Untuk menjalankan atau masuk ke dalam admin Ghost kita terlebih dahulu harus membuat akun baru Ghost dengan masuk ke dalam `localhost:2368/ghost`. Berikut _screenshot_-nya :
      ![4](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/gohst-web-04.png)
      
9. Next step.

