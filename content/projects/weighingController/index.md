---
title: "Automatic Weighing Controller"
date: 2022-04-10T16:04:46+07:00
lastmod:
tags: [Automation, Electrics, Embedded System]
categories: [Projects]
slug: PenakarTepungTulang
thumbnailLink: "https://drive.google.com/uc?export=view&id=1VFEnuClZz7xtp1397IYXS08nnSF1oDW4"
draft: false
---

Perkembang teknologi di skala Global membawa dampak terhadap industri di segala sektor, agar tidak tertinggal dan untuk meningkatkan produktivitas Industri harus menyesuaikan dengan zaman untuk mencapai efisiensi yang lebih baik.

Di Industri 4.0 (atau bahkan di sejumlah bagian dari dunia yang transisi ke Industri 5.0) pengembangan lini produksi adalah sebuah keharusan. Berdasarkan pengalaman dari Kerja Praktik ketika dulu kuliah, saya mendapati beberapa dari teman saya (termasuk saya sendiri) mendapati proyek untuk merubah/mengadaptasi/membuat plant yang semula masih dikontrol secara analog, menjadi kontrol secara digital serta adanya perangkat kontroler.

Dulu ketika saya Kerja Praktik, saya mendapati 2 proyek di tempat Kerja Praktik CV. Karya Brawijaya yang bertempat di Kecamatan Dau, Kabupaten Malang. CV. Karya Brawijaya ini bergerak di bidang pembuatan berbagai macam mesin, dan alat untuk kebutuhan segala Perusahaan dari yang berukuran menengah hingga besar. CV. Karya Brawijaya ini juga sebagai salah satu pemasok mesin-mesin UMKM yang ada di sekitar Kabupaten Malang. Dalam periode saya melakukan Kerja Praktik, 2 Proyek ini yakni Pengerjaan Modifikasi Mesin CNC Milling menjadi CNC Plasma untuk Kebutuhan Pemotongan Plat, dan Proyek Mesin Penakar Tepung.

## Problem

Kelompok kami memutuskan untuk memilih mengerjakan mesin penakar tepung. Pengerjaan utama pada proyek ini adalah merancang logika sistem otomasi dari mesin penakar tepung yang nantinya akan diatur dengan Relay serta dikontrol menggunakan mikrokontroler. Untuk memudahkan penggunaan dan pengembangan kedepannya, kontroler yang digunakan berbasis AVR dengan framework Arduino karena pemrogramannya yang cukup membutuhkan IDE Arduino serta kabel USB, dan banyak mikrokontroler ATMega328p yang (pada waktu itu) masih murah untuk dibeli. Karena mesin ini digunakan untuk proses produksi dan dipakai dikondisi riil, dari koordinator lapangan mewajibkan untuk menggunakan modul teruji Industri untuk mengurangi resiko gagal dari sisi Hardware.

## Perancangan Sistem

Berdasarkan informasi sebelumnya, saya memutuskan untuk mengurangi komponen modul kelas hobbyist dan menggunakan komponen standar Industri agar didapatkan hasil yang teruji dan mengurangi debugging dari sisi modul komponen. Selanjutnya saya membagi kerja dengan 2 teman saya lainnya dalam satu kelompok, saya mengerjakan bagian elektrik, perancangan sistem, dan pemrograman kontroler. 2 teman lainnya membantu dalam wiring elektrik, dan desain mekanik.

### Desain Sistem

Untuk kontroler utama, saya memutuskan untuk menggunakan kontroler berbasis ATMega328p dengan pilihan board Arduino Uno, alasan saya memilih Uno karena board Uno memiliki regulator tegangan yang lebih baik dibandingkan dengan board Nano, perlu diingat juga karena kebanyakan board Arduino di Indonesia yang beredar terlebih untuk harga yang paling murah adalah board Clone, board Nano terkadang memiliki regulator tegangan yang tidak menentu bahkan ada yang memiliki regulator tegangan tanpa kapasitor yang bertujuan untuk memfilter noise (decoupling capacitor).

Obyektif dari plant yang perlu dikontrol adalah sebagai berikut:

