---
title: "Automatic Sprinkler Sprayer memakai Microcontroller (STM32)"
date: 2024-08-26T14:42:35+07:00
lastmod:
tags: [Automation, Electrics, Embedded Systems]
categories: [Projects]
slug: automatic_sprinkler
thumbnailLink: "https://drive.google.com/uc?export=view&id=1SdpEiI7gp73A63zyIJS_6mGndv-BA7vj"
draft: false
---

Proyek ini berlangsung antara Oktober 2023 hingga Desember 2023 namun pasca saya intern di Toyota, paman saya mengajak untuk melanjutkan kembali pengerjaan proyek ini karena demand yang cukup potensial untuk dikembangkan menjadi produk jadi, namun pada tahap 2 akan ada pengembangan di bagian ranah IoT dan Monitoring data. Untuk proyek asli kami menggunakan mikrokontroler STM32 sebagai basis mikrokontroler nya.

## Identifikasi Masalah

Ide pembuatan Automated Sprinkler Sprayer ini berawal dari paman saya yang ingin mengotomasikan penyiraman tanaman yang ada di taman depan rumah dan di tengah rumah. Kemudian saya menawarkan diri untuk membantu membuatkan solusi dengan cara membuat kontrol otomasi dari aksi yang ingin dilakukan dengan menggunakan kontroler. Selanjutnya kebutuhan elektrik dan hardware sebagian telah ada dan terpasang di rumah paman saya karena sebelumnya juga telah mencoba sendiri namun belum mendapatkan metode yang optimal.

Problem kedua adalah pengembangan kemampuan menggunakan STM32 karena dari paman saya bersikeras untuk menggunakan kontroler STM32 sebagai kontroler utama sistem otomasi ini, karena dari saya juga ingin mengembangkan skillset saya di kontroler STM32, maka saya mengiyakan.

## Planning

Selanjutnya pada tahapan planning saya mendesain untuk topologi hardware dan kontroler secara garis besar dari fitur yang telah ditentukan dan disetujui. Kemudian dari topologi hardware ini kita akan bergerak ke dalam pemrograman, perancangan (pemilihan) komponen, desain layout PCB (prototip), serta testing.

