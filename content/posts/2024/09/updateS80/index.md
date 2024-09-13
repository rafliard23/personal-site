---
title: "Update Repair Mouse S80 (Survive!)"
date: 2024-09-13T06:30:13+07:00
lastmod:
tags: [Casual, Computer]
categories: [Posts]
slug: repair_s80
thumbnailLink: "https://drive.google.com/uc?export=view&id=1zDNfWTyYNYoSGpL1b9LqL7XM8udjAppf"
draft: false
index: false
---

{{< lead >}}
Yep, faulty power switch is what it need to be fixed.
{{< /lead >}}

Pada tanggal 12 September karena ada waktu dan setup untuk soldering, akhirnya saya mencoba untuk melakukan repair dengan cara menjumper pad untuk menyamakan koneksi ketika posisi switch pada kondisi mode "Wired". Karena saya tidak memiliki _wire stripper_ sehingga langsung menggunakan kawat kecil (bukan enamel) sehingga kemungkinan terjadi short ada jika masking rusak. Sebelum melanjutkan artikel ini, konteks lebih lanjut dari postingan sebelumnya.

{{< button href="/posts/2024/08/rip_s80/" target="_blank" >}} RIP S80 {{< /button >}}
{{< article link="/posts/2024/08/rip_s80/" >}}

Dengan menghubungkan Pin paling kiri (1) dengan tengah-common (3), maka kita akan menghubungkan secara langsung posisi seperti mode wired untuk mouse dengan mem-bypass switch mode power (yang rusak). Jika koneksi tidak ada problem, maka board secara teori akan bekerja dalam mode wired. Setelah di solder, waktunya diujicoba...

![Attempt to fix](https://1drv.ms/i/s!AnSkAvS9diTVghQGAVxIT5uN89f1?embed=1&width=660 "Fix jumper menggunakan kawat.")

Setelah menghubungkan kabel konektor Type-C ke mouse akhirnya... Mouse kembali berfungsi normal dan bahkan bisa diprogram ulang pada aplikasi _driver_ mouse nya!
{{< gallery >}}
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVghLu-BIY2wn5EnFw?embed=1&width=720&height=1280" class="grid-w33 md:grid-w25" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVghMyg4GhbtkGSrEA?embed=1&width=720&height=1280" class="grid-w33 md:grid-w25" />
  <img src="https://1drv.ms/i/s!AnSkAvS9diTVghH_orkR-D3yXm8s?embed=1&width=720&height=1280" class="grid-w33 md:grid-w25" />
{{< /gallery >}}

Karena target kita untuk repair ini menggunakan mode Wired, akhirnya saya mencoba untuk menggunakan tanpa baterai Li-ion nya, dan ternyata board ini support tanpa adanya baterai (gambar kanan tanpa baterai), sehingga saya putuskan untuk melepas demi keamanan dan mengurangi beban mouse. Sebenernya saya bisa membelikan baterai baru tapi karena saya sudah cukup puas dengan hasil dan tidak ingin menambah kekompleksan rangkaian, akhirnya saya pakemkan untuk wired only. Oh dan juga setidaknya bisa dipakai untuk backup karena mouse nya memiliki sensor yang bagus (PMW3325) dan Switch, Encoder yang telah saya ganti (TTC Gold Switch 80M & TTC Gold Encoder).