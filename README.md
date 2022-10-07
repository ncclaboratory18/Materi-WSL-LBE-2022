# Materi-WSL-LBE-2022

## Daftar Isi
* Pengenalan OS dan Linux
  1. Sistem Operasi/Operating System
  2. Linux
* Teknik-teknik Instalasi Linux
* Instalasi WSL
* Command Dasar pada Bash

## Pengenalan OS dan Linux
### Sistem Operasi/Operating System
Dalam penggunaan komputer sehari-hari, tentu saja kita sering mendengar maupun menggunakan beberapa jenis sistem operasi seperti Windows, Mac OS, dan sebagainya. Tentu saja kita setidaknya pernah menggunakan salah satu dari sistem operasi yang ada, karena penggunaan komputer tidak dapat lepas dari sistem operasi. Hal ini dikarenakan sistem operasi merupakan perangkat lunak yang berfungsi untuk mengatur eksekusi aplikasi, mengelola sumber daya yang tersedia pada komputer, dan menjadi penghubung antara perangkat keras dan perangkat lunak komputer.

Sistem operasi dibagi menjadi tiga komponen penting, yaitu Kernel, Shell, dan Program Utility.
![image](https://user-images.githubusercontent.com/85059763/194484014-625405f3-027a-4ef8-bf6b-49c1158d3cc5.png)
Kernel adalah inti dari komputer. Komponen ini memungkinkan terjadinya komunikasi antara software dan hardware. Jika kernel adalah bagian terdalam dari sebuah sistem operasi, maka shell adalah bagian terluarnya.

Shell adalah program penerjemah perintah yang menjembatani user dengan kernel. Umumnya, shell menyediakan prompt sebagai user interface tempat user menginputkan perintah-perintah yang diinginkan, baik berupa perintah internal maupun eksternal. Setelah menerima input dari user dan menjalankan program/perintah berdasarkan input tersebut, shell akan mengeluarkan output. Shell dapat diakses melalui Terminal.
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

* Kekurangan	:
  - Hanya dapat menggunakan 1 sistem operasi dalam 1 waktu

### Virtualisasi
Melakukan instalasi sistem operasi baru (guest) pada virtual machine/VM yang terdapat pada sistem operasi host.
* Kelebihan	:
  - Dapat menggunakan berbagai sistem operasi secara bersamaan dengan 1 komputer

* Kekurangan	:
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

## Command Dasar pada Bash
