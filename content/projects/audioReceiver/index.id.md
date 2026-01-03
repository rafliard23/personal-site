---
title: "Universal Bluetooth Audio Receiver"
date: 2024-12-02T18:51:33+07:00
lastmod:
tags: [Electrics]
categories: [Posts, Projects]
slug:
thumbnailLink: "https://media.rafliard.net/content/projects/audioReceiver/ar-bts_asm_proto.webp"
summary: "Berawal dari Ide untuk membuat Universal adapter wired-to-wireless, akhirnya tercapai dengan fitur recharge-able dan konektivitas Bluetooth"
draft: false
---

Berawal dari ide untuk membuat universal wireless audio receiver ketika saya mengerjakan tugas akhir di kampus, akhir nya project ini saya kerjakan hampir dua tahun kemudian. Karena sifat nya yang lebih banyak menggunakan module dibandingkan perancangan dari awal (kecuali untuk casing), pendokumentasian project ini sebagai arsip dan mungkin bisa mendorong saya untuk masuk ke dalam dunia Elektronika pensinyalan audio.

## Pakai modul jadi lebih hemat daripada bikin sendiri, apa iya?

Dalam pikiran saya terlintas problem ini terutama bagi saya yang baru kali ini mencoba masuk ke dalam dunia Audio/Video analog sinyal. Demi menjaga timeline agar sesingkat mungkin, kepraktisan pembuatan device, dan menekan biaya (pertama kali), saya memutuskan untuk project ini dengan menggunakan module siap pakai sambil mempelajari module yang dipakai, audio skematik, dan protokol yang digunakan (BLE, aptx beserta temannya).

## Konsep device

{{< figure
    src="https://media.rafliard.net/content/projects/audioReceiver/ar-wiring.webp"
    alt="Device wiring"
    caption="Wiring Device"
    class="w-50"
    >}}

Device yang saya rakit ini bersifat portabel, universal, dan fungsional. Portabilitas dari device didukung dengan baterai Li-ion 3.7V 2.000 mAh yang digunakan sebagai power module ini dan juga sebagai power _mini amplifier_ jika hanya menggunakan port 3.5mm pada perangkat audio. Untuk mendukung fungsi baterai, device dilengkapi dengan module TP4056+DW01A sebagai BMS sekaligus charger controller baterai agar bisa diisi ulang tanpa perlu melepas assembly device. Universal yang dimaksud di sini dengan mengekspose port 3.5mm menyebabkan module bisa digunakan untuk mengadaptasi perangkat audio yang menggunakan input 3.5mm jack agar bisa menjadi _wireless_. Fungsional yang dimaksud dari device ini didesain untuk pemakaian sehari-hari, tanpa ada bug/kendala karena kondisi eksperimental device yang saya buat, jadi harus benar-benar kondisi nya layak untuk digunakan sehari-hari.

Untuk mendukung penampilan device, casing wajib dibuat agar menjadi lebih menarik dan presentable.

## Modul Wireless receiver Bluetooth yang cocok...

Setelah saya melakukan survei dari module Bluetooth receiver yang dijual di E-Commerce Indonesia, pilihan saya mengerucut antara 2 pilihan. VHM314 dan MH-M28. Alasan pilihan saya mengerucut ke dua modul tersebut salah satunya adalah port 3.5mm jack yang sudah ada sehingga tidak perlu repot membuatkan adapter 3.5mm jack dari jalur L dan R output modul board. Yang kedua adalah alasan performa. VHM314 dan MH-M28 (dan MH-MXX series) memiliki performa yang baik namun dari hasil yang saya coba untuk mendrive IEM KZ ZS3 saya, MH-M28 menghasilkan suara yang lebih baik dan cocok untuk profil basshead IEM KZ ZS3.

Berikut ini adalah tabel yang hasil perbandingan berdasarkan data yang saya olah dari internet yang mungkin bisa menjadi referensi bagi pembaca.  
| Fitur | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m18.webp "**MH-M18**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m28.webp "**MH-M28**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m38.webp "**MH-M38**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-vhm314.webp "**VHM314**") |
| :---: | :---: | :---: |  :---: | :---: |
| Power Supply | 5V, Battery | USB, 5V, Battery | USB, 5V, Battery | USB, 3.3V, Battery |
| 3.5mm Jack | ❌ | ✔ | ❌ | ✔ |
| Built-in Amplifier | ❌ | ❌ | (5W + 5W) | ❌ |
| Bluetooth Ver. | 4.2 | 4.2 | 4.2 | 5.0 |
| Button Interface | ✔ | ❌ | ❌ | ❌ |

