# Docker Simplified

<img src="https://msopentech.com/wp-content/uploads/dockericon.png">

## Pengantar Docker
Docker merupakan software container platform. sehingga memungkinkan developer tidak perlu di buat pusing dalam setting up environment dalam sebuah platform. pernah nggak sih kamu pilih-pilih system operasi kalo mau buat apps? misal, OS "a" ribet buat nginstall python harus pake software/install ini itulah sebelum bisa running syntax:

```python
print "Hello World!"
```

Masalah lainnya terjadi saat kamu bekerja dengan team, jadi kamu harus njelasin beberapa hal yang harus diinstall sebelum bisa running dengan mulus tanpa error :sob:, masalah muncul kembali saat ada 10 gelombang dalam meng-hire developer pada sebuah startup, dan kamu harus njelasin sebanyak 10 kali dan mengalami banyak kendala dengan berbedanya OS yang mereka pakai, bukankah seorang developer itu harus efektif && efisien?

daripada running:

```python
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
print "Hello World!"
```
mending pake:
```python
def hai():
  x=1
  while x<=10:
    print "Hello World!"
    x=x+1
hai() # <= konsep docker container
```

Seperti yang dikatakan Solomon Hykes, CTO and founder of Docker
>Everyone is looking for a platform to build new apps, and the biggest problem they have is that these apps don’t run on a single computer from beginning to end. - Hykes

Kata Hykes, Developer mendapat masalah ketika code yang telah dibuat di komputer mereka sendiri, dan mencoba untuk menjalankannya ke komputer lain dengan system operasi, database, dan service yang berbeda. Membuat sebuah program/algoritma itu nggak sesimple yang dibayangkan, masalah lain muncul kembali saat akan melakukan testing atau menyiapkan versi Stable dari apps kita untuk berjalan di production.

> Now your app is supposed to span any number of machines, it’s supposed to continue running even if you swap out machines, as you go from your own servers to Amazon or Google Compute Engine. The biggest problem is how do I package my app so that it can be moved around from machine to machine?

