---
title: "Rancang Bangun IoT Control untuk E-Boiler"
date: 2024-05-28T07:45:41+07:00
lastmod:
tags: [Automation, Electrics, Embedded Systems]
categories: [Projects]
slug:
thumbnailLink: ""
draft: true
---

Pada akhir bulan Desember 2023 kemarin saya mendapati proyek untuk membuat prototip kontrol IoT Boiler dengan memanfaatkan Blynk sebagai middleware IoT monitoring dan kontrol. Proyek ini cukup menarik karena kontrol menggunakan ESP32 secara langsung dengan output daya besar nya di kontrol melalui Relay dan SSR. Sekilas Boiler menggunakan Element Heater sebagai pemanas cairan yang dikontrol menggunakan SSR selanjutnya input SSR ini dikontrol menggunakan Transistor NPN Open drain dengan Base yang dihubungkan ke kaki GPIO ESP32, beberapa output lainnya seperti display LCD 20x4 yang digunakan sebagai tampilan lokal pada box panel, Relay module x4 untuk kebutuhan kontrol Pilot Lamp di box panel, Input Keypad digunakan sebagai navigasi display lokal serta input seting parameter, dan amplifier MAX6675 sebagai pengolah sensor Thermocouple type-K (sensor suhu). Untuk memudahkan integrasi antara ESP32 dan Input/Output saya merancang Custom PCB dan dilengkapi connector sehingga lebih plug-n-play.

## Background

Pengerjaan proyek ini merupakan permintaan dari klien yang ingin membangun Sistem kontrol IoT untuk pengembangan boiler oli di Kapal. Dalam proyek ini juga diberikan beberapa kondisi sebagai berikut:
1. Box panel telah sediakan oleh klien.
2. Pengerjaan rancang bangun sistem, pembuatan PCB, wiring system, serta pemrograman sepenuhnya diserahkan pengerjaannya kepada saya.
3. Untuk Boiler dibuat skala untuk menekan biaya.

## Role

Karena pada saat itu ada teman saya ada yang berminat untuk mengerjakan proyek akhirnya saya berikan Job ini dengan syarat saya tetap mengerjakan beberapa hal dan memantau proses. Sehingga task saya pada proyek ini sebagai berikut:
+ Memanage project.
+ Mengerjakan rancang bangun untuk wiring box panel serta model boiler yang dipakai.
+ Co-develop untuk PCB sistem dan fungsi program mikrokontroler ESP32.

Jika dalam persentase, pengerjaan saya berupa 70% dari sistem, sisanya berupa pemroograman kontrol yang diambil oleh teman saya Maliki.

## Rancang Bangun, dan Desain PCB Sistem

Untuk rancangan sistem menggunakan box panel yang diberikan, selanjutnya saya menggambarkan layout beberapa komponen di tampilan mock up box panel yang sekaligus bagian pintu box panel sebagai tampilan display dan kontrol offline Boiler.

### Layout Komponen pada Box Panel

![Panel Mock Up](src/IoTBoiler-mockUpPanel.webp "Box Panel Mock Up")

Bagian pintu dari box panel terdiri dari Keypad 4x4 yang berfungsi sebagai input, Display LCD 20x4 untuk menampilkan data status boiler dan setpoint, switch power, serta Pilot Lamp sebagai indikator status sistem ketika beroperasi. Karena sifat dari proyek ini yang berupa IoT, sistem mampu dikontrol secara daring beserta parameternya, parameter ini tersimpan dan tersinkron antara data di cloud dengan data yang ada di sistem offline.

### Controller dan Skema Wiring Komponen

![Controller and overall Wiring Scheme]( "Skema wiring")

Untuk sistem secara general menggunakan wiring campuran antara Custom PCB dan wiring instalasi. Untuk Custom PCB di desain bersama dengan kolaborasi menggunakan Git. Untuk memudahkan koneksi antara PCB dan beberapa modul yang digunakan, rangkaian memanfaatkan penggunaan konektor agar pemasangan kabel pada beberapa komponen bisa secara plug n' play dan meminimalisir terjadi salah pasang oleh user.

![PCB Design of Controller Portion](src/IoTBoiler-PCB-3DView.webp "Desain PCB dan Aktual PCB")

### _Mini_ Boiler

![Form of scaled boiler]("Boiler mini dengan menggunakan basis panci bakso")

Untuk model Boiler, karena diskala dan testing menggunakan oli yang tidak perlu volume banyak, maka untuk Boiler saya menggunakan Panci Bakso sebagai bentuk dasar untuk model boiler yang dipakai, kemudian saya modifikasi sedikit dengan membuatkan housing untuk pemasangan sensor Thermocouple dan Heater 800W yang nantinya akan dipakai untuk memanaskan liquid.

## Testing

Untuk bentuk testing kami melakukan serangkaian test statis untuk masing-masing fungsi seperti
+ Tes fungsional keypad
+ Tes fungsional display LCD
+ Tes fungsional pilot lamp & buzzer
+ Tes fungsional kontrol Heater
