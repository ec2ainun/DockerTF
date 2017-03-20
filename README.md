# Docker

<img src="/docker.png" width="300" height="300">

## Introduction of Docker
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

Kata Hykes, Developer mendapat masalah ketika code yang telah dibuat di komputer mereka sendiri, dan mencoba untuk menjalankannya ke komputer lain dengan system operasi, database, dan service yang berbeda. Membuat sebuah program/algoritma itu nggak semudah yang dibayangkan, masalah lain muncul saat akan melakukan testing atau menyiapkan versi Stable dari apps kita untuk berjalan di production.

> Now your app is supposed to span any number of machines, it’s supposed to continue running even if you swap out machines, as you go from your own servers to Amazon or Google Compute Engine. The biggest problem is how do I package my app so that it can be moved around from machine to machine?

Ini Pengenalan simple untuk Docker, untuk lebih lanjutnya bisa dibaca pada [link ini](https://www.docker.com/what-docker)

## Variant Docker
Docker mempunyai 2 variant yaitu Docker Enterprise Edition dan Docker Community Edition

### Docker Enterprise Edition
Dibuat untuk keperluan development sekelas Enterprise dan untuk sebuah team yang memiliki keperluan untuk build, ship, dan run dalam skala production. Docker EE telah Terintergrasi, Tersertifikat, dan di support untuk melayani Perusahan-Perusahan yang memiliki kebutuhan dengan tingkat keamanan tinggi dalam platform contianernya di dalam industri bisnis. untuk informasi lebih lanjut dapat mengunjungi [Docker Enterprise Edition](https://www.docker.com/enterprise-edition/)
### Docker Community Edition
Diperuntukan untuk developer dan orang-orang yang ingin belajar dan bereksperimen dengan continer-base apps. Docker CE memberikan 2 pilihan yaitu versi stable dan edge
 - Stable release per 3 bulan sekali
 - Edge relese per bulan sekali

### Platform support 
Docker CE dan Docker EE dapat berjalan di Linux, Cloud, Windows, dan macOS platform. 

| Platform | Docker CE | Docker EE |
| --- | :---: | :---: |
| [Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/) | :heavy_check_mark: | :heavy_check_mark: |
| [Debian](https://docs.docker.com/engine/installation/linux/debian/) | | :heavy_check_mark: |
| [Red Hat Enterprise Linux](https://docs.docker.com/engine/installation/linux/rhel/) | :heavy_check_mark: |  |
| [CentOS](https://docs.docker.com/engine/installation/linux/centos/) | :heavy_check_mark: | :heavy_check_mark: |
| [Fedora](https://docs.docker.com/engine/installation/linux/fedora/) |  | :heavy_check_mark: |
| [Oracle Linux](https://docs.docker.com/engine/installation/linux/oracle/) | :heavy_check_mark: |  |
| [SUSE Linux Enterprise Server](https://docs.docker.com/engine/installation/linux/suse/) | :heavy_check_mark: |  |		 
| [Microsoft Windows Server 2016](https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-server) | :heavy_check_mark: |  |
| [Microsoft Windows 10](https://docs.docker.com/docker-for-windows/) |  | :heavy_check_mark: |
| [macOS](https://docs.docker.com/docker-for-mac/) |  | :heavy_check_mark: |
| [Microsoft Azure](https://docs.docker.com/docker-for-azure/) | :heavy_check_mark: | :heavy_check_mark: |	
| [Amazon Web Services](https://docs.docker.com/docker-for-aws/) | :heavy_check_mark: | :heavy_check_mark: |

untuk penjelasan setup Docker Cloud di Digital Ocean, Packet, atau SoftLink dapat dilihat [disini](https://docs.docker.com/engine/installation/#on-docker-cloud)

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
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

Setelah itu tambahkan Official Docker GPG key:

```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Cek apakah fingerprint key sesuai dengan 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88

```sh
sudo apt-key fingerprint 0EBFCD88
```
lalu tambah kan repository untuk download versi Stable
```sh
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### Install Docker

update index apt 
```sh
sudo apt-get update
```
setelah itu install versi CE

```sh
sudo apt-get install docker-ce
```

jika menginginkan versi Docker CE tertentu dapat dilakukan command dibawah untuk melihat versi Docker CE yang sesuai dengan versi Ubuntu anda 
```sh
apt-cache madison docker-ce
```

lalu install sesuai dengan versi yang ada
```sh
sudo apt-get install docker-ce=<VERSION>
```

untuk informasi dalam instalasi Docker dengan versi Edge ataupun versi Docker EE dapat mengunjungi [Link berikut](https://docs.docker.com/engine/installation/linux/ubuntu/)

### Checklist
- [x] Introduction
- [x] Variant Docker
- [x] Cara Install Docker CE versi Stable (Ubuntu 16.04)
- [ ] Cara Build docker
- [ ] Command Penting di Docker
