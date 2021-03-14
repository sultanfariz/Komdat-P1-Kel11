# Ghost

![Ghost](https://snipcart.com/media/204295/ghost.png)

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:

## Sekilas Tentang

Ghost adalah platform blogging CMS (content management system) open source yang berdiri di atas stack Node.js modern yang didesain untuk beroperasi dengan powerful, fleksibel, dan minimalis. Ghost menyediakan ruang bagi penggunanya untuk menulis konten dengan editor yang bagus dan mudah untuk didesain sehingga terkesan reader-friendly bagi pembaca. Pengguna dapat mengatur cutom domain sendiri dan men-hosting sekaligus mengedit langsung dari CMS Ghost.


## Instalasi
[`^ kembali ke atas ^`](#)

#### Kebutuhan Sistem :
- Unix, Linux (Ubuntu 18.04 or 20.04), atau Windows.
- RAM (dianjurkan) 4GB
- NGINX 1.9.5 atau terbaru
- Node.js (JavaScript runtime) 12.0 atau terbaru
- MySQL 8.0 atau terbaru
- npm (package manager) 7.5 atau terbaru

#### Proses Instalasi :
##### Membuat user baru :
1. Buka terminal Linux Anda dan login menggunakan SSH, setelah itu dianjurkan untuk membuat akun baru manggunakan _command_ `addUser`. Setelah berhasil membuat akun, berikan _privileges_ dengan mengubah ke _superuser_. Jika berhasil, login dengan akun baru tersebut. Berikut perintah yang harus dilakukan :
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
      
    - Masukkan data diri Anda ketika ingin membuat akun Gost baru. Berikut _screenshot_-nya :
    
      ![5](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-43-31.png)
    
    - Lalu setelah membuat akun Ghost maka Anda langsung diarahkan ke halaman _Invite Staff Users_ yang mana pengguna yang kita undang bisa mengatur admin website dari Ghost. Berikut _screenshot_-nya :
    
      ![6](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-46-08.png)
      
    - Setelah tahap instalasi dan membuat akun Ghost baru selesai maka Anda bisa memakai fitur-fitur atau mengatur website Ghost Anda. Selamat Blogging!. Berikut _screenshot_-nya :
    
      ![7](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-46-19.png)


## Konfigurasi
[`^ kembali ke atas ^`](#)

Mengubah tema :
- Untuk mengubah tema blog dapat melalui menu theme.
![8](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-51-57.png)
- Selanjutnya unduh salah satu tema yang kita inginkan kemudian upload ke Ghost secara manual.
![9](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-54-03.png)
- Setelah upload berhasil, tema dapat langsung diaktivasi melalui Ghost.
![10](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-54-14.png)

Menambah tag pada navbar :
- Masuk ke menu design dan isi judul tag serta link navigasinya.
![11](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-56-33.png)
- Klik save dan buka page utama, maka tag tersebut akan langsung muncul di navigation bar.
![12](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2021-56-50.png)

## Cara Pemakaian
[`^ kembali ke atas ^`](#)

Cara pemakaian ghost cukup mudah, aplikasi ini menyediakan tampilan yang mudah dimengerti. Berikut fitur-fitur yang ada di CMS ghost:

   1. Sebelum menggunakan ghost, kita perlu login terlebih dahulu 
      ![13](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2022-05-48.png)
       
   2. Setelah login, kita masuk ke halaman dashboard. Pada halaman ini terdapat beberapa menu, yang pertama ada menu post
      ![14](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2022-06-03.png)
       
   3. Selanjutnya ada menu page yang berfungsi untuk mengatur halaman yang diinginkan
      ![15](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2022-11-05.png)
      
   4. Terdapat juga menu staff yang berfungsi untuk memanage tim. Di sini kita bisa mengatur role sesuai keinginan
      ![16](https://github.com/sultanfariz/Komdat-P1-Kel11/blob/main/img/Screenshot%20from%202021-03-13%2022-12-50.png)

## Pembahasan
[`^ kembali ke atas ^`](#)

**Ghost** menawarkan beberapa keunggulan yang menjadikannya sebagai salah satu content management system berbasis Javascript yang banyak dipakai di dunia, antara lain:
- Ghost memiliki fitur SEO Optimization, yang mana merupakan salah satu fitur wajib dan penting dalam suatu CMS.
- Dikembangkan dengan bahasa pemrograman Javascript yang lebih modern dan memiliki performa cukup baik.
- Desain yang minimalis dan reader-friendly.
- Ghost hanya fokus pada blogging, sehingga ringan dan sangat cepat untuk dikembangkan.
- Dokumentasi yang tersedia lumayan lengkap.

Sementara itu di sisi lain, terdapat beberapa kekurangan dari CMS ini antara lain :
- Ghost kurang cocok untuk pengembangan fitur yang lebih dari sekedar blog.
- Tema yang disediakan masih terbatas.
- Setup hosting yang lumayan rumit, sehingga kurang disarankan untuk blogger yang tidak memiliki wawasan teknikal mengenai hosting website.

Sebagai komparasi, kami mencoba membandingkan **Ghost** dengan **Wordpress**. Berikut hasil komparasinya :
- Ghost ditulis dengan bahasa pemrograman Javascript, sementara Wordpress dibangun dengan bahasa pemrograman PHP. Hal ini membuat performa Ghost menjadi lebih kencang dibanding Wordpress yang menggunakan bahasa pemrograman yang lebih tua.
- Fitur-fitur yang tersedia pada Wordpress sangat lengkap, sehingga kustomisasi yang dapat dilakukan dapat bervariasi. Namun ftur yang lengkap menyebabkan Wordpress dianggap *bulk*. Sementara itu Ghost tidak memiliki fitur yang selengkap Wordpress, namun Ghost jauh lebih ringan dan performanya cepat. Akan tetapi hal tersebut membuat Ghost kurang cocok untuk pengembangan blog yang lebih dari sekedar blog biasa.
- Hosting Wordpress didukung oleh banyak layanan hosting, sementara Ghost kurang didukung karena berdiri pada stack Node.js sehingga Ghost menyediakan layanan hosting sendiri.


## Referensi
[`^ kembali ke atas ^`](#)

- Dokumentasi resmi Ghost : https://ghost.org/docs
- Review Ghost : https://medium.com/menlo-office/ghost-blogging-platform-review-2020-publishing-on-ghost-cms-for-3-months-c5833db3cc41