1. Mengontrol kapan memulai proses penakaran tepung, berhentinya penakaran, kemudian menurunkan hasil takaran tepung kedalam kemasan.
2. Mengontrol jalannya konveyor belt yang membawa kemasan menuju dropper yang menurunkan hasil takaran, kemudian membawa kemasan yang terisi untuk dikemas.
3. Mengontrol logika dari proximity sensor untuk menentukan kapan konveyor berhenti.
4. Human Machine Interface (HMI) berupa layar sentuh berukuran 3.5” yang digunakan untuk mengontrol mesin penakar tepung.

Untuk komponen seperti Kontrol Timbangan Digital, Human Machine Interface (HMI), Proximity Sensor, kami menggunakan standar Industri untuk meminimalisir kesalahan komponen, untuk mengontrol relay tegangan tinggi dengan output dari Arduino Uno, kami menggunakan relay 5V 8 Channel. 

{{< drive
    src="1WAmZSL-V3r2tdTlRV7kpCyk39sxT5Xbd"
    alt="Komponen Automatic Weighing Controller"
    caption="Komponen yang digunakan untuk kendali dari Kontroler"
    >}}

+ Proximity Sensor digunakan sebagai input untuk mendeteksi keberadaan kemasan produk yang untuk diberhentikan tepat di bawah corong penakar dan ujung konveyor mendekati tempat pengemasan.
+ Load Cell digunakan sebagai input pengukuran takaran dari tepung tulang. Cara kerja dari sistem load cell ini seperti jembatan whetstone yang menghasilkan output dengan sinyal yang lemah. Agar dapat dibaca, maka sinyal tersebut perlu diperkuat dengan menggunakan op-amp atau modul ADC khusus seperti HX711.
+ Weighing Controller digunakan sebagai pengolah data dari load cell, penggunaan modul ini sesuai dengan standar industri untuk meminimalisir bug pada program, keandalan dan mempercepat pengembangan sistem. Weighing Controller dari MYPIN ini memiliki input empat kabel dari load cell, dan output dua alarm yang keduanya menunjukkan *threshold* dari penakaran. Alaram pertama akan menyala ketika penakaran mencapai *threshold* set pertama, alarm kedua akan menyala ketika penakaran mencapai ke *threshold* kedua.
+ Relay 5V 8 Channel dipergunakan sebagai penjembatan kontrol relay dari tegangan TTL (3.3V - 5V) ke tegangan induksi coil yang umum digunakan pada sebuah relay (seperti 12V, 24V, 220V).
+ Board Modul Arduino UNO sebagai kontroler dari sistem secara keseluruhan. kontroler ATMega328p pada board UNO digunakan untuk mengontrol logika serta urutan kerja sistem ketika sistem dijalankan pada mode Otomatis.
+ HMI menggunakan seri Nextion 3.5" Touchscreen Monitor berjenis Basic dengan protokol komuikasi Serial. Agar HMI bisa berinteraksi dengan sistem, dipergunakan komunikasi serial antara HMI dan Arduino UNO. 

Gambar dibawah ini menunjukkan wiring dari sistem dalam lingkup kontroler.

{{< drive
    src="1zjAJek4YruqoPBGEsKiDbH4hCt4ksV29"
    alt="Komponen Automatic Weighing Controller"
    caption="Wiring sistem lingkup kontroler"
    >}}

Pada output alarm dari Weighing Controller diberikan resistor Pull Down 10k dengan kondisi Alarm active high. Hal tersebut menjaga agar ketika proses booting, dari Arduino UNO tidak mempengaruhi sinyal dari output weighing Controller.

Untuk diagram kerja dari sistem penakar tepung bisa dilihat pada bagan dibawah ini:

{{< drive
    src="1ThzRMkr0zxNy6g5LJ4GAf0qLjEYspklk"
    alt="Flowchart Sistem"
    caption="Diagram kerja dari sistem"
    >}}

