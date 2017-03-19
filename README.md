# Docker

## Introduction of Docker
Docker merupakan software container platform. sehingga memungkinkan developer tidak perlu di buat pusing dalam setting up environment dalam sebuah platform. pernah nggak sih kamu pilih-pilih system operasi kalo mau buat apps? misal, OS "a" ribet buat nginstall python harus pake software/install ini itulah sebelum bisa running syntax ini:

```python
print "Hello World!"
```

Masalah lainnya terjadi saat kamu bekerja dengan team, jadi kamu harus njelasin beberapa hal yang harus diinstall sebelum bisa running dengan mulus tanpa merah merah :sob: iya klo satu kali penjelasan, masalah lainnya terjadi saat ada 10 gelombang dalam meng-hire developer, dan kamu harus njelasin sebanyak 10 kali, bukankah seorang developer itu harus efektif dan efisien?

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
hai() # <= ini docker
```

Seperti yang dikatakan Solomon Hykes, CTO and founder of Docker
>Everyone is looking for a platform to build new apps, and the biggest problem they have is that these apps don’t run on a single computer from beginning to end. - Hykes

Kata Hykes, Developer mendapat masalah ketika code yang telah dibuat di komputer mereka sendiri, dan mencoba untuk menjalankannya ke komputer lain dengan system operasi, database, dan service yang berbeda. Membuat sebuah program/algoritma itu nggak semudah yang dibayangkan, masalah lain muncul saat akan melakukan testing atau menyiapkan versi Stable dari apps kita untuk berjalan di production.

> Now your app is supposed to span any number of machines, it’s supposed to continue running even if you swap out machines, as you go from your own servers to Amazon or Google Compute Engine. The biggest problem is how do I package my app so that it can be moved around from machine to machine?

yakk itu Pengenalan dalam Docker, untuk lebih lanjutnya bisa dibaca pada [link ini](https://www.docker.com/what-docker)

### Checklist
- [x] Introduction
- [ ] Cara Install docker
- [ ] Cara Build docker
- [ ] Command Penting di Docker
