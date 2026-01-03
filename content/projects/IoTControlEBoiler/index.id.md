---
title: "Rancang Bangun IoT Control untuk E-Boiler"
date: 2024-05-28T07:45:41+07:00
lastmod:
tags: [Automation, Electrics, Mechanics, Embedded Systems]
categories: [Posts, Projects]
slug: e_boiler
thumbnailLink: "https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-plant.webp"
summary: "Boiler Elektronik yang dilengkapi kontrol, monitoring data secara Online dan Offline. Rangkaian elektronik terpadu antara arus lemah dan kuat."
draft: false
excludeFromSearch: true
---

Pada akhir bulan Desember 2023 kemarin saya mendapati proyek untuk membuat prototip kontrol IoT Boiler dengan memanfaatkan Blynk sebagai middleware IoT monitoring dan kontrol. Proyek ini cukup menarik karena kontrol menggunakan ESP32 secara langsung dengan output daya besar nya di kontrol melalui Relay dan SSR. Sekilas Boiler menggunakan Element Heater sebagai pemanas cairan yang dikontrol menggunakan SSR selanjutnya input SSR ini dikontrol menggunakan Transistor NPN Open drain dengan Base yang dihubungkan ke kaki GPIO ESP32, beberapa output lainnya seperti display LCD 20x4 yang digunakan sebagai tampilan lokal pada box panel, Relay module x4 untuk kebutuhan kontrol Pilot Lamp di box panel, Input Keypad digunakan sebagai navigasi display lokal serta input seting parameter, dan amplifier MAX6675 sebagai pengolah sensor Thermocouple type-K (sensor suhu). Untuk memudahkan integrasi antara ESP32 dan Input/Output saya merancang Custom PCB dan dilengkapi connector sehingga lebih plug-n-play.

## Background

Pengerjaan proyek ini merupakan permintaan dari klien yang ingin membangun Sistem kontrol IoT untuk pengembangan boiler oli di Kapal. Dalam proyek ini juga diberikan beberapa kondisi sebagai berikut:
1. Box panel telah sediakan oleh klien.
2. Pengerjaan rancang bangun sistem, pembuatan PCB, wiring system, serta pemrograman sepenuhnya diserahkan pengerjaannya kepada saya.
3. Untuk Boiler dibuat skala untuk menekan biaya.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-blockDiagramSystem.webp"
    alt="Simplified Diagram Block Scheme"
    caption="System Diagram"
    class="w-75 xl:grid-w50"
    >}}

## Role

Karena pada saat itu ada teman saya ada yang berminat untuk mengerjakan proyek akhirnya saya berikan Job ini dengan syarat saya tetap mengerjakan beberapa hal dan memantau proses. Sehingga task saya pada proyek ini sebagai berikut:
+ Memanage project.
+ Mengerjakan rancang bangun untuk wiring box panel serta model boiler yang dipakai.
+ Co-develop untuk PCB sistem dan fungsi program mikrokontroler ESP32.

Jika dalam persentase, pengerjaan saya berupa 70% dari sistem, sisanya berupa pemrograman kontrol yang diambil oleh teman saya Maliki.

## Rancang Bangun, dan Desain PCB Sistem

Untuk rancangan sistem menggunakan box panel yang diberikan, selanjutnya saya menggambarkan layout beberapa komponen di tampilan mock up box panel yang sekaligus bagian pintu box panel sebagai tampilan display dan kontrol offline Boiler.

### Layout Komponen pada Box Panel

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-mockUpPanel.webp"
    alt="Panel Mock Up"
    caption="Mock Up Panel Box"
    >}}

Bagian pintu dari box panel terdiri dari Keypad 4x4 yang berfungsi sebagai input, Display LCD 20x4 untuk menampilkan data status boiler dan setpoint, switch power, serta Pilot Lamp sebagai indikator status sistem ketika beroperasi. Karena sifat dari proyek ini yang berupa IoT, sistem mampu dikontrol secara daring beserta parameternya, parameter ini tersimpan dan tersinkron antara data di cloud dengan data yang ada di sistem offline.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-peletakanKomponen.webp"
    alt="Component Layout Box Panel"
    caption="Layout Komponen pada Box Panel"
    class="w-50"
    >}}

### Controller dan Skema Wiring Komponen

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-schematic.webp"
    alt="Controller and overall Wiring Scheme"
    caption="Schematic Wiring"
    class="w-75 xl:grid-w50"
    >}}

Untuk sistem secara general menggunakan wiring campuran antara Custom PCB dan wiring instalasi. Untuk Custom PCB di desain bersama dengan kolaborasi menggunakan Git. Untuk memudahkan koneksi antara PCB dan beberapa modul yang digunakan, rangkaian memanfaatkan penggunaan konektor agar pemasangan kabel pada beberapa komponen bisa secara plug n' play dan meminimalisir terjadi salah pasang oleh user.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-PCB-3DView.webp"
    alt="PCB Design of Controller Portion"
    caption="PCB design and fabricated PCB"
    class="xl:grid-w50"
    >}}

### _Mini_ Boiler

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-boiler.webp" class="grid-w25 md:grid-w25 xl:grid-w25" />
  <img src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-heaterSensor.webp" class="grid-w50 xl:grid-w50" />
{{< /gallery >}}

Untuk model Boiler, karena diskala dan testing menggunakan oli yang tidak perlu volume banyak, maka untuk Boiler saya menggunakan Panci Bakso sebagai bentuk dasar untuk model boiler yang dipakai, kemudian saya modifikasi sedikit dengan membuatkan housing untuk pemasangan sensor Thermocouple dan Heater 800W yang nantinya akan dipakai untuk memanaskan liquid. Bagian kotak merah adalah bagian dari Heater 800W AC dan bagian kotak hijau adalah sensor thermocouple untuk sensing Suhu.

### GUI

Tampilan GUI menggunakan program Blynk IoT untuk memudahkan pengembangan kontrol dan monitoring data tanpa perlu memrogram aplikasi di HP. Karena keterbatasan plan pricing, maka kami menggunakan tier layanan Gratis dengan batasan 5 Widget pada satu tampilan app widget.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-GUI.webp"
    alt="GUI Component"
    caption="GUI Blynk IoT"
    class="w-80"
    >}}