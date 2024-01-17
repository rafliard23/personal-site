---
title: "Laptop Cooler"
date: 2023-01-28T12:40:11+07:00
lastmod:
tags: [Electrics, Mechanics, Analog System]
categories: [Projects]
slug: laptop_cooler
thumbnailLink: "https://drive.google.com/uc?export=view&id=1UogA-AM5PKEhE3lN3kbGRDNCq2IeIwsM"
draft: false
---

Jika kita ingin memaksimalkan performa dari laptop, hal yang perlu diperhatikan untuk mencapai hasil yang optimal adalah mengimbangi pendinginan dari sistem laptop yang kita gunakan. Pendinginan laptop memiliki dua faktor yakni internal dan eksternal. 

## Faktor Internal
Faktor internal berupa hal-hal yang berhubungan langsung dengan model yang saat ini kita punya, seperti casing dari laptop, lubang ventilasi laptop, konfigurasi sistem pendinginan (heatsink) yang ada di dalam laptop, algoritma *power draw* CPU laptop, lama waktu dari terakhir kali dilakukan penggantian thermal paste/thermal pad, dan umur laptop.

## Faktor Eksternal
Faktor eksternal berupa hal-hal yang ada diluar kendali dari model laptop yang kita gunakan, seperti suhu lingkungan kerja, penempatan laptop, cara penggunaan laptop, dan alat bantu eksternal.

Jika kita berbicara mengenai alat bantu eksternal ada dua opsi yang paling efisien dan teruji, yang pertama adalah penggunaan Laptop stand. Kemudian opsi kedua adalah penambahan kipas eksternal untuk rekayasa sirkulasi udara yang ada disekitar laptop.

## Laptop Stand

{{< figure
    src="https://drive.google.com/uc?export=view&id=19gqvwlaB_muSo_VhFSLWh3g-iYZGfRUN"
    alt="Laptop Stand Mediatech"
    caption="Salah satu Laptop Stand yang dijual di pasaran Indonesia"
    >}}

Laptop Stand adalah sebuah alat yang digunakan untuk menaikkan posisi laptop dengan tujuan agar posisi monitor dari laptop sebanding dengan ketinggian bidang pandang dari mata kita ketika menggunakan pada suatu permukaan (contoh, meja). Penggunaan Laptop Stand membantu meringankan leher tegang dan mengurangi resiko nyeri leher jika kita menggunakan laptop dalam jangka waktu yang lama.

Secara tidak langsung Laptop Stand juga meningkatkan sirkulasi udara yang masuk kedalam laptop jika ventilasi masuk (*inlet*) dari laptop ada di bawah. Karena posisi dari laptop yang berada di atas permukaan dan lubang-lubang ventilasi mendapati sirkulasi yang lebih bebas, akhirnya membuat pendinginan menjadi lebih efisien (bahkan bisa turun mencapai 10-20° pada kasus tertentu) meskipun pasif karena tidak ada elemen aktif untuk memaksa sirkulasi lebih baik.

## Laptop Cooler

{{< figure
    src="https://drive.google.com/uc?export=view&id=1MD6bFKAwufrsFvgcZOk1nAh5-k8NdmSe"
    alt="Laptop Cooler Coolermaster"
    caption="Laptop Cooler Notepal X3 dari Coolermaster"
    >}}

Laptop Cooler adalah alat yang dikhususkan untuk membantu pendinginan laptop dengan tambahan kipas yang ada dibagian bawah. Umumnya Laptop cooler ini memiliki kipas dengan jumlah satu hingga lima dengan ukuran kipas dari 60mm hingga 140mm. Performa pendinginan dari Laptop Cooler bervariasi, untuk memaksimalkan hasil diperlukan jarak antara lubang ventilasi dengan posisi kipas agar sirkulasi yang di dorong oleh kipas merata dan tidak terlalu sempit.

## Planning Desain

Karena saya ingin membuat (hampir) keseluruhan dari project ini secara mandiri, maka seluruh tahapan disketsa terlebih dahulu untuk mematangkan rencana manufaktur, mulai dari sisi mekanik, dan sisi elektronik. Dari sisi mekanik akan tercipta laptop stand yang mampu menopang hingga ukuran 15.6" (berdasarkan dimensi ukuran laptop ASUS TUF FX505 Tahun 2019) dengan proses manufaktur berbasis 3D Print. File STL dari desain akan saya bagikan atau bisa cek melalui link Grabcad yang nantinya saya bagikan dibawah halaman ini.

Untuk bagian dari elektronik, saya membuat rangkaian pengatur kecepatan kipas berbasis rangkaian Timer 555 yang memberikan sinyal PWM. Desain rangkaian elektronik dikhususkan untuk kipas model 3PIN JST (bukan yang menggunakan connector Molex ataupun 4PIN PWM). Desain juga akan saya bagikan dibawah halaman ini.

### Desain Mekanik

Desain mekanik saya buat sesederhana mungkin namun memperhatikan aspek struktural dan praktikal karena saya utamakan agar dapat dicetak menggunakan 3D Printer Ender-3. Proses pencetakan menggunakan filamen PLA, dan hingga saat ini (sejak Februari 2023), kondisi hasil cetak masih kuat dan bagus.

{{< figure
    src="https://drive.google.com/uc?export=view&id=1-rVLW5xyAtQ6vs7VK0JENr4apUkyhIHm"
    alt="Desain Laptop Stand DIY"
    caption="Desain Laptop Stand"
    >}}

Untuk pemasangan kipas, ditambahkan part dari akrilik untuk tempat pemasangan kipas.

{{< figure
    src="https://drive.google.com/uc?export=view&id=1UogA-AM5PKEhE3lN3kbGRDNCq2IeIwsM"
    alt="Fan Bracket Fitting"
    caption="Desain Laptop Stand dengan pemasangan kipas 2x120mm"
    >}}

