---
title: "3-Axis CNC Plasma Cutting"
date: 2022-02-16T11:59:25+07:00
lastmod:
tags: [Electrics, Hardware]
categories: [Posts, Projects]
slug: "CNCPlasma"
thumbnailLink: "https://media.rafliard.net/content/projects/3axisCNC/cncp_cncplasma_machine.webp"
summary: "Proyek ini merupakan salah satu proyek Kerja Praktik saya di CV. Karya Brawijaya. Kami merangkai sistem kontrol _Torch High Control_ (THC) pada mesin CNC Plasma berbasis Mach 3"
draft: false
excludeFromSearch: false
---

Proyek merupakan salah satu proyek ketika saya melakukan Kerja Praktik di CV. Karya Brawijaya. Dalam proyek ini, saya dibantu dengan rekan-rekan satu kelompok untuk membuat mesin CNC Plasma cutting menggunakan bahan-bahan yang telah ada di lokasi bengkel workshop pada saat itu. Untuk kebutuhan mekanik (Desain, serta perwujudan benda) telah direalisasikan sehingga untuk pengerjaan kami adalah rewiring komponen, memrogram komponen dengan Mach 3 (pada komputer), serta penyetelan parameter untuk skema kontrol open loop motor servo.

{{< figure
    src="https://media.rafliard.net/content/projects/3axisCNC/cncp_cncplasma_machine.webp"
    alt="Frame Mesin CNC"
    caption="Rangka Mesin CNC yang akan digunakan."
    class="w-half"
    >}}

Untuk pengerjaan yang saya lakukan, saya mengecek kelayakan komponen yang akan digunakan, karena "Mesin" CNC ini dibuat dengan alat dan bahan yang ada pada waktu itu, konfigurasi aktuator yang digunakan juga bisa dibilang unik karena motor stepper yang digunakan adalah motor stepper ukuran Nema 17 dengan masing-masing sumbu memiliki dua motor stepper untuk membagi beban.

{{< figure
    src="https://media.rafliard.net/content/projects/3axisCNC/cncp_comp_board.webp"
    alt="Breakout Board CNC"
    caption="Foto breakout board Mach3."
    >}}

Karena penggunaan program kendali proses CNC yang digunakan masih menggunakan Mach3, maka kami memerlukan untuk mencari komputer dengan port Paralel agar mesin CNC bisa dikendalikan langsung oleh komputer. Penggunaan komputer dengan port Paralel ini sangat penting karena kemampuan untuk Torch Height Control (THC) hanya dapat digunakan pada board dengan port Paralel, board CNC Mach3 yang menggunakan interface USB tidak dapat menggunakan fitur ini karena pada program kontroler bawaan board CNC Mach3 USB tidak diimplementasikan untuk Plasma cutting, hanya mampu untuk digunakan sebagai CNC Milling/Laser Cutting.

{{< figure
    src="https://media.rafliard.net/content/projects/3axisCNC/cncp_mach3_interface.webp"
    alt="Interface Mach3"
    caption="Tampilan interface program Mach3."
    >}}

Setelah selesai penyetelan kalibrasi motor stepper+driver terhadap program Mach3, kemudian dilakukan penyetelan Torch Height Control (THC) dengan membuat kontroler THC sendiri (berbasis Voltage divider dan ADC op-amp). Pembuatan kontrol THC ini menggunakan prinsip kondisi tegangan dari Torch ketika Torch menyala, Torch akan memiliki nilai tegangan threshold ketika tegangan ini melibihi ambang batas, maka Torch akan menempel pada pelat ketika proses pemotongan sheet metal, hal ini terjadi karena nilai tegangan tersebut dihasilkan dari beda potensial tegangan yang terjadi antara ujung Torch dengan sheet metal yang akan dipotong, sehingga perbedaan tegangan ini dapat digunakan sebagai referensi untuk kontrol ketinggian Torch ketika proses cutting sheet metal.

Berikut ini adalah demo dari mesin yang telah dikalibrasi dengan mencoba profil cutting sederhana

<iframe class="max-w-prose mb-20" src="https://drive.google.com/file/d/1O-ML7REfJu4DVBcBIwxg9Xn_motW99qD/preview" width="640" height="360" allow="autoplay" allowfullscreen></iframe>

<iframe class="max-w-prose mb-20" src="https://drive.google.com/file/d/1V_YkD3pN4nft3TI-xxOdbJmIunbJsdNo/preview" width="640" height="360" allow="autoplay" allowfullscreen></iframe>

