# Step 1: Prepare Ubuntu
## The first thing you need to do before you start installing SSH on Ubuntu is to update all apt packages to the latest versions. To do this, use the following command: 
### sudo apt update && sudo apt upgrade

![7 1](https://github.com/user-attachments/assets/0db69688-7b57-4fa4-8a1e-08fe00abffe0)

## sudo apt update:
### >Perintah ini memperbarui daftar paket dari repositori perangkat lunak yang terdaftar. Artinya, sistem akan mengunduh informasi terbaru mengenai versi terbaru dari paket-paket perangkat lunak yang tersedia, tetapi tidak melakukan instalasi atau perubahan apa pun.
### >Fungsinya adalah untuk memastikan bahwa sistem mengetahui paket-paket terbaru dan versi-versi terbaru yang tersedia di repositori yang terdaftar.

## sudo apt upgrade:
### >Setelah memperbarui daftar paket dengan apt update, perintah ini meng-upgrade atau memperbarui semua paket yang terinstal ke versi terbaru yang tersedia. Ini termasuk instalasi versi baru dari paket-paket tersebut dan penghapusan paket-paket lama yang sudah tidak dibutuhkan.
### >Pada dasarnya, apt upgrade menginstal pembaruan yang ditemukan oleh perintah apt update.

### &&:
## >Ini adalah operator logika yang digunakan di terminal Linux untuk menggabungkan dua perintah. Perintah kedua (sudo apt upgrade) hanya akan dijalankan jika perintah pertama (sudo apt update) berhasil dijalankan tanpa kesalahan.

# Step 2: Install SSH on Ubuntu
## OpenSSH is not pre-installed on the system, so let's install it manually. To do this, type in the terminal:
### sudo apt install openssh-server

![7 2](https://github.com/user-attachments/assets/811d7ec0-c8d5-4992-a59e-cda227e2f589)

## sudo:
### Perintah ini memberi izin superuser atau administrator untuk melakukan tindakan. Karena instalasi memodifikasi sistem, Anda memerlukan hak akses administratif.
## apt install: 
### Ini adalah perintah untuk menginstal perangkat lunak atau paket di Ubuntu. Dalam hal ini, kita menginstal OpenSSH Server.
## openssh-server: 
### Ini adalah nama paket yang akan diinstal, yang menyediakan kemampuan server SSH di Ubuntu.

# Step 3: Start SSH
## Now you need to enable the service you just installed using the command below:
### sudo systemctl enable --now ssh

![7 3](https://github.com/user-attachments/assets/9bb2366a-470f-423a-aca9-375506103d11)

## sudo:
### Perintah ini dijalankan dengan hak akses superuser (administrator), yang diperlukan untuk mengelola layanan sistem. Anda membutuhkan hak administratif untuk memulai atau mengaktifkan layanan.
## systemctl:
### systemctl adalah perintah yang digunakan untuk mengontrol layanan pada sistem berbasis systemd. Anda bisa menggunakannya untuk memulai, menghentikan, memeriksa status, atau mengaktifkan layanan tertentu (seperti layanan SSH dalam kasus ini).
## enable:
### Bagian ini mengatur agar layanan SSH otomatis dimulai setiap kali sistem di-boot (dinyalakan ulang). Dengan kata lain, layanan SSH akan selalu berjalan secara otomatis setiap kali komputer Anda dinyalakan, tanpa perlu mengaktifkannya secara manual.
## --now:
### Opsi ini menginstruksikan agar layanan dimulai saat ini juga, selain diaktifkan untuk dijalankan secara otomatis pada saat boot. Jadi, alih-alih hanya mengaktifkan layanan untuk start-up, perintah ini juga langsung menjalankan layanan SSH setelah perintah dijalankan.
## ssh:
### Ini adalah nama layanan yang dikelola oleh systemd. Dalam hal ini, ssh mengacu pada layanan OpenSSH yang diinstal di sistem, yang memungkinkan koneksi jarak jauh melalui protokol SSH

## On successful startup, you will see the following system message.
## The --now key helps you launch the service and simultaneously set it to start when the system boots.
## To verify that the service is enabled and running successfully, type:
### sudo systemctl status ssh

![7 4](https://github.com/user-attachments/assets/712b5e8e-65b4-41e7-8d9c-a6d5333328e8)

### sudo systemctl status ssh digunakan untuk memeriksa status layanan SSH (Secure Shell) pada sistem berbasis systemd

# Step 4: Configure the firewall
## Before connecting to the server via SSH, check the firewall to ensure it is configured correctly.
## In our case, we have the UFW installed, so we will use the following command:
### sudo ufw status

![7 5](https://github.com/user-attachments/assets/ac0c6a05-fc6d-4789-8d5b-f2cac65b13cf)

## sudo:
### Dijalankan dengan hak akses superuser atau administratif, karena memeriksa atau mengelola status firewall memerlukan izin khusus pada sistem.
## ufw:
### UFW (Uncomplicated Firewall) adalah alat firewall yang dirancang untuk memudahkan pengaturan firewall di Linux. Ini memberikan cara yang lebih sederhana untuk mengelola aturan iptables, yang biasanya lebih rumit.
## status:
### Opsi ini digunakan untuk menampilkan status UFW, termasuk apakah firewall aktif atau tidak, serta aturan firewall yang sedang diterapkan.


## In the output, you should see that SSH traffic is allowed. If you don't have it listed, you need to allow incoming SSH connections. This command will help with this:
### sudo ufw allow ssh

![7 6](https://github.com/user-attachments/assets/e84441a6-1ff5-45f7-9b35-fdffa7275d66)


### Perintah sudo ufw allow ssh digunakan untuk mengizinkan koneksi SSH (Secure Shell) melalui firewall yang dikelola oleh UFW (Uncomplicated Firewall) di sistem Linux.

# Step 5: Connect to the server
## Once you complete all the previous steps, you can log into the server using the SSH protocol.
## To do this, you will need the server's IP address or domain name and the name of a user created on the server.
## In the terminal line, enter the command:
### ssh username@IP_address

![7 7](https://github.com/user-attachments/assets/aff0b975-a6ef-4a67-a346-2c592ce051d1)

![7 8](https://github.com/user-attachments/assets/68e8702b-1bde-4659-88ed-6f8cfa241aad)

## ssh:
### Ini adalah perintah untuk memulai sesi SSH. SSH adalah protokol jaringan yang menyediakan cara aman untuk mengakses perangkat dari jarak jauh melalui jaringan yang tidak aman.
## username:
### Ini adalah nama pengguna (user) yang digunakan untuk masuk ke komputer atau server jarak jauh. Anda harus memiliki akun yang valid pada sistem yang Anda coba akses. Misalnya, jika nama pengguna Anda di server adalah "Nadia", maka Anda akan menuliskan Nadia sebagai username.
## @:
### Simbol ini digunakan untuk memisahkan nama pengguna dari alamat IP atau nama host. Ini adalah sintaks standar dalam banyak aplikasi jaringan.
## IP_address:
### Ini adalah alamat IP dari komputer atau server yang ingin Anda akses. Alamat IP dapat berupa alamat IPv4 (misalnya, 192.168.1.10) atau IPv6. Anda juga dapat menggunakan nama host (seperti example.com) jika DNS (Domain Name System) telah dikonfigurasi.

# Step 6: Configure SSH
## Having completed the previous five steps, you can already connect to the server remotely. However, you can further increase the connection's security by changing the default connection port to another or changing the password authentication to key authentication. These and other changes require editing the SSH configuration file.
## The main OpenSSH server settings are stored in the main configuration file sshd_config (location: /etc/ssh). Before you start editing, you should create a backup of this file: 
### sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.initial


## If you get any errors after editing the configuration file, you can restore the original file without problems.
## After creating the backup, you can proceed to edit the configuration file. To do this, open it using the nano editor:
### sudo nano /etc/ssh/sshd_config

![7 9](https://github.com/user-attachments/assets/1f696dbf-59ed-4ccb-9881-dd178d931ebd)

![7 10](https://github.com/user-attachments/assets/a60fc7a9-0b1f-4b2b-8990-afde77782865)

![7 12](https://github.com/user-attachments/assets/081a3f88-226d-4ffb-a26a-19ca684fce23)


## sudo:
### Perintah ini digunakan untuk menjalankan perintah dengan hak akses superuser atau administratif. Mengedit file konfigurasi sistem seperti sshd_config memerlukan izin khusus, sehingga Anda harus menggunakan sudo.
## nano:
### Ini adalah editor teks berbasis terminal yang mudah digunakan. Nano memungkinkan pengguna untuk membuat dan mengedit file teks langsung dari command line. Ini adalah pilihan yang baik untuk pengguna yang mungkin tidak nyaman dengan editor teks yang lebih kompleks seperti vim atau emacs.
## /etc/ssh/sshd_config:
### >Ini adalah jalur lengkap ke file konfigurasi untuk OpenSSH Server:
### >/etc: Direktori ini adalah tempat di mana banyak file konfigurasi sistem disimpan.
### >ssh: Ini adalah subdirektori yang berisi file konfigurasi terkait dengan SSH.
### >sshd_config: Ini adalah file konfigurasi utama untuk daemon SSH (sshd), yang mengatur berbagai pengaturan untuk server SSH. Ini mencakup konfigurasi tentang keamanan, port yang digunakan, metode autentikasi, dan banyak lagi.

## After making all the changes in the main configuration file, save them and close the editor. 
## Restart the service to make the changes take effect:

![7 11](https://github.com/user-attachments/assets/e9154850-5d9a-4bd0-831b-fd1e29aed012)

## sudo:
### Perintah ini dijalankan dengan hak akses superuser atau administratif. Mengelola layanan sistem memerlukan izin khusus, sehingga Anda perlu menggunakan sudo untuk menjalankan perintah ini.
## systemctl:
### systemctl adalah alat yang digunakan untuk mengelola layanan dan unit lainnya di sistem berbasis systemd. Anda dapat menggunakan perintah ini untuk memulai, menghentikan, mengaktifkan, menonaktifkan, atau memeriksa status layanan.
## restart:
### Opsi ini memberi tahu systemctl untuk memulai ulang layanan. Ini berarti layanan akan dihentikan dan kemudian dimulai kembali. Restart diperlukan untuk menerapkan perubahan konfigurasi atau untuk memperbaiki masalah yang mungkin terjadi pada layanan tersebut.
## ssh:
### Ini merujuk pada layanan yang dioperasikan oleh OpenSSH, yang memungkinkan koneksi jarak jauh melalui protokol SSH. Nama layanan ini digunakan untuk mengidentifikasi layanan yang akan direstart.

## If you have changed the port in the configuration file, you should connect using the new port: 
### ssh -p port_number username@IP_address

![7 13](https://github.com/user-attachments/assets/3abb8bcb-8c09-41d6-94e1-3f68e1d42c43)

## ssh:
### Ini adalah perintah untuk memulai sesi SSH. Protokol SSH digunakan untuk mengamankan komunikasi antara klien dan server melalui jaringan.
## -p port_number:
### Opsi -p diikuti oleh port_number digunakan untuk menentukan nomor port yang akan digunakan untuk koneksi SSH. Port default untuk SSH adalah 22, tetapi jika server SSH dikonfigurasi untuk menggunakan port yang berbeda, Anda harus menyertakan opsi ini.
#### >Misalnya, jika server SSH Anda berjalan pada port 49532, Anda akan menggunakan -p 49532.
## username:
### Ini adalah nama pengguna yang akan digunakan untuk masuk ke server. Anda harus memiliki akun yang valid di server yang ingin Anda akses.
## @:
### Simbol ini digunakan untuk memisahkan nama pengguna dari alamat IP atau nama host. Ini adalah sintaks standar dalam banyak aplikasi jaringan.
## IP_address:
### Ini adalah alamat IP dari server atau komputer yang ingin Anda akses. Anda dapat menggunakan alamat IPv4 (misalnya, 10.8.143.150) atau alamat IPv6. Anda juga bisa menggunakan nama host (seperti example.com) jika DNS telah dikonfigurasi


![7 14](https://github.com/user-attachments/assets/b8b22f87-6d5b-4759-b859-dd866c5e3094)
![7 16](https://github.com/user-attachments/assets/554b1a64-ffbc-4df8-8e91-fdc10d523da3)
![7 17](https://github.com/user-attachments/assets/c0927016-7313-4564-96c5-42056c3f73ff)



















