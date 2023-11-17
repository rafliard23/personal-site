---
title: "Macropad RFR16E"
date: 2021-12-12T09:52:11+07:00
lastmod:
tags: [Mechanics, Electrics, Embedded System]
categories: [Projects]
slug: macropad_rfr16e
thumbnailLink: "https://drive.google.com/uc?export=view&id=1aU8lCN9cHqO3-I4rmVjUX_ktRh9ds7jH"
draft: false
---

Bagi kalian yang memiliki hobi Keyboard tentunya kalian mengenal Macropad. Macropad adalah sebuah keyboard yang memiliki layout umumnya lebih kecil dibandingkan dengan keyboard fungsional yang digunakan untuk mengetik dan seringkali digunakan sebagai tombol tambahan yang dapat diprogram. Jika kita jeli beberapa perangkat alat bantu yang dijual secara komersil sebenarnya hanyalah sebuah Macropad yang memiliki fungsi yang pakem. Contoh Stream Deck yang digunakan streamer, CAD Mouse; mouse yang digunakan dengan fungsi tambahan yang dapat digunakan pada software CAD.


{{< drive
    src="17KzrBzUDcvwal3V8YMciNHKxFQOTufLp"
    alt="Macropad Adafruit"
    caption="DIY kit Macropad buatan [Adafruit](https://learn.adafruit.com/adafruit-macropad-rp2040/featured_products)"
    >}}

Kemudahan akses informasi pada saat ini memungkinkan kita untuk membuat macropad sendiri, baik secara barebone yang terdiri dari komponen dan kabel, hingga yang lebih rapi menggunakan PCB. Dengan harga komponen mikrokontroler yang lebih murah, juga menjadi salah satu faktor yang membuat hobi atau membuat keyboard sendiri ini menjadi lebih banyak penggemarnya saat ini. Dari kontroler AVR ATMega (yang mendukung antarmuka USB HID), ESP32 (dengan USB HID atau melalui Bluetooth BLE), Raspberry Pi Pico (RP2040), hingga STM32, pilihan kontroler dan hardware yang digunakan beragam membuat hobi ini sangat fresh, baik dari sisi kepuasan entertain dan teknis nya.

## Latar Belakang

Alasan saya ingin membuat Macropad adalah saya ingin membuat programmable Macropad yang bisa saya atur sendiri dan tanpa terikat dengan software pihak ketiga yang _closed source_ serta meningkatkan workflow untuk beberapa program yang saya gunakan. Selain itu, pembuatan macropad ini saya gunakan sebagai tugas untuk proyek pendesainan Sistem Benam pada kuliah saya waktu Semester 5.

## Desain Sistem

Karena macropad ini juga saya masukkan sebagai tugas dalam perkuliahan, beberapa komponen yang saya gunakan memiliki beberapa alasan berdasarkan persyaratan dari project tugas mata kuliah. Salah satunya adalah batasan waktu.

### Pemilihan Kontroler

Karena pada saat itu saya hanya memiliki board F401 yang tidak digunakan (Board WeAct "BlackPill"), akhirnya saya memutuskan untuk menggunakan basis STM32 dengan seri F401. Pemilihan board ini menghadirkan masalah yang tidak terduga ketika saya memprogram board ini. Singkat cerita, board WeAct ini memiliki bootloader yang "proprietary" dari pihak WeAct, sehingga menutup salah satu metode untuk memprogram firmware macropad ke dalam board kontroler ini.

{{< drive
    src="1ONUYwiSR3ikX-HkJnQj1jDUJDvBgcDIy"
    alt="WeAct F401 Blackpill"
    caption="WeAct \"Blackpill\" F401CCU6. [Sumber](https://stm32-base.org/boards/STM32F411CEU6-WeAct-Black-Pill-V2.0)"
    >}}

Bagi pembaca terutama yang paham secara teknis, tentu menggunakan F401 untuk macropad sangatlah "overkill" namun pada waktu pembelian dulu, saya mendapati board ini dengan harga sekitar dibawah Rp. 50.000,- sehingga saya tidak perlu khawatir terhadap performa yang "terbuang" (mengingat pada saat itu juga dalam kondisi Chip Shortage). Selain itu, saya memilih board ini karena port USB nya sudah dilengkapi dengan Type C sehingga memudahkan untuk menghubungkan board dengan komputer atau laptop yang akan dipakai, sedangkan jika kita menggunakan basis board "Bluepill" atau Arduino Pro Micro, port USB nya masih menggunakan USB micro yang sudah mulai berkurang penggunaannya.

### Desain Board

{{< figure
    src="https://github.com/rafliard23/rfr16e-hardware/blob/main/img/schematic.jpg?raw=true"
    alt="Skematik Rangkaian Macropad"
    caption="Skematik Macropad RFR16E"
    >}}

{{< figure
    src="https://github.com/rafliard23/rfr16e-hardware/blob/main/img/board.jpg?raw=true"
    alt="Single Layer PCB"
    caption="Layout PCB Single Layer dari Macropad RFR16E"
    >}}

Karena sebagai tugas kuliah, saya mendesainkan board PCB agar tampilan akhir dari "produk" Macropad ini menjadi lebih rapi dan kompak. Karena secara desain dapat dibuat dengan single layer, saya memutuskan untuk mendesain board PCB dengan single layer. PCB ini saya desain dengan dua layout, layout pertama berupa full 16 Key switch, dan layout kedua 15 Key switch dan satu rotary encoder. Rotary Encoder ini sangat membantu sekali untuk kebutuhan saya karena dapat diprogram sebagai tombol pengatur volume, pengatur level zoom layar, atau fungsi serupa dalam sebuah proram. Hal yang wajib ketika kita mendesain Keyboard adalah perlunya dioda zener pada masing-masing Switch agar tidak menimbulkan efek "Ghosting" ketika menekan beberapa tombol secara bersamaan.


