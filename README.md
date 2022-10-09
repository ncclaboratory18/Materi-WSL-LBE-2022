# Materi-WSL-LBE-2022

## Daftar Isi
* [Pengenalan OS dan Linux](#pengenalan-os-dan-linux)
  1. [Sistem Operasi/Operating System](#sistem-operasioperating-system)
  2. [Linux](#linux)
* [Teknik-teknik Instalasi Linux](#teknik-teknik-instalasi-linux)
* [Instalasi WSL](#instalasi-wsl)
* [Bash](#bash)
  1. [Command Dasar pada Bash](#command-dasar-pada-bash)
  2. [Text Editor](#text-editor)
  3. [File Permission](#file-permission)
  4. [Tambahan](#tambahan)

## Pengenalan OS dan Linux
### Sistem Operasi/Operating System
Dalam penggunaan komputer sehari-hari, tentu saja kita sering mendengar maupun menggunakan beberapa jenis sistem operasi seperti Windows, Mac OS, dan sebagainya. Tentu saja kita setidaknya pernah menggunakan salah satu dari sistem operasi yang ada, karena penggunaan komputer tidak dapat lepas dari sistem operasi. Hal ini dikarenakan sistem operasi merupakan perangkat lunak yang berfungsi untuk mengatur eksekusi aplikasi, mengelola sumber daya yang tersedia pada komputer, dan menjadi penghubung antara perangkat keras dan perangkat lunak komputer.

Sistem operasi dibagi menjadi tiga komponen penting, yaitu Kernel, Shell, dan Program Utility.
![image](https://user-images.githubusercontent.com/85059763/194484014-625405f3-027a-4ef8-bf6b-49c1158d3cc5.png)
Kernel adalah inti dari komputer. Komponen ini memungkinkan terjadinya komunikasi antara software dan hardware. Jika kernel adalah bagian terdalam dari sebuah sistem operasi, maka shell adalah bagian terluarnya.

Shell adalah program penerjemah perintah yang menjembatani user dengan kernel. Umumnya, shell menyediakan prompt sebagai user interface tempat user menginputkan perintah-perintah yang diinginkan, baik berupa perintah internal maupun eksternal. Setelah menerima input dari user dan menjalankan program/perintah berdasarkan input tersebut, shell akan mengeluarkan output. Shell dapat diakses melalui Terminal.<br>

Program Utility adalah system software yang menjalankan tugas-tugas maintenance. Program utility ini dibuat secara khusus untuk melakukan fungsi tertentu pada suatu area komputasi secara spesifik, seperti memformat harddisk, atau melakukan pengecekan konektivitas jaringan dll.

### Linux
Linux merupakan salah satu sistem operasi UNIX-like yang pertama kali dikeluarkan oleh Linus Torvalds. Linux bersifat open-source yang berarti source codenya tersedia di internet dan tidak memiliki hak cipta sehingga siapapun dapat mengembangkan dan memakai sistem operasi ini.<br>
Kelebihan	:
- Sebagian besar dapat digunakan secara gratis karena tidak memerlukan lisensi
- Dapat menggunakan root yaitu superuser yang memiliki akses lebih terhadap komputer
- Tidak memerlukan antivirus karena sistem root dan sifatnya yang open-source

Kekurangan	:
- Lebih jarang digunakan sehingga aplikasi yang tersedia lebih sedikit

Berbeda dengan sistem operasi lainnya, versi pada linux lebih dikenal sebagai distro (distribution). Terdapat ratusan distro linux yang dapat digunakan karena siapapun dapat memodifikasi source code linux dan membuat distro baru.

Umumnya tiap distro memiliki spesialisasi sendiri-sendiri dan update yang tidak bergantung pada distro lainnya, sehingga selama masih ada pengembang untuk suatu distro maka dukungan terhadap distro tersebut masih ada sehingga tidak perlu mengganti dengan distro baru.

Berikut beberapa contoh distro linux:
- Ubuntu	: Salah satu distro Linux yang bersifat general-purpose. Sering digunakan karena sifatnya yang umum dan lebih mudah digunakan bagi pengguna Windows maupun MacOS.
- Android	: Salah satu sistem operasi berbasis Linux yang digunakan pada perangkat bergerak/mobile
- Tails		: Salah satu distro Linux yang memiliki fungsi utama privasi sehingga penggunanya dapat mengakses internet secara anonim karena menggunakan network TOR.
- Kali		: Salah satu distro Linux yang memiliki fungsi utama keamanan informasi karena memiliki berbagai software penguji keamanan yang telah terinstall secara default.

## Teknik-teknik Instalasi Linux
### Multi-Boot
Menginstall lebih dari 1 sistem operasi pada komputer, sehingga ketika booting pengguna dapat memilih sistem operasi yang ingin digunakan.
* Kelebihan	:
  - Transfer file lebih mudah
  - Seluruh sumber daya dapat digunakan secara maksimal

* Kekurangan :
  - Hanya dapat menggunakan 1 sistem operasi dalam 1 waktu

### Virtualisasi
Melakukan instalasi sistem operasi baru (guest) pada virtual machine/VM yang terdapat pada sistem operasi host.
* Kelebihan	:
  - Dapat menggunakan berbagai sistem operasi secara bersamaan dengan 1 komputer

* Kekurangan :
  - Sumber daya yang dapat digunakan lebih sedikit karena harus dibagi untuk beberapa sistem operasi
  - Sistem operasi guest bergantung pada host

#### Windows Subsystem for Linux (WSL)
Fitur yang tersedia pada Windows 10 dan Windows 11 sehingga pengguna dapat menginstall dan menggunakan fungsi Linux secara native pada Windows.
* Alasan penggunaan	:
Windows menggunakan command prompt sebagai command-line interface/CLInya. Berbeda dengan sistem operasi macOS dan Linux yang menggunakan bash sebagai CLI, cmd memiliki fitur yang lebih terbatas sehingga dengan WSL pengguna Windows dapat menggunakan bash.


## Instalasi WSL
1. Buka command prompt Windows, lalu cek apakah WSL sudah terinstall dengan `wsl -l -v`. Secara default WSL sudah terinstall pada Windows 10 & 11.
* Jika menggunakan Windows 10, maka kita perlu mengganti versi wsl menjadi versi terbaru (wsl2) dengan `wsl --set-default-version 2`
* Jika terjadi error "WSL 2 requires an update to its kernel component.", maka kita perlu update wsl pada komputer terlebih dahulu pada link berikut: https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel

2. `wsl -l -o` akan menampilkan daftar distro linux yang dapat di install, sedangkan `wsl -l -all` menampilkan daftar distro linux yang sudah terinstall, selanjutnya kita tinggal memilih distro yang ingin diinstall dengan command `wsl --install -d <Distribution Name>`

3. Karena akan digunakan tujuan umum maka salah satu distro yang dapat diinstall adalah Ubuntu, install Ubuntu dengan `wsl --install -d Ubuntu-20.04`. Selanjutnya tunggu saja hingga instalasi selesai.

4. Jika instalasi sudah selesai maka Ubuntu akan muncul ketika kita mencari program di start. Jika kita menjalankan program tersebut maka akan menampilkan command line/terminal baru. Pada command line ini kita sudah dapat menggunakan fungsi-fungsi terminal pada linux.
* Jika ingin mengetahui pada directory mana Ubuntu terinstall, kita dapat menggunakan command `explorer.exe .` pada terminal Ubuntu atau memindah path ke `\\wsl$` jika menggunakan Windows Explorer secara langsung.
* Jika ingin mengakses file Windows pada terminal Ubuntu, maka pindah ke directory root dengan `cd /`, lalu pindah directory "mnt" dengan `cd mnt`. File-file Windows akan termount pada directory ini.

## Bash
### Command Dasar pada Bash
1. echo<br>
Memberikan output text yang diberikan
```bash
echo <string>
```
2. whoami<br>
Mengetahui user yang saat ini login pada sistem
```bash
whoami
```
3. pwd<br>
Print Working Directory, melihat isi directory yang sedang dikunjungi sekarang
```bash
pwd
```
4. ls<br>
Listing, melihat isi dari directory tertentu
```bash
ls <path directory>
```
Jika path directory tidak diisi maka akan menampilkan isi directory sekarang<br>
5. cd<br>
Change Directory, merubah directory yang dikunjungi
```bash
cd <path directory>
```
6. mkdir<br>
Make Directory, membuat directory
```bash
mkdir <nama/path directory>
```
7. touch<br>
Membuat file
```bash
touch <nama file/path>
```
8. cat<br>
Concatenate, menampilkan isi file
```bash
cat <nama file/path>
```
9. rm<br>
Remove, menghapus file
```bash
rm <nama file/path>
```
* Jika file yang dihapus merupakan folder, maka perlu command `rm -r <nama file/path>` agar penghapusan file dilakukan secara rekursif
10. cp<br>
Copy, menyalin isi file
```bash
cp <nama file/path yang ingin dicopy> <nama file/path tujuan>
```
* Jika file yang ingin dicopy merupakan folder, maka perlu command `cp -r <nama file/path yang ingin dicopy> <nama file/path tujuan>` agar penyalinan file dilakukan secara rekursif
11. mv<br>
Move, memindah file
```bash
mv <nama file/path yang ingin dipindah> <nama file/path tujuan>
```
12. grep<br>
Mencari konten file tertentu (string)
```bash
grep <string yang dicari> <nama file>
```
13. find<br>
Mencari path file tertentu
```bash
find <path> <kriteria> <file yang dicari>
```
14. clear<br>
Membersihkan terminal
```bash
clear
```
15. man<br>
Manual, membuka manual page dari sebuah command
```bash
man <nama command>
```

### Text Editor
Pada bash, terdapat beberapa terminal text editor antara lain vim dan nano.
```bash
<vim/nano> <nama file>
```
Kedua text editor memiliki kelebihan masing-masing, yaitu nano lebih mudah digunakan dan vim memiliki lebih banyak fungsionalitas.

### File Permission
#### Permission User
Tiap user pada linux memiliki permission yang berbeda-beda. Salah satu cara mengetahui permission yang dimiliki oleh user adalah dengan command `ls -l`. Tiap user memiliki 3 jenis permission yaitu r atau read untuk melihat isi file, w atau write untuk merubah isi file, dan x atau execute untuk menjalankan isi file. Jika karakter diganti dengan `-` maka user tidak memiliki permission melakukan aksi tersebut.
![image](https://user-images.githubusercontent.com/85059763/194747589-5e1d6cfa-688c-4b12-80cc-4d2bc704b281.png)<br>
Permission terletak pada bagian kiri dengan format 10 karakter ABBBCCCDDD.<br>
A: Berisi karakter `d` jika file merupakan directory atau `-` jika file bukan merupakan directory<br>
B: Berisi permission dari owner file dengan format `rwx`<br>
C: Berisi permission dari group (user yang diberikan akses file) dengan format `rwx`<br>
D: Berisi permission dari other (user lain) dengan format `rwx`<br>

#### chmod
Permission suatu file dapat diubah dengan command `chmod`
```bash
chmod <syntax> <nama file>
```
`<syntax>` terdiri dari format `<who><what><which>`
- Who: Dapat diisi dengan `u` (owner), `g`(group), atau `o`(others) yaitu tipe user mana yang permissionnya ingin diubah. Jika dikosongi maka perubahan permission akan dilakukan untuk seluruh user.
- What: Dapat diisi dengan `-` (mengurangi permission), `+` (menambah permission), `=` (set sebuah permission dan menghapus permission lainnya yang dimiliki tipe user tersebut)
- Which: Dapat diisi dengan `r` (read), `w` (write), atau `x` (execute). Bisa lebih dari satu.
Contoh:
```bash
chmod +x test
```
Menambahkan permission execute file/folder `test` untuk seluruh user.
```bash
chmod u=rw,go=r file.txt
```
Mengubah permission owner `file.txt` menjadi read dan write. Mengubah permission group dan others `file.txt` menjadi read only
<br><br>
Selain itu, `<syntax>` dapat diganti dengan format [3 digit yang masing-masing berisi angka 0-7](https://www.marksanborn.net/linux/changing-permissions-with-chmod-binary-values/). 3 digit melambangkan permission untuk owner, group, dan others sedangkan angka 0-7 didapat dari susunan biner `rwx`.
```bash
chmod 345 test.txt
```
- Mengubah permission `test.txt` owner menjadi 3 (011)<sub>2</sub> = `-wx`
- Mengubah permission `test.txt` group menjadi 4 (100)<sub>2</sub> = `r--`
- Mengubah permission `test.txt` others menjadi 5 (101)<sub>2</sub> = `r-x`

#### su
Digunakan untuk mengubah user yang sedang digunakan sekarang
```bash
su <nama user>
```

#### root
Root merupakan account superuser pada Linux. Umumnya penggunaan root dibatasi karena root memiliki seluruh permission sehingga memungkinkan untuk mengubah file sistem yang dapat berbahaya karena dapat merusak sistem. Untuk menggunakan account root dapat menggunakan command `su root` atau `sudo su` tergantung distro Linux yang sedang digunakan.

#### sudo
Superuser do, digunakan untuk menjalankan suatu command sebagai superuser ketika sedang menggunakan user yang bukan root. Umumnya digunakan ketika ingin mengubah file konfigurasi maupun melakukan install dan update software.
```bash
sudo nano file.conf
```
Digunakan untuk membuka isi file `file.conf` menggunakan text editor nano
```bash
sudo ./program
```
Digunakan untuk mengeksekusi file `program`

### Tambahan
#### /
/ merupakan directory root yaitu directory yang terletak paling atas sehingga seluruh file berada pada directory ini sehingga ketika menuliskan nama path perlu untuk menambahkan directory root.
Contoh:
1. folder `home` yang berisi folder `guest` yang memiliki `file.txt` perlu ditulis sebagai `/home/guest/file.txt` bukan `home/guest/file.txt`
2.
```bash
cd /
```
merubah directory yang dikunjungi ke root directory
#### .. dan .
Ketika menggunakan command-command bash, .. (parent directory) dan . (current directory) dapat digunakan sebagai pengganti path yang digunakan untuk mempersingkat penulisan path.
Contoh:
```bash
cd ..
```
Mundur ke directory sebelumnya, sehingga jika path sebelumnya adalah `/home/guest` maka akan menjadi `/home`

#### > dan >> (Redirection)
Memasukkan output dari suatu command ke file
```bash
echo "Hello world" > hello.txt
```
`hello.txt` akan berisi string "Hello world"
* Jika ingin menambahkan output pada bagian belakang file, maka ganti `>` dengan `>>`

#### | (Pipeline)
Menggunakan output dari suatu command sebagai input dari command lain
```bash
ls | grep "text"
```
Mencari string "text" dari hasil command `ls`

#### &&
Digunakan untuk menjalankan beberapa command dalam 1 line, command akan dijalankan dimulai dari command yang terletak paling kiri
```bash
ls && pwd
```
Setelah menampilkan isi directory sekarang, akan ditampilkan path dari directory sekarang

#### apt
Merupakan package manager untuk distro Linux berbasis Debian (Termasuk ubuntu), digunakan ketika ingin menginstall atau mengupdate software yang dimiliki. Umumnya penggunaan apt memerlukan akses superuser atau root. Terdapat beberapa command yang sering digunakan:
1. `apt-get update`: Digunakan untuk mendapatkan list paket/software yang dapat diupdate
2. `apt-get upgrade`: Digunakan untuk mengupdate paket/software yang sudah terinstall pada sistem
3. `apt-get dist-upgrade`: Digunakan untuk mengupdate sistem dan mengupdate paket/software yang sudah terinstall pada sistem
4. `apt-get install <nama software>`: Digunakan untuk menginstall suatu paket/software yang belum terinstall pada sistem

#### &
Menjalankan command pada background, digunakan dengan cara menambahkan `&` pada akhir sebuah command
Contoh:
```bash
ping www.google.com
```
Ketika ping `www.google.com` tidak dapat melakukan aktivitas lain. Umumnya untuk exit sebuah proses dapat menggunakan `CTRL + Z` atau `CTRL + C`.
```bash
ping www.google.com &
```
Ketika menjalankan command ini process ID dari command yang dilakukan akan ditampilkan, sehingga jika ingin menghentikan command tersebut dapat menggunakan `kill <process ID>`

#### Help
Umumnya ketika ingin mengetahui cara menggunakan suatu software kita dapat menggunakan command
```bash
<nama software> <--help atau -h>
```
Perbedaan `--help` dengan `man` yaitu command `man` akan membuka halaman manual dari command/software yang digunakan sedangkan `--help` akan menampilkan petunjuk penggunaan pada terminal.

#### Extension Visual Studio Code
Jika menggunakan vscode, extension WSL dari Microsoft dapat digunakan sehingga dapat langsung membuka vscode dari terminal WSL.
