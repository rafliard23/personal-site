---
title: "UAV Amfibi"
date: 2022-09-28T12:09:05+07:00
lastmod:
tags: [Computer Vision]
categories: [Projects]
slug:
thumbnailLink: "https://drive.google.com/uc?export=view&id=1rOvX_RuVM2R1qSpDaD5v4I8O_PY7zH5p"
draft: false
---

{{< figure
    src="https://lh3.googleusercontent.com/drive-viewer/AKGpihbmyKk_mELv4ZU7ofOPwCAXlTDZU3x9ksKQtCFomo2psOlwmmkwSDbxpl6e722GNgvx5vJURoO0XyYWzMTqT72DILkwpNAtqH8=s1600"
    >}}

Penggunaan teknologi video pada wahana UAV pemantau memiliki dampak yang terasa bagi tim SAR, karena dengan bantuan data (rekaman) video, wahana pemantau memiliki data yang lebih banyak jika dibandingkan menyurvei lokasi secara langsung dengan menggunakan kendaraan besar seperti mobil atau helikopter. Pada project ini kami memanfaatkan teknologi computer vision yang dipadu dengan wahana UAV yang telah kami kembangkan dengan beberapa modifikasi agar wahana UAV dapat landing pada permukaan air serta modifikasi airframe.

{{< button href="rafliard.xyz/projects/evaro/" target="_blank" >}} EVARO {{< /button >}}
{{< article link="/projects/evaro/" >}}

Project ini merupakan perwujudan lolos pendanaan dari aktivitas Program Kreaktivitas Mahasiswa (PKM) 2022 dengan satu tim berisikan empat anggota, pada tim ini, saya bertugas untuk mengimplementasikan Computer Vision pada komputer mini PC (Single board computer Raspberry Pi 3B) untuk mendeteksi korban dari input video kamera yang diletakkan menghadap ke arah bawah lambung pesawat.

Untuk implementasi vision, saya menggunakan basis YoloV3-tiny implementasi darknet. Karena Raspberry Pi 3B secara komputasi tidak mendukung untuk pemrosesan video yang cepat, saya menggunakan basis C++ dan dataset yolov3-tiny dan membatasi input resolusi untuk mode livestream (pemrosesan langsung melalui input video kamera) agar mendapatkan metrik FPS yang mendukung (~5-7 FPS).

{{< github repo="pjreddie/darknet" >}}

Sistem mini PC ini dapat digunakan dalam dua mode, mode pertama yakni pemrosesan video secara online (rekognisi obyek secara langsung), serta pemrosesan video secara offline (rekognisi obyek dilakukan secara terpisah). Untuk operasional disarankan untuk menggunakan mode offline agar penggunaan daya bisa mendapatkan hasil yang lebih baik.

Untuk flowchart kerja sistem dari pengindera citra, bisa dilihat pada gambar di bawah ini.
{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21131&authkey=!AFDEcT_98K6fXvk"
    alt="Diagram Sistem"
    caption="Flowchart simplifikasi kerja vision pada UAV Amfibi"
    >}}
Sistem akan booting dengan mengeksekusi program yang telah diset untuk running secara _headless_, input perangkat kamera sebagai pengambil data dari kamera yang menghadap kamera menunjukkan medan area, selanjutnya input akan di _pre-process_ sebagai input dari model algoritma YOLO, kemudian algoritma YOLO mengekstraksi informasi data yang relevan dengan parameter kelas yang ditentukan (obyek manusia/korban bencana) kemudian menyimpan informasi data tersebut mereferensikan lokasi titik GPS dari kontroler Pixhawk ketika pengambilan citra dilakukan. Hasil deteksi tersimpan pada media penyimpanan SD Card pada Raspberry Pi 3. Proses ini dilakukan berulang hingga kondisi terbang selesai atau suplai baterai sistem mini pc mencapai ambang batas bawah.

dibawah ini adalah hasil video dari uji coba yang telah kami lakukan. Karena keterbatasan waktu, kami hanya mengujicobakan wahana UAV di areal sekitar kampus.

Uji Statis:<iframe src="https://drive.google.com/file/d/1h1-m4DplsvcgpHVSnmM812SnqZ08IKCZ/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>
Uji Horizontal:<iframe src="https://drive.google.com/file/d/1j09x9fVix6wY8g5hmPhqTY33EhSPujMN/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>
Uji Vertikal:<iframe src="https://drive.google.com/file/d/1yDpbiVFlFkXGyZKOs61JnQa8b50IFTAy/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>

Berikut ini adalah poster infografik dari hasil tim PKM kami:
{{< drive
    src="https://lh3.googleusercontent.com/drive-viewer/AKGpihZPSCW3Vp5Q0WXsYo8z7Sj1L1R5ZVbgp9cVY64dJjJ9KHgWyr6ZNjUqhG8Cm8hlM7JNOH8fI1-KhLlhQfQiWkSnbMNV0yEOnJM=s1600"
    alt="Poster PKM"
    caption="Poster PKM Infografik"
    >}}