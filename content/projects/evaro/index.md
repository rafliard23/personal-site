---
title: "EEPIS Versatile Cargo Aeroplane"
date: 2021-12-31T21:57:24+07:00
lastmod:
tags: [Electrics, Hardware]
categories: [Projects]
slug: evaro
thumbnailLink: "https://drive.google.com/uc?export=view&id=1P-DUEc6QyT4zjn734WHlQbyj8-NFKdlK"
draft: false
---

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21164&authkey=%21AFdN4ahMAbaz724&width=660"
    >}}

Proyek ini saya lakukan dulu ketika saya mengikuti kegiatan kemahasiswaan sewaktu kuliah, EEPIS Versatile Cargo Aeroplane (EVARO) merupakan pengembangan pesawat UAV yang dibuat pada tahun 2021 oleh tim EFRISA Subdivisi Airframe Innovation. Dalam subdivisi ini, kami berlima dengan rincian tiga orang sebagai kepala penanggung jawab pengembangan, dan dua orang sebagai kru yang membantu pengerjaan. Di sini saya bertugas untuk menghandle bagian hardware kelistrikan dari pesawat UAV, serta juga membantu dalam manufaktur, dan pemeliharaan bagian mekanik dari pesawat.

## Overview

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21168&authkey=%21AMe1vTtS-THKGNY&width=660"
    alt="Packaging Kit"
    caption="Salah satu hasil kit yang telah dirakit dengan kotak kemasan"
    >}}

EEPIS Versatile Cargo Aeroplane (EVARO) adalah wahana UAV yang dikembangkan dengan latar belakang sebuah wahana UAV logistik dipergunakan untuk mengangkut barang. Wahana UAV ini merupakan hasil dari perlombaan Kontes Robot Terbang Indonesia (KRTI) yang diselenggarakan pada tahun 2021 secara Online untuk kategori Techno Development sub divisi Airframe Innovation. Pada kategori ini, penjurian dilakukan berdasarkan hasil pengembangan teknologi pada bidang konfigurasi pesawat UAV, sistem wahana UAV, dan hal-hal terkait pengembangan struktur mekanikal pesawat.

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21163&authkey=%21ALdf5N5hs_hTSYw"
    alt=""
    caption="Salah satu gambar cetak dari plan wahana UAV EVARO"
    >}}

UAV EVARO memiliki spesifikasi wahana sebagai berikut:
+ Konfigurasi pesawat: Skyhunter Hybrid Tilt Rotor Hybrid
  + Klasifikasi: Hybrid VTOL
  + Bentuk sayap: V-Tail
  + Propulsi: 3 Motor; 2 Motor Hybrid, dan 1 Motor Fixed
+ Lebar sayap (Wingspan): 1400mm
+ Panjang pesawat (Length): 970mm
+ Beban Maksimal untuk Lepas Landas (MTOW): 3200g
+ Muatan maksimal: 500g
+ Material: Komposit dan PET

## Hardware Kelistrikan

Karena konfigurasi wahana yang membawa konsep Tilt rotor hybrid dipadukan dengan model Skyhunter tail boom tunggal, membuat wahana UAV ini bisa lebih efisien jika dibandingkan dengan basis model Quadplane yang menggunakan empat motor vertikal untuk take off, sedangkan pada konfigurasi yang dikembangkan ini menggunakan total tiga motor dengan satu motor vertikal tetap, dan dua motor tilt yang dapat berubah arah hadap antara menghadap ke atas ketika mode take off VTOL, dan menghadap ke depan ketika mode Cruise.

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21166&authkey=%21AL99vtHQQthnD8g&width=800&height=290"
    alt="EVARO Tilt Rotor"
    caption="Penggunaan motor servo pada motor Tilt"
    >}}

Karena konfigurasi ini memiliki dua tilt motor, penambahan komponen servo dipergunakan untuk mengatur orientasi dari dua motor tilt ini. Agar sistem tilt rotor kuat, dipergunakan motor servo dengan spesifikasi gearbox dalam yang mampu diberi beban 35kg (faktor safety), dalam pengujian penggunaan motor servo dengan spesifikasi gearbox rating 15kg sudah kuat. Pemasangan tilt motor pada motor servo diletakkan pada arm servo sehingga arah hadap dari motor sama dengan arah arm servo untuk mempermudah setelan kontrol pada Flight Control.

## Kendali Servo Tilt Rotor

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21167&authkey=%21ADOMbiBpwQPTvjo&width=800&height=576"
    alt="EVARO Tilt Rotor"
    caption="Mekanisme tilt rotor dengan tampilan Servo"
    >}}

Untuk mode terbang wahana UAV ini memiliki dua mode utama yakni mode VTOL ketika orientasi servo tilt menghadap ke arah atas **(B)**, dan mode Fixed Wing/Cruise ketika orientasi servo tilt menghadap ke arah depan **(A)**. Pergantian mode terbang ini dapat dikontrol melalui Ground Control Station (GCS) ketika terbang maupun pra-terbang. Mode VTOL dipergunakan ketika lepas landas dan mendarat, sedangkan mode Cruise digunakan ketika dilakukan penjelajahan. Pengembangan konfigurasi 3 Tilt motor hybrid ini karena pada tahun sebelumnya menggunakan konfigurasi Quadplane 4 Motor Vertikal + 1 Motor pusher, konfigurasi 3 Tilt motor hybrid ini lebih efisien karena penggunaan motor yang lebih sedikit.

Penggunaan tilt rotor hybrid ini membuat kami harus menggunakan tiga motor dengan spesifikasi yang identik untuk mendapatkan keseimbangan yang tepat serta propeller dengan ukuran yang sama. Ketiga motor yang terpasang pada wahana UAV ini menggunakan motor dengan jenis ukuran 2280 dengan pertimbangan thrust, ukuran, serta biaya. Selain tiga motor yang identik, untuk mengurangi resiko ketidakseimbangan, dipergunakan ESC yang identik juga dengan spesifikasi rating arus 60A.

Untuk informasi lebih lanjut, bisa melihat poster infografik dari hasil riset kami:
Berikut ini adalah poster infografik dari hasil tim PKM kami:
{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21165&authkey=%21AK6Br0H_LMFQ77I&width=720&height=1018"
    alt="Poster Riset"
    caption="Poster Riset KRTI 2021 TDA"
    >}}