Catatan penulis: Rata-rata modul wireless receiver Bluetooth dengan harga murah di pasaran menggunakan controller dari JieLi khusus nya pada seri seperti AC6XXXX. [Pengguna github ini menuliskan temuannya mengenai kontroler JieLi yang kerap kali ditemui pada perangkat TWS, Wireless Receiver modul yang dijual di pasaran terlebih jika dijual dengan harga murah.](https://github.com/christian-kramer/JieLi-AC690X-Familiarization) Kontroler dari JieLi ini juga bermacam-macam form factor nya, dari SOIC-16, SOIC-24, QSOP-24 hingga QFP ada. Jadi bisa saya pastikan modul seperti MH-M18, MH-M28, dan MH-M38 pasti menggunakan salah satu dari chip buatan JieLi ini [karena dari temuan pengguna github di atas menunjukkan bahwa module "MH-M18" menggunakan IC JieLi yang belum dihapus dan diganti marking nya.](https://camo.githubusercontent.com/be9dba30b418bb6ed952c691872ee4996a7216ba95a456335a171ce45cd1eb6e/68747470733a2f2f692e696d6775722e636f6d2f61783252695a502e706e67)


## Desain casing!

Untuk fabrikasi casing saya menggunakan proses 3D Printing untuk menekan biaya dan untuk memudahkan pengerjaan dari tahapan desain menuju realisasi. Casing saya desain sendiri dengan ukuran relatif kecil 64.80 mm x 54.80 mm x 27.00 mm sehingga cukup kecil dan tidak terlalu besar untuk dibawa ke mana-mana. Untuk meningkatkan kekuatan material, bisa menggunakan material seperti ABS dan PETG agar casing bisa lebih tahan terhadap suhu panas (outdoor).

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-design.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-render.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-render2.webp" class="grid-w25 md:grid-w33" />
{{< /gallery >}}

## Kekurangan yang saya rasakan

Dari hasil pengujian device yang saya buat, Ada beberapa poin yang perlu diperhatikan mengenai pengoperasian dan fungsionalitas device karena mungkin dari pembaca berpikir bahwa dengan "Universal" bisa bermakna berfungsi sebagai non speaker (Microphone). Berikut ini adalah poin-poin yang menarik dan sebagai batasan dari perangkat:
1. Sinyal audio hanya output, tidak bisa menerima sinyal input (baik Microphone, maupun tombol dari headset/headphone).
2. Jarak efektif antara perangkat yang terhubung dengan Bluetooth dengan Receiver maksimal 4 meter dari test yang saya lakukan untuk mempertahankan kualitas stream audio.
3. Untuk MH-M28, hasil suara yang dihasilkan tanpa adanya filter tambahan pada volume rendah memiliki noise statik sedang, namun ketika volume dinaikkan noise akan hilang.

## Kesimpulan

Bagi saya, membuat dan merakit device ini cukup asyik dan puas dengan hasilnya. Dari menggali informasi mengenai IC komponen Bluetooth receiver ini membuat saya sadar bahwa sebetulnya IC dari JieLi ini sangat luas digunakan pada perangkat-perangkat wireless murah. Saran saya bagi pembaca yang menginginkan kualitas atau kontrol yang lebih advance, lebih baik membeli komponen kontroler sendiri terutama sangat disarankan untuk membaca datasheet, menurut saya meskipun murah kualitas nya cukup baik namun memang jika di adu dengan kontroler wireless seperti dari Qualcomm pasti lebih baik kontroler Qualcomm karena banyak yang sudah mendukung protokol lebih baru seperti aptX dan juga pengembangan hardware di IC kontroler nya, memang kontroler dari Qualcomm jauh lebih mahal dari kontroler seperti JieLi ini yang bisa didapatkan dengan harga dibawah Rp. 30.000,- dalam bentuk modul siap pakai.

## Behind the Scene

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_solder.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_on.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_asm_proto.webp" class="grid-w25 md:grid-w33" />
{{< /gallery >}}

## Bacaan lebih lanjut
https://avdweb.nl/tech-tips/electronics/mh-m18-m28-m38-bluetooth-audio-receiver-amplifier-tear-down  
https://oshwlab.com/hichm/bleutooth-5-audio  
https://www.reddit.com/r/AC690X/  
https://kagaimiq.github.io/jielie/chips/chip-marks.html