### Desain Rangkaian Elektronik

Rangkaian berbasis Timer 555 yang memberikan output PWM kepada gate Mosfet sebagai kontrol kecepatan, karena saya menggunakan kipas 3PIN JST yang pin 3 nya adalah output "Tachometer" dari unit kipas, maka pengontrolan kecepatan langsung saya lakukan melalui input power dari kipas, sehingga daya yang diberikan kekipas berupa variabel bukan konstan 12VDC. Keputusan penggunaan timer 555 karena fungsinya yang simpel, cukup untuk keperluan pengontrolan kecepatan, serta murah dan banyak beredar dipasaran Indonesia. Untuk detail mengenai komponen yang digunakan, bisa dicek melalui tautan yang dilampirkan dibawah halaman.

{{< figure
    src="https://drive.google.com/uc?export=view&id=1QCVAxF6I3goQcQML_ykSMplRkWGkSTYS"
    alt="Skematik Rangkaian KiCAD"
    caption="Skematik rangkaian kontrol kecepatan kipas"
    >}}

{{< figure
    src="https://drive.google.com/uc?export=view&id=1dK_Y-Hq2b75y4AkHdGNwtIiBcSEAP_U8"
    alt="Layout Trace PCB"
    caption="Layout PCB kontroler kipas"
    >}}

Untuk informasi lebih lanjut dari PCB yang saya buat, bisa mengunjungi repositori Github dibawah ini:

{{< github repo="rafliard23/laptopCooler-hardware" >}}

### Perakitan Komponen Elektrik.

{{< figure
    src="https://drive.google.com/uc?export=view&id=1O2o7vAPcuv3ZFhv5hh7A4G8vM8POIEcJ"
    alt="Skematik Rangkaian KiCAD"
    caption="PCB yang telah dirakit"
    >}}

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Perhatikan K3 ketika proses menyolder.
{{< /alert >}}

Karena PCB didesain dengan komponen THT, penyolderan mudah untuk dilakukan tanpa memerlukan alat solder khusus. PCB kompatibel dengan layout single layer (dengan menambahkan beberapa jumper) maupun double layer. Utamakan menyolder komponen THT kecil terlebih dahulu untuk memudahkan penyolderan komponen-komponen besar seperti DC Barrel Jack, DIP8 socket, Mosfet, dan Potensio.


### Uji Penggunaan

Untuk penggunaan hanya sebagai Laptop Stand, hasil cetak 3D menggunakan filamen PLA dengan merk SUNLU menunjukkan hasil yang ok, sejak penggunaan dari bulan Februari tidak ditemui deformasi maupun struktur yang rusak dari penyangga yang terbuat dari hasil cetak 3D ini.

Untuk penggunaan dilengkapi kipas fan, hasil bacaan dengan software HWiNFO menunjukkan hasil dengan rata-rata suhu turun hingga 10-15° yang darinya sekitar 80° mampu turun ke 70-68°. Kecepatan kipas dapat diatur dengan memutar knob potensio yang tersolder pada board PCB. Karena pada implementasi yang saya gunakan memakai kipas bermerk Zalman 12VDC 2x0.16A untuk penggunaan kecepatan full (100%), secara teori daya yang digunakan *hanya* sebesar 3.84 Watt atau mendekati 4 Watt, jika kita menjalankan dengna kecepatan yang lebih rendah tentunya daya yang digunakan juga lebih kecil, sehingga bisa dikategorikan sebagai hemat daya (bagi saya) dengan pertimbangan karena sistem yang kita jalankan adalah kipas aktif untuk laptop. Penggunaan kipas juga mempengaruhi adapter yang kita gunakan. Karena secara penggunaan daya saya mengetahui bahwa tidak akan melewati 12VDC 1A, maka saya cukup membeli adapter 12V 1A, jika diinginkan menggunakan kipas yang lebih kencang (misal menggunakan kipas Delta), maka pemilihan adapter untuk suplai daya perlu diperhatikan.  

## Kesimpulan/Penutup

Penggunaan Laptop Stand atau Laptop Cooler merupakan salah satu metode untuk meningkatkan performa pendinginan dari laptop, meskipun mampu menurunkan suhu kerja laptop, patut diperhatikan juga sisi maintenance laptop karena setiap 1 atau 2 tahun disarankan untuk dilakukan pembersihan laptop serta repaste ulang CPU (dan GPU jika laptop memiliki GPU terpisah dari CPU), selain dapat mengembalikan performa pendinginan laptop, maintenance ini dapat memperpanjang umur laptop karena menurunkan resiko overheat ketika digunakan.

Meskipun kita dapat membuat Laptop Stand dan Laptop Cooler secara mandiri, hal yang patut diperhatikan disini adalah faktor kepraktisan dari alat. Untuk pengguna biasa yang tidak memiliki waktu untuk merancang dan membuat tentu lebih baik untuk membeli produk jadi, tentu mungkin *agak* mahal namun harga tersebut sudah termasuk dengan nilai praktis dari pengguna yang tidak perlu repot-repot untuk mengatasi masalah. Nilai lebih dari pembuatan alat sendiri adalah faktor kualitas yang dapat kita tentukan sendiri (karena kitalah yang mengatur kualitas itu), dan dapat memungkinkan untuk dilakukan upgrade/peningkatan komponen secara mandiri tanpa perlu merubah keseluruhan alat, seperti contoh saya ingin mengganti kipas Zalman menjadi merk Noctua yang memiliki efisiensi dan Airflow yang lebih tinggi.

Referensi:<br>
https://www.build-electronic-circuits.com/555-pwm-circuit/<br>
https://www.electronics-tutorials.ws/waveforms/555_timer.html