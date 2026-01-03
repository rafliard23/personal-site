---
title: "Update Situs 2024/01/15"
date: 2024-01-16T15:55:58+07:00
lastmod:
tags: []
categories: [Posts]
slug: Update_Blog
thumbnailLink: "https://media.rafliard.net/content/posts/2024/01/16_UpdateBlog/UB_WatuJengger.webp"
draft: false
summary: "*Hello there!*, Perubahan kebijakan layanan Google Drive membuat Google Drive tidak bisa digunakan sebagai \"CDN\" lagi :/"
excludeFromSearch: true
---
*Hello there!*

Mungkin karena sedikit update di blog ini karena saya sedang sibuk untuk mempersiapkan kerja, jadi pada postingan ini saya ingin memberikan *sedikit* update tentang kondisi blog ini serta masalah dari Google yang menimpa pengguna Google Drive sebagai *CDN* mereka.

Oke, jadi kabar baiknya situs ini akan terus diupdate <ins>dan saya memiliki komitmen</ins> untuk menggunakan situs ini menjadi *catatan pribadi* saya. Sekian.

{{< figure
    src="https://media.rafliard.net/content/posts/2024/01/16_UpdateBlog/UB_driveIssue.webp"
    alt="Issue Tracker Google Drive"
    caption="Laporan bug yang diunggah pada halaman Issuetracker Google."
    >}}

Kabar buruknya (untuk saat ini), tepat pada 2024/01/11 00.00UTC, Google melakukan rolling update yang menyebabkan [akses tipe data embed menjadi tidak responsif dan menyebabkan gambar tidak muncul ketika diembed pada dokumen HTML.](https://issuetracker.google.com/issues/319531488?pli=1) Masalah ini tidak hanya saya saja yang mengalaminya, beberapa saya lihat mencapai hingga ratusan yang mengalami masalah serupa. Hingga kini per tanggal 2024/01/16 masih belum ada statement resmi dari Google terhadap permasalahan ini akan selesai. Karena saya *percaya* dengan Google, saya membiarkan untuk halaman-halaman sebelumnya menjadi demikian hingga menunggu langkah lebih lanjut Google. Saat ini saya menggunakan beberapa layanan sebagai backup CDN seperti Onedrive dan Storj. Dengan kondisi terakhir yang sepertinya Google hingga saat ini belum memberikan respons secara resmi, saya bisa pastikan bahwa masalah ini akan dibiarkan oleh google, [Justin Poehnelt mendokumentasikan temuannya dari masalah ini baik secara identifikasi, solusi dan batasan, saya merasa perlu menginvestasikan CDN dan Storage hosting untuk menyimpan foto jika ingin dalam jangka panjang aman](https://justin.poehnelt.com/posts/google-drive-embed-images-403/).

*Until next time!*

*Photo oleh Muhammad Rafli Ardiansyah; diambil pada 2018/10/20 di Watu Jengger Mojokerto*