![Simplified Diagram Block Scheme](https://1drv.ms/i/s!AnSkAvS9diTVgVL-7dvdYpSyW9dg?embed=1&width=660 "Blok Diagram Sistem")

### Pemrograman

![Program's Flowchart](https://1drv.ms/i/s!AnSkAvS9diTVgVTxxEFnLpYq7jb3?embed=1&height=660 "Flowchart logic program")

Untuk logic program didesain untuk operasi otomatis dan tanpa perlu manual dari user, namun kondisi terakhir untuk power Pompa masih belum otomatis karena dari paman saya tidak menginginkan sistem yang lebih kompleks. Untuk implementasi menggunakan metode timer (terjadwal) untuk penyiraman kami sepakati untuk mengembangkan pada tahapan selanjutnya (Reboot Proyek saat ini). Pemrograman menggunakan framework HAL STM32 dari STElectronics.

### Perancangan (pemilihan komponen)

Pada tahapan ini, saya akan membahas terlebih dahulu komponen yang membuat proyek ini berhasil atau tidak.

#### Moisture Sensor

Moisture Sensor atau Sensor kelembapan tanah merupakan salah satu komponen terpenting dalam skema otomasi penyiraman karena untuk menentukan apakah tanah perlu disiram atau tidak kita menggunakan sensor kelembapan tanah ini. Masalah terbesar terutama untuk bekerja menggunakan sensor grade Hobbyist adalah keandalan sensor yang bervariasi baik yang sangat bagus dan akurat hingga sensor yang mudah rapuh sehingga bersifat _sekali pakai_. Hal tersebut kita temui pada jenis Sensor Kelembapan ini dengan banyak varian ditemukan di E-commerce Indonesia. Jika kita kelompokan, bisa kita bagi menjadi 4 jenis sensor kelembapan.

![Moisture Soil Sensor](https://1drv.ms/i/s!AnSkAvS9diTVgVUdySZREVWWC72g?embed=1&width=660 "Variasi sensor kelembapan tanah")

Berdasarkan pengalaman saya dulu pernah menggunakan sensor-sensor ini, Sensor kelembapan tipe (D). memiliki keandalan yang lebih baik dibandingkan jenis lainnya namun sensor jenis (D). ini juga perlu diberikan proteksi untuk menjaga bagian komponen elektronik (IC dan komponen pasif) agar tidak terkena air dan pengaruh suhu yang berlebih. Jenis (A). dan (B). memiliki bagian tembaga yang terekspos sehingga jelas tidak akan bertahan lama jika terkena air, udara dan suhu yang berubah-ubah. Sensor jenis (C). memiliki pembacaan yang tidak linar sehingga kurang cocok.

Jika pembaca memiliki waktu lebih, kalian bisa melihat video dari Andreas Spiess di bawah ini yang membahas sensor kelembapan tanah ini serta artikel yang dicantumkan di deskripsi video yang benar-benar membantu dalam penggunaan sensor dan mencapai keakuratan mendekati sensor linear.

{{< youtubeLite id="m0mcCtcViTY" label="[463] Why most Arduino Soil Moisture Sensors suck (incl. solution) - Andreas Spiess" >}}

#### Microcontroller

Untuk bagian mikrokontroller menggunakan STM32F103CXT6 (C6/C8 kompatibel), alasan menggunakan STM32 karena dari paman saya menginginkan program kontroler yang _aman_ dan _susah_ untuk dikopi, akhirnya dari saya mengikuti instruksi sekaligus untuk mengembangkan skillset saya menggunakan STM32 dengan HAL dari STElectronics.

#### LCD 16x02, Relay

LCD digunakan untuk display status berjalannya sistem, pada saat itu digunakan untuk menunjukkan relay ON atau OFF dan kelembapan tanah pada masing-masing sensor. Relay digunakan untuk mengaktuasi output beban yang dihubungkna dengan Relay karena Relay sendiri adalah _saklar_ elektronik yang bisa dikontrol melalui input sinyal tertentu (coil energize).

#### Power Adapter 5V

Karena saya ingin agar desain power lebih sederhana, saya memutuskan untuk mendesain PCB dengan power input 5V dan regulasi ke level 3.3V menggunakan regulator LDO AMS1117-3.3. Dengan menggunakan base input 5V kita tidak perlu DC-DC Switching regulator untuk menurunkan level tegangan karena jarak dari 3.3V ke 5V cukup untuklangsung menggunakan regulator LDO. Penggunaan basis 5V untuk menyalakan Relay 5V pada bagian VCC.

### Desain layout PCB (prototip)

![Schematics and PCB Layout](https://1drv.ms/i/s!AnSkAvS9diTVgVeclUovA5-4aT52?embed=1&width=1080 "Skematik dan layout PCB")

Untuk skematik saya membuat sendiri dengan KiCAD serta mempergunakan komponen-komponen yang telah ada (meminimalkan pembelian). Konektor Relay, LCD, Rotary Encoder, dan Sensor saya rancang pada PCB agar memudahkan instalasi dengan konsep "Plug n' Play" dan agar konektor tidak terbalik saya menggunakan konektor Molex dan JST XH. Untuk driver Relay saya menggunakan transistor NPN 2N2222 agar logic kembali ke Active High dalam aktuasi relay karena modul Relay yang dipakai memiliki aktuasi Active Low. Untuk input power saya menggunakan Jack DC untuk memudahkan input power tanpa perlu mengupas kabel sehingga lebih aman.

Untuk desain layout PCB saya menggunakan Single Layer karena keterbatasan fabrikasi PCB yang murah dan bisa cepat (saya mencetak di Surabaya dulu) dan tanpa menggunakan masking. Menurut saya beberapa hal bisa ditingkatkan lagi untuk pengembangan lebih lanjut seperti dengan menggunakan IC seperti ULN2003A (seperti yang saya pakai di Proyek Vehicle Remote Operation). Karena kita menggunakan komponen campuran SMT dan THT, maka board kita tidak ideal dan banyak tempat yang terbuang karena keterbatasan fabrikasi dan THT ini.

## Testing

![Testing Phase](https://1drv.ms/i/s!AnSkAvS9diTVgVieePiFUlmZcb6b?embed=1&width=660 "Fase Testing")


<iframe class="max-w-prose mb-20" src="https://drive.google.com/file/d/1QeUXbqRyoAKniZ0qwAhQPWqXwc2yQIl5/preview" width="660" height="371" allow="autoplay" allowfullscreen></iframe>

## Gallery

{{< gallery >}}
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgVxlKBDo-HB1_3gd?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgVqfFtQqbFiq0RhZ?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgV2gS0NfaBldflDU?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgV_OoWS5ZRG6ieds?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w25" />
  
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgV6-OI7PF-D9Kcm4?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgVuQISEe_S5G7P0Q?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVgWBrB87PiOE6dfMc?embed=1&width=1024" class="grid-w33 md:grid-w33 xl:grid-w33" />
{{< /gallery >}}