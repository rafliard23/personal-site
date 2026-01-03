---
title: "Custom Remote Vehicle Operation device"
date: 2024-08-26T14:45:24+07:00
lastmod:
tags: [Electrics, Hardware, Embedded Systems]
categories: [Posts, Projects]
slug: rfr_RC
thumbnailLink: "https://media.rafliard.net/content/projects/remoteOperationVehicle/remoteOp-featured.webp"
summary: "Desain Perangkat Custom dengan memanfaatkan jalur CAN bus dan Controller STM32"
draft: false
excludeFromSearch: true
---

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada halaman ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}

Proyek ini merupakan task yang diberikan kepada saya ketika intern di PT TMMIN (Toyota Motor Manufacturing Indonesia). Secara tidak langsung pada proyek ini sebagai Embedded System Design Engineer karena melakukan pembuatan device dengan tahapan mendekati tahap mass-production dari planning Tujuan device hingga tahapan troubleshooting post-PCBA dan perbaikan program Embedded untuk penyempurnaan software dan hardware.

Proyek ini start pada pekan ke-2 Maret 2024 hingga pekan ke-2 Mei 2024 karena pekan ke-3 Februari 2024 hingga pekan ke-1 Maret 2024 masih di isi Training yang wajib diikuti, serta diskusi internal untuk penentuan hal-hal yang perlu dikerjakan seperti tujuan, fitur yang perlu diimplementasikan, skema implementasi dan approval untuk pengerjaan.

## Goal

Tanpa membahas tujuan internal, untuk proyek ini bertujuan untuk menciptakan device yang mampu berkomunikasi dengan kendaraan untuk mengembangkan teknologi Telematics Remote Operation dengan ranah implementasi saat ini Remote Engine Start/Stop serta Remote Door Lock/Unlock.

## Planning

Tahapan planning kami menyetujui untuk di sisa pekan Februari hingga pekan ke-2 Maret digunakan untuk studi mengenai wiring mobil, prototip yang telah dikembangkan sebelumnya.

## Reconnaissance/Studi

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada bagian ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}

Studi dilakukan dengan melakukan benchmark terhadap fitur yang dimiliki kompetitor, selanjutnya dari informasi ini kami bedah dan disesuaikan dengan kebutuhan per masing-masing riset grup. Untuk riset grup Remote Operation Vehicle kami memiliki target untuk merealisasikan fitur Remote Engine start/stop, dan Remote Door Lock/Unlock. Untuk progres terakhir yang dilakukan oleh tim Telematics grup Remote Operation telah membuat prototip dengan menggunakan modul kontroler STM32F103 "Bluepill". Selanjutnya pada tahap ini saya diperintahkan untuk mencoba melihat demonstrasi prototip ini kemudian memberikan masukan untuk pengembangan selanjutnya dari prototip.

## Programming dengan prototip yang telah ada

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada bagian ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}

Program mikrokontroller menggunakan HAL STM32 dengan mikrokontroler prototip yang telah ada menggunakan modul Bluepill (STM32F103C8T6). Pengembangan yang dilakukan yakni merubah perilaku penekanan fungsi relay, selanjutnya akan diujicobakan fungsi Remote Start/Stop, dan Remote Door Lock/Unlock. Fitur kontrol power window tidak memungkinkan diimplementasi/dikontrol oleh mikrokontroler karena arus yang lewat dikontrol melebihi dari standar relay mini 5V yang digunakan sehingga beresiko untuk dilewatkan melalui PCB.

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/awal/remoteOp-protoCCAwal.webp" class="grid-w50 md:grid-w33 xl:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/awal/remoteOp-beginning.webp" class="grid-w50 md:grid-w33 xl:grid-w33" />
{{< /gallery >}}

## Benchmark Produk Lain untuk PCB

Pada bagian studi dan recon saya juga diberikan referensi Universal Keyless Entry + Remote Control module sebagai acuan pengembangan device. Secara harga setelah pasca-produksi kalkulasi, device yang saya kembangkan hanya berharga ~35% dari harga produk yang dibeli ini (bahan benchmark). Untuk dimensi yang saya kembangkan saya memiliki target pribadi agar dimensi tidak lebih besar (worst case dengan dimensi yang mirip) dengan modul yang dibeli ini.

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/benchmark_device_market/remoteOp-overall.webp" class="grid-w33 md:grid-w33 xl:grid-w15" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/benchmark_device_market/remoteOp-closeup_relay1.webp" class="grid-w33 md:grid-w33 xl:grid-w15" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/benchmark_device_market/remoteOp-closeup_kontroler.webp" class="grid-w33 md:grid-w33 xl:grid-w15" />
  
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/benchmark_device_market/remoteOp-closeup_relay2.webp" class="grid-w50 md:grid-w50 xl:grid-w20" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/benchmark_device_market/remoteOp-closeup_relay_driver.webp" class="grid-w50 md:grid-w50 xl:grid-w20" />
{{< /gallery >}}

## Perancangan device dari tahapan pemilihan komponen, skematik!

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada bagian ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}

Untuk skematik saya mendesain dari awal minimum system kontroler kemudian bergerak ke arah kebutuhan Power Stage (regulator 12V kemudian ke 5V dan 3.3V), lalu kebutuhan umum seperti SWD Interface, Serial Interface, Bluetooth Serial, dan yang terakhir untuk bagian Input/Output.

## Layout PCB, Double Layer & Fabrikasi Profesional!

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada bagian ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}

Desain PCB menggunakan Double Layer untuk mempermudah pendesainan serta mempermudah grounding, komponen mayoritas menggunakan SMT, dan untuk fabrikasi menggunakan fabrikasi lokal namun standar nya cukup baik (mampu mengerjakan trace hingga 0.154mm). Beberapa komponen saya "siapkan" untuk _future provisining_ jika dibutuhkan, misalnya pada pin Molex 2x7 yang masih tersisa 2 untuk peningkatan desain kedepannya nantinya, serta footprint modul CAN Transceiver sehingga board ini bisa digunakan untuk berkomunikasi dengan traffic CAN bus. PCB di cetak di Gerai Cerdas yang saya rasa hasil cetaknya benar-benar bagus dan cocok jika tidak ingin mencetak di China untuk rapid prototyping.

{{< figure
    src="https://media.rafliard.net/content/projects/remoteOperationVehicle/pcb_layout/remoteOp-TMMIN_PCBLayout.webp"
    alt="PCB Layout"
    caption="Layout PCB"
    class="grid-w66 xl:grid-w50"
    >}}

## PCB Assembly & Troubleshooting

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Informasi yang tertulis pada bagian ini telah dibatasi sesuai dengan perjanjian NDA yang telah disetujui.
{{< /alert >}}
<br>
{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/pcba/remoteOp-pcba1.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/pcba/remoteOp-pcb_casing_base.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/remoteOperationVehicle/pcba/remoteOp-pcba2.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
{{< /gallery >}}

Untuk assembly PCB masih menggunakan penyolderan manual (bukan Hotplate), assembly dilakukan dari komponen-komponen terkecil kemudian progresif dengan komponen besar untuk memudahkan pengerjaan soldering.

Proses troubleshooting yang pertama dengan mencoba respon apakah program dapat terdownload ke dalam STM32, setelah berhasil kemudian mencoba test debug LED onboard serta tes respon output Relay satu per satu. Jika input/output test telah berhasil maka dilanjutkan dengan mendownload program yang telah dibuat ke dalam board. Setelah memastikan logic bekerja dan tidak ada yang salah, board di test pada kendaraan.