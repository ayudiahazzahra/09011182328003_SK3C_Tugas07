# Step 1: Prepare Ubuntu
## The first thing you need to do before you start installing SSH on Ubuntu is to update all apt packages to the latest versions. To do this, use the following command: 
# sudo apt update && sudo apt upgrade

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
## On successful startup, you will see the following system message.
## The --now key helps you launch the service and simultaneously set it to start when the system boots.
## To verify that the service is enabled and running successfully, type:

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
### Ini adalah nama layanan yang dikelola oleh systemd. Dalam hal ini, ssh mengacu pada layanan OpenSSH yang diinstal di sistem, yang memungkinkan koneksi jarak jauh melalui protokol SSH.