Ini Pengenalan sederhana untuk Docker, untuk lebih lanjutnya bisa dibaca pada [link ini](https://www.docker.com/what-docker)

## Variant Docker
Docker mempunyai 2 variant yaitu Docker Enterprise Edition dan Docker Community Edition

### Docker Enterprise Edition
Dibuat untuk keperluan development sekelas Enterprise dan untuk sebuah team yang memiliki keperluan untuk build, ship, dan run dalam skala production. Docker EE telah Terintergrasi, Tersertifikat, dan di support untuk melayani Perusahan-Perusahan yang memiliki kebutuhan dengan tingkat keamanan tinggi dalam platform containernya di dalam industri bisnis. untuk informasi lebih lanjut dapat mengunjungi [Docker Enterprise Edition](https://www.docker.com/enterprise-edition/)

### Docker Community Edition
Diperuntukan untuk developer dan orang-orang yang ingin belajar dan bereksperimen dengan continer-base apps. Docker CE memberikan 2 pilihan yaitu versi stable dan edge
 - Stable release per 3 bulan sekali
 - Edge relese per bulan sekali

### Platform support 
Docker CE dan Docker EE dapat berjalan di Linux, Cloud, Windows, dan macOS platform. 

| Platform | Docker CE | Docker EE |
| --- | :---: | :---: |
| [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/) | o | o |
| [Debian](https://docs.docker.com/engine/installation/linux/debian/) | | o |
| [Red Hat Enterprise Linux](https://docs.docker.com/engine/installation/linux/rhel/) | o |  |
| [CentOS](https://docs.docker.com/engine/installation/linux/centos/) | o | o |
| [Fedora](https://docs.docker.com/engine/installation/linux/fedora/) |  | o |
| [Oracle Linux](https://docs.docker.com/engine/installation/linux/oracle/) | o |  |
| [SUSE Linux Enterprise Server](https://docs.docker.com/engine/installation/linux/suse/) | o |  |		 
| [Microsoft Windows Server 2016](https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-server) | o |  |
| [Microsoft Windows 10](https://docs.docker.com/docker-for-windows/) |  | o |
| [macOS](https://docs.docker.com/docker-for-mac/) |  | o |
| [Microsoft Azure](https://docs.docker.com/docker-for-azure/) | o | o |	
| [Amazon Web Services](https://docs.docker.com/docker-for-aws/) | o | o |

untuk penjelasan setup Docker di Cloud seperti: Digital Ocean, Packet, atau SoftLink dapat dilihat [disini](https://docs.docker.com/engine/installation/#on-docker-cloud)

## Cara Install Docker CE versi Stable (Ubuntu 16.04)
Disini saya hanya akan menjelaskan tata cara menginstall Docker di Linux Ubuntu, untuk OS lainnya dapat [dilihat di sini](https://docs.docker.com/engine/getstarted/step_one/)

### OS requirements
Untuk menginstall Docker, diperlukan versi 64 bit dari versi ubuntu ini:
- Yakkety 16.10
- Xenial 16.04 (LTS)
- Trusty 14.04 (LTS)

### Set Up Repository

masuk cmd lalu run command:
```sh
  > sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common
```

Setelah itu tambahkan Official Docker GPG key:
```sh
  > curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Cek apakah fingerprint key sesuai dengan 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
```sh
  > sudo apt-key fingerprint 0EBFCD88
```

lalu tambah-kan repository untuk download versi Stable
```sh
  > sudo add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) \
      stable"
```

### Install Docker
update index apt 
```sh
  > sudo apt-get update
```

setelah itu install versi CE
```sh
  > sudo apt-get install docker-ce
```

jika kamu menginginkan versi Docker CE tertentu, dapat menjalankan command dibawah untuk melihat versi Docker CE yang sesuai dengan versi Ubuntu yang kamu pakai
```sh
  > sudo apt-cache madison docker-ce
```

lalu install sesuai dengan versi yang ada
```sh
  > sudo apt-get install docker-ce=<VERSION>
```

untuk informasi dalam instalasi Docker dengan versi Edge ataupun versi Docker EE dapat mengunjungi [Link berikut](https://docs.docker.com/engine/installation/linux/ubuntu/)

## Build docker

### Membuat Dockerfile
Dockerfile, bisa dikatakan "resep", file-file apa saja yang perlu ada, setting-an environment, dan kumpulan perintah-perintah untuk membuat sebuah "image". jika kamu pernah menginstall OS pada laptop ataupun komputer, kamu perlu sebuah image OS dimana akan menyimpan file OS dan data-data apapun yang terkait dengan program. dengan Dockerfile, anda hanya perlu menuliskan file-file apa saja yang dibutuhkan dan selebihnya akan diatur oleh Docker.

Terdapat 3 Command penting dalam membuat image
- FROM
- RUN
- CMD

Command "FROM" berguna untuk menentukan Image apa yang nantinya dipakai sebagai dasar OS/environment, terdapat banyak pilihan dalam menetukan aplikasi kita berjalan di OS/environment yang mana, untuk lebih lengkapnya dapat mengunjungi [Docker Hub](https://hub.docker.com/explore/)

Command "RUN" berguna untuk menjalankan perintah-perintah saat membuat image, seperti:
```sh
  > RUN sudo apt-get update
```
atau perintah-perintah lain untuk menginstall missing depedencies yang diperlukan untuk Workspace anda nantinya

Command "CMD" berguna untuk menjalankan perintah saat Image yang telah dibangun, dijalankan pertamakali. hal ini bisa dianalogikan saat kita menghidupkan laptop ataupun komputer, perintah-perintah apa saja yang perlu berjalan dan atau apps-apps mana yang auto-start saat komputer/laptop hidup

### Membangun Image
Setelah membuat Dockerfile, saatnya membangun Image dari Dockerfile, Dengan cara:
```sh
  > docker build -t namaImage .
  #namaImage bisa anda ganti sesuai interest anda
```

Setelah itu Docker akan mengatur semua yang perlu ada dalam membangun Image,
setelah proses membangun image, kita perlu me-running Image yang ada yang nantinya akan di taruh pada Container, konsep container ibarat seperti kita menginstall Image yang kita buat ke Laptop/Komputer yang mana.
```sh
  > docker run -p 8888:8888 -p 6006:6006 --name namaContainer -it namaImage
  #namaImage, dan namaContainer bisa anda ganti sesuai interest anda
  # -p digunakan untuk mengekspose port yang mana yang dibuka dan diberi akses dari luar 
```

jika telah shutdown/stop container berjalan, kita dapat kembali dengan cara
```sh
docker start -ai namaContainer
```


## Command Penting Docker
```sh
  > docker ps -a
  #digunakan untuk melihat semua container yang sedang berjalan ataupun tidak
```

```sh
  > docker images -a
  #digunakan untuk melihat semua Image yang tersedia
```

```sh
  > docker exec -it containerID
  #digunakan untuk masuk ke dalam sistem Container
```

```sh
  > docker rmi imageID
  #digunakan untuk menghapus Image Tertentu
```

```sh
  > docker rm containerID
  #digunakan untuk menghapus container Tertentu
```

### Checklist
- [x] Introduction
- [x] Variant Docker
- [x] Install Docker CE versi Stable (Ubuntu 16.04)
- [x] Build docker
- [x] Command Penting Docker
