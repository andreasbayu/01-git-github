# Tugas MDPL Praktik

***

Daftar isi :

1. [Install GIT](#install-git)
2. [Konfigurasi GIT](#konfigurasi-git)
3. [Mengelola Repositori](#mengelola-repositori)
    - [Mengelola repositori di akun sendiri](#mengelola-repositori-di-akun-sendiri)
    - [Mengelola repositori di organisasi](#mengelola-repositori-di-organisasi)

***

## Install Git

Pemasangan [Git](https://git-scm.com/) pada linux sangat mudah karena hanya menggunakan paket manager sesuai distribusi yang digunakan. dan git sendiri umumnya sudah tersedia di Linux.

```shell
# pacman -S git
```

![install-git](images/1/install-git.png)

Ketikkan perintah berikut untuk mengetahui versi dari git yang terinstall.

```shell
$ git --version
git version 2.33.0 
```

***

## Konfigurasi GIT

Sebelum mengguanakan git sebaiknya melakukan 2 konfigurasi username dan email, dengan menggunakan perintah berikut ini :

```shell
$ git config --global user.name "username"
$ git config --global user.email emailkamu@domain.tld
```

Pastikan username dan email untuk memasukkan username dan email yang sama dengan github yang digunakan.dan gunakan perintah dibawah ini untuk melihat configurasinya.

```shell
$ git config --list
user.email=emailkamu@domain.tld
user.user=username
user.name=username
init.defaultbranch=main
credential.helper=wincred
```

***

## Mengelola Repositori

### Personal access token

Mulai 13 Agustus 2021, penggunakan token merupakan hal wajib ubtuk semua akses ke github yang memerlukan otentikasi. Sehingga perlu membuat personal access token. dapat melihat pada link berikut : <https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token>

### Mengelola repositori di akun sendiri

#### Membuat Repository

1. Langkah pertama yang dilakukkan adalah membuat repositori baru
klik tanda + dibagian pojok kanan atas, lalu pilih **New repository**.

    ![1](images/3/1.png)

2. isikan nama repositori, deskripsi (opsional), dan lisensi (bila diperlukan), dan repositori dapat dibuat public maupun private.

    ![1](images/3/2.png)

3. klik tombol **Create repository**

#### Clone Repository

Clone repositori adalah cara ubtuk menduplikasi ropositori kita yang berada digithub ke komputer lokal. caranya dengan menggunakan perintah berikut ini `$ git clone https://alamatrepo.git`.

![1](images/3/3.png)

Setelah melakukan clone di komputer lokal kita dapat melakukan perubahan maupun penambahan yang nantinya dapat dipush ke github.

#### Mengubah - Push tanpa branching dan merging

perubahan terjadi karena :

1. Ada file atau direktori yang dihapus
2. Isi File berubah, atau file diedit
3. Ada File atau direktori baru

![4](images/3/4.png)

Ketika menabahkan file `README.md` dan memasukan text otomatis telah terjadi perubahan kita perlu untuk melakukan perintah `$ git add -A` untuk memasukan file mana saja yang akan dicommit, setelah itu kita perlu melakukan commit dengan perintah `$ git commit -m "pesan"` barulah melakukan push dengan perintah `$ git push origin branch`.

#### Mengubah isi dengan branching dan merging

Dengan cara ini ketika akan melakukan perubahan, perubajhan itu dilakukan di komuter lokal dengan membuat branch yang nantinya akan digunakan untuk menampung perubahan - perubahan. Dan nantinya branch itu akan di merge dengan branch utama biasanya bernama master atau main.

![5](images/3/5.png)

Pertama buat branch baru lalu buka file `README.md` kemudian isikan text, dan untuk memastikan kita berada di branch baru ketik perintah `$ git status`, lalu lakukkan commit, setelah itu kita dapat berindah ke branch utama, dan kita dapat melakkan push di branch baru yang kita buat.

Lalu kirim pull request.

![6](images/3/6.png)

Kemudian klik `Merge pull request`.

![7](images/3/7.png)

Dan Setelah itu lakukan merge di komputer lokal.

![8](images/3/8.png)

#### Sinkronisasi

Bila kita melakukkan perubahan di komputer lain kita perlu melakukkan sinkronisasi pada komputer lainnya. Dengan perintah berikut :

```shell
$ git pull
```

#### Membatalkan Perubahan

![9](images/3/9.png)

Pertama buat branch baru lalu ubah atau tambahkan sebuah text di README.md pindah ke branch utama lalu hapus branch yang baru dibuat. terlihat meskipun branch telah dihapus tetapi riwayat pengeditan masih ada, yang perlu kita lakukkan adalah menggunakan perintah berikut `$ git reset --hard` dan riwayat pengeditan telah hilang sepenuhnya.

#### Undo commit terakhir

![10](images/3/10.png)

![11](images/3/11.png)

Pada gambar diatas dicontohkan pada saat kita mengubah README.md dan melakukan commit. dan setelah itu kita dapat mengembalikan pada commit sebelumnya dengan perintah dibawah ini

```shell
$ git revert HEAD
```

![12](images/3/12.png)

![13](images/3/13.png)

Setelah itu dapat di push ke repositori github.

![14](images/3/14.png)

Jika sudah melakukkan commit, tetapi belum dipush ke repo github, cara membalkannya dengan perintah `$ get reset --hard HEAD^` seperti pada contoh berikut ini :

![15](images/3/15.png)

Dapat terlihat perbahan yang dilakukkan pada file `README.md` sudah tidak ada lagi.

Cara Untuk kembali ke perubahaan yang sudah lama dapat juga dengan perintah git revert namun pada argumen ke 3 diganti dengan posisi terakhir, `$ git revert <posisi>`, dan kemudian edit file secara manual baru dapat dipush.

![16](images/3/16.png)
![17](images/3/17.png)

Dan setelah itu, terlihat pada file README.md muncul tambahan pesan, pesan tersebut memudahkan kita untuk mengeditnya. setelah merubahnya kita dapat melakukkan commit.

![18](images/3/18.png)

Edit file tersebut dan simpan.

![19](images/3/19.png)

langkah berikutnya adalah mengetikkan perintah `$ git revert --continue`.

![20](images/3/20.png)

### Mengelola repositori di organisasi

Repositori dapat kita buat diakun kita maupun berada di organisasi. Organisasi dapat kita buat sendiri juga bila dimasukkan menjadi anggota organisasi. Perbedaan pada saat membuat diakun sendiri adalah pada bagian Owner, Owner dari repositori yang kita buat adalah organisasi.

![21](images/3/21.png)

***