1. Untuk mode manual, ketika kita memilih mode manual, HMI akan menampilkan 3 tombol untuk masing-masing operasi; Penakar, Penuang, dan Konveyor. Untuk operasional harus runtut sesuai urutan sebagai mestinya operasional penakaran dan pengemasan.
2. Ketika ‘Penakar’ ditekan pada layar, program akan menjalankan operasi dengan menjalankan konveyor damenunggu referensi input Proximity sensor penakar. Ketika Proximity sensor penakar mendeteksi benda, maka konveyor akan mati dan dilanjutkan ke proses penakaran.
3. Pada proses penakaran, Pada kondisi pertama, ketika Alarm 1 dan Alarm 2 mati, Solenoid penakar akan membuka dan speed vibrator pada posisi HIGH atau cepat. Ketika Alarm 1 menyala, Solenoid penakar akan menutup dan speed vibrator pada posisi LOW atau lambat. Ketika Alarm 1 dan Alarm 2 menyala, vibrator akan mati, menghentikan proses penakaran. Disini sistem akan menunggu input dari operator.
4. Ketika proses penakaran selesai dan operator menekan tombol ‘Tuang’, sistem akan menjalankan proses penuangan hasil takaran kedalam kemasan yang ada pada konveyor. Proses akan berjalan hingga menunggu input dari operator untuk langkah selanjutnya.
5. Ketika proses penakaran, dan penuang selesai, dan operator menekan tombol ‘Konveyor’ sistem akan mengaktifkan konveyor untuk menggerakkan benda yang telah terisi dan kemudian akan terus aktif selama dari Proximity sensor penakar tidak mendeteksi benda.
6. Untuk mode otomatis, sama seperti mode manual hanya saja operator tidak perlu menekan tombol pada tiap proses, hanya perlu menekan ‘START’ atau ‘STOP’ untuk memulai atau mengakhiri proses

### Elektrik

Karena penggunaan kontroler Arduino Uno, saya kemudian mendesainkan PCB untuk membuka koneksi-koneksi pin digital dari ATMega328p ini. PCB saya desain dengan konsep “Plug n’ Play” untuk bagian kontroler sehingga ketika ada kerusakan pada kontroler, board Arduino Uno dapat langsung dicabut dari PCB Breakout Board diganti dengan board Arduino Uno yang baru. Untuk menghubungkan sinyal dari luar, saya menggunakan terminal screw untuk memudahkan pemasangan kabel.

{{< drive
    src="1KHDuowKv9eM48bdkpeD0zeXvVuEf2jHE"
    alt="Laptop Stand Mediatech"
    caption="Hasil pengerjaan desain PCB dan Elektrik"
    >}}

{{< github repo="rafliard23/kb-weighing-control-hardware" >}}

### Program Kontroler

Untuk program mikrokontroler dipergunakan framework IDE untuk memudahkan pembacaan program dan dukungan library. Komponen yang memerlukan library adalah monitor HMI yang berkomunikasi secara serial dan membutuhkan command set khusus agar dapat berinteraksi antara mikrokontroler dan monitor layar sentuh HMI. Untuk informasi lebih lanjut mengenai instruction set komunikasi serial HMI Nextion ini, bisa mengunjungi dokumentasi resmi dari Nextion:

{{< button href="https://nextion.tech/instruction-set/" target="_blank" >}} Nextion.tech {{< /button >}}

Karena pada waktu itu saya tidak menemukan library yang cocok, saya memutuskan untuk menggunakan basis library dari Nextion kemudian mengubah beberapa bagian agar cocok dengan kebutuhan komunikasi.

Karena sistem berjalan dengan GUI berasal dari HMI Nextion, maka untuk logika program juga memerlukan feedback dari sistem GUI agar tidak terjadi hilang sinkronisasi antara layar HMI dan logika sistem pada program kontroler Arduino UNO.

Pada tampilan HMI, ketika sehabis booting sistem, Operator akan diberikan menu dengan dua pilihan mode operasi, yakni Operasi Otomatis, dan Manual. Ketika dipilih proses Otomatis, maka sistem akan bekerja secara otomatis tanpa perlu input tambahan dari operator, di dalam opsi Otomatis ini, kita mendapati dua button, yakni "Start" dan "Stop" yang keduanya merupakan perintah untuk memulai dan menghentikan proses otomatis dari sistem. Untuk uraian logika dari sistem seperti pada Diagram Kerja yang sebelumnya telah disampaikan.

{{< github repo="rafliard23/kb-weighing-control" >}}