{{< figure
    src="https://golem.hu/pic/article/diodes/1N4148-diodes.jpg"
    alt="Dioda 1N4148"
    caption="Yup, komponen seharga Rp. 100,- ini membuat keyboard mekanikal mu anti ghosting. [Sumber](https://golem.hu/guide/diodes/)"
    >}}

Jika kalian melihat dari gambar board, mungkin ada yang mencari-cari LED, karena pada saat itu saya kurang memahami cara mendrive LED dengan QMK, saya tidak menambahkan fitur RGB backlight yang mungkin dapat membantu untuk kondisi kurang cahaya 🤣.

Untuk informasi selengkapnya mengenai hardware dari macropad ini, bisa melihat repositori github dibawah ini:

{{< github repo="rafliard23/rfr16e-hardware" >}}

### Pemrograman Firmware Board

{{< figure
    src="https://qmk.fm/assets/images/social.png"
    alt="QMK FM"
    caption="QMK Firmware, firmware open source yang seringkali digunakan oleh penggemar keyboard. [Sumber](https://qmk.fm/)"
    >}}

Untuk pembuatan firmware macropad, saya menggunakan QMK yang telah terbukti sebagai andalan bagi "Hobbyist" Mekanikal Keyboard di seluruh dunia, selain keyboard, QMK juga mendukung fungsi Mouse sehingga kita dapat membuat perangkat Mouse kita sendiri! Selain dari kalangan penggemar, beberapa keyboard mekanikal yang diproduksi secara massal juga ada yang mendukung QMK sehingga lebih memungkinkan bagi konsumen untuk mendapatkan fungsi yang lebih dari keyboard yang mereka beli, Nice!

Untuk memrogram board ini, kita perlu mendownload SDK nya terlebih dahulu dari repositori Github serta bagi kalian yang menggunakan Windows, perlu mendownload MSYS atau Cygwin untuk mengompile firmware di Windows.

Pada tahapan ini, kita memprogramkan layout, keymap yang ingin kita kehendaki serta memasukkan layout key matrix yang telah kita buat berdasarkan desain PCB yang dibuat sebelumnya. Untuk desain keymap secara fungsional, saya menambahkan 4 layer dengan masing-masing layer untuk beberapa program khusus, seperti Adobe Premiere, OBS Stream/Record, dan Fungsional Numpad.

Jika kita telah selesai menulis setelan firmware yang diperlukan untuk board, kemudian kita compile dan siap untuk memrogram. Namun tunggu dulu, ingat permasalahan terkait bootloader yang saya singgung sebelumnya? Yep. Jika anda menggunakan board WeAct ketika memasuki mode Bootloader STM32, anda akan disapa dengan Bootloader tambahan dari WeAct.

{{< drive
    src="1YpZt3gyg6Opwg7_ZVg-ZCw9Lvur9t9d1"
    alt="WeAct Bootloader"
    caption="Sepertinya tidak hanya saya yang menemui masalah ini..."
    >}}

Berdasarkan hasil pencarian dengan kata kunci "WeAct+Blackpill+F401+Bootloader" anda akan menemui banyak postingan forum yang menanyakan mengenai masalah bootloader dari WeAct yang "menyusup" ke tempat bootloader STM32. Untuk memasuki bootloader STM32, kita harus memaksa "masuk" ke dalam bootloader dengan menjumper beberapa pin ketika booting kontroler ini (Sayangnya dokumentasi yang saya miliki ketika mentroubleshooting ini telah hilang). Setelah kita berhasil memasuki bootloader STM32, kita kemudian kembali ke QMK CLI untuk melanjutkan memprogram board dengan firmware yang telah dibuat.

Untuk firmware yang telah saya buat untuk Macropad RFR16E ini bisa dilihat pada repositori Github dibawah ini:

{{< github repo="rafliard23/rfr16e" >}}

### Desain Casing dan Keycaps

Untuk desain casing, saya membuat keseluruhan dengan manufaktur 3D Print. Keycaps saya memesan dengan desain profil keycaps yang saya kirim (DSA profile). Untuk desain casing, bisa dilihat pada entri yang telah saya unggah pada [Grabcad](https://grabcad.com/library/macropad-rfr16e-1) saya.

{{< figure
    src="https://d2t1xqejof9utc.cloudfront.net/screenshots/pics/1cb96cf16ef20a944f6b2a06f5b082ee/original.jpg"
    alt="Case RFR16E"
    caption="Casing RFR16E Jadi"
    >}}

## Penutup

Menurut saya, project ini menarik bagi saya karena pertama kali saya menggunakan STM32 untuk keperluan penggunaan selain seperti perangkat kontrol (namun secara teknis keyboard juga termasuk perangkat kontrol). Meskipun biaya masuk untuk hobi ini beragam (tergantung kebutuhan) saya akui jika ingin mendapatkan hasil yang memuaskan perlu melihat budget terlebih dahulu agar kepuasan membangun keyboard tidak berat sebelah dengan biaya yang dikeluarkan😅

Kini dengan dukungan QMK yang hampir memiliki kompatibilitas yang universal dengan beberapa kontroler yang banyak dijumpai di pasar Indonesia, membuat saya ingin membuat keyboard lagi dengan kontroler lain, seperti RP2040, F103C8, ESP32 (Jika bisa wireless, kenapa tidak?).

Berikut ini adalah video yang saya buat untuk submission dari tugas ini

{{< youtube AKXApj0U3cg >}}