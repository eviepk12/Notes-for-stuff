---
title   : Notes untuk Development Android dan Concepts
tags     : [Android, Fundamentals]
---

## Fundamental Concepts

- suffix .apk *(Android Package)* mempunyai semua `konten yang dibutuhkan untuk sebuah aplikasi android pada saat runtime atau dijalankan.
- suffix .aab *(App Bundle)* mempunyai semua konten **project** aplikasi android termasuk **metadata** yang tidak diperlukan pada saat runtime, digunakan sebagai format publishing dan tidak bisa diinstall pada android.

### Setiap aplikasi android tinggal pada sebuah box security tersendiri, yang dilindungi oleh beberapa fitur security berikut

1. Sistem android adalah **multi-user Linux system** yang berarti setiap aplikasi menjalankan user tersendiri.
2. Secara default, system android memberikan setiap aplikasi ID Linux user yang unik *(ID hanya digunakan oleh system dan tidak diketahui oleh aplikasi)*. Sistem memberi **security permission** pada semua file di aplikasi supaya hanya user ID yang sesuai hanya bisa mengakses file tersebut.
3. Setiap proses mempunyai VM *(Virtual Machine)* tersendiri supaya setiap aplikasi berjalan terpisah dari aplikasi lain.
4. Secara default, setiap aplikasi berjalan dengan Linux Process tersendiri. Sistem android menjalankan prosesnya disaat komponen aplikasi dijalankan, dan dimatikan saat proses tidak lagi dibutuhkan, atau saat sistem membutuhkan memorynya untuk aplikasi lain.

Sistem android mempunyai prinsip **The principle of least privilege**, yaitu setiap aplikasi **hanya** mempunyai akses kepada komponen yang dibutuhkan untuk berjalan dan tidak lagi.

### Tetapi ada beberapa cara untuk membagi data dengan aplikasi lain dan untuk aplikasi mengakses servis sistem

1. dua aplikasi bisa mempunyai Linux user ID yang sama, dimana mereka akan bisa mengakses file satu sama lain. Untuk menghemat resource system, aplikasi dengan user ID yang sama juga bisa dijalankan pada Linux Process dan VM yang sama, dan bahkan dengan certificate yang sama.
2. Sebuah aplikasi bisa meminta izin untuk mengakses data perangkat seperti lokasi, camera, koneksi bluetooth, dll. Tetapi user harus memberi izin explicit.

## App Components

*App Components* adalah dasar essential dari sebuah aplikasi android. Setiap komponen adalah titik masuk dimana system atau user bisa memasuki aplikasi.

### Ada empat jenis komponen aplikasi, yaitu

1. Activities
2. Services
3. Broadcast Receivers
4. Content Providers

### 1. Activity

*Activity* adalah sebuah titik masuk untuk interaksi dengan user. Merepresentasikan satu layar dengan UI. contoh :

 > Sebuah aplikasi email yang mempunyai satu activity yang menunjukan semua email baru, activity dua untuk membuat >email, activity tiga untuk membaca email. Walaupun semua activity bekerja bersama untuk membuat satu aplikasi >mereka tetap mandiri satu sama lain. Maka aplikasi lain bisa memulai activity di aplikasi email jika >diperbolehkan. Seperti aplikasi kamera bisa memulai activity di aplikasi email yang membuat email untuk memasuki > sebuah foto.

#### Sebuah **Activity** memfasilitasikan interaksi penting antara system dengan aplikasi

1. Melacak apa yang user sedang lakukan untuk memastikan sistem tetap menjalankan proses yang menghosting activity tersebut.
2. Mengetahui proses yang sudah dipakai berisi hal yang akan dikembalikan oleh user *(stopped activities)*, dan memprioritaskan untuk menjaga prosesnya.
3. Membantu aplikasi menangani prosesnya dimatikan supaya user bisa kembali ke activity dengan status sebelumnya dikembalikan.
4. Memberi cara untuk aplikasi untuk berjalan user antar satu sama lain, dan untuk system mengkoordinasikan perjalanannya dengan benar.

### 2. Services

*Service* adalah titk masuk umum yang digunakan untuk menjalankan aplikasi di belakang. Sebuah **Service** tidak mengasih UI, seperti sebuah servis aplikasi musik player akan tetap memainkan lagu jikapun aplikasinya sudah di tutup atau dikeluarkan.

#### Ada dua tipe *Service*

1. *Started Service* : memberi instruksi ke sistem untuk tetap menjalankannya sampai kerjanya selesai.
2. *Bound Service*  : berjalan karena aplikasi lain atau sistemnya sendiri membutuhkan service itu untuk berjalan yang membuat sebuah relasi yang dependant satu sama lain.

### 3. Broadcast Receivers
